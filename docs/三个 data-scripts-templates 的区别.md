# 项目中三处 data / scripts / templates 目录的功能区隔与协作规范

在整个工程架构中，共存在三处 `data`、`scripts` 与 `templates` 结构。它们各自承担着不同的系统职责。

## 目录功能与区隔一览

| 目录物理路径 | 核心业务职责 | 维护建议 / 能否删除 |
|------|------|--------|
| **`src/ui-ux-pro-max/`** | **核心源码库**。所有 CSV 数据集、搜索引擎脚本、指令模板的唯一事实来源 (Source of Truth)。 | ❌ **绝对不可删除**。这是整个项目最上游的源头。 |
| **`.claude/skills/ui-ux-pro-max/`** | **AI 技能扩展插槽 (Skill)**。面向 Claude Code / Cursor 等 AI 编程助手提供的本地技能描述与检索入口。在架构设计上，此处的 `data` 与 `scripts` 应作为指向 `src/` 的符号链接 (Symlinks)，从而避免冗余维护。 | ❌ **绝对不可删除**（否则本地 AI 助手将无法消费该技能）。但必须确保以符号链接方式与 `src/` 进行绑定，不要保留物理副本。 |
| **`cli/assets/`** | **CLI 打包静态资产**。供发布在 npm 上的全局包 `uipro-cli` 使用。当终端用户执行 `npm install -g uipro-cli` 并运行 `uipro init` 进行初始化时，本地生成的资源全部提取自此处的打包目录。 | ❌ **绝对不可删除**。每次发布 npm 包前，需使用同步脚本从 `src/` 一键覆盖同步。 |

## 是否能够进行物理合并？

- **不能物理删除任何一处**：这三处目录的消费方与环境（源码开发、本地 AI 开发检索、最终全球用户安装）完全不同，必须共同存在。
- **但可实现逻辑上的“单一事实来源”维护**：
  1. 所有业务层面的修改**有且仅在** `src/ui-ux-pro-max/` 内进行。
  2. `.claude/` 目录下相关的 `data`、`scripts` 和 `templates` 必须以**符号链接 (Symlink)** 形式指向 `src/ui-ux-pro-max/` 对应的子目录，实现自动同步。
  3. 在执行 npm 发布流程前，通过自动化命令将最新的 `src/ui-ux-pro-max/` 静态资产拷贝到 `cli/assets/` 下。

这样您日常仅需聚焦维护 `src/` 目录，其他两处则会自动同步或在发布时按需构建。

## 推荐开发工作流

1. 日常迭代仅限修改 `src/ui-ux-pro-max/data/`、`src/ui-ux-pro-max/scripts/` 和 `src/ui-ux-pro-max/templates/`。
2. 确保 `.claude/skills/ui-ux-pro-max/` 下的 `data` 和 `scripts` 是正确的 symlink，并指向 `src/ui-ux-pro-max/`（参见「恢复符号链接」指引）。
3. 每次发布 npm 包之前，执行同步拷贝命令：
   ```bash
   cp -r src/ui-ux-pro-max/data/* cli/assets/data/
   cp -r src/ui-ux-pro-max/scripts/* cli/assets/scripts/
   cp -r src/ui-ux-pro-max/templates/* cli/assets/templates/
   ```
