# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

Lightweight web UI for the upstream **Hermes Agent** (`NousResearch/hermes-agent`), localized for mainland China users. The default UI language is `zh` (`static/i18n.js`), and the README is in Chinese. This repo contains only the UI server — the actual agent (LLM clients, tools, MCP, cron jobs, etc.) lives in a separate `hermes-agent` checkout that the server discovers and imports at runtime.

## Run / develop

```bash
python3 bootstrap.py          # one-shot launcher: installs deps, finds agent, starts server, opens browser
./scripts/start.sh             # same, but --no-browser, sources .env first
python3 server.py              # bare server (assumes deps + agent already discoverable)
```

- Server listens on `http://127.0.0.1:8787` by default.
- Health: `GET /health` (used by `bootstrap.wait_for_health`).
- There is **no test suite, no linter config, no CI**. Don't invent commands; if you change behavior, exercise it in the browser.
- Runtime dependency for *this repo* is just `pyyaml`. Heavy deps (openai, anthropic SDKs, hermes-agent itself) live in the agent's venv. `bootstrap.py` will create a local `.venv/` only if the discovered Python lacks `yaml`.

## Architecture

### Two-process boundary: WebUI vs hermes-agent

`api/config.py` does multi-strategy discovery (`HERMES_WEBUI_AGENT_DIR` env → `$HERMES_HOME/hermes-agent` → sibling/parent of repo → `~/hermes-agent`) to find the agent checkout, then **appends it to the END of `sys.path`** (intentional — see the long comment in `config.py`; prepending breaks when `pip install --target .` was used inside the agent dir on a different platform). Once on `sys.path`, this codebase imports the agent directly: `from run_agent import AIAgent`, `from hermes_cli.models import list_available_providers`, `from tools.approval import ...`, `from tools.mcp_tool import discover_mcp_tools`, etc. **Many of these imports are wrapped in `try/except ImportError` with lambda fallbacks** so the UI still boots when the agent is missing — preserve that pattern when adding new agent integrations.

### Server shell

`server.py` is intentionally thin: a custom `QuietHTTPServer` (suppresses noisy `ConnectionResetError`/`BrokenPipeError`) plus a `Handler(BaseHTTPRequestHandler)` whose `do_GET`/`do_POST` delegate to `api.routes.handle_get` / `handle_post`. Logs are emitted as one-line JSON via `log_request`. Optional TLS is wired here (env vars `HERMES_WEBUI_TLS_CERT` / `HERMES_WEBUI_TLS_KEY`).

### Single-file router with co-located business logic

All ~80 HTTP routes live in `api/routes.py` as a flat `if parsed.path == "..."` chain inside `handle_get` / `handle_post`. This file is large (~2.5k lines) **on purpose** — adding a route means adding a clause here, not a new framework abstraction. Helpers it pulls in:

- `api/config.py` — env/path discovery, `cfg` (parsed `config.yaml`), settings I/O, `resolve_model_provider()` (the routing logic that decides whether a model string goes direct, via `@provider:model` hint, or through OpenRouter), `get_available_models()` (provider auto-detection with SSRF-guarded `/v1/models` fetch).
- `api/models.py` — `Session` class; sessions are JSON files under `SESSION_DIR` with an in-memory LRU (`SESSIONS`, capped at `SESSIONS_MAX=100`) and an `_index.json` for O(1) listing.
- `api/streaming.py` — runs the agent in a background thread per request and writes Server-Sent Events to a per-stream `queue.Queue` in `STREAMS`. `CANCEL_FLAGS` is checked cooperatively. **`_ENV_LOCK` serializes `os.environ` writes around `AIAgent` runs** because the agent reads provider keys from env, and two concurrent sessions targeting different providers must not interleave their save/restore.
- `api/auth.py` — optional password auth, off by default. Public paths whitelist (`PUBLIC_PATHS`); PBKDF2-HMAC-SHA256 password hash; HMAC-signed session cookie; in-memory rate limit on `/api/auth/login`. CSRF: POSTs check Origin/Referer in `routes._check_csrf`.
- `api/profiles.py` — wraps `hermes_cli.profiles`. Switching profile mutates `os.environ['HERMES_HOME']` **for the whole process** and monkey-patches cached paths inside hermes-agent modules. The base `~/.hermes` path is resolved from `HERMES_BASE_HOME` (not `HERMES_HOME`, which moves) — see the long comment in `_resolve_base_hermes_home`.
- `api/gateway_watcher.py` — daemon thread polling `<HERMES_HOME>/state.db` (SQLite) every 5s for telegram/discord/slack sessions, pushing diffs to subscribed SSE clients on `/api/sessions/gateway/stream`.
- `api/onboarding.py`, `api/upload.py`, `api/clarify.py`, `api/state_sync.py`, `api/updates.py`, `api/workspace.py`, `api/helpers.py` — single-purpose modules called from routes.

### Frontend

Plain JS + CSS in `static/`, **no build step, no framework, no bundler**. `static/index.html` loads each `*.js` and `*.css` directly (KaTeX and Prism are CDN). i18n: `static/i18n.js` defines `LOCALES = { en, zh, ... }`; UI strings use `data-i18n="key"` attributes; missing keys fall back to English. Default locale is `zh` and is enforced as the persisted setting default in `_SETTINGS_DEFAULTS` (`api/config.py`). The login page is server-rendered from a small string template in `routes.py` with localized strings in `_LOGIN_LOCALE` (currently `en` + `zh`).

### State layout (outside the repo)

```
~/.hermes/                    # base, resolved as $HERMES_BASE_HOME or ~/.hermes
├── webui/                    # $HERMES_WEBUI_STATE_DIR (default)
│   ├── sessions/             # one .json per chat session + _index.json
│   ├── settings.json         # UI settings (default model, theme, language, password_hash, ...)
│   ├── workspaces.json       # registered workspace dirs
│   ├── projects.json         # session groupings
│   └── .signing_key          # 32 bytes; chmod 600; auto-generated on first auth use
├── hermes-agent/             # the upstream agent checkout (one common location)
├── config.yaml               # per-profile, agent-side
├── auth.json                 # per-profile, agent-side
├── state.db                  # SQLite, per-profile, written by hermes-agent
└── profiles/<name>/...       # alternate profiles, same layout as the base
```

`bootstrap.py` uses `~/.hermes/webui` as its state dir; running `server.py` directly defaults to the same path via `HERMES_WEBUI_STATE_DIR`. The default workspace is the first writable of `$HERMES_WEBUI_DEFAULT_WORKSPACE`, `~/workspace`, `~/work`, then `STATE_DIR/workspace`.

## Conventions worth preserving

- **Never put state inside the repo.** Paths default under `$HOME` and are env-overridable. The repo dir should stay clean enough to `git pull` without conflicts.
- **Soft-degrade when the agent is missing.** Every agent import in `api/*` should keep a `try/except ImportError` fallback so the UI can still serve `/login`, `/health`, settings, and the onboarding wizard before the agent is installed.
- **Don't introduce a build step for the frontend.** Adding a bundler/framework is a much larger change than it looks — the static-file pattern is intentional.
- **Routes are flat string-equality matches, not regex/DSL.** Add a new clause; resist the urge to factor in a router library.
- **Settings keys are gated.** `save_settings` ignores anything not in `_SETTINGS_ALLOWED_KEYS` and validates enum/bool/language fields. Add new persisted settings to `_SETTINGS_DEFAULTS` *and* the appropriate validator set in `api/config.py`.
- **Anything writing to `os.environ` during a chat must hold `_ENV_LOCK`** (see `api/streaming.py`) — concurrent sessions otherwise corrupt each other's provider credentials.
