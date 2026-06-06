## When to Apply

当任务涉及 **UI 结构、视觉设计决策、交互模式或用户体验质量控制** 时，应使用此 Skill。

### Must Use

在以下情况必须调用此 Skill：

- 设计新的页面（Landing Page、Dashboard、Admin、SaaS、Mobile App）
- 创建或重构 UI 组件（按钮、弹窗、表单、表格、图表等）
- 选择配色方案、字体系统、间距规范或布局体系
- 审查 UI 代码的用户体验、可访问性或视觉一致性
- 实现导航结构、动效或响应式行为
- 做产品层级的设计决策（风格、信息层级、品牌表达）
- 提升界面的感知质量、清晰度或可用性

### Recommended

在以下情况建议使用此 Skill：

- UI 看起来"不够专业"，但原因不明确
- 收到可用性或体验方面的反馈
- 准备上线前的 UI 质量优化
- 需要对齐跨平台设计（Web / iOS / Android）
- 构建设计系统或可复用组件库

### Skip

在以下情况无需使用此 Skill：

- 纯后端逻辑开发
- 仅涉及 API 或数据库设计
- 与界面无关的性能优化
- 基础设施或 DevOps 工作
- 非视觉类脚本或自动化任务

**判断准则**：如果任务会改变某个功能 **看起来如何、使用起来如何、如何运动或如何被交互**，就应该使用此 Skill。

## Rule Categories by Priority

*供人工/AI 查阅：按 1→10 决定先关注哪类规则；需要细则时用 `--domain <Domain>` 查询。脚本不读取本表。*

| 优先级 | 类别 | 影响度 | 领域 | 关键检查项 (必须满足) | 反面模式 (避免使用) |
|----------|----------|--------|--------|------------------------|------------------------|
| 1 | 可访问性 (Accessibility) | 严重 (CRITICAL) | `ux` | 对比度 4.5:1、Alt 文本、键盘导航、Aria 标签 | 移除焦点环、无标签的仅图标按钮 |
| 2 | 触控与交互 (Touch & Interaction) | 严重 (CRITICAL) | `ux` | 最小尺寸 44×44px、8px+ 间距、加载反馈 | 仅依赖悬停 (hover)、瞬间状态切换 (0ms) |
| 3 | 性能 (Performance) | 高 (HIGH) | `ux` | WebP/AVIF、懒加载、保留空间 (CLS < 0.1) | 布局抖动、累积布局偏移 (CLS) |
| 4 | 风格选择 (Style Selection) | 高 (HIGH) | `style`, `product` | 匹配产品类型、一致性、SVG 图标 (不用表情符号) | 随机混合扁平与拟物风格、使用表情符号作为图标 |
| 5 | 布局与响应式 (Layout & Responsive) | 高 (HIGH) | `ux` | 移动优先断点、视口 meta 标签、无水平滚动 | 水平滚动、固定 px 容器宽度、禁用缩放 |
| 6 | 排版与色彩 (Typography & Color) | 中 (MEDIUM) | `typography`, `color` | 基础 16px、行高 1.5、语义化颜色 Token | 正文字体小于 12px、灰底灰字、在组件中硬编码十六进制颜色值 |
| 7 | 动画与动效 (Animation) | 中 (MEDIUM) | `ux` | 时长 150–300ms、动效传达意图、空间连续性 | 仅作装饰的动画、对宽度/高度进行动画处理、不支持减弱动态效果 (reduced-motion) |
| 8 | 表单与反馈 (Forms & Feedback) | 中 (MEDIUM) | `ux` | 可见标签、邻近字段的错误提示、帮助文本、渐进式呈现 | 仅占位符标签、错误仅显示在顶部、一开始展示过多信息 |
| 9 | 导航模式 (Navigation Patterns) | 高 (HIGH) | `ux` | 可预测的返回、底部导航 ≤5、深层链接 | 导航项过载、损坏的返回行为、缺少深层链接 |
| 10 | 图表与数据 (Charts & Data) | 低 (LOW) | `chart` | 图例、工具提示、无障碍色彩 | 仅依靠颜色来传达数据含义 |

## Quick Reference

### 1. Accessibility (CRITICAL)

- `color-contrast` - 普通文本的对比度至少为 4.5:1（大号文本为 3:1）；参考 Material Design
- `focus-states` - 交互元素上可见的焦点环（2–4px；参考 Apple HIG，MD）
- `alt-text` - 为有实际意义的图片提供描述性的 alt 属性
- `aria-labels` - 针对仅图标的按钮提供 aria-label 属性；在原生端使用 accessibilityLabel（参考 Apple HIG）
- `keyboard-nav` - 键盘 Tab 键切换顺序应与视觉顺序一致；提供完整的键盘导航支持（参考 Apple HIG）
- `form-labels` - 使用带有 for 属性的 label 标签关联输入框
- `skip-links` - 为键盘用户提供“跳过至主要内容”的快捷链接
- `heading-hierarchy` - 严格按 h1→h6 的顺序使用标题，不要跳级
- `color-not-only` - 不要仅通过颜色传达信息（应同时添加图标或文字）
- `dynamic-type` - 支持系统文字缩放；避免在文字变大时发生截断（参考 Apple Dynamic Type，MD）
- `reduced-motion` - 尊重 prefers-reduced-motion 属性；在用户有减弱动态效果需求时减少或禁用动画（参考 Apple Reduced Motion API，MD）
- `voiceover-sr` - 提供有意义的 accessibilityLabel/accessibilityHint；为 VoiceOver/屏幕阅读器设计合理的阅读顺序（参考 Apple HIG，MD）
- `escape-routes` - 在模态框和多步骤流程中提供取消或返回的出口（参考 Apple HIG）
- `keyboard-shortcuts` - 保留系统和辅助功能快捷键；为拖拽操作提供键盘替代方案（参考 Apple HIG）

### 2. Touch & Interaction (CRITICAL)

- `touch-target-size` - 触控目标尺寸最小为 44×44pt (Apple) / 48×48dp (Material)；必要时将点击区域扩展到视觉边界之外
- `touch-spacing` - 触控目标之间至少保持 8px/8dp 的间距（参考 Apple HIG，MD）
- `hover-vs-tap` - 使用点击/触控作为主要交互方式；不要仅依赖悬停 (hover)
- `loading-buttons` - 在异步操作期间禁用按钮；展示加载动效 (spinner) 或进度条
- `error-feedback` - 在问题字段邻近区域显示清晰的错误提示信息
- `cursor-pointer` - 为可点击元素添加 `cursor-pointer` 样式（Web 端）
- `gesture-conflicts` - 避免在主要内容区使用水平滑动交互；优先使用垂直滚动
- `tap-delay` - 使用 `touch-action: manipulation` 来消除 300ms 的点击延迟（Web 端）
- `standard-gestures` - 一致地使用平台标准手势，不要重新定义其功能（例如侧滑返回、捏合缩放）（参考 Apple HIG）
- `system-gestures` - 不要屏蔽或干扰系统手势（如控制中心、侧滑返回等）（参考 Apple HIG）
- `press-feedback` - 按压时提供即时的视觉反馈（涟漪效果/高亮；参考 MD 状态层设计）
- `haptic-feedback` - 在确认和重要操作时使用触觉反馈，但避免滥用（参考 Apple HIG）
- `gesture-alternative` - 不要依赖仅手势的交互；为关键操作始终提供可见的控制控件
- `safe-area-awareness` - 避开刘海屏 (notch)、动态岛 (Dynamic Island)、底部手势条及屏幕边缘，将主要触控目标置于安全区域内
- `no-precision-required` - 避免要求用户在微小的图标或极窄的边缘上进行像素级精准的点击
- `swipe-clarity` - 滑动操作必须提供清晰的视觉暗示或提示（如箭头、文字标签、新手引导）
- `drag-threshold` - 在开始拖拽前设置移动阈值，以避免误触触发拖拽

### 3. Performance (HIGH)

- `image-optimization` - 使用 WebP/AVIF 格式，使用响应式图片（srcset/sizes），延迟加载非关键资源
- `image-dimension` - 声明图片的 width/height 或使用 aspect-ratio 属性，以防布局偏移（核心网页指标：CLS）
- `font-loading` - 使用 `font-display: swap/optional` 以避免文字隐形 (FOIT)；保留布局空间以减少布局偏移（参考 MD）
- `font-preload` - 仅预加载关键字体；避免过度预加载每个字体变体
- `critical-css` - 优先处理首屏 CSS（内联关键 CSS 或尽早加载样式表）
- `lazy-loading` - 通过动态导入或路由级分包懒加载非首屏组件
- `bundle-splitting` - 按路由/功能进行代码分包（如 React Suspense / Next.js dynamic），以减少首次加载时间和可交互时间 (TTI)
- `third-party-scripts` - 异步 (async/defer) 加载第三方脚本；审计并移除不必要的脚本（参考 MD）
- `reduce-reflows` - 避免频繁的布局读取与写入；合并 DOM 读取和写入操作
- `content-jumping` - 为异步加载的内容保留空间，以避免页面布局跳动（核心网页指标：CLS）
- `lazy-load-below-fold` - 对折行（首屏）以下图片和重度媒体资源使用 `loading="lazy"`
- `virtualize-lists` - 对包含 50 个以上条目的列表进行虚拟化处理，以提高内存效率和滚动性能
- `main-thread-budget` - 确保每帧的计算工作控制在 ~16ms 以内，以维持 60fps；将重度任务移出主线程（参考 HIG, MD）
- `progressive-loading` - 对于超过 1s 的操作，使用骨架屏/微光效果 (skeleton screens / shimmer) 代替长时间阻塞的加载圈 (spinner)（参考 Apple HIG）
- `input-latency` - 确保触控/滚动的输入延迟控制在 ~100ms 以内（参考 Material 响应性标准）
- `tap-feedback-speed` - 在触控后 100ms 内提供视觉反馈（参考 Apple HIG）
- `debounce-throttle` - 对高频事件（如滚动、调整窗口大小、输入）使用防抖/节流
- `offline-support` - 提供离线状态消息和基础回退方案 (PWA / mobile)
- `network-fallback` - 为慢速网络提供降级模式（低分辨率图片、减少动画）

### 4. Style Selection (HIGH)

- `style-match` - 确保界面风格与产品类型相匹配（使用 `--design-system` 获取推荐建议）
- `consistency` - 在所有页面中使用统一的界面风格
- `no-emoji-icons` - 使用 SVG 图标（如 Heroicons, Lucide），不要使用 Emoji 表情作为图标
- `color-palette-from-product` - 根据产品/行业选择配色方案（使用 `--domain color` 进行查询）
- `effects-match-style` - 阴影、模糊、圆角等效果必须与所选的风格对齐（如玻璃拟态 glass / 扁平化 flat / 粘土拟态 clay 等）
- `platform-adaptive` - 尊重平台设计惯例（iOS HIG 对比 Material Design）：包括导航、控件、排版、动效等
- `state-clarity` - 确保悬停 (hover)、按压 (pressed) 和禁用 (disabled) 状态在保持风格统一的同时，在视觉上清晰可辨（参考 Material 状态层）
- `elevation-consistent` - 在卡片、面板和模态框中使用一致的层级/阴影规范；避免使用随机的阴影数值
- `dark-mode-pairing` - 同时设计亮色和暗色版本，以保持品牌感、对比度和风格的一致性
- `icon-style-consistent` - 在整个产品中使用统一的图标集和视觉语言（如线条粗细、圆角大小）
- `system-controls` - 优先使用原生/系统控件而非完全自定义的控件；仅在品牌调性有明确要求时进行自定义（参考 Apple HIG）
- `blur-purpose` - 使用模糊效果来暗示背景的弱化/关闭（如模态框、底面板），而不是仅作为装饰（参考 Apple HIG）
- `primary-action` - 每个屏幕应有且仅有一个主要 CTA（行动召唤按钮）；次要操作应在视觉上处于从属地位（参考 Apple HIG）

### 5. Layout & Responsive (HIGH)

- `viewport-meta` - 确保设置 `width=device-width initial-scale=1`（切勿禁用用户缩放）
- `mobile-first` - 采用移动优先设计，然后逐步向上适配平板和桌面端
- `breakpoint-consistency` - 使用系统化的断点（例如 375 / 768 / 1024 / 1440）
- `readable-font-size` - 移动端正文字体最小为 16px（以避免 iOS 自动缩放）
- `line-length-control` - 移动端每行限制在 35–60 个字符；桌面端限制在 60–75 个字符
- `horizontal-scroll` - 移动端禁止出现水平滚动；确保内容完全自适应视口宽度
- `spacing-scale` - 采用 4pt/8dp 增量间距系统（参考 Material Design）
- `touch-density` - 保持适合触控的组件间距：不要过于拥挤，防止发生误触
- `container-width` - 桌面端保持一致的最大容器宽度（如 `max-w-6xl` / `7xl`）
- `z-index-management` - 定义分层的 z-index 规范（例如 0 / 10 / 20 / 40 / 100 / 1000）
- `fixed-element-offset` - 固定定位的导航栏/底栏必须为底层内容保留足够的安全边距
- `scroll-behavior` - 避免使用干扰主滚动体验的嵌套滚动区域
- `viewport-units` - 在移动端优先使用 `min-h-dvh` 代替 `100vh`
- `orientation-support` - 确保横屏模式下布局依然清晰易读且可操作
- `content-priority` - 在移动端优先展示核心内容；折叠或隐藏次要内容
- `visual-hierarchy` - 通过大小、间距、对比度来建立清晰的视觉层级，不要仅依靠颜色

### 6. Typography & Color (MEDIUM)

- `line-height` - 正文文字使用 1.5 - 1.75 的行高
- `line-length` - 限制每行文字长度为 65 - 75 个字符
- `font-pairing` - 确保标题与正文字体的性格特征相匹配
- `font-scale` - 使用一致的字号阶梯（例如 12 14 16 18 24 32）
- `contrast-readability` - 在亮色背景上使用深色文字（例如在白色背景上使用 `slate-900`）
- `text-styles-system` - 使用平台字体系统：iOS 11 的 Dynamic Type 样式 / Material 5 的字体角色（display, headline, title, body, label）（参考 HIG, MD）
- `weight-hierarchy` - 使用字重强化视觉层级：粗体标题（600–700）、常规体正文（400）、中等字重标签（500）（参考 MD）
- `color-semantic` - 定义语义化颜色 Token（primary, secondary, error, surface, on-surface），不要在组件中直接硬编码十六进制颜色值（参考 Material 颜色系统）
- `color-dark-mode` - 暗色模式应使用低饱和度或更亮的色调变体，而不是简单地反转颜色；且需单独测试对比度（参考 HIG, MD）
- `color-accessible-pairs` - 前景/背景色对必须满足 4.5:1 (AA) 或 7:1 (AAA) 的对比度要求；使用工具进行验证（参考 WCAG, MD）
- `color-not-only-decorative` - 具有功能性含义的颜色（如代表错误的红色、代表成功的绿色）必须同时附带图标或文字；避免仅通过颜色表达含义（参考 HIG, MD）
- `truncation-strategy` - 换行优先于截断；需要截断时使用省略号，并通过工具提示（tooltip）或展开操作提供完整文本（参考 Apple HIG）
- `letter-spacing` - 尊重平台的默认字距；避免在正文中使用过于紧密的字距（参考 HIG, MD）
- `number-tabular` - 对数据列、价格和计时器使用等宽/表格数字（tabular figures），以防止因数字变动导致布局抖动
- `whitespace-balance` - 有意识地利用留白来对相关元素进行归组和划分区域；避免界面视觉杂乱（参考 Apple HIG）

### 7. Animation (MEDIUM)

- `duration-timing` - 微交互控制在 150–300ms 以内；复杂的过渡动画 ≤400ms；避免使用超过 500ms 的动画（参考 MD）
- `transform-performance` - 仅对 `transform` 和 `opacity` 进行动画处理；避免对 `width` / `height` / `top` / `left` 等引发回流的属性使用动画
- `loading-states` - 当加载时间超过 300ms 时，应展示骨架屏或进度指示器
- `excessive-motion` - 每个视图中最多对 1-2 个关键元素应用动画，避免过多动效
- `easing` - 进入动效使用 ease-out，退出动效使用 ease-in；避免在 UI 过渡中使用 linear（线性）渐变
- `motion-meaning` - 每一个动画都必须表达因果关系，而不仅是作为纯粹的装饰（参考 Apple HIG）
- `state-transition` - 状态变化（如悬停 / 激活 / 展开 / 折叠 / 模态）应平滑过渡，避免瞬间跳变
- `continuity` - 页面/屏幕过渡应保持空间连续性（如共享元素、方向性滑动）（参考 Apple HIG）
- `parallax-subtle` - 谨慎使用视差效果；必须尊重减弱动态效果设置，且不能引起眩晕感（参考 Apple HIG）
- `spring-physics` - 优先使用基于弹簧/物理特性的曲线，而非线性或贝塞尔曲线，以获得更自然的触感（参考 Apple HIG 流体动画）
- `exit-faster-than-enter` - 退出动画应比进入动画更快（约为进入时长的 60%–70%），以使界面感觉更灵敏（参考 MD 动效规范）
- `stagger-sequence` - 将列表/网格项的入场动画错开 30–50ms；避免一次性展示或过慢的依次呈现（参考 MD）
- `shared-element-transition` - 使用共享元素 / 英雄过渡动画以保持屏幕之间的视觉连续性（参考 MD, HIG）
- `interruptible` - 动画必须是可打断的；用户点击或手势应能立即取消进行中的动画（参考 Apple HIG）
- `no-blocking-animation` - 决不能在动画执行期间阻塞用户输入；UI 必须保持可交互状态（参考 Apple HIG）
- `fade-crossfade` - 在同一个容器内替换内容时，使用交叉淡入淡出 (crossfade) 效果（参考 MD）
- `scale-feedback` - 用户按压可点击的卡片/按钮时，提供细微的缩放（0.95–1.05）反馈；释放时恢复（参考 HIG, MD）
- `gesture-feedback` - 拖拽、滑动和捏合必须提供实时跟随手指的视觉响应（参考 MD 动效规范）
- `hierarchy-motion` - 使用位移/缩放方向来表达层级关系：从下方进入 = 更深层级，向上方退出 = 返回（参考 MD）
- `motion-consistency` - 在全局统一动画时长 and 缓动 Token；所有动画应共享相同的节奏和质感
- `opacity-threshold` - 渐隐元素的透明度低于 0.2 时不应拖沓；应迅速完全隐去或保持可见
- `modal-motion` - 模态框/底面板应从其触发源开始动画（缩放+渐变或滑入），以提供空间上下文（参考 HIG, MD）
- `navigation-direction` - 前进导航向左/向上移动；后退导航向右/向下移动 —— 保持方向逻辑一致（参考 HIG）
- `layout-shift-avoid` - 动画绝对不能触发布局回流或导致 CLS；使用 transform 改变位置

### 8. Forms & Feedback (MEDIUM)

- `input-labels` - 每个输入框都必须有可见的 label 标签（不推荐仅使用占位符 placeholder）
- `error-placement` - 在关联字段的下方显示错误提示信息
- `submit-feedback` - 提交时展示加载中状态，随后展示成功或错误状态
- `required-indicators` - 标明必填字段（例如使用星号 *）
- `empty-states` - 无内容时提供有用的提示信息和操作引导
- `toast-dismiss` - Toast 提示应在 3-5 秒内自动消失
- `confirmation-dialogs` - 在执行破坏性操作前进行二次确认
- `input-helper-text` - 在复杂的输入框下方提供持久的辅助/帮助文本，而不仅仅依赖占位符（参考 Material Design）
- `disabled-states` - 禁用状态的元素应使用降低的透明度 (0.38–0.5) + 光标改变 + 语义化属性（参考 MD）
- `progressive-disclosure` - 渐进式展示复杂选项；不要在最开始展示过多信息让用户感到负担（参考 Apple HIG）
- `inline-validation` - 在失去焦点 (blur) 时进行校验（而非每次按键敲击）；且只在用户完成输入后才显示错误（参考 MD）
- `input-type-keyboard` - 使用语义化的输入类型（如 email, tel, number）来触发正确的移动端键盘布局（参考 HIG, MD）
- `password-toggle` - 为密码字段提供显示/隐藏的切换按钮（参考 MD）
- `autofill-support` - 使用 autocomplete / textContentType 属性，以便系统能够自动填充信息（参考 HIG, MD）
- `undo-support` - 允许撤销破坏性或批量操作（例如提供带有“撤销删除”的 Toast 提示）（参考 Apple HIG）
- `success-feedback` - 操作完成时使用简短的视觉反馈进行确认（打勾图标、Toast 提示、颜色闪烁）（参考 MD）
- `error-recovery` - 错误消息必须包含一条清晰的恢复路径（如重试、编辑、帮助链接）（参考 HIG, MD）
- `multi-step-progress` - 多步骤流程中应展示步骤指示器或进度条；并允许返回上一步（参考 MD）
- `form-autosave` - 长表单应自动保存草稿，防止因意外关闭导致数据丢失（参考 Apple HIG）
- `sheet-dismiss-confirm` - 在关闭有未保存更改的底面板/模态框前提示用户确认（参考 Apple HIG）
- `error-clarity` - 错误消息必须说明原因以及如何修复（而不仅仅是“输入无效”）（参考 HIG, MD）
- `field-grouping` - 合理地对相关字段进行分组（使用 fieldset/legend 或视觉上的归组）（参考 MD）
- `read-only-distinction` - 只读状态应在视觉和语义上与禁用状态有所区分（参考 MD）
- `focus-management` - 提交出错后，自动将焦点定位到第一个无效的输入字段（参考 WCAG, MD）
- `error-summary` - 对于多个错误，在表单顶部展示错误汇总，并提供指向各个出错字段的锚点链接（参考 WCAG）
- `touch-friendly-input` - 移动端输入框高度应 ≥44px，以满足触控尺寸要求（参考 Apple HIG）
- `destructive-emphasis` - 破坏性操作使用语义化的危险颜色（红色），且在视觉上与主要操作分隔开（参考 HIG, MD）
- `toast-accessibility` - Toast 提示不能夺取焦点；使用 `aria-live="polite"` 以供屏幕阅读器播报（参考 WCAG）
- `aria-live-errors` - 表单错误提示使用 `aria-live` 区域或 `role="alert"` 以通知屏幕阅读器（参考 WCAG）
- `contrast-feedback` - 错误与成功状态的颜色必须满足 4.5:1 的对比度要求（参考 WCAG, MD）
- `timeout-feedback` - 请求超时必须展示清晰的反馈，并提供重试选项（参考 MD）

### 9. Navigation Patterns (HIGH)

- `bottom-nav-limit` - 底部导航栏最多 5 个项目；同时使用文字标签与图标（参考 Material Design）
- `drawer-usage` - 使用抽屉/侧边栏进行次要导航，而不是放置主要操作（参考 Material Design）
- `back-behavior` - 返回导航必须可预测且保持一致；保留页面滚动位置/状态（参考 Apple HIG，MD）
- `deep-linking` - 所有关键屏幕都必须支持深层链接 / URL，以便于分享和发送通知（参考 Apple HIG，MD）
- `tab-bar-ios` - iOS：在顶层导航中使用底部的 Tab Bar（参考 Apple HIG）
- `top-app-bar-android` - Android：使用带有导航图标的顶部应用栏 (Top App Bar) 作为主要结构（参考 Material Design）
- `nav-label-icon` - 导航项必须同时包含图标和文字标签；仅有图标的导航不利于用户发现（参考 MD）
- `nav-state-active` - 在导航中对当前位置进行视觉高亮（使用颜色、字重或指示条）（参考 HIG, MD）
- `nav-hierarchy` - 主导航（标签页/底栏）与次级导航（抽屉/设置）必须清晰区分（参考 MD）
- `modal-escape` - 模态框和底面板必须提供清晰的关闭/取消按钮；在移动端支持下滑关闭（参考 Apple HIG）
- `search-accessible` - 搜索入口必须易于触及（置于顶栏或标签页中）；提供最近搜索和推荐词（参考 MD）
- `breadcrumb-web` - Web：对层级深度在 3 级以上的结构使用面包屑导航以帮助用户定位（参考 MD）
- `state-preservation` - 返回导航必须恢复先前的滚动位置、过滤状态和输入内容（参考 HIG, MD）
- `gesture-nav-support` - 支持系统级手势导航（iOS 侧滑返回、Android 预测性回退），避免手势冲突（参考 HIG, MD）
- `tab-badge` - 谨慎使用导航项上的徽标 (Badge) 来展示未读/待办；在用户访问后清除（参考 HIG, MD）
- `overflow-menu` - 当操作超出可用空间时，使用溢出/更多菜单，而不是强行挤入（参考 MD）
- `bottom-nav-top-level` - 底部导航仅用于顶层屏幕；决不能在其中嵌套子导航（参考 MD）
- `adaptive-navigation` - 大屏幕（≥1024px）优先选用侧边栏；小屏幕使用底部/顶部导航（参考 Material 响应式规范）
- `back-stack-integrity` - 决不能在后台默默重置导航栈或意外跳转到首页（参考 HIG, MD）
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
- `large-dataset` - 对于 1000+ 的数据点，应进行聚合或抽样；提供下钻（drill-down）操作来查看详情，而不是一次性渲染所有数据（参考 MD）
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

## How to Use

Search specific domains using the CLI tool below.

---