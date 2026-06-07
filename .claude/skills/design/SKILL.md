---
name: ckm:design
description: "综合设计技能：包含品牌身份、设计标记、UI 样式、Logo 生成（55 种风格，搭载 Gemini AI）、企业识别系统项目（CIP，支持 50 多项交付物与 CIP 效果图）、HTML 演示文稿（集成 Chart.js）、横幅设计（22 种风格，适配社交/广告/网页/印刷）、图标设计（15 种风格，输出 SVG 格式，搭载 Gemini 3.1 Pro）、社交媒体图片（采用 HTML 转化为截图方式，支持多平台）。操作：设计 Logo、创建 CIP、生成效果图、构建幻灯片、设计横幅、生成图标、创建社交媒体图片。适配平台：Facebook、Twitter、LinkedIn、YouTube、Instagram、Pinterest、TikTok、Threads、Google 展示广告。"
argument-hint: "[design-type] [context]"
license: MIT
metadata:
  author: claudekit
  version: "2.1.0"
---

# 设计 (Design)

一站式设计开发技能系统：涵盖品牌体系 (brand)、设计标记 (tokens)、UI 设计 (UI)、徽标 (logo)、企业识别系统 (CIP)、演示幻灯片 (slides)、横幅 (banners)、社交媒体图片 (social photos) 及图标 (icons)。

## 适用场景 (When to Use)

- 品牌识别 (Brand identity)、语气与资产管理
- 设计系统标记 (Design system tokens) 与规格定义
- 使用 shadcn/ui + Tailwind 进行 UI 样式设计 (UI styling)
- Logo 设计及 AI 生成
- 企业识别系统 (CIP) 交付物设计
- 演示文稿和路演幻灯片 (Pitch decks)
- 社交媒体、广告、网页及印刷的横幅 (Banner) 设计
- Instagram、Facebook、LinkedIn、Twitter、Pinterest、TikTok 的社交媒体图片设计

## 技能路由 (Skill Routing)

| 任务 | 子技能 | 详情 |
|------|-----------|---------|
| 品牌识别、语气与资产 | `brand` | 外部技能 |
| 设计标记、规范与 CSS 变量 | `design-system` | 外部技能 |
| shadcn/ui、Tailwind、代码实现 | `ui-styling` | 外部技能 |
| Logo 创建、AI 生成 | Logo (内置) | `references/logo-design.md` |
| CIP 效果图与交付物 | CIP (内置) | `references/cip-design.md` |
| 演示文稿、路演幻灯片 | Slides (内置) | `references/slides.md` |
| 横幅、封面、头部设计 | Banner (内置) | `references/banner-sizes-and-styles.md` |
| 社交媒体图片/照片 | Social Photos (内置) | `references/social-photos-design.md` |
| SVG 图标、图标集 | Icon (内置) | `references/icon-design.md` |

## Logo 设计 (内置)

55+ 种风格，30 种配色方案，25 种行业指南。基于 Gemini 图像生成模型。

### Logo：生成设计简报

```bash
python3 ~/.claude/skills/design/scripts/logo/search.py "tech startup modern" --design-brief -p "BrandName"
```

### Logo：搜索风格/颜色/行业

```bash
python3 ~/.claude/skills/design/scripts/logo/search.py "minimalist clean" --domain style # 搜索极简干净的风格
```

```bash
python3 ~/.claude/skills/design/scripts/logo/search.py "tech professional" --domain color # 搜索科技专业配色
```

```bash
python3 ~/.claude/skills/design/scripts/logo/search.py "healthcare medical" --domain industry # 搜索医疗健康行业
```

### Logo：使用 AI 生成

**务必**在生成输出的 Logo 图片时使用白色背景。

```bash
python3 ~/.claude/skills/design/scripts/logo/generate.py --brand "TechFlow" --style minimalist --industry tech # 为 TechFlow 生成极简风格科技行业 Logo
```

```bash
python3 ~/.claude/skills/design/scripts/logo/generate.py --prompt "coffee shop vintage badge" --style vintage # 为复古风格咖啡店徽章生成 Logo
```

**开发提示**：若脚本在执行期间发生报错，请优先进行代码级排错与修复。

生成完成后，**必须**调用 `AskUserQuestion` 交互工具，询问用户是否需要生成 HTML 预览。若用户确认，调用 `/ui-ux-pro-max` 技能以画廊形式在浏览器中呈现。

## 企业识别系统设计 (CIP Design - 内置)

50+ 种交付物，20 种风格，20 个行业。基于 Gemini (Flash/Pro) 图像生成模型。

### CIP：生成设计简报

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "tech startup" --cip-brief -b "BrandName"
```

### CIP：搜索类别

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "business card letterhead" --domain deliverable # 搜索名片与信头交付物
```

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "luxury premium elegant" --domain style # 搜索奢华优雅风格
```

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "hospitality hotel" --domain industry # 搜索酒店餐饮行业
```

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "office reception" --domain mockup # 搜索办公室前台效果图
```

### CIP：生成效果图 (Mockups)

```bash
# 带有 Logo 的生成（推荐）
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo /path/to/logo.png --deliverable "business card" --industry "consulting"
```

```bash
# 生成全套 CIP 交付物
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo /path/to/logo.png --industry "consulting" --set
```

```bash
# 使用 Pro 模型（4K 文本渲染）
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo logo.png --deliverable "business card" --model pro
```

```bash
# 不带 Logo 的生成
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TechFlow" --deliverable "business card" --no-logo-prompt
```

可选模型：`flash`（默认，`gemini-2.5-flash-image`），`pro`（`gemini-3-pro-image-preview`）

### CIP：渲染 HTML 演示文稿

```bash
python3 ~/.claude/skills/design/scripts/cip/render-html.py --brand "TopGroup" --industry "consulting" --images /path/to/cip-output
```

**设计贴士**：如果该品牌尚未生成专属 Logo，请先参考前文的“Logo 设计”流程完成标志的生成。

## 幻灯片演示文稿 (Slides - 内置)

集成了 Chart.js、设计标记 (design tokens) 以及文案写作公式的战略性 HTML 演示文稿。

若要了解具体的创建工作流，请阅读 `references/slides-create.md`。

### 幻灯片：知识库

| 主题 | 文件 |
|-------|------|
| 创建指南 (Creation Guide) | [slides-create.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-create.md) |
| 布局模式 (Layout Patterns) | [slides-layout-patterns.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-layout-patterns.md) |
| HTML 模板 (HTML Template) | [slides-html-template.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-html-template.md) |
| 文案写作 (Copywriting) | [slides-copywriting-formulas.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-copywriting-formulas.md) |
| 演示策略 (Strategies) | [slides-strategies.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-strategies.md) |

## 横幅设计 (Banner Design - 内置)

横跨社交、广告、网页和印刷的 22 种艺术指导风格。使用 `frontend-design`、`ai-artist`、`ai-multimodal`、`chrome-devtools` 技能。

阅读 [banner-sizes-and-styles.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/banner-sizes-and-styles.md) 以获取完整的尺寸和风格参考。

### 横幅：工作流程

1. **需求交互收集**：使用 `AskUserQuestion` 工具交互收集：设计诉求、发布平台、文案内容、品牌定位、视觉风格及产出数量。
2. **设计意向与灵感检索**：激活 `/ui-ux-pro-max` 技能，通过 Pinterest 检索相关的成熟设计进行参考。
3. **原型编码与视觉生成**：使用 `/frontend-design` 技能搭建 HTML/CSS 横幅骨架，并结合 `/ai-artist` 或 `/ai-multimodal` 生成适配的视觉核心资产。
4. **精确截图导出**：调用 `/chrome-devtools` 技能在准确的物理尺寸下进行区域截图，导出为高保真 PNG 图片。
5. **展示迭代**：并排展示所有选项，根据反馈进行迭代。

### 横幅：快速尺寸参考

| 平台 | 类型 | 尺寸 (px) |
|----------|------|-----------|
| Facebook | 封面 (Cover) | 820 x 312 |
| Twitter/X | 头部 (Header) | 1500 x 500 |
| LinkedIn | 个人 (Personal) | 1584 x 396 |
| YouTube | 频道图片 (Channel art) | 2560 x 1440 |
| Instagram | 故事 (Story) | 1080 x 1920 |
| Instagram | 帖子 (Post) | 1080 x 1080 |
| Google 广告 | 中等矩形 (Med Rectangle) | 300 x 250 |
| 网站 | Hero 区域 | 1920 x 600-1080 |

### 横幅：主流艺术风格

| 风格 | 最适合 |
|-------|----------|
| 极极简主义 (Minimalist) | SaaS、科技 |
| 粗体排版 (Bold Typography) | 宣告、通知 |
| 渐变 (Gradient) | 现代品牌 |
| 基于照片 (Photo-Based) | 生活方式、电商 |
| 几何 (Geometric) | 科技、金融科技 |
| 毛玻璃效果 (Glassmorphism) | SaaS、应用 |
| 霓虹/赛博朋克 (Neon/Cyberpunk) | 游戏、活动 |

### 横幅：设计规则

- 安全区 (Safe zones)：关键内容需置于画布中央 70-80% 区域
- 单个横幅只能有一个 CTA，右下角，最小高度 44px
- 最多使用 2 种字体，正文最小 16px，标题大于等于 32px
- 广告图片中的文字比例低于 20%（Meta 会对文字过多的图片进行处罚）
- 印刷：300 DPI、CMYK、3-5mm 出血

## 图标设计 (Icon Design - 内置)

15 种风格，12 种分类。基于 Gemini 3.1 Pro Preview 直接生成 SVG 文本输出。

### 图标：生成单个图标

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "settings gear" --style outlined # 生成线框风格设置齿轮图标
```

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "shopping cart" --style filled --color "#6366F1" # 生成填充风格靛蓝色购物车图标
```

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --name "dashboard" --category navigation --style duotone # 生成导航分类的双色调仪表盘图标
```

### 图标：批量生成变体

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "cloud upload" --batch 4 --output-dir ./icons # 为云上传生成 4 个变体图标并输出至 ./icons
```

### 图标：多尺寸导出

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "user profile" --sizes "16,24,32,48" --output-dir ./icons # 为用户个人资料图标导出多种尺寸
```

### 图标：主流风格

| 风格 | 最适合 |
|-------|----------|
| 线条 (outlined) | UI 界面、Web 应用 |
| 填充 (filled) | 移动端 App、导航栏 |
| 双色调 (duotone) | 营销页面、落地页 |
| 圆润 (rounded) | 亲和力强的应用、医疗健康 |
| 锐利 (sharp) | 科技、金融科技、企业级应用 |
| 扁平 (flat) | 材料设计 (Material Design)、谷歌风格 |
| 渐变 (gradient) | 现代品牌、SaaS |

**使用模型：** `gemini-3.1-pro-preview` —— 仅输出文本格式（SVG 本质是 XML 文本）。无需调用图像生成 API。

## 社交媒体图片 (Social Photos - 内置)

多平台社交媒体图像设计：利用 HTML/CSS 编写样式并导出截图。使用 `ui-ux-pro-max`、`brand`、`design-system`、`chrome-devtools` 技能。

阅读 [social-photos-design.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/social-photos-design.md) 获取关于尺寸、模板和最佳实践的详细指导。

### 社交媒体图片：工作流程

1. **任务编排**：使用 `project-management` 技能创建待办任务；为独立工作派遣并行子代理。
2. **需求分析**：解析提示词中的主题、平台、风格、品牌上下文和内容元素。
3. **概念构思**：构思 3-5 个设计概念，通过 `AskUserQuestion` 展示给用户。
4. **编码设计**：调用 `/ckm:brand` -> `/ckm:design-system` -> 随机调用 `/ck:ui-ux-pro-max` 或 `/ck:frontend-design` 进行设计；为每个概念按尺寸编写 HTML。
5. **图片导出**：使用 `chrome-devtools` 或 Playwright 进行截图，输出精确像素（以 2x 设备缩放因子 `deviceScaleFactor` 导出）。
6. **视觉校验**：使用 Chrome 开发者工具或 `chrome-devtools` 技能视觉检查导出的设计，修复布局或样式问题并重新导出。
7. **成果汇报**：将包含设计决定的总结报告写入 `plans/reports/` 目录下。
8. **文件整理**：调用 `assets-organizing` 技能整理导出的文件和报告。

### 社交媒体图片：核心尺寸

| 平台 | 尺寸 (px) | 平台 | 尺寸 (px) |
|----------|-----------|----------|-----------|
| IG 帖子 (Post) | 1080×1080 | FB 帖子 (Post) | 1200×630 |
| IG 故事 (Story) | 1080×1920 | X 帖子 (Post) | 1200×675 |
| IG 轮播图 (Carousel) | 1080×1350 | LinkedIn 帖子 | 1200×627 |
| YT 缩略图 (Thumb) | 1280×720 | Pinterest 图片 | 1000×1500 |

## 工作流程

### 完整的品牌包装方案

1. **徽标** → 使用 `scripts/logo/generate.py` 生成 Logo 变体。
2. **企业识别系统 (CIP)** → 使用 `scripts/cip/generate.py --logo ...` 创建交付物效果图。
3. **演示文稿** → 阅读 [slides-create.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-create.md) 以构建商业路演幻灯片。

### 新设计系统搭建

1. **品牌** (基于 brand 技能) → 定义配色方案、字体排版以及品牌语气。
2. **标记** (基于 design-system 技能) → 创建语义化 Token 图层。
3. **实现** (基于 ui-styling 技能) → 配置 Tailwind 和 shadcn/ui。

## 参考文档 (References)

| 主题 | 文件 |
|-------|------|
| 设计路由导航 (Design Routing) | [design-routing.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/design-routing.md) |
| Logo 设计指南 (Logo Design Guide) | [logo-design.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/logo-design.md) |
| Logo 风格样式 (Logo Styles) | [logo-style-guide.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/logo-style-guide.md) |
| Logo 色彩心理学 (Logo Colors) | [logo-color-psychology.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/logo-color-psychology.md) |
| Logo 提示词 engineering (Logo Prompts) | [logo-prompt-engineering.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/logo-prompt-engineering.md) |
| CIP 设计指南 (CIP Design Guide) | [cip-design.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/cip-design.md) |
| CIP 交付物指南 (CIP Deliverables) | [cip-deliverable-guide.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/cip-deliverable-guide.md) |
| CIP 风格样式 (CIP Styles) | [cip-style-guide.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/cip-style-guide.md) |
| CIP 提示词 engineering (CIP Prompts) | [cip-prompt-engineering.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/cip-prompt-engineering.md) |
| 幻灯片创建 (Slides Create) | [slides-create.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-create.md) |
| 幻灯片布局 (Slides Layouts) | [slides-layout-patterns.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-layout-patterns.md) |
| 幻灯片 HTML 模板 (Slides Template) | [slides-html-template.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-html-template.md) |
| 幻灯片文案 (Slides Copy) | [slides-copywriting-formulas.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-copywriting-formulas.md) |
| 幻灯片战略 (Slides Strategy) | [slides-strategies.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/slides-strategies.md) |
| 横幅尺寸与风格 (Banner Sizes & Styles) | [banner-sizes-and-styles.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/banner-sizes-and-styles.md) |
| 社交媒体图片指南 (Social Photos Guide) | [social-photos-design.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/social-photos-design.md) |
| 图标设计指南 (Icon Design Guide) | [icon-design.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/icon-design.md) |

## 脚本 (Scripts)

| 脚本 | 用途 |
|--------|---------|
| `scripts/logo/search.py` | 搜索 Logo 风格、配色和行业 |
| `scripts/logo/generate.py` | 使用 Gemini AI 生成 Logo |
| `scripts/logo/core.py` | 用于 Logo 数据的 BM25 搜索引擎 |
| `scripts/cip/search.py` | 搜索 CIP 交付物、风格和行业 |
| `scripts/cip/generate.py` | 使用 Gemini 生成 CIP 效果图 |
| `scripts/cip/render-html.py` | 基于 CIP 效果图渲染 HTML 演示文稿 |
| `scripts/cip/core.py` | 用于 CIP 数据的 BM25 搜索引擎 |
| `scripts/icon/generate.py` | 使用 Gemini 3.1 Pro 生成 SVG 图标 |

## 安装与配置

```bash
export GEMINI_API_KEY="your-key"  # 填入您的 API Key，获取地址：https://aistudio.google.com/apikey
pip install google-genai pillow
```

## 集成与协作

**外部子技能：** brand (品牌)、design-system (设计系统)、ui-styling (UI 样式)
**关联技能：** frontend-design (前端设计)、ui-ux-pro-max (UI/UX 智能设计)、ai-multimodal (AI 多模态)、chrome-devtools (Chrome 开发者工具)
