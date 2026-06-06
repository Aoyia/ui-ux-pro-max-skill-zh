# uipro-cli

用于为 AI 编程助手安装 UI/UX Pro Max 技能的 CLI 工具。

## 安装指南

```bash
npm install -g uipro-cli
```

## 使用方法

```bash
# 为指定的 AI 助手进行安装
uipro init --ai claude      # Claude Code
uipro init --ai cursor      # Cursor
uipro init --ai windsurf    # Windsurf
uipro init --ai antigravity # Antigravity
uipro init --ai copilot     # GitHub Copilot
uipro init --ai kiro        # Kiro
uipro init --ai codex       # Codex (Skills)
uipro init --ai roocode     # Roo Code
uipro init --ai qoder       # Qoder
uipro init --ai gemini      # Gemini CLI
uipro init --ai trae        # Trae
uipro init --ai opencode    # OpenCode
uipro init --ai continue    # Continue (Skills)
uipro init --ai all         # 所有助手

# 参数选项
uipro init --offline        # 跳过 GitHub 下载，仅使用本地打包的资源
uipro init --force          # 覆盖已存在的文件

# 其他命令
uipro versions              # 列出可用版本
uipro update                # 更新到最新版本
```

## 工作原理

默认情况下，`uipro init` 会尝试从 GitHub 下载最新的 Release 版本，以确保你获取的是最新版。如果下载失败（由于网络错误、速率限制等），它会自动回退并使用 CLI 包中自带的打包资源。

使用 `--offline` 参数可以跳过 GitHub 下载，直接使用本地的打包资源。

## 本地开发

```bash
# 安装依赖
bun install

# 本地运行
bun run src/index.ts --help

# 构建打包
bun run build

# 创建本地测试的软链接
bun link
```

## 开源协议

CC-BY-NC-4.0
