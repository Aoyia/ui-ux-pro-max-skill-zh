# UI-UX-Pro-Max-Skill 中文翻译项目实施计划

本项目旨在将英文版的 ui-ux-pro-max-skill （包括所有的 AI 技能指令、设计参考指南、设计数据库 CSV 以及相关文档等约 1.9 万行文本）完整、高质量地翻译并适配为中文版本，供中文开发者及 AI 编码工具（如 Claude Code, Cursor, Antigravity 等）直接安装、使用和阅读。

## 翻译总则与字段翻译对照指南

### 1. Markdown 文件翻译原则
- **保留结构**：所有的 Markdown 标题、列表格式、代码块及特殊语法（如 `> [!NOTE]`、`> [!IMPORTANT]`）必须严格保留。
- **保留链接**：所有指向本地文件或 line range 的链接必须保留其原格式（例如 `[layout-patterns.md](file:///...#L12-L20)` 仅翻译链接的文本部分，保留 `file:///...` 路径）。
- **保留技术专有名词**：如 `flex-direction`, `Backdrop blur`, `Z-index`, `Bento Layout` 等技术词汇可使用 “中文名称（英文原名）” 形式或直接保留原英文，确保开发者理解。

### 2. CSV 数据文件翻译字段级对照表

| CSV 文件名 | 必须保留英文的字段（作为键） | 必须翻译为中文的字段 | 备注 |
| :--- | :--- | :--- | :--- |
| `products.csv` | `No`, `Product Type`, `Keywords`, `Landing Page Pattern`, `Dashboard Style (if applicable)`, `Primary Style Recommendation`, `Secondary Styles`, `Color Palette Focus` | `Key Considerations` | `Product Type` 是搜索引擎主键，绝不能改动。 |
| `styles.csv` | `No`, `Style Category`, `Type`, `Keywords`, `AI Prompt Keywords`, `CSS/Technical Keywords`, `Light Mode ✓`, `Dark Mode ✓` | `Primary Colors`, `Secondary Colors`, `Effects & Animation`, `Best For`, `Do Not Use For`, `Performance`, `Accessibility`, `Mobile-Friendly`, `Conversion-Focused`, `Framework Compatibility`, `Era/Origin`, `Complexity`, `Implementation Checklist`, `Design System Variables` | 翻译所有描述性说明和清单。 |
| `colors.csv` | `No`, `Product Type`, `Primary`, `On Primary`, `Secondary`, `On Secondary`, `Accent`, `On Accent`, `Background`, `Foreground`, `Card`, `Card Foreground`, `Muted`, `Muted Foreground`, `Border`, `Destructive`, `On Destructive`, `Ring` | `Notes` | HEX 颜色值和产品类型必须保留英文。 |
| `typography.csv` | `No`, `Font Pairing Name`, `Category`, `Heading Font`, `Body Font`, `Mood/Style Keywords`, `CSS Import`, `Tailwind Config`, `Google Fonts URL` | `Best For`, `Notes` | 字体名及配置均保留英文。 |
| `ui-reasoning.csv`| `No`, `UI_Category`, `Recommended_Pattern`, `Style_Priority`, `Severity` | `Color_Mood`, `Typography_Mood`, `Key_Effects`, `Decision_Rules`, `Anti_Patterns` | `Decision_Rules` 内的 JSON 键保持原样，值做对照。 |
| `ux-guidelines.csv`| `No`, `Category`, `Issue`, `Platform`, `Severity`, `Code Example Good`, `Code Example Bad` | `Description`, `Do`, `Don't` | 代码示例内部的注释需要翻译为中文。 |
| `charts.csv` | `No`, `Data Type`, `Keywords`, `Best Chart Type`, `Secondary Options`, `Data Volume Threshold`, `Library Recommendation`, `Interactive Level` | `When to Use`, `When NOT to Use`, `Color Guidance`, `Accessibility Grade`, `Accessibility Notes`, `A11y Fallback` | |
| `landing.csv` | `No`, `Pattern Name`, `Keywords`, `Section Order`, `Primary CTA Placement` | `Color Strategy`, `Recommended Effects`, `Conversion Optimization` | |
| `app-interface.csv`| `No`, `Category`, `Issue`, `Keywords`, `Platform`, `Severity`, `Code Example Good`, `Code Example Bad` | `Description`, `Do`, `Don't` | 与 `ux-guidelines.csv` 策略一致。 |
| `react-performance.csv`| `No`, `Category`, `Issue`, `Keywords`, `Platform`, `Severity`, `Code Example Good`, `Code Example Bad` | `Description`, `Do`, `Don't` | 与 `ux-guidelines.csv` 策略一致。 |
| `stacks/*.csv` | `No`, `Category`, `Guideline`, `Severity`, `Docs URL`, `Code Good`, `Code Bad` | `Description`, `Do`, `Don't` | 框架特有规则，翻译指导和代码注释。 |
| `design.csv` | 结构标记如 `<design-system>`, `Colors`, `Typography` 等 | 每种设计风格下的说明段落、设计理念（Design Philosophy）、视觉氛围（Visual Vibe）及组件设计规范的具体文本说明 | 这是一个大型 Markdown 嵌套 CSV，需要逐段细致翻译描述部分。 |
| `draft.csv` | 同上 | 同上 | 备份参考数据。 |

*注：`google-fonts.csv` 包含 Google 字体数据库，全部为字体英文元数据，明确排除在翻译范围外，不需要进行任何翻译。*

### 3. CSV 翻译对齐示例 (以 `ux-guidelines.csv` 为例)

*翻译前 (英文)*:
```csv
1,Layout,Non-responsive margins,Web,Grid container padding,Ensure content has 24px padding on desktop and 16px on mobile. Avoid clipping.,Use px-4 md:px-6,Use w-full paddingless,// Good
const Container = () => <div className="px-4 md:px-6">Content</div>,// Bad
const Container = () => <div>Content</div>,HIGH
```

*翻译后 (中文)*:
```csv
1,Layout,Non-responsive margins,Web,Grid container padding,确保内容在桌面端具有 24px 的内边距（padding），在移动端具有 16px 的内边距。避免内容被裁剪。,Use px-4 md:px-6,Use w-full paddingless,// 优秀实践
const Container = () => <div className="px-4 md:px-6">内容</div>,// 不良做法
const Container = () => <div>内容</div>,HIGH
```

---

## Proposed Changes (任务划分与详情)

### Task 1: 项目初始化与工作区准备
- [x] **Step 1: 创建本地工作区目录结构并复制源仓库**  
  运行 `rsync -av --exclude='.git' /tmp/ui-ux-pro-max-skill-source/ /Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/`。
- [x] **Step 2: 初始化 Git 并提交基础版本**  
  执行 `git init && git add . && git commit -m "init: import original english repository files"`。

### Task 2: 核心技能指令与模板翻译 (P0)
- [x] **Step 1: 补全翻译 `src/ui-ux-pro-max/templates/base/quick-reference.md`**  
  已有前 37 行中文，补全后续 260 行（各平台快速参考配置、搜索命令）。
- [x] **Step 2: 翻译主技能模版 `src/ui-ux-pro-max/templates/base/skill-content.md`**  
  翻译 358 行主技能模版（交互推理步骤、核对清单等）。
- [x] **Step 3: 翻译主技能最终文件 `.claude/skills/ui-ux-pro-max/SKILL.md`**  
  翻译 659 行主技能指令（合并模版结果，确保插件运行核心）。

### Task 3: 核心子技能指令翻译 (P1)
- [x] **Step 1: 翻译横幅设计技能 `banner-design/SKILL.md`** (192 行)
- [x] **Step 2: 翻译品牌设计技能 `brand/SKILL.md`** (97 行)
- [x] **Step 3: 翻译通用设计技能 `design/SKILL.md`** (302 行)
- [x] **Step 4: 翻译设计系统技能 `design-system/SKILL.md`** (244 行)
- [x] **Step 5: 翻译幻灯片设计技能 `slides/SKILL.md`** (42 行)
- [x] **Step 6: 翻译 UI 样式技能 `ui-styling/SKILL.md`** (324 行)

### Task 4: 设计参考指南 Markdown 文档翻译 (P1)
- [x] **Step 1: 翻译 Banner 与品牌参考指南** (共 13 个 md 文件)
- [x] **Step 2: 翻译设计系统参考指南** (共 7 个 md 文件)
- [x] **Step 3: 翻译通用设计指南文档** (共 17 个 md 文件)
- [x] **Step 4: 翻译幻灯片参考指南文档** (共 5 个 md 文件)
- [x] **Step 5: 翻译 UI 样式与框架应用指南** (共 7 个 md 文件)

### Task 5: 设计数据库 (CSV) 翻译 (P1)
- [x] **Step 1: 翻译核心 UI/UX 指南规则数据**  
  翻译 `ux-guidelines.csv` (100 行)、`ui-reasoning.csv` (162 行)、`app-interface.csv` (31 行) 和 `react-performance.csv` (45 行) 里的描述、Do 和 Don't 字段。
- [x] **Step 2: 翻译产品及分类配置数据**  
  翻译 `products.csv`、`styles.csv`、`colors.csv`、`typography.csv`、`charts.csv`、`landing.csv` 和 `icons.csv` 里的对应描述性列（保留英文检索键）。
- [x] **Step 3: 翻译 17 个框架 stacks 数据**  
  翻译 `src/ui-ux-pro-max/data/stacks/` 目录下的 17 个 CSV 文件中描述 and Do/Don't 指引。
- [x] **Step 4: 翻译大型设计手册数据**  
  翻译 `design.csv` (1776 行) 和 `draft.csv` (1779 行) 中每种设计风格下的文本段落和组件设计规范。

### Task 6: 全局文档与安装平台配置翻译 (P2)
- [x] **Step 1: 翻译安装及全局文档**  
  翻译 `README.md` (513 行) 和 `CLAUDE.md` (98 行) 等。
- [x] **Step 2: 翻译技能及平台配置文件**  
  翻译 `skill.json` (41 行) 及 `src/ui-ux-pro-max/templates/platforms/*.json` 的 `description` 部分。

### Task 7: 资产同步与校验 (P0)
- [x] **Step 1: 运行同步衍生脚本对齐数据库**  
  在核心目录下运行：`python3 src/ui-ux-pro-max/data/_sync_all.py`。
- [x] **Step 2: 将 core 目录的全部翻译内容同步到 CLI assets 文件夹**  
  使用 rsync 复制最新 CSV 到 `cli/assets/` 中。
- [x] **Step 3: 运行 CSV 完整性自动化校验**  
  运行 Python 脚本自检 CSV 行列是否对齐。
- [x] **Step 4: 校验搜索引擎功能**  
  执行 `python3 src/ui-ux-pro-max/scripts/search.py` 测试检索。

---

## Verification Plan

### 自动化测试
1. **CSV 校验**: 通过 Python 自检脚本逐一读取所有的 CSV 数据，确保数据流结构正常（行数与头一致）。
2. **搜索测试**: 运行 `python3 src/ui-ux-pro-max/scripts/search.py` 检查检索。
3. **Markdown 坏链测试**: 检查主技能与子技能中的本地 `file:///` 相对引用是否无误。

### 手动验证
1. **AI 技能挂载测试**：在 AI 配置插件中指向 `.claude/skills/ui-ux-pro-max/SKILL.md`，测试能否正确加载。
2. **提示词交互测试**：使用中文向 AI 提问以生成设计系统，观察产出内容的完整性与可读性。
