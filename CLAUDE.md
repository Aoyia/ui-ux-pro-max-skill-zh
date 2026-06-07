# CLAUDE.md

此文件在与本仓库中的代码协作时，为 Claude Code (claude.ai/code) 提供指导。

## 项目概述 (Project Overview)

Antigravity Kit 是一款由 AI 驱动的设计智能工具包，提供了一个包含 UI 风格、色彩搭配、字体配对、图表类型以及 UX 指南的可检索数据库。它可以用作 AI 编程助手（如 Claude Code、Windsurf、Cursor 等）的 AI 技能插件或工作流。

## 搜索命令 (Search Command)

```bash
python3 src/ui-ux-pro-max/scripts/search.py "<query>" --domain <domain> [-n <max_results>]
```

**领域专项搜索：**
- `product` —— 产品类型推荐（SaaS、电子商务、个人作品集等）
- `style` —— UI 风格（磨砂玻璃拟态、极简主义、粗野主义等）及相应的 AI 提示词和 CSS 关键属性
- `typography` —— 字体配对组合（支持 Google Fonts 导入）
- `color` —— 色彩搭配方案（按产品类别分类）
- `landing` —— 页面骨架结构与 CTA 转化策略
- `chart` —— 图表类型及可视化库推荐
- `ux` —— UX 最佳实践与反模式（体验误区）规避

**技术栈专项搜索：**
```bash
python3 src/ui-ux-pro-max/scripts/search.py "<query>" --stack <stack>
```
可用技术栈：`html-tailwind`（默认）、`react`、`nextjs`、`astro`、`vue`、`nuxtjs`、`nuxt-ui`、`svelte`、`swiftui`  、`react-native`、`flutter`、`shadcn`、`jetpack-compose`

## 架构说明 (Architecture)

```
src/ui-ux-pro-max/                # 单一事实来源 (Source of Truth)
├── data/                         # 规范化的 CSV 数据库
│   ├── products.csv, styles.csv, colors.csv, typography.csv, ...
│   └── stacks/                   # 特定技术栈指南
├── scripts/
│   ├── search.py                 # CLI 入口点
│   ├── core.py                   # BM25 + 正则混合搜索引擎
│   └── design_system.py          # 设计系统生成器
└── templates/
    ├── base/                     # 基础模板 (skill-content.md, quick-reference.md)
    └── platforms/                # 平台特定配置文件 (claude.json, cursor.json, ...)

cli/                              # CLI 安装程序 (npm 上的 uipro-cli)
├── src/
│   ├── commands/init.ts          # 带模板生成的安装命令
│   └── utils/template.ts         # 模板渲染引擎
└── assets/                       # 打包的静态资产 (~564KB)
    ├── data/                     # src/ui-ux-pro-max/data/ 的副本
    ├── scripts/                  # src/ui-ux-pro-max/scripts/ 的副本
    └── templates/                # src/ui-ux-pro-max/templates/ 的副本

.claude/skills/ui-ux-pro-max/     # Claude Code 技能插件（软链接至 src/）
.factory/skills/ui-ux-pro-max/   # Droid (Factory) 技能插件（软链接至 src/）
.shared/ui-ux-pro-max/            # 软链接至 src/ui-ux-pro-max/
.claude-plugin/                   # Claude 插件市场发布包
```

搜索引擎采用 BM25 排序算法与正则表达式混合匹配。省略 `--domain` 参数时将自动检测检索领域。

## 文件同步规范 (Sync Rules)

**单一事实来源：** `src/ui-ux-pro-max/`

修改文件时请遵循以下规范：

1. **数据与脚本** —— 在 `src/ui-ux-pro-max/` 中编辑：
   - `data/*.csv` 和 `data/stacks/*.csv`
   - `scripts/*.py`
   - 所做的更改将通过 `.claude/`、`.factory/`、`.shared/` 目录下的符号链接自动生效。

2. **模板** —— 在 `src/ui-ux-pro-max/templates/` 中编辑：
   - `base/skill-content.md` —— 通用的 SKILL.md 指令模板
   - `base/quick-reference.md` —— 快速参考部分（仅限 Claude 平台）
   - `platforms/*.json` —— 平台特定配置文件

3. **CLI 资产同步** —— 在发布包版本前，请运行以下同步命令：
   ```bash
   cp -r src/ui-ux-pro-max/data/* cli/assets/data/
   cp -r src/ui-ux-pro-max/scripts/* cli/assets/scripts/
   cp -r src/ui-ux-pro-max/templates/* cli/assets/templates/
   ```

4. **编译输出目录** —— 无需手动同步，CLI 会在执行 `uipro init` 时自动基于模板渲染并生成这些内容。

## 开发前提条件 (Prerequisites)

Python 3.x（零外部依赖，开箱即用）

## Git 开发工作流 (Git Workflow)

禁止直接向 `main` 分支推送代码。请遵循以下规范：

1. 基于最新主干创建特性/修复分支：`git checkout -b feat/...` 或 `git checkout -b fix/...`
2. 提交代码更改
3. 推送本地分支：`git push -u origin <branch>`
4. 发起 Pull Request：`gh pr create`
