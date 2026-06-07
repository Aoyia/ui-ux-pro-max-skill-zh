# CIP 设计参考指南

企业形象识别系统（CIP）设计，包含 50+ 种交付物、20 种风格、20 个行业。使用 Gemini 图像生成模型 (Flash/Pro) 生成样机效果图。

## 脚本

| 脚本 | 用途 |
|--------|---------|
| `scripts/cip/search.py` | 搜索交付物、风格、行业；生成 CIP 简报 |
| `scripts/cip/generate.py` | 使用 Gemini (Flash/Pro) 生成 CIP 样机效果图 |
| `scripts/cip/render-html.py` | 从 CIP 样机效果图渲染 HTML 演示文稿 |
| `scripts/cip/core.py` | 用于 CIP 数据的 BM25 搜索引擎 |

## 命令行指令

### CIP 简报（从此开始）

```bash
python3 ~/.claude/skills/design/scripts/cip/search.py "tech startup" --cip-brief -b "BrandName"
```

### 搜索领域

```bash
# 交付物
python3 ~/.claude/skills/design/scripts/cip/search.py "business card letterhead" --domain deliverable

# 设计风格
python3 ~/.claude/skills/design/scripts/cip/search.py "luxury premium elegant" --domain style

# 行业指南
python3 ~/.claude/skills/design/scripts/cip/search.py "hospitality hotel" --domain industry

# 样机上下文
python3 ~/.claude/skills/design/scripts/cip/search.py "office reception" --domain mockup
```

### 生成样机效果图

```bash
# 包含 Logo（推荐 - 使用图像编辑）
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo /path/to/logo.png --deliverable "business card" --industry "consulting"

# 包含 Logo 的完整 CIP 组合
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo /path/to/logo.png --industry "consulting" --set

# 用于 4K 文本渲染的 Pro 模型
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TopGroup" --logo logo.png --deliverable "business card" --model pro

# 带有宽高比的自定义交付物
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "GreenLeaf" --logo logo.png --industry "organic food" --deliverables "letterhead,packaging,vehicle" --ratio 16:9

# 不含 Logo（由 AI 自行生成创意）
python3 ~/.claude/skills/design/scripts/cip/generate.py --brand "TechFlow" --deliverable "business card" --no-logo-prompt
```

### 渲染 HTML 演示文稿

```bash
python3 ~/.claude/skills/design/scripts/cip/render-html.py --brand "TopGroup" --industry "consulting" --images /path/to/cip-output
python3 ~/.claude/skills/design/scripts/cip/render-html.py --brand "TopGroup" --industry "consulting" --images ./topgroup-cip --output presentation.html
```

## 模型

- `flash`（默认）：`gemini-2.5-flash-image` —— 快速、高性价比
- `pro`：`gemini-3-pro-image-preview` —— 高画质、支持 4K 文本渲染

## 交付物类别

| 类别 | 项目 |
|----------|-------|
| 核心识别 | Logo、Logo 变体 |
| 办公用品 | 名片、信纸、信封、文件夹、笔记本、签字笔 |
| 安全/门禁 | 工作牌、挂绳、门禁卡 |
| 办公环境 | 前台标识、路标导视、会议室标牌、墙体画面 |
| 服饰 | Polo 衫、T 恤、帽子、夹克、围裙 |
| 促销礼品 | 帆布袋、礼盒、U 盘、水杯、马克杯、雨伞 |
| 载具 | 轿车、面包车、卡车 |
| 数字化 | 社交媒体、邮件签名、PowerPoint、文档模板 |
| 产品 | 包装盒、标签、吊牌、零售展示架 |
| 活动 | 展位、易拉宝、桌布、背景板 |

## 设计风格

| 风格 | 颜色 | 适用场景 |
|-------|--------|----------|
| 极简商务 | 藏青、白、蓝 | 金融、法律、咨询 |
| 现代科技 | 紫色、青色、绿色 | 科技、初创公司、SaaS |
| 奢华尊贵 | 黑色、金色、白色 | 时尚、珠宝、酒店 |
| 温暖有机 | 棕色、绿色、奶油色 | 食品、有机、手工艺 |
| 醒目动感 | 红色、橙色、黑色 | 运动、娱乐 |

## HTML 演示文稿功能特性

- 包含品牌名称、行业、风格、调性的 Hero 头部区域
- 带有样机效果图的交付物卡片
- 描述信息：设计概念、用途、规格说明
- 响应式桌面/移动端，深色主题
- 图像以 base64 嵌入（单文件便携）

## 工作流

1. 生成 CIP 简报 → `scripts/cip/search.py --cip-brief`
2. 结合 Logo 生成样机效果图 → `scripts/cip/generate.py --brand --logo --industry --set`
3. 渲染 HTML 演示文稿 → `scripts/cip/render-html.py --brand --industry --images`

**提示：** 如果还没有 Logo，先使用内置的 Logo 设计功能生成一个。

## 详细参考指南

- [cip-deliverable-guide.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/cip-deliverable-guide.md) - 交付物规格说明
- [cip-style-guide.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/cip-style-guide.md) - 设计风格说明
- [cip-prompt-engineering.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/cip-prompt-engineering.md) - AI 生成提示词

## 环境配置

```bash
export GEMINI_API_KEY="your-key"
pip install google-genai pillow
```
