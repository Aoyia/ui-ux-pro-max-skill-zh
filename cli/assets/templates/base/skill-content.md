# {{TITLE}}

{{DESCRIPTION}}
{{QUICK_REFERENCE}}
# 前提条件 (Prerequisites)

检查是否已安装 Python：

```bash
python3 --version || python --version
```

如果未安装 Python，请根据您的操作系统进行安装：

**macOS:**
```bash
brew install python3
```

**Ubuntu/Debian:**
```bash
sudo apt update && sudo apt install python3
```

**Windows:**
```powershell
winget install Python.Python.3.12
```

---

## 如何使用此 Skill

当用户请求以下任何内容时，应使用此 Skill：

| 场景 (Scenario) | 触发示例 (Trigger Examples) | 从何处开始 (Start From) |
|----------|-----------------|------------|
| **新项目 / 页面** | "做一个 landing page"、"Build a dashboard" | 步骤 1 → 步骤 2（设计系统） |
| **新组件** | "Create a pricing card"、"Add a modal" | 步骤 3（领域搜索：style, ux） |
| **选择风格 / 配色 / 字体** | "What style fits a fintech app?"、"推荐配色" | 步骤 2（设计系统） |
| **审查现有 UI** | "Review this page for UX issues"、"检查无障碍" | 上方的快速参考清单 |
| **修复 UI 缺陷 (Bug)** | "Button hover is broken"、"Layout shifts on load" | 快速参考 → 相关章节 |
| **改进 / 优化** | "Make this faster"、"Improve mobile experience" | 步骤 3（领域搜索：ux, react） |
| **实现暗色模式** | "Add dark mode support" | 步骤 3（领域搜索：style "dark mode"） |
| **添加图表 / 数据可视化** | "Add an analytics dashboard chart" | 步骤 3（领域搜索：chart） |
| **技术栈最佳实践** | "React performance tips"、"SwiftUI navigation" | 步骤 4（技术栈搜索） |

请遵循以下工作流：

### 步骤 1：分析用户需求

从用户请求中提取关键信息：
- **产品类型**：娱乐（社交、视频、音乐、游戏）、工具（扫描仪、编辑器、转换器）、效率（任务管理、笔记、日历）或混合型
- **目标受众**：C 端消费者用户；考虑年龄段、使用场景（通勤、闲暇、工作）
- **风格关键词**：活泼 (playful)、活力 (vibrant)、极简 (minimal)、暗色模式 (dark mode)、内容优先 (content-first)、沉浸式 (immersive) 等
- **技术栈**：React Native（当前项目的唯一技术栈）

### 步骤 2：生成设计系统（必须执行）

**请始终首先运行 `--design-system`**，以获取包含推导逻辑的完整设计建议：

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<product_type> <industry> <keywords>" --design-system [-p "Project Name"]
```

该命令会：
1. 并行搜索多个领域（产品 product、风格 style、颜色 color、落地页 landing、排版 typography）
2. 应用来自 `ui-reasoning.csv` 的推理规则来选择最佳匹配项
3. 返回完整的设计系统：模式、风格、配色、排版、效果
4. 包含需要避免的反面模式

**示例：**
```bash
python3 skills/ui-ux-pro-max/scripts/search.py "beauty spa wellness service" --design-system -p "Serenity Spa"
```

### 步骤 2b：持久化设计系统（主系统 + 页面覆盖模式）

如需保存设计系统以便在**跨会话时进行分层检索**，请添加 `--persist` 参数：

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<query>" --design-system --persist -p "Project Name"
```

这会创建：
- `design-system/MASTER.md` — 包含所有设计规则的全局唯一真理源 (Global Source of Truth)
- `design-system/pages/` — 存放特定页面覆盖规则的文件夹

**带有特定页面覆盖规则的示例：**
```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<query>" --design-system --persist -p "Project Name" --page "dashboard"
```

这还会创建：
- `design-system/pages/dashboard.md` — 特定于仪表盘 (dashboard) 页面且偏离 Master 的覆盖规则

**分层检索是如何工作的：**
1. 在构建特定页面（例如 "Checkout"）时，首先检查 `design-system/pages/checkout.md` 文件是否存在
2. 如果该页面文件存在，它的规则将**覆盖** Master 文件中的规则
3. 如果不存在，则完全使用 `design-system/MASTER.md`

**上下文感知检索提示词 (Prompt)：**
```
我正在构建 [页面名称] 页面。请阅读 design-system/MASTER.md。
同时检查 design-system/pages/[page-name].md 是否存在。
如果该页面文件存在，请优先使用其规则。
如果不存在，请完全使用 Master 文件中的规则。
现在，请生成代码……
```

### 步骤 3：补充细节搜索（根据需要）

获取设计系统后，可以通过领域搜索来获取额外的设计细节：

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<keyword>" --domain <domain> [-n <max_results>]
```

**何时使用细节搜索：**

| 需求 | 领域 (Domain) | 示例 (Example) |
|------|--------|---------|
| 产品类型模式 | `product` | `--domain product "entertainment social"` |
| 更多风格选择 | `style` | `--domain style "glassmorphism dark"` |
| 配色方案 | `color` | `--domain color "entertainment vibrant"` |
| 字体搭配 | `typography` | `--domain typography "playful modern"` |
| 图表推荐 | `chart` | `--domain chart "real-time dashboard"` |
| UX 最佳实践 | `ux` | `--domain ux "animation accessibility"` |
| 落地页结构 | `landing` | `--domain landing "hero social-proof"` |
| React Native 性能优化 | `react` | `--domain react "rerender memo list"` |
| 应用界面无障碍/平台规范 | `web` | `--domain web "accessibilityLabel touch safe-areas"` |
| AI 提示词 / CSS 关键词 | `prompt` | `--domain prompt "minimalism"` |

### 步骤 4：技术栈指南（React Native）

获取特定于 React Native 实现的最佳实践：

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "<keyword>" --stack react-native
```

---

## 搜索参考

### 可用领域

| 领域 (Domain) | 用途 | 示例关键词 |
|--------|---------|------------------|
| `product` | 产品类型推荐建议 | SaaS, e-commerce, portfolio, healthcare, beauty, service |
| `style` | UI 风格、颜色、特效 | glassmorphism, minimalism, dark mode, brutalism |
| `typography` | 字体搭配、Google Fonts 推荐 | elegant, playful, professional, modern |
| `color` | 根据产品类型推荐的配色方案 | saas, ecommerce, healthcare, beauty, fintech, service |
| `landing` | 页面结构、CTA (行动召唤) 策略 | hero, hero-centric, testimonial, pricing, social-proof |
| `chart` | 图表类型、推荐的图表库 | trend, comparison, timeline, funnel, pie |
| `ux` | 用户体验最佳实践与反面模式 | animation, accessibility, z-index, loading |
| `react` | React/Next.js 性能优化 | waterfall, bundle, suspense, memo, rerender, cache |
| `web` | 应用界面设计指南（iOS/Android/React Native） | accessibilityLabel, touch targets, safe areas, Dynamic Type |
| `prompt` | AI 提示词、CSS 关键词 | (style name) |

### 可用技术栈

| 技术栈 (Stack) | 核心关注点 |
|-------|-------|
| `react-native` | 组件 (Components)、导航 (Navigation)、列表 (Lists) |

---

## 示例工作流

**用户请求**："制作一个 AI 搜索首页。"

### 步骤 1：分析需求
- 产品类型：工具（AI 搜索引擎）
- 目标受众：寻求快速、智能化搜索的 C 端用户
- 风格关键词：现代、极简、内容优先、暗色模式
- 技术栈：React Native

### 步骤 2：生成设计系统（必须执行）

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "AI search tool modern minimal" --design-system -p "AI Search"
```

**输出**：完整的设计系统，包含模式、风格、配色、排版、特效以及反面模式。

### 步骤 3：补充细节搜索（根据需要）

```bash
# 获取现代工具类产品的风格选项
python3 skills/ui-ux-pro-max/scripts/search.py "minimalism dark mode" --domain style

# 获取关于搜索交互和加载状态的 UX 最佳实践
python3 skills/ui-ux-pro-max/scripts/search.py "search loading animation" --domain ux
```

### 步骤 4：技术栈指南

```bash
python3 skills/ui-ux-pro-max/scripts/search.py "list performance navigation" --stack react-native
```

**随后**：综合设计系统与细节搜索结果，并实现设计方案。

---

## 输出格式

`--design-system` 标志支持两种输出格式：

```bash
# ASCII 框（默认）- 最适合终端显示
python3 skills/ui-ux-pro-max/scripts/search.py "fintech crypto" --design-system

# Markdown 格式 - 最适合文档记录
python3 skills/ui-ux-pro-max/scripts/search.py "fintech crypto" --design-system -f markdown
```

---

## 获得更好结果的实用技巧

### 查询策略

- 使用**多维度关键词** —— 结合产品 + 行业 + 基调 + 密度，例如：`"entertainment social vibrant content-dense"`，而不是简单地使用 `"app"`
- 尝试对同一需求使用不同的关键词：`"playful neon"` → `"vibrant dark"` → `"content-first minimal"`
- 首先使用 `--design-system` 获取完整推荐，然后使用 `--domain` 对你不确定的任何维度进行深度探索
- 始终添加 `--stack react-native` 以获得特定于实现的开发指导

### 常见痛点与解决方案

| 问题 | 解决方案 |
|---------|------------|
| 无法决定风格或配色 | 使用不同的关键词重新运行 --design-system |
| 暗色模式下的对比度问题 | 参考快速参考手册第 6 节：color-dark-mode + color-accessible-pairs |
| 动画效果显得不自然 | 参考快速参考手册第 7 节：spring-physics + easing + exit-faster-than-enter |
| 表单的 UX 体验较差 | 参考快速参考手册第 8 节：inline-validation + error-clarity + focus-management |
| 导航体验令人困惑 | 参考快速参考手册第 9 节：nav-hierarchy + bottom-nav-limit + back-behavior |
| 布局在小屏幕上发生错乱 | 参考快速参考手册第 5 节：mobile-first + breakpoint-consistency |
| 性能问题 / 界面卡顿 | 参考快速参考手册第 3 节：virtualize-lists + main-thread-budget + debounce-throttle |

### 交付前核对清单

- 在实现前运行 `--domain ux "animation accessibility z-index loading"` 作为 UX 校验步骤
- 仔细检查快速参考手册的 **§1–§3**（严重 + 高优先级）作为最终审查
- 在 375px（小屏幕手机）以及横屏模式下进行测试
- 在启用 **减弱动态效果 (reduced-motion)** 以及 **动态字体 (Dynamic Type)** 最大字号时验证界面表现
- 独立检查暗色模式的对比度（不要假定亮色模式的参数直接可用）
- 确保所有触控目标 ≥44pt 且没有任何内容被遮挡在安全区域之外

---

## 专业 UI 的通用规则

以下是经常被忽视、会导致 UI 显得不够专业的常见问题：
范围说明：以下规则适用于 App UI（iOS/Android/React Native/Flutter），而非桌面端网页的交互模式。

### 图标与视觉元素

- 默认图标库使用 **Phosphor (`@phosphor-icons/react`)**。`src/ui-ux-pro-max/data/icons.csv` 中列出的只是常用推荐图标，不是完整集合。
- 当推荐表中找不到合适的图标时：
  - **优先继续从 Phosphor 的完整图标集中选择任何语义更贴切的图标**；
  - 如果 Phosphor 也没有理想选项，可以使用 **Heroicons (`@heroicons/react`)** 作为备选，注意保持风格一致（线性/填充、笔画粗细、圆角风格）。

| 规则 (Rule) | 规范标准 (Standard) | 应避免的反面模式 (Avoid) | 为什么重要 (Why It Matters) |
|------|----------|--------|----------------|
| **No Emoji as Structural Icons** | 使用矢量图标（如 Phosphor `@phosphor-icons/react`、Heroicons `@heroicons/react`、react-native-vector-icons、@expo/vector-icons）。 | 在导航、设置或系统控件中使用 Emoji 表情符号（🎨 🚀 ⚙️）。 | 表情符号依赖系统字体，在不同平台上显示不一致，且无法通过设计 Token 进行控制。 |
| **Vector-Only Assets** | 使用能够干净缩放且支持主题切换的 SVG 或平台矢量图标。 | 使用在缩放时会模糊或出现像素点的位图 PNG 图标。 | 确保可伸缩性、清晰的渲染以及亮/暗色模式的适配能力。 |
| **Stable Interaction States** | 在按压状态下使用颜色、不透明度或高度过渡，而不改变布局的边界尺寸。 | 使用会移动周围内容或引发视觉抖动的、会导致布局偏移的形变 (transform)。 | 防止不稳定的交互，保持流畅的动效并提升移动端用户的感知 quality。 |
| **Correct Brand Logos** | 使用官方品牌资源，并遵循其使用指南（间距、颜色、安全空间）。 | 胡乱猜测 Logo 路径、未经授权重新配色或修改品牌比例。 | 避免品牌滥用，并确保符合法律和平台合规性要求。 |
| **Consistent Icon Sizing** | 将图标尺寸定义为设计 Token（例如 icon-sm, icon-md = 24pt, icon-lg）。 | 随意混用 20pt / 24pt / 28pt 等任意数值。 | 维护整个界面中的视觉节奏和清晰的层级结构。 |
| **Stroke Consistency** | 在同一视觉层级内使用一致的线条描边宽度（例如 1.5px 或 2px）。 | 随意混用粗细不一的描边风格。 | 不一致的描边会降低界面的精致感和整体凝聚力。 |
| **Filled vs Outline Discipline** | 在同一层级内统一使用一种图标样式。 | 在同一层级中混合使用填充型 (filled) 和线性 (outline) 图标。 | 保持语义清晰度和风格的一致连贯。 |
| **Touch Target Minimum** | 至少 44×44pt 的交互区域（如果图标较小，使用 hitSlop 属性扩展点击区域）。 | 使用没有扩展点击区域的小图标。 | 符合无障碍可访问性以及平台可用性规范。 |
| **Icon Alignment** | 将图标与文本基线对齐，并保持一致的内边距。 | 使用未对齐的图标或其周围出现不一致的间距。 | 防止因细微的视觉失衡而降低界面整体的品质感。 |
| **Icon Contrast** | 遵循 WCAG 对比度标准：小元素为 4.5:1，较大的 UI 图形符号最小为 3:1。 | 使用会融入背景之中的低对比度图标。 | 确保在亮色和暗色模式下的无障碍可访问性。 |


### 交互规则 (App)

| 规则 (Rule) | 正面实践 (Do) | 反面模式 (Don't) |
|------|----|----- |
| **Tap feedback** | 在 80-150ms 内提供清晰的按压反馈（涟漪/透明度/高度等） | 点击时没有任何视觉响应 |
| **Animation timing** | 微交互控制在 150-300ms 左右，采用平台原生缓动曲线 | 使用瞬间切换或过于缓慢的动画（>500ms） |
| **Accessibility focus** | 确保屏幕阅读器的焦点顺序与视觉顺序一致，且文本标签具有描述性 | 使用未加标签的控件或令人困惑的焦点遍历顺序 |
| **Disabled state clarity** | 使用禁用语义（disabled 或原生禁用属性）、降低视觉强调度、且不响应点击操作 | 控件看起来可以点击但点击后毫无反应 |
| **Touch target minimum** | 确保点击区域 >=44x44pt (iOS) 或 >=48x48dp (Android)，在图标较小时扩展热区 | 使用极小的点击目标，或没有外边距的纯图标热区 |
| **Gesture conflict prevention** | 在每个区域中只保留一种主要手势，并避免嵌套点击/拖拽冲突 | 重叠的手势引发用户的误操作 |
| **Semantic native controls** | 优先使用原生交互原语（如 Button, Pressable 或平台等效控件），并带有正确的 accessibility role | 在没有语义的情况下使用普通容器作为主要交互控件 |

### 亮/暗色模式对比度

| 规则 (Rule) | 正面实践 (Do) | 反面模式 (Don't) |
|------|----|----- |
| **Surface readability (light)** | 使用足够的透明度或高度差，使卡片/表面与背景有清晰的区隔 | 使用过度透明的表面而使层级关系变得模糊 |
| **Text contrast (light)** | 确保正文文本在亮色表面上的对比度 >=4.5:1 | 使用低对比度的灰色正文 |
| **Text contrast (dark)** | 确保在暗色表面上，主要文本对比度 >=4.5:1，次要文本对比度 >=3:1 | 暗色模式下的文本融入了背景中 |
| **Border and divider visibility** | 确保分割线在两个主题下均清晰可见（而不仅仅是亮色模式） | 特定主题的边框在某一种模式下完全消失 |
| **State contrast parity** | 确保在亮色和暗色主题下，按压/获取焦点/禁用的状态具有同等的可区分性 | 只针对其中一种主题定义交互状态 |
| **Token-driven theming** | 在应用表面、文本、图标中统一使用与各主题建立映射的语义化颜色 Token | 在每个屏幕的样式中硬编码十六进制颜色值 |
| **Scrim and modal legibility** | 使用足够强的模态框背景遮罩 (scrim) 以隔离前景内容（通常为 40-60% 的黑色半透明） | 使用太淡的遮罩使得背景内容依然与前景在视觉上产生竞争 |

### 布局与间距

| 规则 (Rule) | 正面实践 (Do) | 反面模式 (Don't) |
|------|----|----- |
| **Safe-area compliance** | 为所有固定页眉、标签栏和 CTA 栏严格预留顶部/底部安全区域 | 将固定 UI 放置在刘海屏、状态栏或手势区域的下方且未作适配 |
| **System bar clearance** | 为状态栏/导航栏和底部手势指示条添加足够的间距 | 让可点击内容与操作系统的系统 UI 元素相冲突 |
| **Consistent content width** | 按设备类别（手机/平板）保持可预测的、统一的内容宽度 | 在不同屏幕之间混用随意的宽度 |
| **8dp spacing rhythm** | 在内边距/元素间距/区域间距中统一使用一致的 4/8dp 间距系统 | 使用毫无节奏感、随意递增的间距值 |
| **Readable text measure** | 在大屏设备上保持长篇文本的易读性（避免在平板上出现通栏横跨的段落） | 直接使用通栏长句而损害文本的可读性 |
| **Section spacing hierarchy** | 按层级定义清晰的垂直间距阶梯（例如 16/24/32/48） | 在相似的 UI 层级上使用不一致的间距 |
| **Adaptive gutters by breakpoint** | 在更宽的屏幕上以及横屏模式下，增加两侧的水平边距 | 在所有设备尺寸和屏幕方向下均使用相同的窄边距 |
| **Scroll and fixed element coexistence** | 添加底部/顶部内容内边距 (insets)，以确保滚动列表底端不会被固定定位的底栏遮挡 | 滚动内容被粘性定位的头部/尾部底栏永久遮挡 |

---

## 交付前核对清单

在交付 UI 代码前，请逐一核对以下各项：
范围说明：此清单适用于 App UI（iOS/Android/React Native/Flutter）。

### 视觉品质
- [ ] 不使用 Emoji 表情符号作为图标（应使用 SVG/矢量图标）
- [ ] 所有图标均来自风格和家族统一的图标集
- [ ] 使用官方品牌资源，保持正确的比例和安全距离
- [ ] 按压状态下的视觉效果不会引发布局边框偏移或抖动
- [ ] 统一使用语义化主题 Token（不使用硬编码的单页面颜色值）

### 交互体验
- [ ] 所有可点击的元素均提供清晰的按压反馈（涟漪/透明度/高度等）
- [ ] 触控热区满足最小尺寸要求（iOS >=44x44pt，Android >=48x48dp）
- [ ] 微交互时长保持在 150-300ms 范围内，具有原生质感的缓动曲线
- [ ] 禁用状态在视觉上清晰可辨，且不响应任何交互
- [ ] 屏幕阅读器的焦点顺序与视觉顺序匹配，且交互控件标签具有描述性
- [ ] 手势区域避开嵌套/冲突的交互手势（避免点击、拖拽、侧滑返回发生冲突）

### 亮/暗色模式
- [ ] 在亮色和暗色模式下，主要文本对比度均 >=4.5:1
- [ ] 在亮色和暗色模式下，次要文本对比度均 >=3:1
- [ ] 分割线/边框以及各种交互状态在亮暗两种模式下均可清晰辨识
- [ ] 模态框/抽屉的背景遮罩透明度足够强，以确保前景文本易读（通常为 40-60% 的黑色半透明）
- [ ] 交付前对两个主题均进行了实际测试（不要仅凭单一主题的效果推断另一主题）

### 布局表现
- [ ] 页眉、标签栏和底部 CTA 栏均已对安全区域（Safe Areas）进行避让适配
- [ ] 滚动列表的内容尾部不会被固定/粘性底栏遮掩
- [ ] 已经在小屏手机、大屏手机以及平板上（含横竖屏）进行了验证
- [ ] 水平页边距/槽宽 (insets/gutters) 能够针对设备尺寸和屏幕方向进行正确适配
- [ ] 在组件、区域和页面层级上均维护了统一的 4/8dp 间距节奏
- [ ] 在大屏设备上限制了长篇文本的单行字数（不直接使用通栏段落）

### 无障碍可访问性
- [ ] 所有有实际意义的图片/图标都带有辅助说明标签 (accessibility labels)
- [ ] 表单字段具有标签、提示信息以及清晰的错误消息
- [ ] 颜色不是传达数据的唯一指示标识
- [ ] 支持减弱动态效果与动态字体缩放，且不会导致界面布局错乱
- [ ] 各种辅助功能属性/角色/状态（如 selected, disabled, expanded）能被系统正确播报