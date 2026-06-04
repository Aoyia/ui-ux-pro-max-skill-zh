# 调色板管理

关于定义、提取和强制执行品牌颜色的指南。

## 颜色系统结构

### 层级结构
```
主色 (Primary Colors) (1-2)
├── 主要品牌色 - 用于呼吁操作 (CTA)、页眉、关键元素
└── 辅助主色 - 次要强调

辅助色 (Secondary Colors) (2-3)
├── 强调色 - 突出显示、交互状态
└── 辅助视觉效果 - 图标、插图

中性调色板 (Neutral Palette) (3-5)
├── 背景色 - 页面、卡片、模态框背景
├── 文本颜色 - 标题、正文、暗色文本
└── UI 元素 - 边框、分割线、阴影

语义色 (Semantic Colors) (4)
├── 成功 - #22C55E (绿色)
├── 警告 - #F59E0B (琥珀色)
├── 错误 - #EF4444 (红色)
└── 信息 - #3B82F6 (蓝色)
```

## 颜色文档格式

### Markdown 表格
| 名称 | 十六进制 (Hex) | RGB | HSL | 用途 |
|------|-----|-----|-----|-------|
| 主要蓝 | #2563EB | rgb(37,99,235) | hsl(217,91%,53%) | CTA、链接 |

### CSS 变量
```css
:root {
  /* 主色 */
  --color-primary: #2563EB;
  --color-primary-light: #3B82F6;
  --color-primary-dark: #1D4ED8;

  /* 辅助色 */
  --color-secondary: #8B5CF6;
  --color-accent: #F59E0B;

  /* 中性色 */
  --color-background: #FFFFFF;
  --color-surface: #F9FAFB;
  --color-text-primary: #111827;
  --color-text-secondary: #6B7280;
  --color-border: #E5E7EB;
}
```

### Tailwind 配置
```javascript
colors: {
  primary: {
    DEFAULT: '#2563EB',
    50: '#EFF6FF',
    100: '#DBEAFE',
    500: '#3B82F6',
    600: '#2563EB',
    700: '#1D4ED8',
  }
}
```

## 无障碍设计要求

### 对比度 (WCAG 2.1)
| 级别 | 普通文本 | 大文本 | UI 组件 |
|-------|-------------|------------|---------------|
| AA | 4.5:1 | 3:1 | 3:1 |
| AAA | 7:1 | 4.5:1 | 4.5:1 |

### 对比度检查
```javascript
// 相对亮度的计算公式
function luminance(r, g, b) {
  const [rs, gs, bs] = [r, g, b].map(v => {
    v /= 255;
    return v <= 0.03928 ? v / 12.92 : Math.pow((v + 0.055) / 1.055, 2.4);
  });
  return 0.2126 * rs + 0.7152 * gs + 0.0722 * bs;
}

function contrastRatio(l1, l2) {
  const lighter = Math.max(l1, l2);
  const darker = Math.min(l1, l2);
  return (lighter + 0.05) / (darker + 0.05);
}
```

## 颜色提取

### 从图像中提取
使用 `extract-colors.cjs` 脚本：
1. 加载图像文件
2. 使用 k-means 聚类算法提取主导颜色
3. 映射到最接近的品牌颜色
4. 报告品牌契合度百分比

### 从品牌指南中提取
解析 Markdown 文件以提取：
- 表格中的十六进制值
- CSS 变量定义
- 颜色名称和用途描述

## 品牌合规性验证

### 规则
1. **主色比例**：占设计的 60-70%
2. **辅助色比例**：占设计的 20-30%
3. **强调色比例**：占设计的 5-10%
4. **不合规颜色容差**：非调色板颜色最多占 20%

### 验证输出
```json
{
  "compliance": 85,
  "colors": {
    "brand": ["#2563EB", "#8B5CF6", "#FFFFFF"],
    "offBrand": ["#FF5500"],
    "dominant": "#2563EB"
  },
  "issues": [
    "检测到非品牌色 #FF5500 (覆盖率 15%)",
    "主色使用不足 (45%，目标为 60%)"
  ]
}
```

## 颜色使用指南

### 推荐做法 (Do's)
- 在主要 CTA 和关键元素上使用主色
- 保持一致的悬停 (hover)/激活 (active) 状态
- 测试所有搭配的无障碍可达性对比度
- 记录颜色决策的文档

### 避免做法 (Don'ts)
- 单个组件中避免使用超过 2-3 种颜色
- 避免在没有明确意图的情况下混用冷暖色调
- 文本避免使用纯黑 (#000)（使用 #111 或类似的暗色）
- 避免仅靠颜色传递信息（也应使用图标/文字）

## 调色板示例

### 科技 / SaaS
```
主色: #2563EB (蓝色)
辅助色: #8B5CF6 (紫色)
强调色: #10B981 (祖母绿)
背景色: #F9FAFB
文本色: #111827
```

### 营销 / 创意
```
主色: #F97316 (橙色)
辅助色: #EC4899 (粉色)
强调色: #14B8A6 (蓝绿色)
背景色: #FFFFFF
文本色: #1F2937
```

### 专业 / 企业商务
```
主色: #1E40AF (藏青色)
辅助色: #475569 (石板灰)
强调色: #0EA5E9 (天蓝色)
背景色: #F8FAFC
文本色: #0F172A
```

## 工具与资源

- [Coolors](https://coolors.co) - 调色板生成器
- [WebAIM 对比度检查器](https://webaim.org/resources/contrastchecker/)
- [Tailwind 颜色参考](https://tailwindcss.com/docs/customizing-colors)
- [Color Hunt](https://colorhunt.co) - 精选调色板
