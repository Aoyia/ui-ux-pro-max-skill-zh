# Token 架构

面向可扩展、可主题化设计系统的三层 Token 系统。

## 分层概述

```
┌─────────────────────────────────────────┐
│  组件 Token                             │  单组件级覆盖
│  --button-bg, --card-padding            │
├─────────────────────────────────────────┤
│  语义 Token                             │  基于用途的别名
│  --color-primary, --spacing-section     │
├─────────────────────────────────────────┤
│  基础 Token                             │  原始设计数值
│  --color-blue-600, --space-4            │
└─────────────────────────────────────────┘
```

## 为什么采用三层架构？

| 层级 | 作用 | 何时修改 |
|-------|---------|----------------|
| 基础 (Primitive) | 基础数值 (颜色、尺寸) | 极少修改 - 属于基石 |
| 语义 (Semantic) | 赋予具体含义 | 切换主题时 |
| 组件 (Component) | 组件定制 | 满足单个组件的特殊需求时 |

## 第一层：基础 Token (Primitive Tokens)

不带语义信息的原始设计数值。

```css
:root {
  /* 颜色 */
  --color-gray-50: #F9FAFB;
  --color-gray-900: #111827;
  --color-blue-500: #3B82F6;
  --color-blue-600: #2563EB;

  /* 间距 (以 4px 为基础) */
  --space-1: 0.25rem;  /* 4px */
  --space-2: 0.5rem;   /* 8px */
  --space-4: 1rem;     /* 16px */
  --space-6: 1.5rem;   /* 24px */

  /* 排版 */
  --font-size-sm: 0.875rem;
  --font-size-base: 1rem;
  --font-size-lg: 1.125rem;

  /* 圆角 */
  --radius-sm: 0.25rem;
  --radius-default: 0.5rem;
  --radius-lg: 0.75rem;

  /* 阴影 */
  --shadow-sm: 0 1px 2px rgb(0 0 0 / 0.05);
  --shadow-default: 0 1px 3px rgb(0 0 0 / 0.1);
}
```

## 第二层：语义 Token (Semantic Tokens)

引用基础 Token 的基于用途的别名。

```css
:root {
  /* 背景 */
  --color-background: var(--color-gray-50);
  --color-foreground: var(--color-gray-900);

  /* 主色 */
  --color-primary: var(--color-blue-600);
  --color-primary-hover: var(--color-blue-700);

  /* 次要色 */
  --color-secondary: var(--color-gray-100);
  --color-secondary-foreground: var(--color-gray-900);

  /* 暗淡/置灰 */
  --color-muted: var(--color-gray-100);
  --color-muted-foreground: var(--color-gray-500);

  /* 破坏性/危险 */
  --color-destructive: var(--color-red-600);
  --color-destructive-foreground: white;

  /* 间距 */
  --spacing-component: var(--space-4);
  --spacing-section: var(--space-6);
}
```

## 第三层：组件 Token (Component Tokens)

引用语义层的组件专属 Token。

```css
:root {
  /* 按钮 */
  --button-bg: var(--color-primary);
  --button-fg: white;
  --button-hover-bg: var(--color-primary-hover);
  --button-padding-x: var(--space-4);
  --button-padding-y: var(--space-2);
  --button-radius: var(--radius-default);

  /* 输入框 */
  --input-bg: var(--color-background);
  --input-border: var(--color-gray-300);
  --input-focus-ring: var(--color-primary);
  --input-padding: var(--space-2) var(--space-3);

  /* 卡片 */
  --card-bg: var(--color-background);
  --card-border: var(--color-gray-200);
  --card-padding: var(--space-4);
  --card-radius: var(--radius-lg);
  --card-shadow: var(--shadow-default);
}
```

## 暗黑模式

在暗黑主题下覆盖语义 Token：

```css
.dark {
  --color-background: var(--color-gray-900);
  --color-foreground: var(--color-gray-50);
  --color-muted: var(--color-gray-800);
  --color-muted-foreground: var(--color-gray-400);
  --color-secondary: var(--color-gray-800);
}
```

## 命名规范

```
--{类别}-{条目}-{变体}-{状态}

示例：
--color-primary           # 类别-条目 (category-item)
--color-primary-hover     # 类别-条目-状态 (category-item-state)
--button-bg-hover         # 组件-属性-状态 (component-property-state)
--space-section-sm        # 类别-语义-变体 (category-semantic-variant)
```

## 类别

| 类别 | 示例 |
|----------|----------|
| color (颜色) | primary, secondary, muted, destructive |
| space (空间/间距) | 1, 2, 4, 8, section, component |
| font-size (字体大小) | xs, sm, base, lg, xl |
| radius (圆角) | sm, default, lg, full |
| shadow (阴影) | sm, default, lg |
| duration (持续时间) | fast, normal, slow |

## 文件组织结构

```
tokens/
├── primitives.css     # 基础 Token (原始数值)
├── semantic.css       # 语义 Token (用途别名)
├── components.css     # 组件 Token (专属 Token)
└── index.css          # 导入所有 Token 文件的入口文件
```

或者使用带有层级注释的单个文件：

```css
/* === 基础 Token (PRIMITIVES) === */
:root { ... }

/* === 语义 Token (SEMANTIC) === */
:root { ... }

/* === 组件 Token (COMPONENTS) === */
:root { ... }

/* === 暗黑模式 (DARK MODE) === */
.dark { ... }
```

## 从扁平化 Token 进行迁移

迁移前 (扁平化):
```css
--button-primary-bg: #2563EB;
--button-secondary-bg: #F3F4F6;
```

迁移后 (三层):
```css
/* 基础 Token (Primitive) */
--color-blue-600: #2563EB;
--color-gray-100: #F3F4F6;

/* 语义 Token (Semantic) */
--color-primary: var(--color-blue-600);
--color-secondary: var(--color-gray-100);

/* 组件 Token (Component) */
--button-bg: var(--color-primary);
--button-secondary-bg: var(--color-secondary);
```

## 对齐 W3C DTCG 规范

Token JSON 格式 (W3C 设计 Token 社区小组规范):

```json
{
  "color": {
    "blue": {
      "600": {
        "$value": "#2563EB",
        "$type": "color"
      }
    }
  }
}
```
