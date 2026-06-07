# shadcn/ui 无障碍设计模式

ARIA 模式、键盘导航、屏幕阅读器支持以及无障碍组件使用。

## 基础：Radix UI Primitives (Radix UI 原生组件)

shadcn/ui 构建在 Radix UI 原生组件之上 —— 它们是无样式、符合 WAI-ARIA 设计模式的无障碍组件。

优势：
- 内置键盘导航
- 屏幕阅读器播报
- 焦点管理
- 自动应用 ARIA 属性
- 通过无障碍标准测试

## 键盘导航 (Keyboard Navigation)

### 焦点管理 (Focus Management)

**可见焦点的状态 (Focus visible states)：**
```tsx
<Button className="focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2">
  Accessible Button
</Button>
```

**跳转至主要内容 (Skip to content)：**
```tsx
<a href="#main-content" className="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4 focus:z-50 focus:px-4 focus:py-2">
  跳转至主要内容
</a>

<main id="main-content">
  {/* 内容 */}
</main>
```

### 对话框/模态框导航 (Dialog/Modal Navigation)

对话框通过 Radix Dialog 原生组件自动进行焦点捕获 (Focus trap)：

```tsx
import { Dialog, DialogContent, DialogTrigger } from "@/components/ui/dialog"

<Dialog>
  <DialogTrigger>打开</DialogTrigger>
  <DialogContent>
    {/* 焦点捕获于此 */}
    <input />  {/* 自动聚焦 */}
    <Button>操作</Button>
    {/* 按 Esc 键关闭，按 Tab 键进行导航 */}
  </DialogContent>
</Dialog>
```

特性：
- 焦点被捕获在对话框内
- 按 Esc 键可以关闭对话框
- 按 Tab 键在可聚焦元素之间循环
- 关闭时焦点返回到触发器按钮

### 下拉菜单/菜单导航 (Dropdown/Menu Navigation)

```tsx
import { DropdownMenu, DropdownMenuContent, DropdownMenuItem, DropdownMenuTrigger } from "@/components/ui/dropdown-menu"

<DropdownMenu>
  <DropdownMenuTrigger>打开</DropdownMenuTrigger>
  <DropdownMenuContent>
    <DropdownMenuItem>个人资料</DropdownMenuItem>
    <DropdownMenuItem>设置</DropdownMenuItem>
    <DropdownMenuItem>退出登录</DropdownMenuItem>
  </DropdownMenuContent>
</DropdownMenu>
```

键盘快捷键：
- ` 空格键/回车键 `：打开菜单
- ` 上/下方向键 `：导航菜单项
- `Esc`：关闭菜单
- `Tab`：关闭菜单并将焦点移出

### 命令面板导航 (Command Palette Navigation)

```tsx
import { Command } from "@/components/ui/command"

<Command>
  <CommandInput placeholder="搜索..." />
  <CommandList>
    <CommandGroup heading="建议">
      <CommandItem>日历</CommandItem>
      <CommandItem>搜索</CommandItem>
    </CommandGroup>
  </CommandList>
</Command>
```

特性：
- 输入文本进行过滤
- 方向键导航
- 回车键进行选择
- Esc 键关闭

## 屏幕阅读器支持 (Screen Reader Support)

### 语义化 HTML (Semantic HTML)

使用恰当的 HTML 元素：

```tsx
// 推荐：语义化 HTML
<button>点击我</button>
<nav><a href="/">首页</a></nav>

// 避免：无语义的 div 堆砌
<div onClick={handler}>点击我</div>
```

### ARIA 标签 (ARIA Labels)

**为交互元素添加标签 (Label interactive elements)：**
```tsx
<Button aria-label="关闭对话框">
  <X className="h-4 w-4" />
</Button>

<Input aria-label="邮箱地址" type="email" />
```

**描述元素 (Describe elements)：**
```tsx
<Button aria-describedby="delete-description">
  删除账号
</Button>
<p id="delete-description" className="sr-only">
  此操作将永久删除您的账号，且无法撤销
</p>
```

### 仅供屏幕阅读器阅读的文本 (Screen Reader Only Text)

使用 `sr-only` 类名处理仅供屏幕阅读器可见的内容：

```tsx
<Button>
  <Trash className="h-4 w-4" />
  <span className="sr-only">删除项目</span>
</Button>

// sr-only 的 CSS 样式
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

### 动态区域播报 (Live Regions)

播报动态更新的内容：

```tsx
<div aria-live="polite" aria-atomic="true">
  {message}
</div>

// 用于紧急更新
<div aria-live="assertive">
  {error}
</div>
```

Toast 组件已包含动态区域播报：
```tsx
const { toast } = useToast()

toast({
  title: "成功",
  description: "个人资料已更新"
})
// 自动向屏幕阅读器进行播报
```

## 表单无障碍 (Form Accessibility)

### 标签与描述 (Labels and Descriptions)

**始终为输入框配置标签：**
```tsx
import { Label } from "@/components/ui/label"
import { Input } from "@/components/ui/input"

<div>
  <Label htmlFor="email">邮箱</Label>
  <Input id="email" type="email" />
</div>
```

**添加描述信息：**
```tsx
import { FormDescription, FormMessage } from "@/components/ui/form"

<FormItem>
  <FormLabel>用户名</FormLabel>
  <FormControl>
    <Input {...field} />
  </FormControl>
  <FormDescription>
    您的公开显示名称
  </FormDescription>
  <FormMessage />  {/* 错误信息 */}
</FormItem>
```

### 错误处理 (Error Handling)

向屏幕阅读器广播错误：

```tsx
<FormField
  control={form.control}
  name="email"
  render={({ field, fieldState }) => (
    <FormItem>
      <FormLabel>邮箱</FormLabel>
      <FormControl>
        <Input
          {...field}
          aria-invalid={!!fieldState.error}
          aria-describedby={fieldState.error ? "email-error" : undefined}
        />
      </FormControl>
      <FormMessage id="email-error" />
    </FormItem>
  )}
/>
```

### 必填字段 (Required Fields)

指示必填字段：

```tsx
<Label htmlFor="name">
  姓名 <span className="text-destructive">*</span>
  <span className="sr-only">(必填)</span>
</Label>
<Input id="name" required />
```

### 字段集与说明 (Fieldset and Legend)

对相关字段进行分组：

```tsx
<fieldset>
  <legend className="text-lg font-semibold mb-4">
    联系信息
  </legend>
  <div className="space-y-4">
    <FormField name="email" />
    <FormField name="phone" />
  </div>
</fieldset>
```

## 组件特定的无障碍模式 (Component-Specific Patterns)

### 手风琴组件 (Accordion)

```tsx
import { Accordion } from "@/components/ui/accordion"

<Accordion type="single" collapsible>
  <AccordionItem value="item-1">
    <AccordionTrigger>
      {/* 自动包含 aria-expanded 和 aria-controls */}
      它符合无障碍标准吗？
    </AccordionTrigger>
    <AccordionContent>
      {/* 折叠时隐藏，展开时播报 */}
      是的。它遵循 WAI-ARIA 设计模式。
    </AccordionContent>
  </AccordionItem>
</Accordion>
```

### 选项卡组件 (Tabs)

```tsx
import { Tabs } from "@/components/ui/tabs"

<Tabs defaultValue="account">
  <TabsList role="tablist">
    {/* 方向键进行导航，空格键/回车键进行激活 */}
    <TabsTrigger value="account">账户</TabsTrigger>
    <TabsTrigger value="password">密码</TabsTrigger>
  </TabsList>
  <TabsContent value="account">
    {/* 除非被选中否则隐藏，aria-labelledby 链接到对应的触发器 */}
    账户内容
  </TabsContent>
</Tabs>
```

### 选择框组件 (Select)

```tsx
import { Select } from "@/components/ui/select"

<Select>
  <SelectTrigger aria-label="选择主题">
    <SelectValue placeholder="主题" />
  </SelectTrigger>
  <SelectContent>
    {/* 可通过键盘导航，且可向屏幕阅读器播报 */}
    <SelectItem value="light">浅色模式</SelectItem>
    <SelectItem value="dark">深色模式</SelectItem>
  </SelectContent>
</Select>
```

### 复选框与单选框 (Checkbox and Radio)

```tsx
import { Checkbox } from "@/components/ui/checkbox"
import { Label } from "@/components/ui/label"

<div className="flex items-center space-x-2">
  <Checkbox id="terms" aria-describedby="terms-description" />
  <Label htmlFor="terms">接受条款</Label>
</div>
<p id="terms-description" className="text-sm text-muted-foreground">
  您同意我们的服务条款和隐私政策
</p>
```

### 警示组件 (Alert)

```tsx
import { Alert } from "@/components/ui/alert"

<Alert role="alert">
  {/* 立即向屏幕阅读器播报 */}
  <AlertTitle>错误</AlertTitle>
  <AlertDescription>
    您的会话已过期
  </AlertDescription>
</Alert>
```

## 色彩对比度 (Color Contrast)

确保文本与背景之间有足够的对比度。

**WCAG 对比度要求：**
- **AA 级**：普通文本 4.5:1，大文本 3:1
- **AAA 级**：普通文本 7:1，大文本 4.5:1

**检查默认值：**
```tsx
// 推荐：高对比度
<p className="text-gray-900 dark:text-gray-100">文本内容</p>

// 避免：低对比度
<p className="text-gray-400 dark:text-gray-600">难以阅读</p>
```

**静音/次要文本 (Muted text)：**
```tsx
// 使用语义化的 muted 前景色
<p className="text-muted-foreground">
  具有符合无障碍对比度的次要文本
</p>
```

## 焦点指示器 (Focus Indicators)

始终提供清晰可见的焦点指示器：

**默认焦点环：**
```tsx
<Button className="focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2">
  按钮
</Button>
```

**自定义焦点样式：**
```tsx
<a href="#" className="focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-primary focus-visible:underline">
  链接
</a>
```

**切勿移除焦点样式：**
```tsx
// 避免
<button className="focus:outline-none">Bad (糟糕做法)</button>

// 应该使用 focus-visible 代替
<button className="focus-visible:ring-2">Good (正确做法)</button>
```

## 动效与动画 (Motion and Animation)

尊重用户关于减弱动效 (reduced motion) 的系统偏好设置：

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

在组件中：
```tsx
<div className="transition-all motion-reduce:transition-none">
  尊重用户减弱动效的偏好
</div>
```

## 测试清单 (Testing Checklist)

- [ ] 所有交互元素都支持键盘操作
- [ ] 焦点指示器清晰可见
- [ ] 屏幕阅读器能够正确播报所有内容
- [ ] 表单错误能被播报并与输入框正确关联
- [ ] 颜色对比度符合 WCAG AA 级标准
- [ ] 使用语义化 HTML
- [ ] 为仅有图标的按钮提供 ARIA 标签
- [ ] 模态框/对话框焦点捕获正常工作
- [ ] 下拉菜单/选择框支持键盘导航
- [ ] 动态区域播报正常宣布更新
- [ ] 尊重减弱动效偏好
- [ ] 支持最高 200% 的浏览器缩放
- [ ] 聚焦导航顺序逻辑正确
- [ ] 提供了跳过主导航的 Skip 链接

## 测试工具 (Tools)

**测试工具：**
- Lighthouse 无障碍审查 (accessibility audit)
- axe DevTools 浏览器扩展
- NVDA/JAWS 屏幕阅读器
- 仅用键盘的导航测试
- 色彩对比度检查器 (Contrast Ratio, WebAIM)

**自动化测试：**
```bash
npm install -D @axe-core/react
```

```tsx
import { useEffect } from 'react'

if (process.env.NODE_ENV === 'development') {
  import('@axe-core/react').then((axe) => {
    axe.default(React, ReactDOM, 1000)
  })
}
```
