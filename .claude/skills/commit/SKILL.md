---
name: commit
description: 按本仓库约定生成并创建 git 提交：中文、Conventional Commits、无 scope、仅 subject 行，不带 body/footer/Co-Authored-By。当用户要求提交、创建 commit 或运行 /commit 时使用。
---

# 本仓库 Git Commit 规范

所有提交都必须遵守以下四条规则。**不要询问用户是否需要 body 或 trailer——默认全部省略**，除非用户在本轮对话中明确要求添加。

## 规则

1. **语言**：commit message 一律用**中文**书写。
2. **格式**：Conventional Commits — `type: 描述`（**不要 scope**，不要括号）。
3. **type 取值**：`feat`、`fix`、`docs`、`style`、`refactor`、`test`、`chore`、`perf`、`ci`、`build`。
4. **只写 subject 行**：不要 body，不要 footer，不要 `Co-Authored-By` 或任何其它 trailer。

### 示例

```
feat: 新增用户登录接口
fix: 修正会话索引在并发写入时丢失的问题
docs: 补充 CLAUDE.md 的架构说明
chore: 升级 pyyaml 到 6.0.2
refactor: 抽离 streaming 中的环境变量保存逻辑
```

### 反例（不要这样做）

```
feat(auth): add login endpoint            ❌ 含 scope、英文
feat: 新增登录接口                          ❌ 看似正确，但下面追加了多行 body 或 Co-Authored-By
fix: 修复 bug                              ❌ 描述过于含糊
```

## 操作步骤

收到提交请求后：

1. **并行**执行 `git status`（不要 `-uall`）、`git diff`（已暂存 + 未暂存）、`git log -n 5 --oneline` 三条命令以了解上下文。
2. 根据变更性质选择合适的 `type`：
   - `feat` 引入新功能（在已有特性上扩展也算 `feat` 还是 `refactor`，按用户意图判断；新接口/新页面/新命令都属 `feat`）。
   - `fix` 修复 bug（行为不符合预期）。
   - `refactor` 仅调整结构，对外行为不变。
   - `docs` 仅改文档（README、CLAUDE.md、注释整理）。
   - `chore` 依赖升级、构建脚本、`.gitignore` 等杂项。
   - `perf` 性能优化。
   - `style` 仅格式（空格、引号、不影响行为）。
   - `test` 仅测试代码。
   - `ci` / `build` 持续集成 / 构建系统。
3. 用一句中文概括"为什么"或"做了什么"，控制在 50 个汉字以内，**避免**只写"修复 bug"、"更新代码"这种没有信息量的描述。
4. 暂存相关文件（按文件名添加，避免 `git add -A` 误带入 `.env` 或大文件）。
5. **以单行字符串**调用 `git commit -m "type: 描述"` 即可——**不要**用 HEREDOC、不要拼接 `Co-Authored-By`。
6. 提交后跑一次 `git status` 确认成功。

## 安全规则（继承自 Claude Code 默认）

- 不要 `git push`、`git reset --hard`、`git push --force`，除非用户明确要求。
- 不要 `git commit --amend`，除非用户明确要求；钩子失败时新建一次提交而非 amend。
- 不要 `--no-verify` 跳过钩子；钩子失败先排查再提交。
- 不要修改 `git config`。
- 不要提交 `.env`、密钥、凭证文件；如果用户坚持，先警告。

## 与全局默认模板的差异

Claude Code 默认会在提交消息里追加英文 body 和 `Co-Authored-By: Claude ...` 这一行。**在本仓库里覆盖这个默认行为**——只要 subject 一行，且必须中文。
