# 布局模式

包含 CSS 结构与动画类的 25 种幻灯片布局。

## 按使用场景选择布局

| 布局 | 使用场景 | 动画效果 |
|--------|----------|-----------|
| 标题幻灯片 | 开场/第一印象 | `animate-fade-up` |
| 问题陈述 | 确立痛点 | `animate-stagger` |
| 解决方案概述 | 引入解决方案 | `animate-scale` |
| 功能网格 | 展示核心能力（3-6 个卡片） | `animate-stagger` |
| 指标看板 | 展示 KPI（3-4 个指标） | `animate-stagger-scale` |
| 对比表格 | 对比不同方案 | `animate-fade-up` |
| 时间线流程 | 展示发展历程/进度 | `animate-stagger` |
| 团队网格 | 介绍团队成员 | `animate-stagger` |
| 引用证言 | 客户背书 | `animate-fade-up` |
| 双栏分栏 | 比较/对比 | `animate-fade-up` |
| 大数字突出 | 单个强有力的核心指标 | `animate-count` |
| 产品截图 | 展示产品 UI 界面 | `animate-scale` |
| 定价卡片 | 呈现价格档位 | `animate-stagger` |
| 呼吁行动（CTA）结语 | 促成行动/转化 | `animate-pulse` |

## CSS 结构

### 标题幻灯片
```css
.slide-title {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
}
```

### 双栏分栏
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

### 功能网格（3 栏）
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

### 指标看板（4 栏）
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
| 左侧图标 | `.card-icon-left` | 带有图标的功能展示 |
| 渐变饰条 | `.card-accent-bar` | 突出显示的功能 |
| 指标卡片 | `.card-metric` | 数字/统计数据 |
| 头像卡片 | `.card-avatar` | 团队成员 |
| 定价卡片 | `.card-pricing` | 价格档位 |

### 指标样式
| 样式 | 效果 |
|-------|--------|
| `gradient-number` | 数字使用渐变文字 |
| `oversized` | 超大字号（120px 以上） |
| `sparkline` | 小型行内图表 |
| `funnel-numbers` | 转化阶段漏斗 |

## 视觉处理效果

| 处理效果 | 适用场景 |
|-----------|-------------|
| `gradient-glow` | 标题页、呼吁行动（CTA）页 |
| `subtle-border` | 问题陈述页 |
| `icon-top` | 功能网格页 |
| `screenshot-shadow` | 产品截图页 |
| `popular-highlight` | 定价页（缩放 1.05 倍突出） |
| `bg-overlay` | 背景图遮罩 |
| `contrast-pair` | 对比/前后效果 |
| `logo-grayscale` | 客户 Logo 灰度化 |

## 搜索指令

```bash
# 查找特定用途的布局
python .claude/skills/design-system/scripts/search-slides.py "metrics dashboard" -d layout

# 上下文推荐
python .claude/skills/design-system/scripts/search-slides.py "traction slide" \
  --context --position 4 --total 10
```

## 布局决策流

```
1. 幻灯片的目标是什么？
   └─> 搜索 layout-logic.csv

2. 应该触发什么样的情感共鸣？
   └─> 搜索 color-logic.csv

3. 内容类型是什么？
   └─> 搜索 typography.csv

4. 是否需要打破常规排版？
   └─> 检查页面位置（在前 1/3 或前 2/3 处）→ 使用全屏无边框（full-bleed）排版
```
