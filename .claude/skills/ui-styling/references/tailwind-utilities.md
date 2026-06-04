# Tailwind CSS 工具类参考指南

用于布局 (Layout)、间距 (Spacing)、排版 (Typography)、颜色 (Colors)、边框 (Borders) 和阴影 (Shadows) 的核心工具类。

## 布局工具类 (Layout Utilities)

### 块级与行内 (Display)

```html
<div class="block">Block (块级)</div>
<div class="inline-block">Inline Block (行内块级)</div>
<div class="inline">Inline (行内)</div>
<div class="flex">Flexbox</div>
<div class="inline-flex">Inline Flex</div>
<div class="grid">Grid (网格)</div>
<div class="inline-grid">Inline Grid</div>
<div class="hidden">Hidden (隐藏)</div>
```

### 弹性盒模型 (Flexbox)

**容器 (Container)：**
```html
<div class="flex flex-row">Row (默认水平方向)</div>
<div class="flex flex-col">Column (垂直方向)</div>
<div class="flex flex-row-reverse">Reverse row (水平反向)</div>
<div class="flex flex-col-reverse">Reverse column (垂直反向)</div>
```

**对齐主轴 (Justify - main axis)：**
```html
<div class="flex justify-start">Start (起点对齐)</div>
<div class="flex justify-center">Center (居中对齐)</div>
<div class="flex justify-end">End (终点对齐)</div>
<div class="flex justify-between">Space between (两端对齐，项目之间间距相等)</div>
<div class="flex justify-around">Space around (每个项目两侧间距相等)</div>
<div class="flex justify-evenly">Space evenly (项目之间及两端间距均等)</div>
```

**对齐交叉轴 (Align - cross axis)：**
```html
<div class="flex items-start">Start (起点对齐)</div>
<div class="flex items-center">Center (居中对齐)</div>
<div class="flex items-end">End (终点对齐)</div>
<div class="flex items-baseline">Baseline (基线对齐)</div>
<div class="flex items-stretch">Stretch (拉伸对齐)</div>
```

**间距 (Gap)：**
```html
<div class="flex gap-4">四边间距</div>
<div class="flex gap-x-6 gap-y-2">X 轴与 Y 轴间距</div>
```

**换行 (Wrap)：**
```html
<div class="flex flex-wrap">Wrap (换行)</div>
<div class="flex flex-nowrap">No wrap (不换行)</div>
```

### 网格布局 (Grid)

**网格列 (Columns)：**
```html
<div class="grid grid-cols-1">1 列</div>
<div class="grid grid-cols-2">2 列</div>
<div class="grid grid-cols-3">3 列</div>
<div class="grid grid-cols-4">4 列</div>
<div class="grid grid-cols-12">12 列</div>
<div class="grid grid-cols-[1fr_500px_2fr]">自定义列宽</div>
```

**网格行 (Rows)：**
```html
<div class="grid grid-rows-3">3 行</div>
<div class="grid grid-rows-[auto_1fr_auto]">自定义行高</div>
```

**跨度 (Span)：**
```html
<div class="col-span-2">跨 2 列</div>
<div class="row-span-3">跨 3 行</div>
```

**网格间距 (Gap)：**
```html
<div class="grid gap-4">四边间距</div>
<div class="grid gap-x-8 gap-y-4">X 轴与 Y 轴间距</div>
```

### 定位 (Positioning)

```html
<div class="static">Static (默认定位)</div>
<div class="relative">Relative (相对定位)</div>
<div class="absolute">Absolute (绝对定位)</div>
<div class="fixed">Fixed (固定定位)</div>
<div class="sticky">Sticky (粘性定位)</div>

<!-- 定位坐标值 -->
<div class="absolute top-0 right-0">右上角</div>
<div class="absolute inset-0">四边均为 0</div>
<div class="absolute inset-x-4">左右边距为 4</div>
<div class="absolute inset-y-8">上下边距为 8</div>
```

### 层叠顺序 (Z-Index)

```html
<div class="z-0">z-index: 0</div>
<div class="z-10">z-index: 10</div>
<div class="z-20">z-index: 20</div>
<div class="z-50">z-index: 50</div>
```

## Spacing 间距工具类

### 内边距 (Padding)

```html
<div class="p-4">四边内边距</div>
<div class="px-6">左右内边距</div>
<div class="py-3">上下内边距</div>
<div class="pt-8">上内边距</div>
<div class="pr-4">右内边距</div>
<div class="pb-2">下内边距</div>
<div class="pl-6">左内边距</div>
```

### 外边距 (Margin)

```html
<div class="m-4">四边外边距</div>
<div class="mx-auto">水平居中</div>
<div class="my-6">上下外边距</div>
<div class="mt-8">上外边距</div>
<div class="-mt-4">负数上外边距</div>
<div class="ml-auto">推至最右侧</div>
```

### 子元素间距 (Space Between)

```html
<div class="space-x-4">水平子元素间距</div>
<div class="space-y-6">垂直子元素间距</div>
```

### 间距比例尺 (Spacing Scale)

- `0`: 0px
- `px`: 1px
- `0.5`: 0.125rem (2px)
- `1`: 0.25rem (4px)
- `2`: 0.5rem (8px)
- `3`: 0.75rem (12px)
- `4`: 1rem (16px)
- `6`: 1.5rem (24px)
- `8`: 2rem (32px)
- `12`: 3rem (48px)
- `16`: 4rem (64px)
- `24`: 6rem (96px)

## Typography 排版工具类

### 字体大小 (Font Size)

```html
<p class="text-xs">Extra small (超小，12px)</p>
<p class="text-sm">Small (小号，14px)</p>
<p class="text-base">Base (默认，16px)</p>
<p class="text-lg">Large (大号，18px)</p>
<p class="text-xl">XL (超大，20px)</p>
<p class="text-2xl">2XL (24px)</p>
<p class="text-3xl">3XL (30px)</p>
<p class="text-4xl">4XL (36px)</p>
<p class="text-5xl">5XL (48px)</p>
```

### 字体粗细 (Font Weight)

```html
<p class="font-thin">Thin (极细，100)</p>
<p class="font-light">Light (细体，300)</p>
<p class="font-normal">Normal (常规，400)</p>
<p class="font-medium">Medium (中等，500)</p>
<p class="font-semibold">Semibold (半粗，600)</p>
<p class="font-bold">Bold (粗体，700)</p>
<p class="font-black">Black (极粗，900)</p>
```

### 文本对齐 (Text Alignment)

```html
<p class="text-left">左对齐</p>
<p class="text-center">居中对齐</p>
<p class="text-right">右对齐</p>
<p class="text-justify">两端对齐</p>
```

### 行高 (Line Height)

```html
<p class="leading-none">1 (无行距)</p>
<p class="leading-tight">1.25 (紧凑)</p>
<p class="leading-normal">1.5 (常规)</p>
<p class="leading-relaxed">1.75 (宽松)</p>
<p class="leading-loose">2 (松散)</p>
```

### 组合字体工具类

```html
<h1 class="text-4xl/tight font-bold">
  字体大小为 4xl 且带有紧凑行高
</h1>
```

### 文本转换 (Text Transform)

```html
<p class="uppercase">UPPERCASE (大写)</p>
<p class="lowercase">lowercase (小写)</p>
<p class="capitalize">Capitalize (首字母大写)</p>
<p class="normal-case">Normal (默认)</p>
```

### 文本修饰 (Text Decoration)

```html
<p class="underline">Underline (下划线)</p>
<p class="line-through">Line through (删除线)</p>
<p class="no-underline">No underline (无装饰)</p>
```

### 文本溢出 (Text Overflow)

```html
<p class="truncate">用省略号截断超长文本...</p>
<p class="line-clamp-3">限制显示为 3 行...</p>
<p class="text-ellipsis overflow-hidden">溢出省略</p>
```

## Colors 颜色工具类

### 文本颜色 (Text Colors)

```html
<p class="text-black">黑色</p>
<p class="text-white">白色</p>
<p class="text-gray-500">灰色 500</p>
<p class="text-red-600">红色 600</p>
<p class="text-blue-500">蓝色 500</p>
<p class="text-green-600">绿色 600</p>
```

### 背景颜色 (Background Colors)

```html
<div class="bg-white">白色</div>
<div class="bg-gray-100">灰色 100</div>
<div class="bg-blue-500">蓝色 500</div>
<div class="bg-red-600">红色 600</div>
```

### 颜色级别 (Color Scale)

每种颜色有 11 个色阶 (50-950)：
- `50`：最浅
- `100-400`：浅色渐变
- `500`：基准色
- `600-800`：深色渐变
- `950`：最深

### 不透明度修饰符 (Opacity Modifiers)

```html
<div class="bg-black/75">75% 不透明度</div>
<div class="text-blue-500/30">30% 不透明度</div>
<div class="bg-purple-500/[0.87]">87% 不透明度</div>
```

### 渐变 (Gradients)

```html
<div class="bg-gradient-to-r from-blue-500 to-purple-600">
  自左向右渐变
</div>
<div class="bg-gradient-to-br from-pink-500 via-red-500 to-yellow-500">
  带有中间过渡色的渐变
</div>
```

方向：`to-t | to-tr | to-r | to-br | to-b | to-bl | to-l | to-tl`

## Borders 边框工具类

### 边框宽度 (Border Width)

```html
<div class="border">四边均为 1px</div>
<div class="border-2">四边均为 2px</div>
<div class="border-t">仅顶部边框</div>
<div class="border-r-4">右侧边框 4px</div>
<div class="border-b-2">底部边框 2px</div>
<div class="border-l">仅左侧边框</div>
<div class="border-0">无边框</div>
```

### 边框颜色 (Border Color)

```html
<div class="border border-gray-300">灰色</div>
<div class="border-2 border-blue-500">蓝色</div>
<div class="border border-red-600/50">带透明度的红色</div>
```

### 圆角半径 (Border Radius)

```html
<div class="rounded">0.25rem</div>
<div class="rounded-md">0.375rem</div>
<div class="rounded-lg">0.5rem</div>
<div class="rounded-xl">0.75rem</div>
<div class="rounded-2xl">1rem</div>
<div class="rounded-full">9999px (圆角/胶囊)</div>

<!-- 单个圆角 -->
<div class="rounded-t-lg">顶部圆角</div>
<div class="rounded-br-xl">右下角圆角</div>
```

### 边框样式 (Border Style)

```html
<div class="border border-solid">实线</div>
<div class="border-2 border-dashed">虚线</div>
<div class="border border-dotted">点线</div>
```

## Shadows 阴影

```html
<div class="shadow-sm">小阴影</div>
<div class="shadow">默认阴影</div>
<div class="shadow-md">中等阴影</div>
<div class="shadow-lg">大阴影</div>
<div class="shadow-xl">超大阴影</div>
<div class="shadow-2xl">极特大阴影</div>
<div class="shadow-none">无阴影</div>
```

### 彩色阴影 (Colored Shadows)

```html
<div class="shadow-lg shadow-blue-500/50">蓝色阴影</div>
```

## 宽度与高度 (Width & Height)

### 宽度 (Width)

```html
<div class="w-full">100%</div>
<div class="w-1/2">50%</div>
<div class="w-1/3">33.333%</div>
<div class="w-64">16rem</div>
<div class="w-[500px]">500px</div>
<div class="w-screen">100vw</div>

<!-- 最小/最大宽度 -->
<div class="min-w-0">min-width: 0</div>
<div class="max-w-md">max-width: 28rem</div>
<div class="max-w-screen-xl">max-width: 1280px</div>
```

### 高度 (Height)

```html
<div class="h-full">100%</div>
<div class="h-screen">100vh</div>
<div class="h-64">16rem</div>
<div class="h-[500px]">500px</div>

<!-- 最小/最大高度 -->
<div class="min-h-screen">min-height: 100vh</div>
<div class="max-h-96">max-height: 24rem</div>
```

## 任意值 (Arbitrary Values)

使用方括号来自定义特殊属性值：

```html
<!-- 间距 -->
<div class="p-[17px]">自定义内边距</div>
<div class="top-[117px]">自定义定位坐标</div>

<!-- 颜色 -->
<div class="bg-[#bada55]">十六进制颜色</div>
<div class="text-[rgb(123,45,67)]">RGB 颜色</div>

<!-- 尺寸 -->
<div class="w-[500px]">自定义宽度</div>
<div class="text-[22px]">自定义字体大小</div>

<!-- CSS 变量 -->
<div class="bg-[var(--brand-color)]">CSS 变量</div>

<!-- 复杂数值 -->
<div class="grid-cols-[1fr_500px_2fr]">自定义网格</div>
```

## 宽高比 (Aspect Ratio)

```html
<div class="aspect-square">1:1 正方形</div>
<div class="aspect-video">16:9 视频比例</div>
<div class="aspect-[4/3]">4:3 比例</div>
```

## 溢出处理 (Overflow)

```html
<div class="overflow-auto">自动滚动</div>
<div class="overflow-hidden">内容隐藏</div>
<div class="overflow-scroll">始终显示滚动条</div>
<div class="overflow-x-auto">水平滚动</div>
<div class="overflow-y-hidden">禁止垂直滚动</div>
```

## 不透明度 (Opacity)

```html
<div class="opacity-0">0% (完全透明)</div>
<div class="opacity-50">50%</div>
<div class="opacity-75">75%</div>
<div class="opacity-100">100% (完全不透明)</div>
```

## 光标样式 (Cursor)

```html
<div class="cursor-pointer">手型 (Pointer)</div>
<div class="cursor-wait">等待 (Wait)</div>
<div class="cursor-not-allowed">禁止 (Not allowed)</div>
<div class="cursor-default">默认 (Default)</div>
```

## 文本选择 (User Select)

```html
<div class="select-none">禁止选择</div>
<div class="select-text">文本可选择</div>
<div class="select-all">点击全选</div>
```
