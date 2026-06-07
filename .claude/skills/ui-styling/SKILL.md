---
name: ckm:ui-styling
description: 使用 shadcn/ui 组件（基于 Radix UI + Tailwind）、Tailwind CSS 原子化（Utility-first）样式以及基于 Canvas 的视觉设计来创建美观且符合无障碍规范的用户界面。适用于构建用户界面、落地设计系统、创建响应式布局、添加无障碍组件（对话框、下拉菜单、表单、表格）、定制主题与配色、实现暗色模式、生成视觉设计和海报，或在应用程序中建立一致的样式规范。
argument-hint: "[component or layout]"
license: MIT
metadata:
  author: claudekit
  version: "1.0.0"
---

# UI 样式设计技能 (UI Styling Skill)

整合 shadcn/ui 组件库、Tailwind CSS 实用工具优先样式系统以及 Canvas 级视觉合成设计，致力于构建极具设计美感且深度符合 A11y 无障碍标准的现代化用户界面。

## 参考链接

- shadcn/ui: https://ui.shadcn.com/llms.txt
- Tailwind CSS: https://tailwindcss.com/docs

## 适用场景 (When to Use)

- 使用基于 React 的框架（Next.js、Vite、Remix、Astro）构建 UI
- 实现无障碍组件（对话框、表单、表格、导航）
- 采用原子化（Utility-first）CSS 方式进行样式设计
- 创建响应式、移动优先（Mobile-first）的布局
- 实现暗色模式与主题自定义
- 构建具有一致设计标记（Design tokens）的设计系统
- 生成视觉设计、海报或品牌物料
- 快速构建原型并获得即时视觉反馈
- 引入复杂的 UI 模式（数据表格、图表、命令面板）

## 核心技术栈

### 组件层：shadcn/ui（强主张的组件级真理源）
- 底座基于 Radix UI 无样式原语组件，提供顶级且开箱即用的无障碍体验
- 倡导代码所有权，组件以源码形式直接注入您的项目中（自由定制，不强锁依赖）
- TypeScript 优先，具有完整的类型安全保障
- 提供可组合的组件基底以构建复杂的 UI
- 采用基于命令行（CLI）的方式进行安装与管理

### 样式层：Tailwind CSS（原子化实用工具优先样式）
- 原子化（Utility-first）的 CSS 框架
- 构建时处理，零运行时开销
- 移动优先的响应式设计
- 一致的设计标记（配色方案、间距、排版比例）
- 自动消除未使用的 CSS 代码（Dead code elimination）

### Canvas 视觉设计层（博物馆级合成表达）
- 博物馆级的视觉合成效果
- 哲学驱动的设计方法
- 精致的视觉传达
- 极简的文字，最大化的视觉冲击力
- 系统化的图案与精致的美学呈现

## 快速开始

### 组件与样式配置

**安装集成了 Tailwind 的 shadcn/ui：**
```bash
npx shadcn@latest init
```

CLI 将提示您选择框架、TypeScript 偏好、路径以及主题偏好。这会自动完成 shadcn/ui 和 Tailwind CSS 的配置。

**添加组件：**
```bash
npx shadcn@latest add button card dialog form
```

**结合原子化样式使用组件：**
```tsx
import { Button } from "@/components/ui/button"
import { Card, CardHeader, CardTitle, CardContent } from "@/components/ui/card"

export function Dashboard() {
  return (
    <div className="container mx-auto p-6 grid gap-6 md:grid-cols-2 lg:grid-cols-3">
      <Card className="hover:shadow-lg transition-shadow">
        <CardHeader>
          <CardTitle className="text-2xl font-bold">Analytics</CardTitle>
        </CardHeader>
        <CardContent className="space-y-4">
          <p className="text-muted-foreground">View your metrics</p>
          <Button variant="default" className="w-full">
            View Details
          </Button>
        </CardContent>
      </Card>
    </div>
  )
}
```

### 替代方案：纯 Tailwind 配置

**Vite 项目：**
```bash
npm install -D tailwindcss @tailwindcss/vite
```

```javascript
// vite.config.ts
import tailwindcss from '@tailwindcss/vite'
export default { plugins: [tailwindcss()] }
```

```css
/* src/index.css */
@import "tailwindcss";
```

## 组件库指南

**包含用法模式、安装说明和组合示例的完整组件目录。**

参见：[shadcn-components.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/shadcn-components.md)

涵盖以下内容：
- 表单与输入组件（Button, Input, Select, Checkbox, Date Picker, Form validation 表单验证）
- 布局与导航（Card, Tabs, Accordion, Navigation Menu）
- 遮罩与对话框（Dialog, Drawer, Popover, Toast, Command）
- 反馈与状态（Alert, Progress, Skeleton）
- 展示组件（Table, Data Table, Avatar, Badge）

## 主题与定制

**主题配置、CSS 变量、暗色模式实现以及组件自定义。**

参见：[shadcn-theming.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/shadcn-theming.md)

涵盖以下内容：
- 结合 next-themes 配置暗色模式
- CSS 变量系统
- 颜色自定义与调色板
- 组件变体自定义
- 主题切换开关的实现

## 无障碍设计模式 (Accessibility Patterns)

**ARIA 规范、键盘导航、屏幕阅读器支持以及无障碍组件用法。**

参见：[shadcn-accessibility.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/shadcn-accessibility.md)

涵盖以下内容：
- Radix UI 的无障碍特性
- 键盘导航模式
- 焦点管理 (Focus management)
- 屏幕阅读器朗读提示 (Screen reader announcements)
- 表单验证的无障碍支持

## Tailwind 常用工具类

**用于布局、间距、排版、颜色、边框和阴影的核心工具类。**

参见：[tailwind-utilities.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/tailwind-utilities.md)

涵盖以下内容：
- 布局工具类（Flexbox、Grid、定位）
- 间距系统（内边距 padding、外边距 margin、间隙 gap）
- 字体排版（字号、字重、对齐方式、行高）
- 颜色与背景
- 边框与阴影
- 适用于自定义样式的任意值（Arbitrary values）

## 响应式设计

**移动优先的断点、响应式工具类以及自适应布局。**

参见：[tailwind-responsive.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/tailwind-responsive.md)

涵盖以下内容：
- 移动优先（Mobile-first）的设计方法
- 断点系统（sm, md, lg, xl, 2xl）
- 响应式工具类模式
- 容器查询 (Container queries)
- 最大宽度查询 (Max-width queries)
- 自定义断点

## Tailwind 自定义

**配置文件结构、自定义工具类、插件以及主题扩展。**

参见：[tailwind-customization.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/tailwind-customization.md)

涵盖以下内容：
- 用于自定义标记的 @theme 指令
- 自定义颜色与字体
- 间距与断点扩展
- 自定义工具类的创建
- 自定义变体
- 图层组织（@layer base, components, utilities）
- 用于提取组件的 @apply 指令

## 视觉设计系统

**基于 Canvas 的设计哲学、视觉传达原则以及精致的画面合成。**

参见：[canvas-design-system.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/canvas-design-system.md)

涵盖以下内容：
- 设计哲学与方法
- 视觉传达优于纯文本
- 系统化的图案与画面构图
- 色彩、形状及空间设计
- 极简的文字融合
- 博物馆级的视觉呈现
- 多页面设计系统

## 辅助脚本

**用于组件安装和配置生成的 Python 自动化脚本。**

### shadcn_add.py
添加具有依赖处理能力的 shadcn/ui 组件：
```bash
python scripts/shadcn_add.py button card dialog
```

### tailwind_config_gen.py
生成带有自定义主题的 tailwind.config.js 配置文件：
```bash
python scripts/tailwind_config_gen.py --colors brand:blue --fonts display:Inter
```

## 最佳实践

1. **组件组合 (Component Composition)**：使用简单、可组合的基底组件来构建复杂的 UI。
2. **原子化优先样式 (Utility-First Styling)**：直接使用 Tailwind 工具类；仅在确有重复使用需求时才提取为单独的组件。
3. **移动优先响应式 (Mobile-First Responsive)**：从移动端样式开始设计，再逐步叠加针对大屏的响应式变体。
4. **无障碍优先 (Accessibility-First)**：充分利用 Radix UI 基础级组件，添加焦点状态，使用语义化的 HTML。
5. **设计标记 (Design Tokens)**：采用一致的间距比例、配色方案及排版系统。
6. **暗色模式一致性 (Dark Mode Consistency)**：将暗色变体应用到所有经过主题设计的元素上。
7. **性能优化 (Performance)**：利用自动 CSS 清洗（purging）机制，避免使用动态拼接的类名。
8. **TypeScript**：采用完整的类型安全保障以提升开发体验。
9. **视觉层级 (Visual Hierarchy)**：通过构图引导视线，有意识地利用间距和色彩。
10. **工匠精神 (Expert Craftsmanship)**：每一个细节都至关重要 —— 将 UI 设计视为一门手艺。

## 参考导航

**组件库**
- [shadcn-components.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/shadcn-components.md) - 完整组件目录
- [shadcn-theming.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/shadcn-theming.md) - 主题与定制
- [shadcn-accessibility.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/shadcn-accessibility.md) - 无障碍设计模式

**样式系统**
- [tailwind-utilities.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/tailwind-utilities.md) - 核心工具类
- [tailwind-responsive.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/tailwind-responsive.md) - 响应式设计
- [tailwind-customization.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/tailwind-customization.md) - 配置与扩展

**视觉设计**
- [canvas-design-system.md](file:///Users/neoyuan/Desktop/aoyi/ui-ux-pro-max-skill-zh/.claude/skills/ui-styling/references/canvas-design-system.md) - 设计哲学与 Canvas 工作流

**自动化**
- `scripts/shadcn_add.py` - 组件安装
- `scripts/tailwind_config_gen.py` - 配置生成

## 常用模式

**带有验证功能的表单：**
```tsx
import { useForm } from "react-hook-form"
import { zodResolver } from "@hookform/resolvers/zod"
import * as z from "zod"
import { Form, FormField, FormItem, FormLabel, FormControl, FormMessage } from "@/components/ui/form"
import { Input } from "@/components/ui/input"
import { Button } from "@/components/ui/button"

// 定义验证 Schema
const schema = z.object({
  email: z.string().email(),
  password: z.string().min(8)
})

export function LoginForm() {
  const form = useForm({
    resolver: zodResolver(schema),
    defaultValues: { email: "", password: "" }
  })

  return (
    <Form {...form}>
      <form onSubmit={form.handleSubmit(console.log)} className="space-y-6">
        <FormField control={form.control} name="email" render={({ field }) => (
          <FormItem>
            <FormLabel>邮箱</FormLabel>
            <FormControl>
              <Input type="email" {...field} />
            </FormControl>
            <FormMessage />
          </FormItem>
        )} />
        <Button type="submit" className="w-full">登录</Button>
      </form>
    </Form>
  )
}
```

**支持暗色模式的响应式布局：**
```tsx
<div className="min-h-screen bg-white dark:bg-gray-900">
  <div className="container mx-auto px-4 py-8">
    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <Card className="bg-white dark:bg-gray-800 border-gray-200 dark:border-gray-700">
        <CardContent className="p-6">
          <h3 className="text-xl font-semibold text-gray-900 dark:text-white">
            卡片内容
          </h3>
        </CardContent>
      </Card>
    </div>
  </div>
</div>
```

## 相关资源

- shadcn/ui 官方文档: https://ui.shadcn.com
- Tailwind CSS 官方文档: https://tailwindcss.com
- Radix UI 官方文档: https://radix-ui.com
- Tailwind UI 官方文档: https://tailwindui.com
- Headless UI 官方文档: https://headlessui.com
- v0 (AI UI 生成器): https://v0.dev
