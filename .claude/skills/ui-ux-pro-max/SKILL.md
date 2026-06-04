---
name: ui-ux-pro-max
description: "UI/UX design intelligence for web and mobile. Includes 50+ styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, and 25 chart types across 10 stacks (React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, and HTML/CSS). Actions: plan, build, create, design, implement, review, fix, improve, optimize, enhance, refactor, and check UI/UX code. Projects: website, landing page, dashboard, admin panel, e-commerce, SaaS, portfolio, blog, and mobile app. Elements: button, modal, navbar, sidebar, card, table, form, and chart. Styles: glassmorphism, claymorphism, minimalism, brutalism, neumorphism, bento grid, dark mode, responsive, skeuomorphism, and flat design. Topics: color systems, accessibility, animation, layout, typography, font pairing, spacing, interaction states, shadow, and gradient. Integrations: shadcn/ui MCP for component search and examples."
---

# UI/UX Pro Max - 设计智能 (Design Intelligence)

适用于 Web 和移动端应用的全面设计指南。包含 50+ 种风格、161 种配色方案、57 种字体搭配、161 种带有推导逻辑规则的产品类型、99 条 UX 指南以及涵盖 10 种技术栈的 25 种图表类型。支持基于优先级推荐的检索数据库。

## 适用场景 (When to Apply)

当任务涉及 **UI 结构、视觉设计决策、交互模式或用户体验质量控制**时，应使用此 Skill。

### 必须使用 (Must Use)

在以下情况下，必须调用此 Skill：

- 设计新页面（落地页、仪表盘、管理后台、SaaS、移动端 App）
- 创建或重构 UI 组件（按钮、模态框、表单、表格、图表等）
- 选择配色方案、排版系统、间距标准或布局系统
- 针对用户体验、无障碍或视觉一致性审查 UI 代码
- 实现导航结构、动画效果或响应式行为
- 做出产品级的设计决策（风格、信息层级、品牌表达）
- 提升界面的感知质量、清晰度或可用性

### 推荐使用 (Recommended)

在以下情况下，推荐使用此 Skill：

- UI 看起来“不够专业”但具体原因不明
- 收到关于可用性或体验的反馈
- 发布前进行 UI 质量优化
- 对齐跨平台设计（Web / iOS / Android）
- 构建设计系统或可重用组件库

### 跳过 (Skip)

在以下情况下，不需要此 Skill：

- 纯后端逻辑开发
- 仅涉及 API 或数据库设计
- 与界面无关的性能优化
- 基础设施或 DevOps 工作
- 非视觉脚本或自动化任务

**决策标准 (Decision criteria)**：如果任务将改变功能的**外观、感觉、动效或交互方式**，则应使用此 Skill。

## 按优先级划分的规则类别 (Rule Categories by Priority)

*供人类/AI 参考：请按照优先级 1→10 决定首先关注哪个规则类别；需要时使用 `--domain <Domain>` 来查询细节。脚本不会读取此表格。*

| 优先级 | 规则类别 | 影响程度 | 领域 (Domain) | 关键检查项（必须具备） | 应避免的反面模式 |
|----------|----------|--------|--------|------------------------|------------------------|
| 1 | 无障碍可访问性 (Accessibility) | 严重 (CRITICAL) | `ux` | 对比度 4.5:1、Alt 文本、键盘导航、Aria 标签 | 移除焦点环、没有标签的纯图标按钮 |
| 2 | 触控与交互 (Touch & Interaction) | 严重 (CRITICAL) | `ux` | 最小尺寸 44×44px、8px+ 间距、加载反馈 | 仅依赖悬停操作、瞬时状态改变 (0ms) |
| 3 | 性能表现 (Performance) | 高 (HIGH) | `ux` | WebP/AVIF、延迟加载、预留空间 (CLS < 0.1) | 布局抖动、累计布局偏移 (CLS) |
| 4 | 风格选择 (Style Selection) | 高 (HIGH) | `style`, `product` | 匹配产品类型、一致性、SVG 图标（无表情符号） | 随机混用扁平与拟物、Emoji 表情用作图标 |
| 5 | 布局与响应式 (Layout & Responsive) | 高 (HIGH) | `ux` | 移动端优先断点、视口 meta、无水平滚动 | 水平滚动、固定像素 container 宽度、禁用缩放 |
| 6 | 排版与色彩 (Typography & Color) | 中 (MEDIUM) | `typography`, `color` | 基础 16px、行高 1.5、语义化颜色 Token | 正文文本 < 12px、灰底灰字、组件内硬编码 Hex 值 |
| 7 | 动画效果 (Animation) | 中 (MEDIUM) | `ux` | 时长 150–300ms、动效传达意图、空间连续性 | 仅作装饰的动画、动画化宽/高、不支持减弱动态效果 |
| 8 | 表单与反馈 (Forms & Feedback) | 中 (MEDIUM) | `ux` | 可见标签、邻近字段的错误提示、帮助文本、渐进式呈现 | 仅有占位符标签、错误仅显示在顶部、一开始呈现过多内容 |
| 9 | 导航模式 (Navigation Patterns) | 高 (HIGH) | `ux` | 可预测的返回、底部导航 ≤5 个、深度链接 | 导航项过载、损坏的返回行为、无深度链接 |
| 10 | 图表与数据 (Charts & Data) | 低 (LOW) | `chart` | 图例、工具提示、无障碍配色 | 仅依赖颜色来表达数据含义 |

## Quick Reference

### 1. Accessibility (CRITICAL)

- `color-contrast` - 普通文本的对比度至少为 4.5:1（大文本为 3:1）（参考 Material Design）
- `focus-states` - 交互元素上必须有清晰可见的焦点环（2–4px；参考 Apple HIG, MD）
- `alt-text` - 为有实际意义的图片提供描述性的 alt 文本
- `aria-labels` - 为纯图标按钮提供 `aria-label`；在原生应用中使用 `accessibilityLabel`（参考 Apple HIG）
- `keyboard-nav` - 键盘 Tab 键的聚焦顺序应与视觉顺序一致；提供完整的键盘支持（参考 Apple HIG）
- `form-labels` - 使用带有 `for` 属性的 label 标签与输入框关联
- `skip-links` - 为键盘用户提供“跳过至主要内容”的快捷链接
- `heading-hierarchy` - 标题级别应按 h1→h6 顺序递增，不能跳过级别
- `color-not-only` - 不要仅通过颜色来传达信息（应辅以图标或文字说明）
- `dynamic-type` - 支持系统文字缩放；避免文本变大时发生截断（参考 Apple Dynamic Type, MD）
- `reduced-motion` - 尊重用户的“减弱动态效果”设置；在用户要求时减少或禁用动画（参考 Apple Reduced Motion API, MD）
- `voiceover-sr` - 提供有意义的 `accessibilityLabel` / `accessibilityHint`；为 VoiceOver / 屏幕阅读器保持逻辑清晰的朗读顺序（参考 Apple HIG, MD）
- `escape-routes` - 在模态框和多步骤流程中提供取消或返回的出口路径（参考 Apple HIG）
- `keyboard-shortcuts` - 保留系统和辅助功能的默认快捷键；为拖拽操作提供键盘替代方案（参考 Apple HIG）

### 2. Touch & Interaction (CRITICAL)

- `touch-target-size` - 最小触控热区为 44×44pt (Apple) / 48×48dp (Material)；如有必要，可将点击热区扩展至视觉边界之外
- `touch-spacing` - 触控目标之间至少保持 8px/8dp 的间距（参考 Apple HIG, MD）
- `hover-vs-tap` - 核心交互使用点击/轻触触发；不要仅依赖悬停操作 (hover)
- `loading-buttons` - 在异步操作期间禁用按钮；显示加载动画 (spinner) 或进度条
- `error-feedback` - 在发生问题的地方邻近处展示清晰的错误提示信息
- `cursor-pointer` - 为可点击元素添加 `cursor-pointer` 样式（Web 端）
- `gesture-conflicts` - 避免在主要内容区域使用水平滑动操作；优先使用垂直滚动
- `tap-delay` - 使用 `touch-action: manipulation` 来消除 300ms 的点击延迟（Web 端）
- `standard-gestures` - 始终一致地使用平台标准手势，不要重新定义其含义（例如：侧滑返回、捏合缩放）（参考 Apple HIG）
- `system-gestures` - 不要阻碍系统手势操作（如控制中心、侧滑返回等）（参考 Apple HIG）
- `press-feedback` - 点击时提供明确的视觉反馈（如涟漪效果/高亮；参考 MD 状态层）
- `haptic-feedback` - 在确认和重要操作时使用触觉反馈，但要避免滥用（参考 Apple HIG）
- `gesture-alternative` - 不要依赖仅手势触发的交互；对于核心操作，必须始终提供可见的常规控件
- `safe-area-awareness` - 核心触控目标必须避开刘海屏、动态岛、底部手势条和屏幕边缘
- `no-precision-required` - 避免要求用户在极小的图标或狭窄的边缘上进行像素级的精准点击
- `swipe-clarity` - 滑动操作必须提供清晰的视觉线索或提示（如箭头、标签、新手引导）
- `drag-threshold` - 在开始拖拽前设置移动阈值，以避免用户的误触拖动

### 3. Performance (HIGH)

- `image-optimization` - 使用 WebP/AVIF 格式，使用响应式图片（`srcset`/`sizes`），延迟加载非核心资源
- `image-dimension` - 明确声明图片的 `width`/`height` 或使用 `aspect-ratio`，以防止页面布局抖动（参考 Core Web Vitals: CLS）
- `font-loading` - 使用 `font-display: swap/optional` 来避免文字隐形 (FOIT)；为文字预留空间以减少布局偏移（参考 MD）
- `font-preload` - 仅预加载最关键的字体；避免对每种字重和变体都使用 preload
- `critical-css` - 优先加载首屏 CSS（使用内联关键 CSS 或尽早加载的样式表）
- `lazy-loading` - 通过动态导入 (dynamic import) / 路由级拆分，延迟加载非首屏组件
- `bundle-splitting` - 按路由/功能进行代码拆分（使用 React Suspense / Next.js dynamic）以减少初始加载体积和缩短 TTI
- `third-party-scripts` - 异步或延迟加载第三方脚本（`async`/`defer`）；审计并移除无用脚本（参考 MD）
- `reduce-reflows` - 避免频繁读写布局；将 DOM 的读取和写入操作分别进行合并批处理
- `content-jumping` - 为异步加载的内容预留占位空间，以避免页面布局发生跳跃（参考 Core Web Vitals: CLS）
- `lazy-load-below-fold` - 对折行（首屏）以下图片和重度媒体资源使用 `loading="lazy"`
- `virtualize-lists` - 对包含 50+ 项的列表使用虚拟化技术，以提高内存效率和滚动性能
- `main-thread-budget` - 保持每帧工作在 ~16ms 以内以达到 60fps；将繁重的计算任务移出主线程（参考 HIG, MD）
- `progressive-loading` - 对于耗时超过 1s 的操作，使用骨架屏/闪光占位符，而不是长时间显示静态加载菊花图（参考 Apple HIG）
- `input-latency` - 保持点击/滚动的输入延迟在 ~100ms 以内（参考 Material 响应性标准）
- `tap-feedback-speed` - 在点击后 100ms 内提供视觉反馈（参考 Apple HIG）
- `debounce-throttle` - 对高频事件（如滚动、调整大小、输入）进行防抖 (debounce) 或节流 (throttle) 处理
- `offline-support` - 提供离线状态提示和基本兜底体验（PWA / 移动端）
- `network-fallback` - 针对慢速网络提供降级模式（低分辨率图片、减少动画效果）

### 4. Style Selection (HIGH)

- `style-match` - 风格必须与产品类型匹配（使用 `--design-system` 获取推荐建议）
- `consistency` - 在所有页面中保持风格一致
- `no-emoji-icons` - 使用矢量 SVG 图标（如 Heroicons, Lucide），不要使用 Emoji 表情符号作为图标
- `color-palette-from-product` - 根据产品/行业属性选择配色方案（使用 `--domain color` 查询）
- `effects-match-style` - 阴影、模糊、圆角大小应与所选风格保持一致（如玻璃拟态、扁平化、粘土拟态等）
- `platform-adaptive` - 尊重平台的设计惯例（iOS HIG vs Material Design）：在导航、控件、排版、动效上做好适配
- `state-clarity` - 使悬停/按压/禁用状态在视觉上清晰可辨，同时与整体风格协调（参考 Material 状态层）
- `elevation-consistent` - 为卡片、面板、模态框使用一致的高度/阴影阶梯；避免使用随意的阴影值
- `dark-mode-pairing` - 同时设计亮色和暗色版本，以保持品牌感、对比度和风格的一致性
- `icon-style-consistent` - 在整个产品中使用统一的图标集/视觉语言（如相同的线宽、圆角）
- `system-controls` - 优先使用系统/原生控件，而不是完全自定义；仅在品牌调性有明确要求时进行定制（参考 Apple HIG）
- `blur-purpose` - 使用模糊效果来暗示背景已被遮罩/关闭（如模态框、面板），而不是单纯作为装饰（参考 Apple HIG）
- `primary-action` - 每个屏幕应有且仅有一个主要 CTA（行动召唤按钮）；次要操作在视觉上应弱化（参考 Apple HIG）

### 5. Layout & Responsive (HIGH)

- `viewport-meta` - 设置 `width=device-width initial-scale=1`（切勿禁用缩放）
- `mobile-first` - 采用移动端优先的设计，随后逐步适配平板和桌面端
- `breakpoint-consistency` - 使用系统化的屏幕断点（例如 375 / 768 / 1024 / 1440）
- `readable-font-size` - 移动端正文文本至少为 16px（以避免 iOS 自动放大输入框）
- `line-length-control` - 移动端每行 35–60 个字符；桌面端每行 60–75 个字符
- `horizontal-scroll` - 移动端避免出现水平滚动条；确保内容完全自适应视口宽度
- `spacing-scale` - 使用 4pt/8dp 增量间距系统（参考 Material Design）
- `touch-density` - 保持适合触控的组件间距：不要过于拥挤，防止用户误触
- `container-width` - 桌面端使用一致的最大宽度（如 `max-w-6xl` / `7xl`）
- `z-index-management` - 定义清晰的 z-index 层级规范（例如 0 / 10 / 20 / 40 / 100 / 1000）
- `fixed-element-offset` - 固定定位的导航栏/底栏必须为底层内容预留安全边距 (padding)
- `scroll-behavior` - 避免使用会干扰主页面滚动体验的嵌套滚动区域
- `viewport-units` - 在移动端优先使用 `min-h-dvh`，而不是 `100vh`
- `orientation-support` - 确保布局在横屏模式下依然易读且可操作
- `content-priority` - 在移动端优先展示核心内容；将次要内容折叠或隐藏
- `visual-hierarchy` - 通过大小、间距、对比度来建立清晰的层级关系 —— 而不仅仅依赖颜色

### 6. Typography & Color (MEDIUM)

- `line-height` - 正文文本使用 1.5-1.75 的行高
- `line-length` - 限制单行字符数在 65-75 个字符以内
- `font-pairing` - 确保标题与正文字体的性格与气质相契合
- `font-scale` - 使用一致的字号阶梯（例如 12 14 16 18 24 32）
- `contrast-readability` - 亮色背景上使用深色文字（例如在白色背景上使用 `slate-900`）
- `text-styles-system` - 使用平台字形排版系统：iOS 11 动态字体样式 / Material 5 字体角色（display, headline, title, body, label）（参考 HIG, MD）
- `weight-hierarchy` - 使用字重强化层级：粗体标题（600-700）、常规正文（400）、中等标签（500）（参考 MD）
- `color-semantic` - 定义语义化颜色 Token（primary, secondary, error, surface, on-surface），不要在组件中直接硬编码 Hex 颜色值（参考 Material 颜色系统）
- `color-dark-mode` - 暗色模式应使用低饱和度/较浅的同音色调，而不是直接反转颜色；独立进行对比度测试（参考 HIG, MD）
- `color-accessible-pairs` - 前景/背景配色必须满足 4.5:1 (AA) 或 7:1 (AAA)；使用工具进行验证（参考 WCAG, MD）
- `color-not-only-decorative` - 功能性颜色（错误红、成功绿）必须辅以图标或文本；避免单纯通过颜色表达含义（参考 HIG, MD）
- `truncation-strategy` - 换行优先于截断；需要截断时使用省略号，并通过工具提示 (tooltip) 或展开操作提供完整文本（参考 Apple HIG）
- `letter-spacing` - 遵循平台默认的字距；避免在正文文本上使用过紧的字距（参考 HIG, MD）
- `number-tabular` - 对数据列、价格和计时器使用等宽数字 (tabular/monospaced figures)，以防止数据变化时布局抖动
- `whitespace-balance` - 有意图地使用留白来对相关项进行分组以及分隔区域；避免界面视觉拥挤（参考 Apple HIG）

### 7. Animation (MEDIUM)

- `duration-timing` - 微交互时长使用 150-300ms；复杂过渡动画 ≤400ms；避免使用 >500ms 的时长（参考 MD）
- `transform-performance` - 仅对 `transform` 和 `opacity` 进行动画处理；避免对 `width` / `height` / `top` / `left` 做动画
- `loading-states` - 当加载时间超过 300ms 时，显示骨架屏或进度指示器
- `excessive-motion` - 每个视图中最多对 1-2 个核心元素进行动画处理
- `easing` - 入场使用 ease-out，出场使用 ease-in；在 UI 过渡中避免使用线性 (linear) 缓动
- `motion-meaning` - 所有的动画必须表达因果关系，而不仅仅是作为装饰（参考 Apple HIG）
- `state-transition` - 状态变化（悬停、激活、展开、收起、模态框）应平滑过渡，避免瞬间生硬切换
- `continuity` - 页面/屏幕过渡应保持空间连续性（如共享元素、方向性滑动）（参考 Apple HIG）
- `parallax-subtle` - 克制地使用视差效果；必须尊重减弱动态效果设置，且不能引起眩晕（参考 Apple HIG）
- `spring-physics` - 优先使用弹簧/物理阻尼曲线，而不是线性或贝塞尔曲线，以获得更自然的质感（参考 Apple HIG 流体动画）
- `exit-faster-than-enter` - 出场动画应快于入场动画（约为入场时长的 60-70%）以显得响应迅速（参考 MD 动效规范）
- `stagger-sequence` - 对列表/网格项的入场动效进行交错处理，每项延迟 30-50ms；避免同时展现或过慢展现（参考 MD）
- `shared-element-transition` - 使用共享元素 / Hero 过渡，以保持屏幕之间的视觉连续性（参考 MD, HIG）
- `interruptible` - 动画必须是可打断的；用户的点击/手势应能立即取消正在进行的动画（参考 Apple HIG）
- `no-blocking-animation` - 绝不要在动画进行中阻塞用户输入；UI 必须保持可即时交互状态（参考 Apple HIG）
- `fade-crossfade` - 在同一个容器内进行内容替换时，使用交叉淡入淡出 (crossfade)（参考 MD）
- `scale-feedback` - 可点击的卡片/按钮在按压时进行轻微缩放 (0.95-1.05)；松开时恢复原状（参考 HIG, MD）
- `gesture-feedback` - 拖拽、滑动和捏合必须提供实时跟随手指运动的视觉响应（参考 MD 动效）
- `hierarchy-motion` - 使用平移/缩放方向来表达层级关系：从下方入场 = 更深层级，向上方退出 = 返回上一级（参考 MD）
- `motion-consistency` - 全局统一时长和缓动 Token；使所有的动画共享相同的节奏和质感
- `opacity-threshold` - 渐隐元素的透明度低于 0.2 时不应停留太久；要么完全淡出，要么保持可见
- `modal-motion` - 模态框/面板应从其触发源位置开始动画（缩放+淡入，或滑入），以提供空间上下文关系（参考 HIG, MD）
- `navigation-direction` - 前进导航向左/向上移动；后退导航向右/向下移动 —— 保持方向逻辑一致（参考 HIG）
- `layout-shift-avoid` - 动画绝对不能引发页面重排或 CLS；使用 transform 改变位置

### 8. Forms & Feedback (MEDIUM)

- `input-labels` - 每一个输入框都必须有可见的 label 标签（不只提供 input 占位符 placeholder）
- `error-placement` - 在对应的输入框下方展示错误提示信息
- `submit-feedback` - 提交时展示加载状态，随后展示成功或错误状态
- `required-indicators` - 标明必填字段（例如使用星号 *）
- `empty-states` - 无内容时提供有帮助的提示信息和操作引导
- `toast-dismiss` - Toast 提示在 3-5 秒内自动消失
- `confirmation-dialogs` - 执行破坏性操作前弹出确认对话框
- `input-helper-text` - 在复杂的输入框下方提供常驻的辅助文本，而不仅仅依赖占位符（参考 Material Design）
- `disabled-states` - 禁用元素使用降低的不透明度 (0.38-0.5) + 光标改变 + 语义化 disabled 属性（参考 MD）
- `progressive-disclosure` - 渐进式呈现复杂选项；不要一开始就展示过多内容让用户手足无措（参考 Apple HIG）
- `inline-validation` - 在失去焦点 (blur) 时进行验证（而不是在打字时）；在用户输入完成后再显示错误（参考 MD）
- `input-type-keyboard` - 使用语义化的 input 类型（email, tel, number），以便在移动端弹出正确的键盘布局（参考 HIG, MD）
- `password-toggle` - 为密码输入框提供显示/隐藏明文的切换开关（参考 MD）
- `autofill-support` - 使用 `autocomplete` / `textContentType` 属性，以便系统可以自动填充表单（参考 HIG, MD）
- `undo-support` - 对破坏性或批量操作提供撤销支持（例如“撤销删除”的 Toast 提示）（参考 Apple HIG）
- `success-feedback` - 操作完成时提供简短的视觉确认反馈（打勾、Toast 提示、颜色闪烁）（参考 MD）
- `error-recovery` - 错误提示信息必须包含清晰的解决路径（重试、编辑、帮助链接）（参考 HIG, MD）
- `multi-step-progress` - 多步骤流程应展示步骤指示器或进度条；且允许返回上一步（参考 MD）
- `form-autosave` - 长表单应能自动保存草稿，防止因意外关闭而丢失数据（参考 Apple HIG）
- `sheet-dismiss-confirm` - 在关闭有未保存更改的面板/模态框前进行确认（参考 Apple HIG）
- `error-clarity` - 错误信息必须说明原因 + 如何修复（不能只说“输入无效”）（参考 HIG, MD）
- `field-grouping` - 将相关的输入框进行逻辑分组（使用 fieldset/legend 或视觉边框/背景分组）（参考 MD）
- `read-only-distinction` - 只读状态与禁用状态在视觉和语义上应有明确的区隔（参考 MD）
- `focus-management` - 提交出错后，自动将焦点移至第一个无效的输入框（参考 WCAG, MD）
- `error-summary` - 存在多个错误时，在顶部显示错误摘要并提供跳转到各输入框的锚点链接（参考 WCAG）
- `touch-friendly-input` - 移动端输入框高度 ≥44px 以满足触控热区要求（参考 Apple HIG）
- `destructive-emphasis` - 破坏性操作使用语义化的危险颜色（红色），并与主要操作进行视觉隔离（参考 HIG, MD）
- `toast-accessibility` - Toast 提示不能强行抢占焦点；使用 `aria-live="polite"` 供屏幕阅读器播报（参考 WCAG）
- `aria-live-errors` - 表单错误使用 `aria-live` 区域或 `role="alert"` 属性以便通知屏幕阅读器（参考 WCAG）
- `contrast-feedback` - 错误和成功状态的颜色必须满足 4.5:1 的对比度要求（参考 WCAG, MD）
- `timeout-feedback` - 请求超时必须提供清晰的反馈以及重试选项（参考 MD）

### 9. Navigation Patterns (HIGH)

- `bottom-nav-limit` - 底部导航栏最多包含 5 个项目；且图标必须搭配文字标签（参考 Material Design）
- `drawer-usage` - 使用抽屉栏/侧边栏进行次要导航，不要用来放置主要操作（参考 Material Design）
- `back-behavior` - 返回导航必须可预测且保持一致；保留页面滚动位置/先前状态（参考 Apple HIG, MD）
- `deep-linking` - 所有核心屏幕必须支持深度链接 / URL 访问，以便于分享和推送通知（参考 Apple HIG, MD）
- `tab-bar-ios` - iOS：在顶层导航中使用底部的 Tab Bar（参考 Apple HIG）
- `top-app-bar-android` - Android：在顶层结构中使用带有导航图标的 Top App Bar（参考 Material Design）
- `nav-label-icon` - 导航项目必须同时包含图标与文字标签；纯图标导航会降低功能的可发现性（参考 MD）
- `nav-state-active` - 在导航栏中，当前所在位置必须有清晰的视觉高亮（颜色、字重、指示条）（参考 HIG, MD）
- `nav-hierarchy` - 主要导航（Tab/底部导航）与次要导航（侧边栏/设置）必须在视觉上清晰隔离（参考 MD）
- `modal-escape` - 模态框和面板必须提供清晰的关闭/退出手势（移动端支持下滑手势关闭）（参考 Apple HIG）
- `search-accessible` - 搜索入口必须易于触达（如置于顶栏或 Tab 栏中）；提供最近搜索和推荐词（参考 MD）
- `breadcrumb-web` - Web 端：对于 3 层以上的层级深度，使用面包屑导航辅助定位（参考 MD）
- `state-preservation` - 返回导航必须能恢复先前的滚动位置、过滤状态和已填输入项（参考 HIG, MD）
- `gesture-nav-support` - 支持系统级手势导航（iOS 的滑动返回、Android 的预测性返回），避免与之发生冲突（参考 HIG, MD）
- `tab-badge` - 极克制地在导航项上使用徽标 (Badge) 来指示未读/待办；在用户访问后清除（参考 HIG, MD）
- `overflow-menu` - 当操作项超出可用空间时，使用“更多”/溢出菜单，而不是强行塞入（参考 MD）
- `bottom-nav-top-level` - 底部导航仅用于顶层屏幕；决不在其中嵌套子导航（参考 MD）
- `adaptive-navigation` - 大屏设备（≥1024px）优先使用侧边栏；小屏设备使用底部/顶部导航（参考 Material Adaptive）
- `back-stack-integrity` - 绝不默默重置导航栈，或出乎意图地直接跳转回首页（参考 HIG, MD）
- `navigation-consistency` - 导航栏的位置在所有页面中应保持一致；不要根据页面类型改变其位置
- `avoid-mixed-patterns` - 避免在同一层级混合使用 Tab、侧边栏和底部导航
- `modal-vs-navigation` - 模态框不能用于主要导航流程；它们会打断用户的路径（参考 HIG）
- `focus-on-route-change` - 页面过渡后，将焦点移至主要内容区域以服务屏幕阅读器用户（参考 WCAG）
- `persistent-nav` - 核心导航必须在深层页面中依然可触及；不要在子流程中将其完全隐藏（参考 HIG, MD）
- `destructive-nav-separation` - 危险的操作（删除账户、登出）必须与普通导航项在视觉和空间上隔离开（参考 HIG, MD）
- `empty-nav-state` - 当导航目的地不可用时，解释具体原因，而不是直接默默隐藏它（参考 MD）

### 10. Charts & Data (LOW)

- `chart-type` - 图表类型必须与数据类型匹配（趋势 → 折线图，对比 → 柱状图，占比 → 饼图/环形图）
- `color-guidance` - 使用无障碍配色方案；避免针对色盲用户仅提供红绿配色（参考 WCAG, MD）
- `data-table` - 提供表格形式的替代方案以满足无障碍要求；仅有图表对屏幕阅读器并不友好（参考 WCAG）
- `pattern-texture` - 用图案、纹理或形状来辅助颜色，以便在没有颜色的情况下也能区分数据（参考 WCAG, MD）
- `legend-visible` - 始终显示图例；并将其放置在靠近图表的地方，不要分离开放在滚动折行下方（参考 MD）
- `tooltip-on-interact` - 在悬停（Web 端）或点击（移动端）时提供展示确切数值的工具提示/数据标签（参考 HIG, MD）
- `axis-labels` - 标注带有单位和易读刻度的坐标轴；在移动端避免使用截断或旋转的标签
- `responsive-chart` - 图表在小屏幕上必须重新排版或简化（例如，用水平条形图代替垂直柱状图、减少刻度线）
- `empty-data-state` - 无数据时展示有意义的空状态（如“暂无数据” + 操作引导），而不是一张空白的图表（参考 MD）
- `loading-chart` - 在图表数据加载时使用骨架屏或闪光占位符；不要直接显示一个空的坐标轴框架
- `animation-optional` - 图表的入场动画必须尊重减弱动态效果设置；数据应该可以立即读取（参考 HIG）
- `large-dataset` - 对于 1000+ 的数据点，应进行聚合或抽样；提供下钻 (drill-down) 操作来查看详情，而不是一次性渲染所有数据（参考 MD）
- `number-formatting` - 对坐标轴和标签上的数字、日期、货币进行本地化格式化处理（参考 HIG, MD）
- `touch-target-chart` - 交互式的图表元素（如数据点、扇区）必须具有 ≥44pt 的触控区域，或在触控时放大区域（参考 Apple HIG）
- `no-pie-overuse` - 当分类超过 5 个时，避免使用饼图/环形图；改用条形图以提高清晰度
- `contrast-data` - 数据线/数据条与背景的对比度应 ≥3:1；数据文本标签与背景的对比度应 ≥4.5:1（参考 WCAG）
- `legend-interactive` - 图例应该是可点击的，以切换对应数据系列的显示与隐藏（参考 MD）
- `direct-labeling` - 对于小数据集，直接在图表上标注数值，以减少视线移动距离
- `tooltip-keyboard` - 工具提示内容必须是键盘可达的，而不仅仅依赖悬停操作（参考 WCAG）
- `sortable-table` - 数据表必须支持排序，并使用 `aria-sort` 指示当前的排序状态（参考 WCAG）
- `axis-readability` - 坐标轴刻度不能过于拥挤；保持易读的间距，在小屏幕上自动跳过部分刻度
- `data-density` - 限制每个图表的信息密度以避免认知超载；必要时拆分为多个图表
- `trend-emphasis` - 强调数据趋势而非装饰；避免使用遮挡数据的重阴影或渐变
- `gridline-subtle` - 网格线应保持低对比度（例如使用 `gray-200`），以免干扰数据展示
- `focusable-elements` - 交互式图表元素（数据点、柱条、扇区）必须是键盘可导航的（参考 WCAG）
- `screen-reader-summary` - 为屏幕阅读器提供文字摘要或 `aria-label` 描述图表的核心洞察（参考 WCAG）
- `error-state-chart` - 数据加载失败时必须展示带有重试操作的错误提示，而不是一个损坏或空白的图表
- `export-option` - 对于重度依赖数据的产品，提供图表数据的 CSV 或图片导出功能
- `drill-down-consistency` - 下钻交互必须保持清晰的返回路径和层级面包屑
- `time-scale-clarity` - 时间序列图表必须清晰标明时间粒度（日/周/月）并允许切换

## 如何使用 (How to Use)

使用下方的 CLI 工具搜索特定的领域。

---

## 前提条件 (Prerequisites)

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
| **新项目 / 页面** | "Build a landing page", "Build a dashboard" | 步骤 1 → 步骤 2（设计系统） |
| **新组件** | "Create a pricing card", "Add a modal" | 步骤 3（领域搜索：style, ux） |
| **选择风格 / 配色 / 字体** | "What style fits a fintech app?", "Recommend a color palette" | 步骤 2（设计系统） |
| **审查现有 UI** | "Review this page for UX issues", "Check accessibility" | 上方的快速参考清单 |
| **修复 UI 缺陷 (Bug)** | "Button hover is broken", "Layout shifts on load" | 快速参考 → 相关章节 |
| **改进 / 优化** | "Make this faster", "Improve mobile experience" | 步骤 3（领域搜索：ux, react） |
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
| 替代字体 | `typography` | `--domain typography "elegant luxury"` |
| 单个 Google 字体 | `google-fonts` | `--domain google-fonts "sans serif popular variable"` |
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
| `google-fonts` | 单个 Google Font 查询 | sans serif, monospace, japanese, variable font, popular |
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

| 规则 (Rule) | 规范标准 (Standard) | 应避免的反面模式 (Avoid) | 为什么重要 (Why It Matters) |
|------|----------|--------|----------------|
| **No Emoji as Structural Icons** | 使用矢量图标（如 Lucide、react-native-vector-icons、@expo/vector-icons）。 | 在导航、设置或系统控件中使用 Emoji 表情符号（🎨 🚀 ⚙️）。 | 表情符号依赖系统字体，在不同平台上显示不一致，且无法通过设计 Token 进行控制。 |
| **Vector-Only Assets** | 使用能够干净缩放且支持主题切换的 SVG 或平台矢量图标。 | 使用在缩放时会模糊或出现像素点的位图 PNG 图标。 | 确保可伸缩性、清晰的渲染以及亮/暗色模式的适配能力。 |
| **Stable Interaction States** | 在按压状态下使用颜色、不透明度或高度过渡，而不改变布局的边界尺寸。 | 使用会移动周围内容或引发视觉抖动的、会导致布局偏移的形变 (transform)。 | 防止不稳定的交互，保持流畅的动效并提升移动端用户的感知质量。 |
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