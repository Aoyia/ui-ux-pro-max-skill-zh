---
name: ckm:design-system
description: 设计标记 (Token) 架构、组件规范和演示幻灯片生成。三层 Token 结构（基础级Primitive→语义级Semantic→组件级Component）、CSS 变量、间距/排版比例、组件规范、战略性演示幻灯片创建。适用于设计标记、系统化设计和符合品牌规范的演示文稿。
argument-hint: "[component or token]"
license: MIT
metadata:
  author: claudekit
  version: "1.0.0"
---

# 设计系统 (Design System)

设计标记 (Token) 架构、组件规范、系统化设计、演示幻灯片生成。

## 使用时机

- 设计标记 (Design token) 创建
- 组件状态定义 (Component states)
- CSS 变量系统构建
- 间距与排版比例定义
- 设计到代码的交付与对接
- Tailwind 主题配置
- **演示幻灯片生成 (Slide/presentation generation)**

## 设计标记架构 (Token Architecture)

加载文档：`references/token-architecture.md`

### 三层架构结构

```
Primitive (基础级 - 原始值)
       ↓
Semantic (语义级 - 用途别名)
       ↓
Component (组件级 - 特定组件专用)
```

**示例：**
```css
/* Primitive (基础级) */
--color-blue-600: #2563EB;

/* Semantic (语义级) */
--color-primary: var(--color-blue-600);

/* Component (组件级) */
--button-bg: var(--color-primary);
```

## 快速开始

**生成标记：**
```bash
node scripts/generate-tokens.cjs --config tokens.json -o tokens.css
```

**验证使用规范：**
```bash
node scripts/validate-tokens.cjs --dir src/
```

## 参考文档 (References)

| 主题 | 文件 |
|-------|------|
| 设计标记架构 (Token Architecture) | `references/token-architecture.md` |
| 基础标记 (Primitive Tokens) | `references/primitive-tokens.md` |
| 语义标记 (Semantic Tokens) | `references/semantic-tokens.md` |
| 组件标记 (Component Tokens) | `references/component-tokens.md` |
| 组件规范 (Component Specs) | `references/component-specs.md` |
| 状态与变体 (States & Variants) | `references/states-and-variants.md` |
| Tailwind 集成 (Tailwind Integration) | `references/tailwind-integration.md` |

## 组件规范模式 (Component Spec Pattern)

| 属性 | 默认值 (Default) | 悬停 (Hover) | 激活 (Active) | 禁用 (Disabled) |
|----------|---------|-------|--------|----------|
| 背景 (Background) | primary | primary-dark | primary-darker | muted |
| 文本 (Text) | white | white | white | muted-fg |
| 边框 (Border) | none | none | none | muted-border |
| 阴影 (Shadow) | sm | md | none | none |

## 脚本 (Scripts)

| 脚本 | 用途 |
|--------|---------|
| `generate-tokens.cjs` | 根据 JSON 标记配置生成 CSS 文件 |
| `validate-tokens.cjs` | 检查代码中硬编码 (hardcoded) 的原始值 |
| `search-slides.py` | BM25 搜索与上下文关联的推荐 |
| `slide-token-validator.py` | 验证幻灯片 HTML 是否符合 Token 标记规范 |
| `fetch-background.py` | 从 Pexels/Unsplash 获取背景图片 |

## 模板 (Templates)

| 模板 | 用途 |
|----------|---------|
| `design-tokens-starter.json` | 包含三层结构的初始 JSON 模板 |

## 集成与协作

**与品牌协作：** 从品牌颜色/排版中提取基础级标记 (Primitives)
**与UI样式协作：** 组件标记 (Component tokens) → Tailwind 配置文件

**技能依赖：** brand (品牌)、ui-styling (UI样式)
**核心代理角色：** ui-ux-designer (UI/UX 设计师)、frontend-developer (前端开发人员)

## 幻灯片系统 (Slide System)

使用设计标记 (design tokens) + Chart.js + 上下文决策系统构建符合品牌规范的演示文稿。

### 单一事实来源

| 文件 | 用途 |
|------|---------|
| `docs/brand-guidelines.md` | 品牌识别、语气、配色方案 |
| `assets/design-tokens.json` | 标记定义（基础级Primitive→语义级Semantic→组件级Component） |
| `assets/design-tokens.css` | CSS 变量（导入到幻灯片中） |
| `assets/css/slide-animations.css` | CSS 动画库 |

### 幻灯片搜索 (BM25)

```bash
# 基础搜索 (自动检测领域)
python scripts/search-slides.py "investor pitch"

# 针对特定领域的搜索
python scripts/search-slides.py "problem agitation" -d copy # 搜索文案领域
python scripts/search-slides.py "revenue growth" -d chart # 搜索图表领域

# 上下文关联搜索 (高级系统)
python scripts/search-slides.py "problem slide" --context --position 2 --total 9 # 第2张幻灯片的上下文搜索
python scripts/search-slides.py "cta" --context --position 9 --prev-emotion frustration # 前一个情感为挫败时的CTA搜索
```

### 决策系统 CSV 文件列表

| 文件 | 用途 |
|------|---------|
| `data/slide-strategies.csv` | 15 种幻灯片框架 + 情感起伏弧线 + 情感律动点 (sparkline beats) |
| `data/slide-layouts.csv` | 25 种布局 + 组件变体 + 动画效果 |
| `data/slide-layout-logic.csv` | 目标 → 布局配置 + break_pattern (打破规律模式) 标记 |
| `data/slide-typography.csv` | 内容类型 → 字体排版比例 |
| `data/slide-color-logic.csv` | 情感表达 → 配色方案处理方式 |
| `data/slide-backgrounds.csv` | 幻灯片类型 → 图片分类（Pexels/Unsplash） |
| `data/slide-copy.csv` | 25 种文案写作公式 (如 PAS、AIDA、FAB 模式) |
| `data/slide-charts.csv` | 25 种图表类型及对应的 Chart.js 配置 |

### 上下文决策流

```
1. 解析目标与上下文
        ↓
2. 检索 slide-strategies.csv → 获取幻灯片策略及情感节奏点
        ↓
3. 针对每张幻灯片：
   a. 查询 slide-layout-logic.csv → 确定布局与 break_pattern
   b. 查询 slide-typography.csv → 确定排版比例
   c. 查询 slide-color-logic.csv → 确定色彩方案处理方式
   d. 查询 slide-backgrounds.csv → 如有需要，获取背景图片分类
   e. 从 slide-animations.css 应用相应的 CSS 动画类
        ↓
4. 生成集成了设计标记 (Design Tokens) 的 HTML
        ↓
5. 使用 slide-token-validator.py 进行合规性验证
```

### 打破规律模式 (Duarte Sparkline 情感曲线)

高阶幻灯片会在不同的情感律动之间交替以增强互动：
```
"What Is" (当前痛点/挫败) ↔ "What Could Be" (未来愿景/希望)
```

系统会自动在整体进度的 1/3 和 2/3 位置计算打破规律的情感律动点。

### 幻灯片基本要求

**所有幻灯片必须：**
1. 导入 `assets/design-tokens.css` - 作为单一的事实来源 (source of truth)
2. 统一使用 CSS 变量：`var(--color-primary)`、`var(--slide-bg)` 等
3. 使用 Chart.js 来绘制图表（绝对不可使用纯 CSS 条形图）
4. 包含导航控制（键盘左右方向键、点击操作、进度条）
5. 居中对齐内容
6. 聚焦于说服与转化率 (persuasion/conversion)

### Chart.js 集成

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>

<canvas id="revenueChart"></canvas>
<script>
new Chart(document.getElementById('revenueChart'), {
    type: 'line',
    data: {
        labels: ['Sep', 'Oct', 'Nov', 'Dec'],
        datasets: [{
            data: [5, 12, 28, 45],
            borderColor: '#FF6B6B',  // 使用品牌珊瑚色
            backgroundColor: 'rgba(255, 107, 107, 0.1)',
            fill: true,
            tension: 0.4
        }]
    }
});
</script>
```

### Token 合规规范

```css
/* 正确做法 - 使用 Token */
background: var(--slide-bg);
color: var(--color-primary);
font-family: var(--typography-font-heading);

/* 错误做法 - 硬编码 */
background: #0D0D0D;
color: #FF6B6B;
font-family: 'Space Grotesk';
```

### 参考实现

包含所有特性的运行示例：
```
assets/designs/slides/claudekit-pitch-251223.html
```

### 命令

```bash
/slides:create "10-slide investor pitch for ClaudeKit Marketing" # 为 ClaudeKit Marketing 创建一个 10 页的投资者路演幻灯片
```

## 最佳实践

1. 组件中绝对不要使用硬编码的 Hex 色值 - 必须始终引用 Token 标记
2. 语义层 (Semantic layer) 能够方便地实现主题切换（亮色/暗色模式）
3. 组件标记 (Component tokens) 支持对单个组件进行个性化定制
4. 使用 HSL 格式以便于对不透明度 (opacity) 进行精确控制
5. 为每个 Token 的用途撰写文档
6. **演示幻灯片必须引入 design-tokens.css，且必须全部使用 var() 变量**
