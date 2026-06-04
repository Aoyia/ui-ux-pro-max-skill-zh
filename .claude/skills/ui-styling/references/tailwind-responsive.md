# Tailwind CSS 响应式设计

移动端优先 (Mobile-First) 的断点、响应式工具类以及自适应布局。

## 移动端优先方法 (Mobile-First Approach)

Tailwind 采用移动端优先的响应式设计。基础样式会应用到所有屏幕尺寸上，然后使用断点前缀在更大的屏幕尺寸上进行样式覆盖。

```html
<!-- 基础: 1 列 (移动端)
     sm: 2 列 (平板端)
     lg: 4 列 (桌面端) -->
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4">
  <div>项目 1</div>
  <div>项目 2</div>
  <div>项目 3</div>
  <div>项目 4</div>
</div>
```

## 断点系统 (Breakpoint System)

**默认断点：**

| 前缀 | 最小宽度 | CSS 媒体查询 |
|--------|-----------|-----------------|
| `sm:` | 640px | `@media (min-width: 640px)` |
| `md:` | 768px | `@media (min-width: 768px)` |
| `lg:` | 1024px | `@media (min-width: 1024px)` |
| `xl:` | 1280px | `@media (min-width: 1280px)` |
| `2xl:` | 1536px | `@media (min-width: 1536px)` |

## 响应式模式 (Responsive Patterns)

### 布局切换 (Layout Changes)

```html
<!-- 移动端垂直排列，桌面端水平排列 -->
<div class="flex flex-col lg:flex-row gap-4">
  <div>左侧</div>
  <div>右侧</div>
</div>

<!-- 1 列 -> 2 列 -> 3 列 -->
<div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-6">
  <div>项目 1</div>
  <div>项目 2</div>
  <div>项目 3</div>
</div>
```

### 可见性控制 (Visibility)

```html
<!-- 移动端隐藏，桌面端显示 -->
<div class="hidden lg:block">
  仅在桌面端显示的内容
</div>

<!-- 移动端显示，桌面端隐藏 -->
<div class="block lg:hidden">
  仅在移动端显示的内容
</div>

<!-- 不同断点显示不同内容 -->
<div class="lg:hidden">移动端菜单</div>
<div class="hidden lg:flex">桌面端导航</div>
```

### 排版 (Typography)

```html
<!-- 响应式字体大小 -->
<h1 class="text-2xl md:text-4xl lg:text-6xl font-bold">
  标题随屏幕尺寸缩放
</h1>

<p class="text-sm md:text-base lg:text-lg">
  正文文本进行适当缩放
</p>
```

### 间距 (Spacing)

```html
<!-- 响应式内边距 -->
<div class="p-4 md:p-6 lg:p-8">
  在更大屏幕上拥有更多内边距
</div>

<!-- 响应式间距 -->
<div class="flex gap-2 md:gap-4 lg:gap-6">
  <div>项目 1</div>
  <div>项目 2</div>
</div>
```

### 宽度 (Width)

```html
<!-- 移动端占满宽度，桌面端限制宽度 -->
<div class="w-full lg:w-1/2 xl:w-1/3">
  响应式宽度
</div>

<!-- 响应式最大宽度 -->
<div class="max-w-sm md:max-w-2xl lg:max-w-4xl mx-auto">
  居中且带响应式最大宽度
</div>
```

## 常见响应式布局 (Common Responsive Layouts)

### 侧边栏布局 (Sidebar Layout)

```html
<div class="flex flex-col lg:flex-row min-h-screen">
  <!-- 侧边栏：移动端满宽，桌面端固定宽度 -->
  <aside class="w-full lg:w-64 bg-gray-100 p-4">
    侧边栏
  </aside>

  <!-- 主内容区 -->
  <main class="flex-1 p-4 md:p-8">
    主内容
  </main>
</div>
```

### 卡片网格 (Card Grid)

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4 md:gap-6">
  <div class="bg-white rounded-lg shadow p-6">卡片 1</div>
  <div class="bg-white rounded-lg shadow p-6">卡片 2</div>
  <div class="bg-white rounded-lg shadow p-6">卡片 3</div>
  <div class="bg-white rounded-lg shadow p-6">卡片 4</div>
</div>
```

### 主视觉区 (Hero Section)

```html
<section class="py-12 md:py-20 lg:py-32">
  <div class="container mx-auto px-4">
    <div class="flex flex-col lg:flex-row items-center gap-8 lg:gap-12">
      <div class="flex-1 text-center lg:text-left">
        <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold mb-4">
          主视觉标题
        </h1>
        <p class="text-lg md:text-xl mb-6">
          主视觉描述信息
        </p>
        <button class="px-6 py-3 md:px-8 md:py-4">
          行动呼吁 (CTA) 按钮
        </button>
      </div>
      <div class="flex-1">
        <img src="hero.jpg" class="w-full rounded-lg" />
      </div>
    </div>
  </div>
</section>
```

### 导航栏 (Navigation)

```html
<nav class="bg-white shadow">
  <div class="container mx-auto px-4">
    <div class="flex items-center justify-between h-16">
      <div class="text-xl font-bold">Logo (标志)</div>

      <!-- 桌面端导航 -->
      <div class="hidden md:flex gap-6">
        <a href="#">首页</a>
        <a href="#">关于我们</a>
        <a href="#">服务</a>
        <a href="#">联系我们</a>
      </div>

      <!-- 移动端菜单按钮 -->
      <button class="md:hidden">
        <svg class="w-6 h-6">...</svg>
      </button>
    </div>
  </div>
</nav>
```

## 最大宽度查询 (Max-Width Queries)

使用 `max-*:` 前缀应用仅在特定断点以下的样式：

```html
<!-- 仅在移动端和平板端生效 (低于 1024px) -->
<div class="max-lg:text-center">
  在移动端/平板端居中对齐，在桌面端左对齐
</div>

<!-- 仅在移动端生效 (低于 640px) -->
<div class="max-sm:hidden">
  仅在移动端隐藏
</div>
```

可用前缀：`max-sm:` `max-md:` `max-lg:` `max-xl:` `max-2xl:`

## 区间查询 (Range Queries)

在断点区间之间应用样式：

```html
<!-- 仅在平板端生效 (介于 md 和 lg 之间) -->
<div class="md:block lg:hidden">
  仅在平板端可见
</div>

<!-- 介于 sm 和 xl 之间 -->
<div class="sm:grid-cols-2 xl:grid-cols-4">
  平板端显示 2 列，超大屏显示 4 列
</div>
```

## 容器查询 (Container Queries)

根据父容器的宽度而非视口宽度来设置元素样式：

```html
<div class="@container">
  <div class="@md:grid-cols-2 @lg:grid-cols-3">
    根据父容器宽度做出响应，而非整个视口
  </div>
</div>
```

容器查询断点：`@sm:` `@md:` `@lg:` `@xl:` `@2xl:`

## 自定义断点 (Custom Breakpoints)

在主题中定义自定义断点：

```css
@theme {
  --breakpoint-3xl: 120rem;  /* 1920px */
  --breakpoint-tablet: 48rem;  /* 768px */
}
```

```html
<div class="tablet:grid-cols-2 3xl:grid-cols-6">
  使用自定义断点
</div>
```

## 响应式状态变体 (Responsive State Variants)

将响应式与悬停 (hover)/聚焦 (focus) 结合：

```html
<!-- 仅在桌面端有悬停放大效果 -->
<button class="lg:hover:scale-105">
  悬停缩放 (仅限桌面端)
</button>

<!-- 在不同断点下有不同的悬停文字颜色 -->
<a class="hover:text-blue-600 lg:hover:text-purple-600">
  链接
</a>
```

## 最佳实践 (Best Practices)

### 1. 移动端优先 design

从移动端样式开始，在更大的断点上逐步增加复杂度：

```html
<!-- 推荐：移动端优先 -->
<div class="text-base md:text-lg lg:text-xl">

<!-- 避免：桌面端优先 -->
<div class="text-xl lg:text-base">
```

### 2. 保持断点使用一致 (Consistent Breakpoint Usage)

在相关元素之间使用相同的断点：

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6 lg:gap-8">
  间距随布局同步缩放
</div>
```

### 3. 在断点临界点进行测试 (Test at Breakpoint Boundaries)

在确切的断点宽度（如 640px, 768px, 1024px 等）进行测试，以发现边缘排版问题。

### 4. 使用 Container 限制内容宽度

```html
<div class="container mx-auto px-4 sm:px-6 lg:px-8">
  <div class="max-w-7xl">
    具有一致最大宽度限制的内容
  </div>
</div>
```

### 5. 渐进式增强 (Progressive Enhancement)

确保核心功能在移动端可用，并在大屏上提供更好的体验：

```html
<!-- 核心布局在移动端能正常工作 -->
<div class="p-4">
  <!-- 桌面端增强内边距 -->
  <div class="lg:p-8">
    内容
  </div>
</div>
```

### 6. 避免使用过多的断点 (Avoid Too Many Breakpoints)

每个元素最好使用 2-3 个断点，以便于维护：

```html
<!-- 推荐：2 个断点 -->
<div class="grid-cols-1 md:grid-cols-2 lg:grid-cols-4">

<!-- 避免：使用过多断点 -->
<div class="grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 2xl:grid-cols-6">
```

## 常见响应式工具类 (Common Responsive Utilities)

### 响应式显示 (Responsive Display)

```html
<div class="block md:flex lg:grid">
  在不同的断点下改变显示类型
</div>
```

### 响应式定位 (Responsive Position)

```html
<div class="relative lg:absolute">
  在不同的断点下定位不同
</div>
```

### 响应式排序 (Responsive Order)

```html
<div class="flex flex-col">
  <div class="order-2 lg:order-1">桌面端排第一</div>
  <div class="order-1 lg:order-2">移动端排第一</div>
</div>
```

### 响应式溢出处理 (Responsive Overflow)

```html
<div class="overflow-auto lg:overflow-visible">
  移动端支持滚动，桌面端展开显示
</div>
```

## 测试清单 (Testing Checklist)

- [ ] 在 320px 测试 (小屏幕手机)
- [ ] 在 640px 测试 (手机断点)
- [ ] 在 768px 测试 (平板断点)
- [ ] 在 1024px 测试 (桌面断点)
- [ ] 在 1280px 测试 (大屏桌面断点)
- [ ] 测试横屏方向
- [ ] 验证触摸目标尺寸 (最小为 44x44px)
- [ ] 检查所有尺寸下的文本可读性
- [ ] 验证导航栏在移动端能正常工作
- [ ] 使用浏览器缩放进行测试
