# 设计路标指南

如何在合适的时候使用各个设计子技能。

## 技能概览

| 技能 | 用途 | 核心文件 |
|-------|---------|-----------|
| brand | 品牌识别、品牌调性、品牌资产 | SKILL.md + 10 references + 3 scripts |
| design-system | 设计标记架构、设计规范 | SKILL.md + 7 references + 2 scripts |
| ui-styling | 组件实现与样式开发 | SKILL.md + 7 references + 2 scripts |
| logo-design | AI 智能生成 Logo（55 种风格，30 种调色板） | SKILL.md + 4 references + 2 scripts |
| cip-design | 企业形象识别系统（50 种交付物） | SKILL.md + 3 references + 3 scripts |
| slides | 基于 Chart.js 的 HTML 演示文稿 | SKILL.md + 4 references |
| banner-design | 适用于社交、广告、网页、印刷的横幅设计（22 种风格） | SKILL.md + 1 reference |
| icon-design | SVG 图标生成（15 种风格，基于 Gemini 3.1 Pro） | SKILL.md + 1 reference + 1 script |

## 按任务类型选择技能

### 品牌识别任务
**→ brand**

- 定义品牌色彩与字体排版
- 创建 Logo 使用规范
- 确立品牌调性与文案风格
- 整理并验证品牌资产
- 构建品牌信息传播框架
- 审计品牌一致性

### 设计标记系统任务
**→ design-system**

- 创建设计标记 JSON
- 生成 CSS 变量
- 定义组件规范
- 将设计标记映射到 Tailwind 配置
- 验证代码中设计标记的使用情况
- 编写状态与变体文档

### 界面开发任务
**→ ui-styling**

- 添加 shadcn/ui 组件
- 使用 Tailwind 类进行样式开发
- 实现深色模式
- 创建响应式布局
- 开发无障碍（A11y）组件

### Logo 设计任务
**→ logo-design**

- 使用 AI 生成 Logo（Gemini Nano Banana）
- 搜索 Logo 风格、调性色彩、行业指南
- 生成设计简报
- 探索 55+ 种风格（极简、复古、奢华、几何等）

### 企业形象识别系统（CIP）任务
**→ cip-design**

- 生成 CIP 交付物（名片、信纸、标牌、载具车身、服饰）
- 编写包含行业与风格分析的 CIP 简报
- 生成包含或不含 Logo 的样机效果图（Gemini Flash/Pro）
- 从 CIP 样机效果图渲染 HTML 演示文稿

### 演示文稿任务
**→ slides**

- 创建富有策略性的 HTML 演示文稿
- 使用 Chart.js 进行数据可视化
- 将文案公式应用于幻灯片内容
- 应用排版布局模式与设计标记

### 横幅设计任务
**→ banner-design**

- 设计适用于主流社交媒体的横幅（Facebook、Twitter、LinkedIn、YouTube、Instagram）
- 创建广告横幅（Google 广告、Meta 广告）
- 网页首屏 Hero 横幅与头部导航背景
- 印刷类横幅与封面
- 22 种艺术指导风格（极简、加粗排版、渐变、毛玻璃幻影效果等）

### 图标设计任务
**→ icon-design**

- 使用 AI 生成 SVG 图标（Gemini 3.1 Pro Preview）
- 批量生成多种风格的图标变体
- 多尺寸导出（16px、24px、32px、48px）
- 15 种风格：描边、填充、双色、圆角、直角、渐变等
- 12 个类别：导航、操作、交流、媒体、电商、数据等

## 按提问类型选择技能

| 提问示例 | 对应技能 |
|----------|-------|
| “这个应该用什么颜色？” | brand |
| “如何为 X 创建设计标记？” | design-system |
| “如何构建一个按钮组件？” | ui-styling |
| “这符合品牌形象吗？” | brand |
| “这里我应该使用 CSS 变量吗？” | design-system |
| “如何添加深色模式支持？” | ui-styling |
| “为我的品牌设计一个 Logo” | logo-design |
| “生成名片样机效果图” | cip-design |
| “制作一份路演 PPT/演示文稿” | slides |
| “设计一整套品牌视觉识别包” | cip-design |
| “什么 Logo 风格适合我的行业？” | logo-design |
| “设计一张 Facebook 封面图” | banner-design |
| “为 Google 制作广告横幅” | banner-design |
| “制作一个网页首屏 Hero 横幅” | banner-design |
| “生成一个设置图标” | icon-design |
| “为我的 App 创建一些 SVG 图标” | icon-design |
| “设计一套图标库” | icon-design |

## 多技能协同工作流

### 新项目搭建

```
1. brand → 定义品牌识别
   - 色彩、字体排版、品牌声音

2. design-system → 创建设计标记
   - 基础（Primitive）、语义（Semantic）、组件（Component）标记

3. ui-styling → 代码实现
   - 配置 Tailwind，添加所需组件
```

### 设计系统迁移

```
1. brand → 审计现有资产
   - 提取品牌颜色与字体

2. design-system → 规范化设计标记
   - 构建三层标记架构

3. ui-styling → 更新代码
   - 替换硬编码的样式值
```

### 组件开发

```
1. design-system → 参考设计规范
   - 按钮的状态、尺寸与变体

2. ui-styling → 代码实现
   - 使用 shadcn/ui + Tailwind 进行搭建
```

## 技能依赖关系

```
brand
    ↓ (色彩、字体排版)
design-system
    ↓ (设计标记、设计规范)
ui-styling
    ↓ (组件)
应用代码
```

## 快速指令

**品牌：**
```bash
node .claude/skills/brand/scripts/inject-brand-context.cjs
node .claude/skills/brand/scripts/validate-asset.cjs <path>
```

**设计标记：**
```bash
node .claude/skills/design-system/scripts/generate-tokens.cjs -c tokens.json
node .claude/skills/design-system/scripts/validate-tokens.cjs -d src/
```

**组件：**
```bash
npx shadcn@latest add button card input
```

## 什么时候联合使用多技能

在以下情况下，使用 **全部八种技能**：
- 从零开始打造完整的品牌识别包（Logo → 视觉交付物样机 → 演示文稿）

在以下情况下，联合使用 **brand + design-system + ui-styling**：
- 设计系统规范的搭建与落地实现

在以下情况下，联合使用 **logo-design + cip-design**：
- 完整的品牌视觉识别包，配有实体交付物效果图

在以下情况下，联合使用 **logo-design + cip-design + slides**：
- 品牌路演推介：生成 Logo、制作 CIP 样机效果图、制作路演演示文稿

在以下情况下，联合使用 **banner-design + brand**：
- 社交媒体宣传：全平台统一的品牌化横幅背景

在以下情况下，联合使用 **icon-design + design-system**：
- 定制图标集，使其色彩与比例完全匹配设计标记和组件规范

在以下情况下，联合使用 **brand + design-system**：
- 仅定义设计语言，暂不涉及代码实现

在以下情况下，联合使用 **design-system + ui-styling**：
- 将现有的品牌视觉用代码在界面上实现
- 搭建企业级组件库
