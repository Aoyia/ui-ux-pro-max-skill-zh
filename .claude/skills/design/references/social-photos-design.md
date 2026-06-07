# 社交媒体照片设计指南 (Social Photos Design Guide)

通过 HTML/CSS 渲染并导出截图来设计社交媒体图像。协调使用 `ui-ux-pro-max`、`brand`、`design-system` 和 `chrome-devtools` 技能。

## 平台尺寸标准 (Platform Sizes)

| 平台 | 类型 | 尺寸 (像素/px) | 宽高比 |
|----------|------|-----------|--------|
| Instagram | 帖子 (Post) | 1080 x 1080 | 1:1 |
| Instagram | 故事 (Story/Reel) | 1080 x 1920 | 9:16 |
| Instagram | 轮播图 (Carousel) | 1080 x 1350 | 4:5 |
| Facebook | 帖子 (Post) | 1200 x 630 | ~1.9:1 |
| Facebook | 故事 (Story) | 1080 x 1920 | 9:16 |
| Twitter/X | 帖子 (Post) | 1200 x 675 | 16:9 |
| Twitter/X | 卡片 (Card) | 800 x 418 | ~1.91:1 |
| LinkedIn | 帖子 (Post) | 1200 x 627 | ~1.91:1 |
| LinkedIn | 文章 (Article) | 1200 x 644 | ~1.86:1 |
| Pinterest | 图钉 (Pin) | 1000 x 1500 | 2:3 |
| YouTube | 缩略图 (Thumbnail) | 1280 x 720 | 16:9 |
| TikTok | 封面 (Cover) | 1080 x 1920 | 9:16 |
| Threads | 帖子 (Post) | 1080 x 1080 | 1:1 |

## 工作流 (Workflow)

### 步骤 1：激活项目管理 (Activate Project Management)

调用 `project-management` 技能，通过 Claude 的原生任务编排创建持久的待办任务清单 (TODO tasks)。细分为：
- 需求分析任务
- 创意构思任务
- HTML 设计任务 —— 可按尺寸/变体并行开展
- 截图导出任务 —— 可按文件并行开展
- 报告生成任务

为独立的子任务生成并派生并行的子智能体（例如针对不同尺寸设计多个 HTML 文件）。

### 步骤 2：分析需求 (Analyze Requirements)

从用户输入中解析以下内容：
- **主题/Topic** —— 社交照片所代表的内容
- **目标平台** —— 需要哪些尺寸（默认：Instagram 帖子 1:1 + 故事 9:16）
- **视觉风格** —— 极简、大胆、渐变网格、基于照片等
- **品牌上下文** —— 如有，读取自 `docs/brand-guidelines.md`
- **内容元素** —— 标题、副标题、行动呼吁 (CTA)、图像、图标
- **数量** —— 需要多少种变体（默认：3 个）

### 步骤 3：生成创意想法 (Generate Ideas)

创建 3-5 个概念方案：
- 符合输入提示与需求
- 考虑不同平台特定的最佳实践
- 在构图、色彩、字体排印方法上有所区分
- 与已有的品牌指南保持一致

在开始设计前，通过 `AskUserQuestion` 将创意方案呈现给用户并获取确认。

### 步骤 4：设计 HTML 文件 (Design HTML Files)

按顺序激活以下技能：

1. **`/ckm:brand`** —— 提取用户项目中的品牌色彩、字体和品牌调性
2. **`/ckm:design-system`** —— 获取设计令牌（间距、字号比例、色彩盘）
3. **随机调用以下之一**：`/ck:ui-ux-pro-max` 或 `/ck:frontend-design` —— 用于布局、层级、视觉平衡。每次运行随机选择一个以保持设计的多样性。

针对每个已批准的方案和目标尺寸，创建一个 HTML 文件：

```
output/social-photos/
├── idea-1-instagram-post-1080x1080.html
├── idea-1-instagram-story-1080x1920.html
├── idea-2-instagram-post-1080x1080.html
├── idea-2-instagram-story-1080x1920.html
└── ...
```

#### HTML 设计规范

- **视口 (Viewport)** —— 设置与目标尺寸完全一致 the 像素宽高
- **自包含 (Self-contained)** —— 内联所有 CSS 样式，通过 Google Fonts CDN 引入所需字体
- **无滚动条 (No scrolling)** —— 所有内容必须完美适配在一个视口中
- **高对比度** —— 文本在缩略图大小下依然清晰可读
- **品牌一致性** —— 使用提取出的品牌色和品牌字体
- **安全区域 (Safe zones)** —— 核心视觉和内容保持在中心 80% 的区域内
- **字体排印** —— 在 1080px 宽度下，标题字号至少 24px，正文字号至少 16px
- **视觉层级** —— 拥有单一的核心视觉焦点，逻辑阅读流向清晰

#### HTML 模板结构

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width={WIDTH}, initial-scale=1.0">
  <link href="https://fonts.googleapis.com/css2?family={FONT}&display=swap" rel="stylesheet">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html, body {
      width: {WIDTH}px;
      height: {HEIGHT}px;
      overflow: hidden;
      font-family: '{FONT}', sans-serif;
    }
    .canvas {
      width: {WIDTH}px;
      height: {HEIGHT}px;
      position: relative;
      /* 背景：渐变色、纯色，或背景图片 */
    }
    /* 来自品牌/设计系统的设计令牌 */
  </style>
</head>
<body>
  <div class="canvas">
    <!-- 内容层级 -->
  </div>
</body>
</html>
```

### 步骤 5：截图导出 (Screenshot Export)

使用 Chrome 无头模式 (headless)、`chrome-devtools` 技能或 Playwright/Puppeteer 来捕获完全符合尺寸要求的截图。

**重要提示：** 页面加载后务必添加延迟 (3-5 秒)，以让字体和外部图像在截图前完全渲染完毕。

#### 方案 A：Chrome Headless CLI (推荐 —— 零外部依赖)

```bash
CHROME="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
DELAY=5  # 等待字体/图像加载的秒数

"$CHROME" \
  --headless \
  --disable-gpu \
  --no-sandbox \
  --hide-scrollbars \
  --window-size="${WIDTH},${HEIGHT}" \
  --virtual-time-budget=$((DELAY * 1000)) \
  --screenshot="output.png" \
  "file:///path/to/file.html"
```

核心参数解释：
- `--virtual-time-budget=5000` —— 虚拟等待 5 秒以让资源（Google 字体、外部图片）加载完毕
- `--hide-scrollbars` —— 防止截图中出现滚动条
- `--window-size=WxH` —— 设置完全相等的像素尺寸

#### 方案 B：使用 chrome-devtools 技能

调用 `/chrome-devtools` 指令来：
1. 在浏览器中打开每个 HTML 文件
2. 将视口设置为目标尺寸大小
3. 等待 3-5 秒以让字体/图片加载完全
4. 对整页进行截图并导出为 PNG 格式
5. 保存至 `output/social-photos/exports/`

#### 方案 C：Playwright 脚本

```javascript
const { chromium } = require('playwright');

async function captureScreenshots(htmlFiles) {
  const browser = await chromium.launch();

  for (const file of htmlFiles) {
    const [width, height] = file.match(/(\d+)x(\d+)/).slice(1).map(Number);

    const page = await browser.newPage();
    await page.setViewportSize({ width, height });
    await page.goto(`file://${file}`, { waitUntil: 'networkidle' });
    // 等待字体/图片完全渲染
    await page.waitForTimeout(3000);

    const outputPath = file.replace('.html', '.png').replace('social-photos/', 'social-photos/exports/');
    await page.screenshot({ path: outputPath, type: 'png' });
    await page.close();
  }

  await browser.close();
}
```

#### 方案 D：Puppeteer 脚本

```javascript
const puppeteer = require('puppeteer');

async function captureScreenshots(htmlFiles) {
  const browser = await puppeteer.launch();

  for (const file of htmlFiles) {
    const [width, height] = file.match(/(\d+)x(\d+)/).slice(1).map(Number);

    const page = await browser.newPage();
    await page.setViewport({ width, height, deviceScaleFactor: 2 }); // 设置 2x 以获得视网膜屏幕高清画质
    await page.goto(`file://${file}`, { waitUntil: 'networkidle0' });
    // 等待字体/图片完全渲染
    await new Promise(r => setTimeout(r, 3000));

    const outputPath = file.replace('.html', '.png').replace('social-photos/', 'social-photos/exports/');
    await page.screenshot({ path: outputPath, type: 'png' });
    await page.close();
  }

  await browser.close();
}
```

**重要提示：** 请在 Puppeteer 中使用 `deviceScaleFactor: 2` 来获得视网膜级高清质量的图片输出。

### 步骤 6：核对与修正设计 (Verify & Fix Designs)

使用 Chrome MCP 或 `chrome-devtools` 技能对每个导出的 PNG 进行视觉审核：

1. 打开导出的截图并检查是否存在布局或样式问题
2. 验证：字体是否渲染正确、色彩是否契合品牌、文字在缩略图大小下是否依然清晰可读
3. 检查：是否存在溢出、内容缺失、安全区域是否遵守、视觉层级是否明确
4. 若发现问题 → 修改 HTML 源码 → 重新导出截图 → 再次验证
5. 重复上述步骤直至所有设计通过视觉质量检查

**需检查的常见问题：**
- 字体未能成功加载 (回退到系统字体)
- 文本溢出或被截断
- 元素超出安全区域 (中心 80% 以外)
- 文字对比度低 (低于 WCAG AA 4.5:1)
- 元素未对齐或布局错乱

### 步骤 7：生成总结报告 (Generate Summary Report)

将报告保存至 `plans/reports/` 目录下，并遵循会话 Hook 的命名规范。

报告结构：

```markdown
# 社交媒体照片设计报告

## 概述
- 提示词与需求：{原始输入内容}
- 目标平台：{目标平台}
- 变体版本：{数量}
- 设计风格：{选定的风格}

## 创意方案生成
1. **{方案名称}** —— {简要描述与设计阐述}
2. ...

## 设计决策说明
- 色盘：{使用的色彩及设计理由}
- 字体排印：{选定字体、字号及设计理由}
- 布局方案：{构图思路及理由}
- 品牌契合：{品牌指南如何影响本设计}

## 输出文件清单
| 文件 | 尺寸 | 平台 | 预览说明 |
|------|------|----------|---------|
| exports/{文件名}.png | {宽 x 高} | {平台} | {说明} |

## 为什么该设计有效
- {平台特定的设计考量原因}
- {品牌一致性层面的原因}
- {视觉层级合理性的原因}
- {互动潜力层面的原因}

## 下一步建议
- {A/B 测试建议}
- {平台特定优化技巧}
- {后续迭代方向}
```

### 步骤 8：整理输出文件 (Organize Output)

调用 `assets-organizing` 技能整理所有导出的文件与报告：
- 将导出的 PNG 移入或复制到恰当的资源文件夹下
- 确保报告保存在 `plans/reports/` 中且命名正确
- 如果用户有要求，清理中间产生的 HTML 临时文件
- 为输出的资源打上元数据标签 (平台、尺寸、概念名称)

## 设计最佳实践 (Design Best Practices)

### 平台特定小技巧

- **Instagram** —— 视觉优先、极简文字 (少于 20%)、高饱和色彩、偏向生活化氛围
- **Facebook** —— 强调信息传达，可适当包含较多文字，在信息流中需引人注目
- **Twitter/X** —— 醒目的大标题、支持暗黑/明亮模式切换的对比度、信息简明扼要
- **LinkedIn** —— 展现专业度、设计干净、数据驱动 of 视觉呈现、体现行业思想领袖调性
- **Pinterest** —— 采用垂直的长图格式、在图片上叠加文字、偏向使用实操性/教程风格
- **YouTube** —— 人像近景封面效果最好、色彩亮丽、在小尺寸下文字依旧可读
- **TikTok** —— 紧跟潮流、富有活力、大胆的字体设计、面向年轻化群体

### 艺术指导风格参考 (Art Direction Styles)

| 风格 | 最适合用于 | 核心视觉要素 |
|-------|----------|--------------|
| Minimalist (极简) | SaaS、科技、奢侈品 | 大面积留白、单一辅助色、干净利落的排版 |
| Bold Typography (大胆文字) | 公告通知、金句分享 | 巨大字号、高对比度、极少使用图形 |
| Gradient Mesh (渐变网格) | 现代品牌、APP 应用 | 流畅的色彩过渡、悬浮元素 |
| Photo-Based (图片基底) | 生活方式、电子商务 | 主视觉大图、柔和的遮罩层、在图片上放置文字 |
| Geometric (几何构图) | 科技、金融科技 | 各种几何形状、纹理背景、极具结构感的布局 |
| Glassmorphism (毛玻璃) | SaaS、现代应用 | 磨砂玻璃质感、模糊效果、半透明层级 |
| Flat Illustration (扁平插画) | 教育、健康咨询 | 定制化插画、极具亲和力和感染力 |
| Duotone (双色双调) | 创意活动、社论设计 | 对照片进行双色滤镜处理 |
| Collage (拼贴风格) | 时尚、流行文化 | 多种媒介混搭、相互重叠的元素组合 |
| 3D/Isometric (等距视角) | 科技产品、功能展示 | 立体感、阴影质感、现代透视视角 |

### 色彩与对比度

- 确保所有文字达到 WCAG AA 对比度标准 (最低 4.5:1)
- 在 50% 尺寸下测试设计以验证可读性
- 考虑平台明暗主题的兼容性
- 将品牌色作为主导色彩，辅助色作为点缀

### 字体排印层级建议

| 元素 | 最小字号 (在 1080px 宽度下) | 字宽/粗细 (Weight) |
|---------|---------------------|--------|
| Headline (标题) | 48px | Bold/Black (粗体/极粗) |
| Subheadline (副标题) | 32px | Semibold (半粗) |
| Body (正文) | 24px | Regular (常规) |
| Caption (备注说明) | 18px | Regular/Light (常规/细) |
| CTA (行动呼吁) | 28px | Bold (粗体) |

## 安全区域与范围划分

本子技能仅用于社交媒体图片的设计。不包含以下内容：
- 视频内容创作
- 动画/动态图形设计
- 印刷物料文件 (CMYK 色彩模式、出血线)
- 直接在社交媒体上发布/排程
- AI 图像生成 (如有此类需求请使用 `ai-artist` 技能)
