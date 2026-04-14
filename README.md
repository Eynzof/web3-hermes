> 原项目 bug 太多，本人正在推倒重构，可用关注下本项目，等我好消息

# Web3Hermes

> 可查看 `issue` 获取社群二维码

* 本项目仅做了汉化工作，其他代码没动，请留意原项目的最新进展及安全情况

Hermes-Agent 中文版 WebUI，便于中国用户使用。由 https://github.com/nesquena/hermes-webui 修改而来。

实现了从安装界面到使用的全过程汉化，默认语言设置为简体中文，修复大量翻译错误。


安装使用：

```bash
git clone https://github.com/Web3CZ/Web3Hermes.git hermes-webui
cd hermes-webui
python3 bootstrap.py
```

<img width="1919" height="1079" alt="微信图片_20260413155246_163_419" src="https://github.com/user-attachments/assets/8795774d-3168-47ab-b32a-313a4603d822" />



---

# Hermes Web UI

[Hermes Agent](https://hermes-agent.nousresearch.com/) 是一个先进的自主代理,运行在您的服务器上,可通过终端或消息应用访问,它会记住所学内容并随着运行时间变得更加强大。

Hermes WebUI 是一个轻量级、深色主题的 Web 应用界面,通过浏览器访问 [Hermes Agent](https://hermes-agent.nousresearch.com/)。与 CLI 体验完全对等 —— 您在终端中能做的所有操作,都可以在这个 UI 中完成。无需构建步骤、无需框架、无需打包器,只需 Python 和原生 JS。

布局采用三栏设计:左侧边栏用于会话和导航,中间用于聊天,右侧用于工作区文件浏览。模型、配置文件和工作区控制位于**编辑器底部栏** —— 编辑时始终可见。一个圆形上下文环可一目了然地显示 Token 使用量。所有设置和会话工具都在 **Hermes 控制中心**(侧边栏底部的启动器)中。

<img alt="Hermes Web UI — 三栏布局" width="1417" height="867" alt="image" src="https://github.com/user-attachments/assets/51adff98-53ee-4800-8508-78b6c34dd3dc" />

<table>
  <tr>
    <td width="50%" align="center">
      <img alt="浅色模式,完整配置文件支持" src="https://github.com/user-attachments/assets/9b68142f-d974-4493-a8d1-fd73e622c7fd" />
      <br /><sub>浅色模式,完整配置文件支持</sub>
    </td>
    <td width="50%" align="center">
      <img alt="自定义设置,配置密码" src="https://github.com/user-attachments/assets/941f3156-21e3-41fd-bcc8-f975d5000cb8" />
      <br /><sub>自定义设置,配置密码</sub>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td width="50%" align="center">
      <img alt="工作区文件浏览器,带内联预览" src="docs/images/ui-workspace.png" />
      <br /><sub>工作区文件浏览器,带内联预览</sub>
    </td>
    <td width="50%" align="center">
      <img alt="会话项目、标签和工具调用卡片" src="docs/images/ui-sessions.png" />
      <br /><sub>会话项目、标签和工具调用卡片</sub>
    </td>
  </tr>
</table>

这为您提供了与 Hermes CLI 几乎 **1:1 对等的便捷 Web UI** 体验,您可以通过 SSH 隧道安全地从 Hermes 设置中访问。只需一条命令即可启动,另一条命令建立 SSH 隧道即可在您的电脑上访问。Web UI 的每个部分都使用您现有的 Hermes 代理和现有模型,无需任何额外设置。

---

## 为什么选择 Hermes

大多数 AI 工具每次会话都会重置。它们不知道您是谁、您在做什么、或者您的项目遵循什么约定。每次都需要重新解释。

Hermes 在会话之间保持上下文,在您离线时运行定时任务,并随着运行时间增长对您的环境变得更智能。它使用您现有的 Hermes 代理设置、现有模型,无需额外配置即可启动。

它与其他代理工具的不同之处:

- **持久记忆** —— 用户配置文件、代理笔记和技能系统保存可复用的流程;Hermes 学习您的环境,无需重新学习
- **自托管调度** —— 离线时触发的定时任务,结果可发送到 Telegram、Discord、Slack、Signal、电子邮件等
- **10+ 消息平台** —— 终端中的同一代理可从手机访问
- **自我改进技能** —— Hermes 从经验中自动编写并保存自己的技能;无需浏览市场、无需安装插件
- **提供商无关** —— 支持 OpenAI、Anthropic、Google、DeepSeek、OpenRouter 等
- **编排其他代理** —— 可以派生 Claude Code 或 Codex 进行繁重的编码任务,并将结果带回自己的记忆中
- **自托管** —— 您的对话、您的记忆、您的硬件

**与其他产品对比** *(格局正在快速变化 —— 完整对比请参阅 [HERMES.md](HERMES.md))*:

| | OpenClaw | Claude Code | Codex CLI | OpenCode | Hermes |
|---|---|---|---|---|---|
| 持久记忆(自动) | 是 | 部分† | 部分 | 部分 | 是 |
| 定时任务(自托管) | 是 | 否‡ | 否 | 否 | 是 |
| 消息应用访问 | 是(15+ 平台) | 部分(Telegram/Discord 预览) | 否 | 否 | 是(10+) |
| Web UI(自托管) | 仅仪表盘 | 否 | 否 | 是 | 是 |
| 自我改进技能 | 部分 | 否 | 否 | 否 | 是 |
| Python / ML 生态 | 否(Node.js) | 否 | 否 | 否 | 是 |
| 提供商无关 | 是 | 否(仅 Claude) | 是 | 是 | 是 |
| 开源 | 是(MIT) | 否 | 是 | 是 | 是 |

† Claude Code 有 CLAUDE.md / MEMORY.md 项目上下文和滚动自动记忆,但没有完整的跨会话自动回忆  
‡ Claude Code 有云端管理的调度(Anthropic 基础设施)和会话范围的 `/loop`;无自托管 cron

**最接近的竞争对手是 OpenClaw** —— 两者都是始终在线、自托管、开源的代理,具有记忆、定时和消息功能。主要区别在于:Hermes 会自动编写并保存自己的技能作为核心行为(OpenClaw 的技能系统以社区市场为中心);Hermes 在更新之间更稳定(OpenClaw 有文档记录的版本回退问题,ClawHub 曾发生恶意技能安全事件);Hermes 原生运行在 Python 生态系统中。完整对比请参阅 [HERMES.md](HERMES.md)。

---

## 快速开始

运行仓库引导脚本:

```bash
git clone https://github.com/Web3CZ/Web3Hermes.git hermes-webui
cd hermes-webui
python3 bootstrap.py
```

或继续使用 shell 启动器:

```bash
./start.sh
```

引导脚本将会:

1. 检测 Hermes Agent,如果缺失则尝试官方安装器 (`curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash`)。
2. 查找或创建包含 WebUI 依赖的 Python 环境。
3. 启动 Web 服务器并等待 `/health`。
4. 除非传递 `--no-browser`,否则打开浏览器。
5. 进入 WebUI 内的首次运行向导。

> 目前不支持原生 Windows 引导。请使用 Linux、macOS 或 WSL2。

如果安装后提供商设置仍未完成,向导将引导您使用 `hermes model` 完成,而不是在浏览器中复制完整的 CLI 设置。

---

## Docker

**预构建镜像**(amd64 + arm64)在每次发布时推送到 GHCR:

确保 `HERMES_WEBUI_STATE_DIR`(默认 `~/.hermes/webui-mvp`,详见 `.env.example` 文件)文件夹存在,且所有者 UID/GID 与 `.hermes` 文件夹一致。容器还会挂载您配置的"workspace"(来自示例 .env.example)为 `/workspace`,根据需要调整位置。

```bash
docker pull ghcr.io/nesquena/hermes-webui:latest
docker run -d \
-e WANTED_UID=`id -u` -e WANTED_GID=`id -g` \
-v ~/.hermes:/home/hermeswebui/.hermes -e HERMES_WEBUI_STATE_DIR=/home/hermeswebui/.hermes/webui-mvp \
-v ~/workspace:/workspace \
-p 8787:8787 ghcr.io/nesquena/hermes-webui:latest
```

或使用 Docker Compose 运行(推荐):

```bash
# 查看 docker-compose.yml 并确保根据需要调整,至少 WANTED_UID/WANTED_GID
docker compose up -d
```

或本地构建:

```bash
docker build -t hermes-webui .
docker run -d \
-e WANTED_UID=`id -u` -e WANTED_GID=`id -g` \
-v ~/.hermes:/home/hermeswebui/.hermes -e HERMES_WEBUI_STATE_DIR=/home/hermeswebui/.hermes/webui-mvp \
-v ~/workspace:/workspace \
-p 8787:8787 hermes-webui
```

在浏览器中打开 http://localhost:8787。

启用密码保护:

```bash
docker run -d \
-e WANTED_UID=`id -u` -e WANTED_GID=`id -g` \
-v ~/.hermes:/home/hermeswebui/.hermes -e HERMES_WEBUI_STATE_DIR=/home/hermeswebui/.hermes/webui-mvp \
-v ~/workspace:/workspace \
-p 8787:8787 -e HERMES_WEBUI_PASSWORD=your-secret ghcr.io/nesquena/hermes-webui:latest
```

> **注意:** 默认情况下,Docker Compose 绑定到 `127.0.0.1`(仅本地)。
> 要在网络中暴露,请在 `docker-compose.yml` 中将端口改为 `"8787:8787"`
> 并设置 `HERMES_WEBUI_PASSWORD` 启用认证。

### 双容器设置(Agent + WebUI)

如果您在单独的 Docker 容器中运行 Hermes Agent,并希望在单独的容器中运行 WebUI:

```bash
docker compose -f docker-compose.two-container.yml up -d
```

这将启动两个共享卷的容器:

- **`hermes-home`** —— 共享 `~/.hermes` 用于配置、会话、技能、记忆
- **`hermes-agent-src`** —— 代理源代码,挂载到 WebUI 容器中,以便在启动时安装代理的 Python 依赖

WebUI 的初始化脚本在首次启动时自动将 hermes-agent 及其所有依赖(openai、anthropic 等)安装到自己的 Python 环境中。后续重启将重用已安装的包。

> **工作原理:** WebUI 直接导入 hermes-agent 的 Python 模块(不通过 HTTP)。共享卷使代理源代码可用,初始化脚本运行 `uv pip install` 设置依赖。两个容器共享同一个 `~/.hermes` 目录用于配置和状态。

完整配置请参阅 `docker-compose.two-container.yml`。

---

## start.sh 自动发现的内容

| 内容 | 发现方式 |
|---|---|
| Hermes 代理目录 | `HERMES_WEBUI_AGENT_DIR` 环境变量,然后 `~/.hermes/hermes-agent`,然后兄弟目录 `../hermes-agent` |
| Python 可执行文件 | 优先代理 venv,然后本仓库的 `.venv`,然后系统 `python3` |
| 状态目录 | `HERMES_WEBUI_STATE_DIR` 环境变量,然后 `~/.hermes/webui-mvp` |
| 默认工作区 | `HERMES_WEBUI_DEFAULT_WORKSPACE` 环境变量,然后 `~/workspace`,然后状态目录 |
| 端口 | `HERMES_WEBUI_PORT` 环境变量或第一个参数,默认 `8787` |

如果自动发现找到所有内容,则无需其他操作。

---

## 覆盖(仅在自动检测失败时需要)

```bash
export HERMES_WEBUI_AGENT_DIR=/path/to/hermes-agent
export HERMES_WEBUI_PYTHON=/path/to/python
export HERMES_WEBUI_PORT=9000
./start.sh
```

或内联:

```bash
HERMES_WEBUI_AGENT_DIR=/custom/path ./start.sh 9000
```

完整环境变量列表:

| 变量 | 默认值 | 描述 |
|---|---|---|
| `HERMES_WEBUI_AGENT_DIR` | 自动发现 | hermes-agent 检出路径 |
| `HERMES_WEBUI_PYTHON` | 自动发现 | Python 可执行文件 |
| `HERMES_WEBUI_HOST` | `127.0.0.1` | 绑定地址 |
| `HERMES_WEBUI_PORT` | `8787` | 端口 |
| `HERMES_WEBUI_STATE_DIR` | `~/.hermes/webui-mvp` | 会话和状态存储位置 |
| `HERMES_WEBUI_DEFAULT_WORKSPACE` | `~/workspace` | 默认工作区 |
| `HERMES_WEBUI_DEFAULT_MODEL` | `openai/gpt-5.4-mini` | 默认模型 |
| `HERMES_WEBUI_PASSWORD` | *(未设置)* | 设置以启用密码认证 |
| `HERMES_HOME` | `~/.hermes` | Hermes 状态基础目录(影响所有路径) |
| `HERMES_CONFIG_PATH` | `~/.hermes/config.yaml` | Hermes 配置文件路径 |

---

## 从远程机器访问

服务器默认绑定到 `127.0.0.1`(仅回环)。如果您在 VPS 或远程服务器上运行 Hermes,请从本地机器使用 SSH 隧道:

```bash
ssh -N -L <本地端口>:127.0.0.1:<远程端口> <用户>@<服务器地址>
```

示例:

```bash
ssh -N -L 8787:127.0.0.1:8787 user@your.server.com
```

然后在本地浏览器中打开 `http://localhost:8787`。

当检测到通过 SSH 运行时,`start.sh` 会自动打印此命令。

---

## 通过 Tailscale 在手机上访问

[Tailscale](https://tailscale.com) 是一个基于 WireGuard 构建的零配置 Mesh VPN。在您的服务器和手机上安装,它们将加入同一个私有网络 —— 无需端口转发、无需 SSH 隧道、无需公开暴露。

Hermes Web UI 完全响应式,具有针对移动端优化的布局(汉堡侧边栏、底部导航栏、触摸友好控件),因此非常适合作为手机上的日常代理界面。

**设置:**

1. 在服务器和 iPhone/Android 上安装 [Tailscale](https://tailscale.com/download)。
2. 启动 WebUI 监听所有接口并启用密码认证:

```bash
HERMES_WEBUI_HOST=0.0.0.0 HERMES_WEBUI_PASSWORD=your-secret ./start.sh
```

3. 在手机浏览器中打开 `http://<服务器-tailscale-ip>:8787`
   (在 Tailscale 应用中或服务器上运行 `tailscale ip -4` 查找服务器的 Tailscale IP)。

就这样。流量由 WireGuard 端到端加密,密码认证在应用层保护 UI。您可以将其添加到主屏幕以获得类似应用的体验。

> **提示:** 如果使用 Docker,在 `docker-compose.yml` 环境中设置 `HERMES_WEBUI_HOST=0.0.0.0`(已是默认值),并设置 `HERMES_WEBUI_PASSWORD`。

---

## 手动启动(不使用 start.sh)

如果您希望直接启动服务器:

```bash
cd /path/to/hermes-agent          # 或任何 sys.path 可以找到 Hermes 模块的位置
HERMES_WEBUI_PORT=8787 venv/bin/python /path/to/hermes-webui/server.py
```

注意:使用代理 venv 的 Python(或任何已安装 Hermes 代理依赖的 Python 环境)。系统 Python 将缺少 `openai`、`httpx` 等必需包。

健康检查:

```bash
curl http://127.0.0.1:8787/health
```

---

## 运行测试

测试动态发现仓库和 Hermes 代理 —— 无硬编码路径。

```bash
cd hermes-webui
pytest tests/ -v --timeout=60
```

或显式使用代理 venv:

```bash
/path/to/hermes-agent/venv/bin/python -m pytest tests/ -v
```

测试在端口 8788 上针对隔离服务器运行,使用单独的状态目录。生产数据和真实定时任务永远不会被触及。当前计数:51 个测试文件中的 **791 个测试**。

---

## 功能特性

### 聊天和代理
- 通过 SSE 流式响应(Token 在生成时即时显示)
- 多提供商模型支持 —— 任何 Hermes API 提供商(OpenAI、Anthropic、Google、DeepSeek、Nous Portal、OpenRouter、MiniMax、Z.AI);动态模型下拉菜单从配置的密钥中填充
- 在处理消息时发送新消息 —— 自动排队
- 内联编辑任何过去的用户消息并从该点重新生成
- 一键重试最后的助手响应
- 直接从编辑器底部栏取消正在运行的任务(发送按钮旁的停止按钮)
- 内联工具调用卡片 —— 每个显示工具名称、参数和结果片段;多工具轮次可展开/折叠全部切换
- 子代理委托卡片 —— 子代理活动以独特图标和缩进边框显示
- 内联 Mermaid 图表渲染(流程图、序列图、甘特图)
- 思考/推理显示 —— Claude 扩展思考和 o3 推理块的可折叠金色主题卡片
- 危险 shell 命令的审批卡片(允许一次/会话/始终/拒绝)
- SSE 在网络抖动时自动重连(SSH 隧道弹性)
- 文件附件在页面重载后保持
- 消息时间戳(每条消息旁显示 HH:MM,悬停显示完整日期)
- 代码块复制按钮,带"已复制!"反馈
- 通过 Prism.js 语法高亮(Python、JS、bash、JSON、SQL 等)
- AI 响应中的安全 HTML 渲染(粗体、斜体、代码转换为 markdown)
- rAF 节流 Token 流式传输,长响应期间渲染更流畅
- 编辑器底部栏的上下文使用指示器 —— Token 计数、成本和填充条(模型感知)

### 会话
- 创建、重命名、复制、删除、按标题和消息内容搜索
- 通过每个会话的 `⋯` 下拉菜单进行会话操作 —— 固定、移至项目、归档、复制、删除
- 固定/加星会话到侧边栏顶部(金色指示器)
- 归档会话(隐藏而不删除,切换显示)
- 会话项目 —— 带颜色的命名组用于组织会话
- 会话标签 —— 在标题中添加 #tag 以获得彩色标签和点击筛选
- 在侧边栏中按今天/昨天/更早分组(可折叠日期组)
- 下载为 Markdown 记录、完整 JSON 导出或从 JSON 导入
- 会话在页面重载和 SSH 隧道重连后保持
- 浏览器标签标题反映活动会话名称
- CLI 会话桥接 —— 来自 hermes-agent SQLite 存储的 CLI 会话出现在侧边栏中,带有金色"cli"徽章;点击导入完整历史记录并正常回复
- Token/成本显示 —— 每个对话显示输入 Token、输出 Token、估计成本(在设置中切换或通过 `/usage` 命令)

### 工作区文件浏览器
- 目录树,支持展开/折叠(单击切换,双击导航)
- 面包屑导航,可点击路径段
- 内联预览文本、代码、Markdown(渲染)和图片
- 编辑、创建、删除和重命名文件;创建文件夹
- 二进制文件下载(服务器自动检测)
- 目录导航时自动关闭文件预览(带未保存编辑保护)
- Git 检测 —— 工作区头部显示分支名和脏文件计数徽章
- 右侧面板可拖动调整大小
- 语法高亮代码预览(Prism.js)

### 语音输入
- 编辑器中的麦克风按钮(Web Speech API)
- 点击录音,再次点击或发送以停止
- 实时临时转录显示在文本区域
- 静默约 2 秒后自动停止
- 追加到现有文本区域内容(不替换)
- 浏览器不支持 Web Speech API 时隐藏(Chrome、Edge、Safari)

### 配置文件
- **编辑器底部栏**中的配置文件芯片 —— 下拉显示所有配置文件及网关状态和模型信息
- 网关状态点(绿色 = 运行中),模型信息,每个配置文件的技能计数
- 配置文件管理面板 —— 从侧边栏创建、切换和删除配置文件
- 创建时从活动配置文件克隆配置
- 创建时可选自定义端点字段 —— Base URL 和 API key 在创建时写入配置文件的 `config.yaml`,因此可以配置 Ollama、LMStudio 和其他本地端点,无需手动编辑文件
- 无缝切换 —— 无需服务器重启;重新加载配置、技能、记忆、定时任务、模型
- 每会话配置文件跟踪(记录创建时活动的配置文件)

### 认证和安全
- 可选密码认证 —— 默认关闭,本地使用零摩擦
- 通过 `HERMES_WEBUI_PASSWORD` 环境变量或设置面板启用
- 签名 HMAC HTTP-only cookie,24 小时 TTL
- `/login` 处有简约深色主题登录页
- 所有响应的安全头(X-Content-Type-Options、X-Frame-Options、Referrer-Policy)
- 20MB POST 请求体大小限制
- CDN 资源使用 SRI 完整性哈希固定

### 主题
- 7 种内置主题:深色(默认)、浅色、Slate、Solarized Dark、Monokai、Nord、OLED
- 通过设置面板下拉菜单切换(即时实时预览)或 `/theme` 命令
- 重载后保持(服务器端 settings.json + localStorage 防闪烁加载)
- 自定义主题:定义 `:root[data-theme="name"]` CSS 块即可使用 —— 参见 [THEMES.md](THEMES.md)

### 设置和配置
- **Hermes 控制中心**(侧边栏启动器按钮) —— 会话选项卡(导出/导入/清除)、首选项选项卡(模型、发送键、主题、语言、所有切换)、系统选项卡(版本、密码)
- 发送键:Enter(默认)或 Ctrl/Cmd+Enter
- 显示/隐藏 CLI 会话切换(默认启用)
- Token 使用显示切换(默认关闭,也通过 `/usage` 命令)
- 控制中心始终打开会话选项卡;关闭时重置
- 未保存更改保护 —— 关闭时有未保存更改时提示丢弃/保存
- 定时任务完成提醒 —— Toast 通知和任务选项卡上的未读徽章
- 后台代理错误提醒 —— 非活动会话遇到错误时显示横幅

### 斜杠命令
- 在编辑器中输入 `/` 获得自动完成下拉菜单
- 内置:`/help`、`/clear`、`/model <名称>`、`/workspace <名称>`、`/new`、`/usage`、`/theme`、`/compact`
- 方向键导航,Tab/Enter 选择,Escape 关闭
- 无法识别的命令传递给代理

### 面板
- **聊天** —— 会话列表、搜索、固定、归档、项目、新对话
- **任务** —— 查看、创建、编辑、运行、暂停/恢复、删除定时任务;运行历史;完成提醒
- **技能** —— 按类别列出所有技能、搜索、预览、创建/编辑/删除;链接文件查看器
- **记忆** —— 查看和编辑 MEMORY.md 和 USER.md 内联
- **配置文件** —— 创建、切换、删除代理配置文件;克隆配置
- **待办** —— 当前会话的实时任务列表
- **空间** —— 添加、重命名、移除工作区;从顶栏快速切换

### 移动端响应式
- 汉堡侧边栏 —— 移动端(<640px)滑入覆盖
- 底部导航栏 —— 5 标签 iOS 风格固定栏
- 文件从右边缘滑出面板
- 所有交互元素触摸目标最小 44px
- 编辑器位于底部导航上方
- 桌面布局完全不变

---

## 架构

```
server.py               HTTP 路由外壳 + 认证中间件 (~154 行)
api/
  auth.py               可选密码认证,签名 cookie (~201 行)
  config.py             发现、全局变量、模型检测、可重载配置 (~1110 行)
  helpers.py            HTTP 辅助函数、安全头 (~175 行)
  models.py             会话模型 + CRUD + CLI 桥接 (~377 行)
  onboarding.py         首次运行向导、OAuth 提供商支持 (~507 行)
  profiles.py           配置文件状态管理、hermes_cli 包装器 (~411 行)
  routes.py             所有 GET + POST 路由处理程序 (~1996 行)
  state_sync.py         /insights 同步 — message_count 到 state.db (~113 行)
  streaming.py          SSE 引擎、run_agent、取消支持 (~545 行)
  updates.py            自更新检查和发布说明 (~257 行)
  upload.py             多部分解析器、文件上传处理程序 (~82 行)
  workspace.py          文件操作、工作区辅助函数、git 检测 (~288 行)
static/
  index.html            HTML 模板 (~600 行)
  style.css             所有 CSS 包括移动端响应式、主题 (~1050 行)
  ui.js                 DOM 辅助函数、renderMd、工具卡片、上下文指示器 (~1496 行)
  workspace.js          文件预览、文件操作、git 徽章 (~286 行)
  sessions.js           会话 CRUD、可折叠组、搜索 (~752 行)
  messages.js           send()、SSE 处理程序、rAF 节流 (~487 行)
  panels.js             定时任务、技能、记忆、配置文件、设置 (~1438 行)
  commands.js           斜杠命令自动完成 (~267 行)
  boot.js               移动导航、语音输入、引导 IIFE (~524 行)
tests/
  conftest.py           隔离测试服务器(端口 8788)
  51 个测试文件          791 个测试函数
Dockerfile              python:3.12-slim 容器镜像
docker-compose.yml      带命名卷和可选认证的 Compose
.github/workflows/      CI: 多架构 Docker 构建 + 标签时 GitHub Release
```

状态默认存储在仓库外的 `~/.hermes/webui-mvp/`(会话、工作区、设置、项目、last_workspace)。使用 `HERMES_WEBUI_STATE_DIR` 覆盖。

---

## 文档

- `HERMES.md` —— 为什么选择 Hermes、心智模型以及与 Claude Code / Codex / OpenCode / Cursor 的详细对比
- `ROADMAP.md` —— 功能路线图和冲刺历史
- `ARCHITECTURE.md` —— 系统设计、所有 API 端点、实现说明
- `TESTING.md` —— 手动浏览器测试计划和自动化覆盖参考
- `CHANGELOG.md` —— 每个冲刺的发布说明
- `SPRINTS.md` —— 前瞻性冲刺计划,包含 CLI + Claude 对等目标
- `THEMES.md` —— 主题系统文档、自定义主题指南

## 贡献者

Hermes WebUI 在开源社区的帮助下构建。每个 PR —— 无论是直接合并还是通过变基整合 —— 都在塑造这个项目,我们感谢每一位花时间贡献的人。

### 主要贡献

**[@aronprins](https://github.com/aronprins)** — v0.50.0 UI 重构(PR #242)
项目最大的单一贡献:完整的 UI 重新设计,将模型/配置文件/工作区控制移至编辑器底部栏,用 Hermes 控制中心(选项卡式模态框)替换齿轮图标设置面板,移除活动栏改用内联编辑器状态,重新设计会话列表添加 `⋯` 操作下拉菜单,并添加工作区面板状态机。26 次提交,经过多轮审查迭代设计完善。

**[@iRonin](https://github.com/iRonin)** — 安全加固冲刺(PR #196–#204)
六个连续的安全和可靠性 PR:会话内存泄漏修复(过期令牌清理)、Content-Security-Policy + Permissions-Policy 头、30 秒慢客户端连接超时、通过环境变量可选 HTTPS/TLS 支持、自更新的上游分支跟踪修复、文件浏览器 API 中的 CLI 会话支持。这是让自托管工具值得信赖的高质量安全工作。

**[@DavidSchuchert](https://github.com/DavidSchuchert)** — 德语翻译(PR #190)
完整的德语区域设置(`de`)涵盖所有 UI 字符串、设置标签、命令和系统消息 —— 同时压力测试了 i18n 系统,暴露了几个尚未可翻译的元素,作为同一 PR 的一部分进行了修复。

### 功能贡献

**[@kevin-ho](https://github.com/kevin-ho)** — OLED 主题(PR #168)
添加第 7 种内置主题:纯黑背景配暖色调,专为降低烧屏风险优化。小改动,OLED 显示屏用户大受益。

**[@Bobby9228](https://github.com/Bobby9228)** — 移动端配置文件按钮(PR #265)
将配置文件选项卡添加到移动端底部导航栏,使手机上无需进入侧边栏即可切换配置文件。

**[@franksong2702](https://github.com/franksong2702)** — 会话标题保护 + 面包屑导航(PR #301, #302)
两个干净的错误修复/功能:会话标题保护,防止 `title_from()` 每轮后覆盖用户重命名的会话;工作区文件预览面板中的可点击面包屑导航。

### 错误修复贡献

**[@tgaalman](https://github.com/tgaalman)** — 思考卡片修复(PR #169)
修复了思考卡片显示中遗漏顶级推理字段的问题 —— Claude 扩展思考块在 API 响应中呈现方式的边缘情况。

**[@smurmann](https://github.com/smurmann)** — 自定义提供商路由修复(PR #189)
修复了带斜杠前缀的自定义提供商模型的路由问题,这些模型在模型选择器中被错误路由。多提供商设置中真实边缘情况的精确修复。

**[@jeffscottward](https://github.com/jeffscottward)** — Claude Haiku 模型 ID 修复(PR #145)
在 Anthropic 发布后立即发现并修正 Claude Haiku 模型 ID(`3-5` → `4-5`) —— 这类快速社区捕获让模型下拉菜单保持准确。

---

想做出贡献?请参阅 [ARCHITECTURE.md](ARCHITECTURE.md) 了解代码库布局,[TESTING.md](TESTING.md) 了解如何运行测试套件。最好的贡献是专注、充分测试、解决实际问题 —— 正如列表上每个人所做的。

## 仓库

```
git@github.com:nesquena/hermes-webui.git
```
