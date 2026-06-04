# 组件规格说明

核心组件的详细规格说明，包含状态和变体。

## 按钮 (Button)

### 变体 (Variants)

| 变体 | 背景色 (Background) | 文本色 (Text) | 边框 (Border) | 使用场景 |
|---------|------------|------|--------|----------|
| default | primary | white | none | 主要操作 |
| secondary | gray-100 | gray-900 | none | 次要操作 |
| outline | transparent | foreground | border | 三级操作 |
| ghost | transparent | foreground | none | 微妙/隐蔽操作 |
| link | transparent | primary | none | 导航链接 |
| destructive | red-600 | white | none | 危险/破坏性操作 |

### 尺寸 (Sizes)

| 尺寸 | 高度 | 水平内边距 (Padding X) | 垂直内边距 (Padding Y) | 字体大小 | 图标大小 |
|------|--------|-----------|-----------|-----------|-----------|
| sm | 32px | 12px | 6px | 14px | 16px |
| default | 40px | 16px | 8px | 14px | 18px |
| lg | 48px | 24px | 12px | 16px | 20px |
| icon | 40px | 0 | 0 | - | 18px |

### 状态 (States)

| 状态 | 背景色 (Background) | 文本色 (Text) | 不透明度 (Opacity) | 光标 (Cursor) |
|-------|------------|------|---------|--------|
| default | token | token | 1 | pointer |
| hover | darker | token | 1 | pointer |
| active | darkest | token | 1 | pointer |
| focus | token | token | 1 | pointer |
| disabled | muted | muted-fg | 0.5 | not-allowed |
| loading | token | token | 0.7 | wait |

### 结构解剖 (Anatomy)

```
┌─────────────────────────────────────┐
│  [icon]  标签文本  [icon]            │
└─────────────────────────────────────┘
     ↑                      ↑
  前导图标                后置图标
```

---

## 输入框 (Input)

### 变体 (Variants)

| 变体 | 描述 |
|---------|-------------|
| default | 标准文本输入框 |
| textarea | 多行文本输入框 |
| select | 下拉选择器 |
| checkbox | 复选框/布尔值切换 |
| radio | 单选框 |
| switch | 开关切换器 |

### 尺寸 (Sizes)

| 尺寸 | 高度 | 内边距 (Padding) | 字体大小 |
|------|--------|---------|-----------|
| sm | 32px | 8px 12px | 14px |
| default | 40px | 8px 12px | 14px |
| lg | 48px | 12px 16px | 16px |

### 状态 (States)

| 状态 | 边框 (Border) | 背景色 (Background) | 轮廓环 (Ring) |
|-------|--------|------------|------|
| default | gray-300 | white | none |
| hover | gray-400 | white | none |
| focus | primary | white | primary/20% |
| error | red-500 | white | red/20% |
| disabled | gray-200 | gray-100 | none |

### 结构解剖 (Anatomy)

```
标签 (可选)
┌─────────────────────────────────────┐
│ [图标] 占位符/值           [操作]    │
└─────────────────────────────────────┘
帮助文本或错误信息
```

---

## 卡片 (Card)

### 变体 (Variants)

| 变体 | 阴影 (Shadow) | 边框 (Border) | 使用场景 |
|---------|--------|--------|----------|
| default | sm | 1px | 标准卡片 |
| elevated | lg | none | 突出的内容 |
| outline | none | 1px | 微妙/不显眼的容器 |
| interactive | sm→md | 1px | 可点击的卡片 |

### 结构解剖 (Anatomy)

```
┌─────────────────────────────────────┐
│ 卡片头部                             │
│   标题                               │
│   描述                               │
├─────────────────────────────────────┤
│ 卡片内容                             │
│   主要内容区域                       │
│                                     │
├─────────────────────────────────────┤
│ 卡片底部                             │
│   操作                               │
└─────────────────────────────────────┘
```

### 间距 (Spacing)

| 区域 | 内边距 (Padding) |
|------|---------|
| header | 24px 24px 0 |
| content | 24px |
| footer | 0 24px 24px |
| gap | 16px |

---

## 徽章 (Badge)

### 变体 (Variants)

| 变体 | 背景色 (Background) | 文本色 (Text) |
|---------|------------|------|
| default | primary | white |
| secondary | gray-100 | gray-900 |
| outline | transparent | foreground |
| destructive | red-600 | white |
| success | green-600 | white |
| warning | yellow-500 | gray-900 |

### 尺寸 (Sizes)

| 尺寸 | 内边距 (Padding) | 字体大小 | 高度 |
|------|---------|-----------|--------|
| sm | 4px 8px | 11px | 20px |
| default | 4px 10px | 12px | 24px |
| lg | 6px 12px | 14px | 28px |

---

## 警告框 (Alert)

### 变体 (Variants)

| 变体 | 图标 (Icon) | 背景色 (Background) | 边框 (Border) |
|---------|------|------------|--------|
| default | info | gray-50 | gray-200 |
| destructive | alert | red-50 | red-200 |
| success | check | green-50 | green-200 |
| warning | warning | yellow-50 | yellow-200 |

### 结构解剖 (Anatomy)

```
┌─────────────────────────────────────┐
│ [图标]  标题                      [×]│
│         描述文本                    │
└─────────────────────────────────────┘
```

---

## 对话框 (Dialog)

### 尺寸 (Sizes)

| 尺寸 | 最大宽度 | 使用场景 |
|------|-----------|----------|
| sm | 384px | 简单确认框 |
| default | 512px | 标准对话框 |
| lg | 640px | 复杂表单 |
| xl | 768px | 包含大量数据的对话框 |
| full | 100% - 32px | 移动端全屏 |

### 结构解剖 (Anatomy)

```
┌───────────────────────────────────────┐
│ 对话框头部                         [×]│
│   标题                                 │
│   描述                                 │
├───────────────────────────────────────┤
│ 对话框内容                            │
│   需要时可滚动                         │
│                                       │
├───────────────────────────────────────┤
│ 对话框底部                            │
│                       [取消] [确认]   │
└───────────────────────────────────────┘
```

---

## 表格 (Table)

### 行状态 (Row States)

| 状态 | 背景色 (Background) | 使用场景 |
|-------|------------|----------|
| default | white | 普通行 |
| hover | gray-50 | 鼠标悬停 |
| selected | primary/10% | 选中行 |
| striped | gray-50/white | 斑马纹交替 |

### 单元格对齐方式 (Cell Alignment)

| 内容类型 | 对齐方式 |
|--------------|-----------|
| 文本 | 左对齐 |
| 数字 | 右对齐 |
| 状态/徽章 | 居中对齐 |
| 操作 | 右对齐 |

### 间距 (Spacing)

| 元素 | 数值 |
|---------|-------|
| 单元格内边距 | 12px 16px |
| 表头内边距 | 12px 16px |
| 行高 (紧凑) | 40px |
| 行高 (默认) | 48px |
| 行高 (宽松) | 56px |
