# 状态与变体

组件状态定义及变体模式。

## 交互状态

### 状态定义

| 状态 | 触发条件 | 视觉变化 |
|-------|---------|---------------|
| default | 无 | 基础外观 |
| hover | 鼠标悬停 | 颜色轻微变化 |
| focus | Tab键/点击 | 聚焦环 |
| active | 鼠标按下 | 最深颜色 |
| disabled | disabled 属性 | 降低不透明度 |
| loading | 异步操作 | 旋转指示器 (Spinner) + 不透明度 |

### 状态优先级

当应用多个状态时，优先级 (从高到低)：

1. disabled
2. loading
3. active
4. focus
5. hover
6. default

### 状态过渡 (State Transitions)

```css
/* 交互元素的标准过渡 */
.interactive {
  transition-property: color, background-color, border-color, box-shadow;
  transition-duration: var(--duration-fast);
  transition-timing-function: ease-in-out;
}
```

| 过渡效果 | 持续时间 | 缓动函数 (Easing) |
|------------|----------|--------|
| 颜色变化 | 150ms | ease-in-out |
| 背景 | 150ms | ease-in-out |
| 变换 (Transform) | 200ms | ease-out |
| 不透明度 | 150ms | ease |
| 阴影 | 200ms | ease-out |

## 聚焦状态

### 聚焦环规格

```css
/* 标准聚焦 ring */
.focusable:focus-visible {
  outline: none;
  box-shadow: 0 0 0 var(--ring-offset) var(--color-background),
              0 0 0 calc(var(--ring-offset) + var(--ring-width)) var(--ring-color);
}
```

| 属性 | 数值 |
|----------|-------|
| 聚焦环宽度 (Ring width) | 2px |
| 聚焦环偏移 (Ring offset) | 2px |
| 聚焦环颜色 (Ring color) | primary (blue-500) |
| 偏移颜色 (Offset color) | background |

### 内部聚焦 (Focus Within)

```css
/* 子元素被聚焦时容器的聚焦样式 */
.container:focus-within {
  border-color: var(--color-ring);
}
```

## 禁用状态

### 视觉处理

```css
.disabled {
  opacity: var(--opacity-disabled); /* 0.5 */
  pointer-events: none;
  cursor: not-allowed;
}
```

| 属性 | 禁用时的值 |
|----------|----------------|
| 不透明度 (Opacity) | 50% |
| 指针事件 (Pointer events) | none |
| 光标 (Cursor) | not-allowed |
| 背景 (Background) | muted |
| 颜色 (Color) | muted-foreground |

### 无障碍设计 (Accessibility)

- 使用 `aria-disabled="true"` 进行语义上的禁用
- 对表单元素使用 `disabled` 属性
- 保持足够对比度 (最低 3:1)

## 加载状态

### 旋转指示器 (Spinner) 放置位置

| 组件 | 旋转指示器位置 |
|-----------|------------------|
| 按钮 (Button) | 替换图标或居中 |
| 输入框 (Input) | 后置位置 |
| 卡片 (Card) | 居中遮罩 |
| 页面 (Page) | 视口中央 |

### 加载状态处理

```css
.loading {
  position: relative;
  pointer-events: none;
}

.loading::after {
  content: '';
  /* 旋转指示器样式 */
}

.loading > * {
  opacity: 0.7;
}
```

## 错误状态

### 视觉指示器

```css
.error {
  border-color: var(--color-error);
  color: var(--color-error);
}

.error:focus-visible {
  box-shadow: 0 0 0 2px var(--color-background),
              0 0 0 4px var(--color-error);
}
```

| 元素 | 错误处理 |
|---------|-----------------|
| 输入框边框 (Input border) | red-500 |
| 输入框聚焦环 (Input focus ring) | red/20% |
| 帮助文本 (Helper text) | red-600 |
| 图标 (Icon) | red-500 |

### 错误信息

- 放置在输入框下方
- 使用错误状态色
- 包含图标以优化无障碍体验
- 在输入有效时清除错误

## 变体模式

### 颜色变体

```css
/* 颜色变体的模式 */
.component {
  --component-bg: var(--color-primary);
  --component-fg: var(--color-primary-foreground);
  background: var(--component-bg);
  color: var(--component-fg);
}

.component.secondary {
  --component-bg: var(--color-secondary);
  --component-fg: var(--color-secondary-foreground);
}

.component.destructive {
  --component-bg: var(--color-destructive);
  --component-fg: var(--color-destructive-foreground);
}
```

### 尺寸变体

```css
/* 尺寸变体的模式 */
.component {
  --component-height: 40px;
  --component-padding: var(--space-4);
  --component-font: var(--font-size-sm);
}

.component.sm {
  --component-height: 32px;
  --component-padding: var(--space-3);
  --component-font: var(--font-size-xs);
}

.component.lg {
  --component-height: 48px;
  --component-padding: var(--space-6);
  --component-font: var(--font-size-base);
}
```

## 无障碍要求

### 色彩对比度

| 元素 | 最低比例 |
|---------|---------------|
| 普通文本 | 4.5:1 |
| 大文本 (18px+) | 3:1 |
| UI 组件 | 3:1 |
| 聚焦指示器 | 3:1 |

### 状态指示器

- 绝不单单依赖颜色
- 使用图标、文本或图案
- 确保聚焦状态清晰可见
- 提供加载状态的屏幕阅读器播报

### ARIA 状态

```html
<!-- 禁用 -->
<button disabled aria-disabled="true">Submit</button>

<!-- 加载中 -->
<button aria-busy="true" aria-describedby="loading-text">
  <span id="loading-text" class="sr-only">加载中...</span>
</button>

<!-- 错误 -->
<input aria-invalid="true" aria-describedby="error-msg">
<span id="error-msg" role="alert">错误信息</span>
```
