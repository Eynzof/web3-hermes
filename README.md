# Web3Hermes

```txt
本项目疯狂更新中，如有 bug 可前往 issue 反馈。但作者始终精力有限，本项目难以避免有不足之处，请注意。
```

基于 [Hermes Agent](https://hermes-agent.nousresearch.com/) 的轻量级 Web 界面，专为中国大陆用户优化。

## 界面预览

<table>
  <tr>
    <td width="50%" align="center">
      <img alt="深色主题界面" src="https://raw.githubusercontent.com/Web3CZ/Web3Hermes/refs/heads/main/docs/images/black.png" />
      <br /><sub>深色主题界面</sub>
    </td>
    <td width="50%" align="center">
      <img alt="浅色主题界面" src="https://raw.githubusercontent.com/Web3CZ/Web3Hermes/refs/heads/main/docs/images/light.png" />
      <br /><sub>浅色主题界面</sub>
    </td>
  </tr>
</table>

## 特色功能

- 🎨 **精美界面** - 深色/浅色主题，完整中文支持
- 🚀 **简化操作** - 优化的交互流程，更符合中文用户习惯
- 💬 **智能对话** - 支持多种 AI 模型，流式响应
- 📁 **文件管理** - 内置工作区文件浏览器
- 🔧 **工具集成** - 完整的 Hermes Agent 功能支持
- 🌐 **纯桌面端** - 专为桌面浏览器优化

## 快速开始

### 环境要求

- WSL 或 Linux 系统

### 安装步骤

```bash
# 1. 克隆仓库
git clone https://github.com/Web3CZ/Web3Hermes.git
cd Web3Hermes

# 2. 启动服务（自动安装依赖）
python3 bootstrap.py
```

或使用启动脚本：

```bash
./start.sh
```

服务将在 `http://127.0.0.1:8787` 启动。

### 配置环境变量

创建 `.env` 文件或设置环境变量：

```bash
# 基础配置
export HERMES_WEBUI_HOST=127.0.0.1      # 监听地址
export HERMES_WEBUI_PORT=8787           # 端口号
export HERMES_WEBUI_PASSWORD=your-pass  # 访问密码（推荐设置）

# 可选配置
export HERMES_WEBUI_STATE_DIR=~/.hermes/webui-mvp
export HERMES_WEBUI_DEFAULT_WORKSPACE=~/workspace
export HERMES_WEBUI_DEFAULT_MODEL=openai/gpt-4o-mini
```

## 主要功能

### 对话功能
- ✅ 流式响应（SSE）
- ✅ 多模型支持（OpenAI、Anthropic、Google、DeepSeek等）
- ✅ 消息编辑和重新生成
- ✅ 工具调用可视化
- ✅ 代码高亮和复制
- ✅ Markdown 渲染
- ✅ 文件附件支持

### 会话管理
- ✅ 创建、重命名、删除会话
- ✅ 会话搜索和过滤
- ✅ 会话固定和归档
- ✅ 项目分组和标签
- ✅ 导出为 Markdown 或 JSON
- ✅ 会话导入

### 工作区
- ✅ 文件树浏览
- ✅ 文件预览（文本、代码、图片、Markdown）
- ✅ 文件编辑、创建、删除
- ✅ 目录导航
- ✅ Git 状态显示

### 任务管理
- ✅ 定时任务（Cron）
- ✅ 技能管理
- ✅ 记忆系统
- ✅ 配置文件管理
- ✅ 待办事项

### 界面特色
- ✅ 深色/浅色主题
- ✅ 完整中文界面
- ✅ 响应式布局
- ✅ 快捷键支持
- ✅ 语音输入（支持的浏览器）

---

**注意**: 本应用暂不支持移动端，请使用桌面浏览器访问。
