# 布局模式

25 种包含 CSS 结构和动画类的幻灯片布局。

## 按使用场景选择布局

| 布局 | 使用场景 | 动画 |
|--------|----------|-----------|
| Title Slide (标题页) | 开场/第一印象 | `animate-fade-up` |
| Problem Statement (问题陈述) | 确立痛点 | `animate-stagger` |
| Solution Overview (方案概述) | 引入解决方案 | `animate-scale` |
| Feature Grid (功能网格) | 展示能力 (3-6 张卡片) | `animate-stagger` |
| Metrics Dashboard (指标仪表盘) | 展示 KPI (3-4 个指标) | `animate-stagger-scale` |
| Comparison Table (对比表格) | 对比不同选项 | `animate-fade-up` |
| Timeline Flow (时间线流程) | 展示进展/演进 | `animate-stagger` |
| Team Grid (团队网格) | 介绍团队成员 | `animate-stagger` |
| Quote Testimonial (引言证言) | 客户背书 | `animate-fade-up` |
| Two Column Split (双栏拆分) | 比较/对比 | `animate-fade-up` |
| Big Number Hero (大数字焦点) | 单个强有力的指标 | `animate-count` |
| Product Screenshot (产品截图) | 展示产品 UI | `animate-scale` |
| Pricing Cards (定价卡片) | 展示不同资费档次 | `animate-stagger` |
| CTA Closing (行动呼吁收尾) | 驱动行动 | `animate-pulse` |

## CSS 结构

### Title Slide (标题页)
```css
.slide-title {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
}
```

### Two Column Split (双栏拆分)
```css
.slide-split {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 48px;
    align-items: center;
}
@media (max-width: 768px) {
    .slide-split { grid-template-columns: 1fr; gap: 24px; }
}
```

### Feature Grid (功能网格 - 3 栏)
```css
.slide-features {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
}
@media (max-width: 768px) {
    .slide-features { grid-template-columns: repeat(2, 1fr); gap: 16px; }
}
@media (max-width: 480px) {
    .slide-features { grid-template-columns: 1fr; }
}
```

### Metrics Dashboard (指标仪表盘 - 4 栏)
```css
.slide-metrics {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 16px;
}
@media (max-width: 768px) {
    .slide-metrics { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 480px) {
    .slide-metrics { grid-template-columns: 1fr; }
}
```

## 组件变体

### 卡片样式
| 样式 | CSS 类 | 适用场景 |
|-------|-----------|---------|
| Icon Left (图标居左) | `.card-icon-left` | 带有图标的功能展示 |
| Accent Bar (强调条) | `.card-accent-bar` | 突出显示的功能 |
| Metric Card (指标卡片) | `.card-metric` | 数字/统计数据 |
| Avatar Card (头像卡片) | `.card-avatar` | 团队成员介绍 |
| Pricing Card (定价卡片) | `.card-pricing` | 价格档次展示 |

### 指标样式
| 样式 | 效果 |
|-------|--------|
| `gradient-number` | 数字上的渐变文字效果 |
| `oversized` | 超大字号 (120px+) |
| `sparkline` | 小型行内图表 |
| `funnel-numbers` | 转化阶段 |

## 视觉处理效果

| 处理效果 | 何时使用 |
|-----------|-------------|
| `gradient-glow` | 标题页、行动呼吁 (CTA) |
| `subtle-border` | 问题陈述 |
| `icon-top` | 功能网格 |
| `screenshot-shadow` | 产品截图 |
| `popular-highlight` | 定价 (缩放 1.05) |
| `bg-overlay` | 背景图像 |
| `contrast-pair` | 对比 (Before/After) |
| `logo-grayscale` | 客户 Logo |

## 检索命令

```bash
# 查找特定用途的布局
python .claude/skills/design-system/scripts/search-slides.py "metrics dashboard" -d layout

# 上下文相关推荐
python .claude/skills/design-system/scripts/search-slides.py "traction slide" \
  --context --position 4 --total 10
```

## 布局决策流程

```
1. 幻灯片的目标是什么？
   └─> 搜索 layout-logic.csv

2. 应该触发何种情感？
   └─> 搜索 color-logic.csv

3. 内容类型是什么？
   └─> 搜索 typography.csv

4. 是否应该打破常规模式？
   └─> 检查幻灯片位置 (1/3, 2/3) → 使用全出血 (full-bleed) 布局
```
