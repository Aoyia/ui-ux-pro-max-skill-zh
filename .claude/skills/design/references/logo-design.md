# Logo 设计参考指南

基于 AI 的 Logo 设计，支持 55+ 种风格、30 种调色板、25 个行业指南。使用 Gemini 图像生成模型。

## 脚本

| 脚本 | 用途 |
|--------|---------|
| `scripts/logo/search.py` | 搜索风格、颜色、行业；生成设计简报 |
| `scripts/logo/generate.py` | 使用 Gemini 图像生成模型 生成 Logo |
| `scripts/logo/core.py` | 用于 Logo 数据的 BM25 搜索引擎 |

## 命令行指令

### 设计简报（从此开始）

```bash
python3 ~/.claude/skills/design/scripts/logo/search.py "tech startup modern" --design-brief -p "BrandName"
```

### 搜索领域

```bash
# 风格
python3 ~/.claude/skills/design/scripts/logo/search.py "minimalist clean" --domain style

# 调色板
python3 ~/.claude/skills/design/scripts/logo/search.py "tech professional" --domain color

# 行业指南
python3 ~/.claude/skills/design/scripts/logo/search.py "healthcare medical" --domain industry
```

### 生成 Logo

输出的 Logo **务必**使用白色背景。

```bash
python3 ~/.claude/skills/design/scripts/logo/generate.py --brand "TechFlow" --style minimalist --industry tech
python3 ~/.claude/skills/design/scripts/logo/generate.py --prompt "coffee shop vintage badge" --style vintage
```

参数：`--style`, `--industry`, `--prompt`

## 可选风格

| 类别 | 风格 |
|----------|--------|
| 基础类型 | 极简风格、字标/文本标、首字母标志/字母徽标、图形标志/品牌徽记、抽象标、吉祥物、徽章标、组合标 |
| 美学风格 | 复古/怀旧、装饰艺术（Art Deco）、奢华、俏皮活泼、企业商务风格、有机自然、霓虹、垃圾摇滚（Grunge）、水彩 |
| 现代风格 | 渐变、扁平化设计、3D/等距投影（Isometric）、几何、线条艺术（Line Art）、双色调（Duotone）、适配动效（Motion-Ready） |
| 创意/巧妙 | 负空间、单线设计（Monoline）、拆分/碎片化、响应式/自适应 |

## 色彩心理学

| 颜色 | 心理暗示 | 适用场景 |
|-------|------------|----------|
| 蓝色 | 信任、沉稳 | 金融、科技、医疗健康 |
| 绿色 | 成长、自然 | 环保、康养、有机 |
| 红色 | 活力、热情 | 食品、运动、娱乐 |
| 金色 | 奢华、尊贵 | 时尚、珠宝、高端酒店 |
| 紫色 | 创意、创新 | 美容、创意产业、科技 |

## 行业默认设置

| 行业 | 风格 | 颜色 | 字体排版 |
|----------|-------|--------|------------|
| 科技 | 极简、抽象 | 蓝色系、紫色系、渐变色 | 几何无衬线体 |
| 医疗健康 | 专业风格、线艺 | 蓝色系、绿色系、青色系 | 干净的无衬线体 |
| 金融 | 企业形象、徽章标 | 藏青、金色 | 衬线体或干净的无衬线体 |
| 食品餐饮 | 复古徽章、吉祥物 | 温暖的红、橙色系 | 亲切的手写体 |
| 时尚时装 | 字标、奢华风格 | 黑色、金色、白色 | 优雅的衬线体 |

## 工作流

1. 生成设计简报 → `scripts/logo/search.py --design-brief`
2. 生成 Logo 变体 → `scripts/logo/generate.py --brand --style --industry`
3. 询问用户是否生成 HTML 预览 → 使用 `AskUserQuestion` 工具
4. 如果是，调用 `/ui-ux-pro-max` 生成 HTML 画廊展示页

## 详细参考指南

- [logo-style-guide.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/logo-style-guide.md) - 详细风格描述
- [logo-color-psychology.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/logo-color-psychology.md) - 颜色含义与配色组合
- [logo-prompt-engineering.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/design/references/logo-prompt-engineering.md) - AI 生成提示词

## 环境配置

```bash
export GEMINI_API_KEY="your-key"
pip install google-genai
```
