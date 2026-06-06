# CLAUDE.md

此文件在与本仓库中的代码协作时，为 Claude Code (claude.ai/code) 提供指导。

## 项目概述 (Project Overview)

Antigravity Kit 是一个 AI 驱动的设计智能工具包，提供了 UI 风格、色彩搭配、字体配对、图表类型和 UX 指南的可搜索数据库。它可作为 AI 编程助手（Claude Code、Windsurf、Cursor 等）的 AI 技能 / 工作流使用。

## 搜索命令 (Search Command)

```bash
python3 src/ui-ux-pro-max/scripts/search.py "<query>" --domain <domain> [-n <max_results>]
```

**领域搜索：**
- `product` - 产品类型推荐（SaaS、电子商务、作品集）
- `style` - UI 风格（玻璃拟态、极简主义、粗野主义） + AI 提示词和 CSS 关键字
- `typography` - 带有 Google Fonts 导入的字体配对
- `color` - 按产品类型分类的色彩搭配
- `landing` - 页面结构和 CTA 策略
- `chart` - 图表类型和库推荐
- `ux` - 最佳实践和反模式

**技术栈搜索：**
```bash
python3 src/ui-ux-pro-max/scripts/search.py "<query>" --stack <stack>
```
可用技术栈：`html-tailwind`（默认）、`react`、`nextjs`、`astro`、`vue`、`nuxtjs`、`nuxt-ui`、`svelte`、`swiftui`、`react-native`、`flutter`、`shadcn`、`jetpack-compose`

## 架构 (Architecture)

```
src/ui-ux-pro-max/                # 单一事实来源 (Source of Truth)
├── data/                         # 规范的 CSV 数据库
│   ├── products.csv, styles.csv, colors.csv, typography.csv, ...
│   └── stacks/                   # 特定技术栈指南
├── scripts/
│   ├── search.py                 # CLI 入口点
│   ├── core.py                   # BM25 + 正则混合搜索引擎
│   └── design_system.py          # 设计 system 生成
└── templates/
    ├── base/                     # 基础模板 (skill-content.md, quick-reference.md)
    └── platforms/                # 平台配置 (claude.json, cursor.json, ...)

cli/                              # CLI 安装程序 (npm 上的 uipro-cli)
├── src/
│   ├── commands/init.ts          # 带模板生成的安装命令
│   └── utils/template.ts         # 模板渲染引擎
└── assets/                       # 打包的资产 (~564KB)
    ├── data/                     # src/ui-ux-pro-max/data/ 的副本
    ├── scripts/                  # src/ui-ux-pro-max/scripts/ 的副本
    └── templates/                # src/ui-ux-pro-max/templates/ 的副本

.claude/skills/ui-ux-pro-max/     # Claude Code 技能（符号链接至 src/）
.factory/skills/ui-ux-pro-max/   # Droid (Factory) 技能（符号链接至 src/）
.shared/ui-ux-pro-max/            # 符号链接至 src/ui-ux-pro-max/
.claude-plugin/                   # Claude 插件市场发布
```

搜索引擎使用 BM25 排名结合正则表达式匹配。省略 `--domain` 时将启用领域自动检测。

## 同步规则 (Sync Rules)

**单一事实来源：** `src/ui-ux-pro-max/`

修改文件时：

1. **数据与脚本** - 在 `src/ui-ux-pro-max/` 中编辑：
   - `data/*.csv` and `data/stacks/*.csv`
   - `scripts/*.py`
   - 更改将通过 `.claude/`、`.factory/`、`.shared/` 中的符号链接自动生效

2. **模板** - 在 `src/ui-ux-pro-max/templates/` 中编辑：
   - `base/skill-content.md` - 通用的 SKILL.md 内容
   - `base/quick-reference.md` - 快速参考部分（仅限 Claude）
   - `platforms/*.json` - 平台特定的配置

3. **CLI 资产** - 在发布前运行同步：
   ```bash
   cp -r src/ui-ux-pro-max/data/* cli/assets/data/
   cp -r src/ui-ux-pro-max/scripts/* cli/assets/scripts/
   cp -r src/ui-ux-pro-max/templates/* cli/assets/templates/
   ```

4. **参考文件夹** - 无需手动同步。CLI 会在 `uipro init` 期间从模板生成这些内容。

## 前提条件 (Prerequisites)

Python 3.x（无需外部依赖）

## Git 工作流 (Git Workflow)

切勿直接推送至 `main`。请始终：

1. 创建新分支：`git checkout -b feat/...` 或 `fix/...`
2. 提交更改
3. 推送分支：`git push -u origin <branch>`
4. 创建 PR：`gh pr create`
