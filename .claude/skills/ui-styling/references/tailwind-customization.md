# Tailwind CSS 定制开发指南

配置文件结构、自定义工具类、插件以及主题扩展。

## @theme 指令

在 CSS 中定制 Tailwind 的现代方法：

```css
@import "tailwindcss";

@theme {
  /* 自定义颜色 */
  --color-brand-50: oklch(0.97 0.02 264);
  --color-brand-500: oklch(0.55 0.22 264);
  --color-brand-900: oklch(0.25 0.15 264);

  /* 自定义字体 */
  --font-display: "Satoshi", "Inter", sans-serif;
  --font-body: "Inter", system-ui, sans-serif;

  /* 自定义间距 */
  --spacing-18: calc(var(--spacing) * 18);
  --spacing-navbar: 4.5rem;

  /* 自定义断点 */
  --breakpoint-3xl: 120rem;
  --breakpoint-tablet: 48rem;

  /* 自定义阴影 */
  --shadow-glow: 0 0 20px rgba(139, 92, 246, 0.3);

  /* 自定义圆角 */
  --radius-large: 1.5rem;
}
```

**用法：**
```html
<div class="bg-brand-500 font-display shadow-glow rounded-large">
  自定义主题元素
</div>

<div class="tablet:grid-cols-2 3xl:grid-cols-6">
  自定义断点
</div>
```

## 颜色自定义 (Color Customization)

### 自定义调色板 (Custom Color Palette)

```css
@theme {
  /* 完整色阶 */
  --color-primary-50: oklch(0.98 0.02 250);
  --color-primary-100: oklch(0.95 0.05 250);
  --color-primary-200: oklch(0.90 0.10 250);
  --color-primary-300: oklch(0.85 0.15 250);
  --color-primary-400: oklch(0.75 0.18 250);
  --color-primary-500: oklch(0.65 0.22 250);
  --color-primary-600: oklch(0.55 0.22 250);
  --color-primary-700: oklch(0.45 0.20 250);
  --color-primary-800: oklch(0.35 0.18 250);
  --color-primary-900: oklch(0.25 0.15 250);
  --color-primary-950: oklch(0.15 0.10 250);
}
```

### 语义化颜色 (Semantic Colors)

```css
@theme {
  --color-success: oklch(0.65 0.18 145);
  --color-warning: oklch(0.75 0.15 85);
  --color-error: oklch(0.60 0.22 25);
  --color-info: oklch(0.65 0.18 240);
}
```

```html
<div class="bg-success text-white">成功信息</div>
<div class="border-error">错误状态</div>
```

## 排版自定义 (Typography Customization)

### 自定义字体

```css
@theme {
  --font-sans: "Inter", system-ui, sans-serif;
  --font-serif: "Merriweather", Georgia, serif;
  --font-mono: "JetBrains Mono", Consolas, monospace;
  --font-display: "Playfair Display", serif;
}
```

```html
<h1 class="font-display">大标题展示</h1>
<p class="font-sans">正文文本</p>
<code class="font-mono">代码块</code>
```

### 自定义字号

```css
@theme {
  --font-size-xs: 0.75rem;
  --font-size-sm: 0.875rem;
  --font-size-base: 1rem;
  --font-size-lg: 1.125rem;
  --font-size-xl: 1.25rem;
  --font-size-2xl: 1.5rem;
  --font-size-3xl: 1.875rem;
  --font-size-4xl: 2.25rem;
  --font-size-5xl: 3rem;
  --font-size-jumbo: 4rem;
}
```

## 间距自定义 (Spacing Customization)

```css
@theme {
  /* 添加自定义间距值 */
  --spacing-13: calc(var(--spacing) * 13);
  --spacing-15: calc(var(--spacing) * 15);
  --spacing-18: calc(var(--spacing) * 18);

  /* 命名间距 */
  --spacing-header: 4rem;
  --spacing-footer: 3rem;
  --spacing-section: 6rem;
}
```

```html
<div class="p-18">自定义内边距</div>
<section class="py-section">区块间距</section>
```

## 自定义工具类 (Custom Utilities)

创建可复用的工具类：

```css
@utility content-auto {
  content-visibility: auto;
}

@utility tab-* {
  tab-size: var(--tab-size-*);
}

@utility glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}
```

**用法：**
```html
<div class="content-auto">优化渲染性能</div>
<pre class="tab-4">使用 4 个空格缩进的代码</pre>
<div class="glass">毛玻璃特效</div>
```

## 自定义变体 (Custom Variants)

创建自定义状态变体：

```css
@custom-variant theme-midnight (&:where([data-theme="midnight"] *));
@custom-variant aria-checked (&[aria-checked="true"]);
@custom-variant required (&:required);
```

**用法：**
```html
<div data-theme="midnight">
  <div class="theme-midnight:bg-navy-900">
    在午夜 (midnight) 主题中应用
  </div>
</div>

<input class="required:border-red-500" required />
```

## 分层组织 (Layer Organization)

将 CSS 组织到不同的图层中：

```css
@layer base {
  h1 {
    @apply text-4xl font-bold tracking-tight;
  }

  h2 {
    @apply text-3xl font-semibold;
  }

  a {
    @apply text-blue-600 hover:text-blue-700 underline-offset-4 hover:underline;
  }

  body {
    @apply bg-background text-foreground antialiased;
  }
}

@layer components {
  .btn {
    @apply px-4 py-2 rounded-lg font-medium transition-colors;
  }

  .btn-primary {
    @apply bg-blue-600 text-white hover:bg-blue-700;
  }

  .btn-secondary {
    @apply bg-gray-200 text-gray-900 hover:bg-gray-300;
  }

  .card {
    @apply bg-white rounded-xl shadow-md p-6 hover:shadow-lg transition-shadow;
  }

  .input {
    @apply w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent;
  }
}

@layer utilities {
  .text-balance {
    text-wrap: balance;
  }

  .scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
  .scrollbar-hide::-webkit-scrollbar {
    display: none;
  }
}
```

## @apply 指令

提取重复的工具类组合模式：

```css
.btn-primary {
  @apply bg-blue-600 hover:bg-blue-700 active:bg-blue-800 text-white font-semibold px-6 py-3 rounded-lg shadow-md hover:shadow-lg transition-all duration-200 focus:outline-none focus:ring-4 focus:ring-blue-300;
}

.input-field {
  @apply w-full px-4 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent disabled:bg-gray-100 disabled:cursor-not-allowed;
}

.section-container {
  @apply container mx-auto px-4 sm:px-6 lg:px-8 max-w-7xl;
}
```

**用法：**
```html
<button class="btn-primary">点击我</button>
<input class="input-field" />
<div class="section-container">内容</div>
```

## 插件 (Plugins)

### 官方插件

```bash
npm install -D @tailwindcss/typography @tailwindcss/forms @tailwindcss/container-queries
```

```javascript
// tailwind.config.js
export default {
  plugins: [
    require('@tailwindcss/typography'),
    require('@tailwindcss/forms'),
    require('@tailwindcss/container-queries'),
  ],
}
```

**排版插件 (Typography plugin)：**
```html
<article class="prose lg:prose-xl">
  <h1>排版美化的文章</h1>
  <p>自动应用精美排版样式的文章内容</p>
</article>
```

**表单插件 (Forms plugin)：**
```html
<!-- 自动美化表单元素 -->
<input type="text" />
<select></select>
<textarea></textarea>
```

### 自定义插件 (Custom Plugin)

```javascript
// tailwind.config.js
const plugin = require('tailwindcss/plugin')

export default {
  plugins: [
    plugin(function({ addUtilities, addComponents, theme }) {
      // 添加自定义工具类
      addUtilities({
        '.text-shadow': {
          textShadow: '2px 2px 4px rgba(0, 0, 0, 0.1)',
        },
        '.text-shadow-lg': {
          textShadow: '4px 4px 8px rgba(0, 0, 0, 0.2)',
        },
      })

      // 添加自定义组件
      addComponents({
        '.card-custom': {
          backgroundColor: theme('colors.white'),
          borderRadius: theme('borderRadius.lg'),
          padding: theme('spacing.6'),
          boxShadow: theme('boxShadow.md'),
        },
      })
    }),
  ],
}
```

## 配置示例

### 完整的 Tailwind 配置

```javascript
// tailwind.config.ts
import type { Config } from 'tailwindcss'

const config: Config = {
  darkMode: ["class"],
  content: [
    './pages/**/*.{ts,tsx}',
    './components/**/*.{ts,tsx}',
    './app/**/*.{ts,tsx}',
  ],
  theme: {
    container: {
      center: true,
      padding: "2rem",
      screens: {
        "2xl": "1400px",
      },
    },
    extend: {
      colors: {
        border: "hsl(var(--border))",
        input: "hsl(var(--input))",
        ring: "hsl(var(--ring))",
        background: "hsl(var(--background))",
        foreground: "hsl(var(--foreground))",
        primary: {
          DEFAULT: "hsl(var(--primary))",
          foreground: "hsl(var(--primary-foreground))",
        },
        brand: {
          50: '#f0f9ff',
          500: '#3b82f6',
          900: '#1e3a8a',
        },
      },
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
        display: ['Playfair Display', 'serif'],
      },
      spacing: {
        '18': '4.5rem',
        '88': '22rem',
        '128': '32rem',
      },
      borderRadius: {
        lg: "var(--radius)",
        md: "calc(var(--radius) - 2px)",
        sm: "calc(var(--radius) - 4px)",
      },
      keyframes: {
        "slide-in": {
          "0%": { transform: "translateX(-100%)" },
          "100%": { transform: "translateX(0)" },
        },
      },
      animation: {
        "slide-in": "slide-in 0.5s ease-out",
      },
    },
  },
  plugins: [require("tailwindcss-animate")],
}

export default config
```

## 暗黑模式配置 (Dark Mode Configuration)

```javascript
// tailwind.config.js
export default {
  darkMode: ["class"],  // 或者是 "media" 实现自动切换
  // ...
}
```

**用法：**
```html
<!-- 基于 Class -->
<html class="dark">
  <div class="bg-white dark:bg-gray-900">
    对 .dark 类名做出响应
  </div>
</html>

<!-- 基于媒体查询 -->
<div class="bg-white dark:bg-gray-900">
    自动对系统偏好设置做出响应
</div>
```

## 扫描内容配置 (Content Configuration)

指定需要扫描以查找 Tailwind 类名物的文件：

```javascript
// tailwind.config.js
export default {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
    "./app/**/*.{js,jsx,ts,tsx}",
    "./components/**/*.{js,jsx,ts,tsx}",
    "./pages/**/*.{js,jsx,ts,tsx}",
  ],
  // ...
}
```

### 白名单 (Safelist)

强制保留动态生成的类名：

```javascript
export default {
  safelist: [
    'bg-red-500',
    'bg-green-500',
    'bg-blue-500',
    {
      pattern: /bg-(red|green|blue)-(100|500|900)/,
    },
  ],
}
```

## 最佳实践

1. **对于简单自定义推荐使用 @theme**：优先选择基于 CSS 的定制方法
2. **谨慎提取组件**：仅对真正重复使用的排版或布局模式使用 @apply
3. **充分利用设计令牌 (Design Tokens)**：在 @theme 中定义自定义的设计令牌
4. **合理的分层组织**：保持 base、components 和 utilities 的分离
5. **处理复杂逻辑推荐使用插件**：对于高级定制或动态工具类使用 plugins
6. **充分测试暗黑模式**：确保自定义颜色在两种主题下都能完美工作
7. **对自定义工具类进行文档记录**：添加必要的 CSS 注释以解释自定义类名的用途
8. **语义化命名**：使用具有业务或视觉含义的名称（如 primary 而不是 blue）
