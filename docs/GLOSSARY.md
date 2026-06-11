# UI/UX Pro Max 本地化核心术语对照表 (Glossary)

为了在后续的文档翻译、数据库更新、以及 AI 技能开发中保持术语的一致性，避免“机翻腔”和“死译”对代码逻辑或可读性造成的破坏，特制定本技术术语表。

---

## 1. 核心框架与技术栈名称 (Frameworks & Libraries)
此类专有名词在任何情况下**禁止翻译**，必须保留原始大小写。

| 英文原名 | 规范写法 | 错误译例 (警示) | 底层机制说明与排版规范 |
| :--- | :--- | :--- | :--- |
| Tailwind CSS | `Tailwind CSS` 或 `Tailwind` | 顺风、尾风 | CSS 框架，中英文混排需加空格。 |
| Chakra UI | `Chakra UI` | 查克拉 UI | React 组件库。 |
| Framer Motion | `Framer Motion` | 帧运动、构架运动 | React 动画库。 |
| Locomotive Scroll | `Locomotive Scroll` | 机车卷轴、火车滚动 | 平滑滚动库。 |
| Three.js | `three.js` | 三.js、3.js | WebGL 3D 库。注意在代码与脚本中，其引入和对象通常为 `three.js` 或 `THREE`，绝不可汉化。 |
| Next.js | `Next.js` | 下一个.js | React 服务端渲染框架。 |
| Nuxt UI | `Nuxt UI` | 纳克斯特 UI | Vue 3 的 UI 组件库。 |

---

## 2. 软件工程与前端底层概念 (Under the Hood Concepts)

| 英文原名 | 推荐中文译名 | 错误译例 (警示) | 核心概念说明与上下文建议 |
| :--- | :--- | :--- | :--- |
| Opinionated | `带有强烈设计预设的`、`主导性强的` | 固执己见的、自以为是的 | 形容框架对目录结构、工具链有强烈的预设定规范（如 Next.js）。在不需要极简的场景下，可意译为“开箱即用规范完备”。 |
| Under the hood | `底层实现`、`底层机制` | 在引擎盖下 | 意指某项技术在底层是如何运作的。 |
| Vanilla | `原生的`、`纯 (JS/CSS)` | 香草 | 指不带任何框架和封装的纯净状态（如 Vanilla JS 表示原生 JavaScript）。 |
| Hydration | `水合过程 (Hydration)` | 水合作用、脱水 | SSR/SSG 中，客户端 JavaScript 接管静态 HTML 并使其具备交互能力的激活过程。 |
| Prop drilling | `属性深层传递 (Prop Drilling)` | 支柱钻探、道具钻孔 | 指 React 等框架中，将 props 跨越数层无关组件向下传递的现象。 |
| Reducer | `Reducer` | 减速器、减速机 | React/Redux 中的状态转换函数。技术交流中保留原词，不进行字面汉化。 |
| Profile / Profiler | `性能分析 (Profile)` / `性能分析器` | 配置文件、个人资料 | 指对代码运行时间、CPU/内存占用进行跑分和分析的动作。 |
| Boilerplate | `样板代码`、`脚手架` | 锅炉板、样板文件 | 用于快速初始化项目的模板代码。 |

---

## 3. UI/UX 交互与排版术语 (UI/UX & Interactions)

| 英文原名 | 推荐中文译名 | 错误译例 (警示) | 底层机制说明与排版规范 |
| :--- | :--- | :--- | :--- |
| Active state | `激活状态`、`点击态` | 活跃状态 | 指按钮、链接在鼠标按下（`:active`）但尚未释放时的视觉反馈状态。 |
| Focus ring | `焦点环` | 聚焦环、焦点戒指 | 当元素获得焦点时，浏览器默认或自定义渲染的边框外围高亮圈，用于键盘无障碍导航。 |
| Blur | `失去焦点`、`失焦` | 模糊 | 元素失焦事件（如 input 的 `onBlur`）。注意区分“滤镜模糊 (filter: blur)”。 |
| Toast | `Toast 轻提示`、`气泡提示` | 烤面包、吐司 | 一种在屏幕边缘短暂弹出、不打断用户操作的弱提示组件。 |
| Hero area / section | `首屏主视觉 (Hero Area)` | 英雄区、英雄板块 | 网页打开时，首屏最核心、最大、最抓眼球的头图和主文案区域。 |
| Skeleton screen | `骨架屏` | 骨架屏幕 | 页面加载未完成时，用来占位的灰色模块预览图。 |
| Infinite scroll | `无限滚动` | 无穷滚动 | 滚动到底部自动加载下一页的交互设计。 |
| Layout shift | `布局偏移` | 布局转移、布局变化 | 页面加载过程中由于资源异步渲染导致的 DOM 元素位置突变（CLS 性能指标相关）。 |

---

## 4. 排版与排版规范约束
* **中英文半角空格**：所有翻译文本中，中文字符与英文字符、数字、行内代码块（如 \`three.js\`、\`--design-system\`）之间**必须且仅能保留一个半角空格**。
  * *正确示例*：在使用 Tailwind CSS 构建响应式布局时...
  * *错误示例*：在使用Tailwind CSS构建响应式布局时... / 在使用 Tailwind CSS 构建响应式布局时... (多空格)
* **保留代码与参数占位符**：所有的命令行参数（如 `--mode`）、API 属性名（如 `children`）、配置键名及自定义占位符（如 `[Page Name]`）在翻译时必须**严格保持原样**，否则将直接导致底层检索与自动化脚本崩溃。
