# Logo AI 提示词工程 (Logo AI Prompt Engineering)

## 核心提示词结构 (Core Prompt Structure)

```
Professional logo design for [brand/industry]:
[Visual description]
Style: [style keywords]
Colors: [color palette]
Requirements: [technical specs]

(为 [品牌/行业] 设计的专业 logo：
[视觉描述]
风格：[风格关键词]
色彩：[色彩盘]
要求：[技术规格])
```

## 按风格划分的有效关键词 (Effective Keywords by Style)

### 极简风格 (Minimalist)
```
minimalist, clean lines, simple geometric shapes, essential elements only,
high white space, flat design, single color, modern, uncluttered,
negative space, subtle, refined

(极简主义、干净的线条、简单的几何形状、仅保留核心元素、大面积留白、扁平设计、单色、现代、整洁、负空间、微妙、精致)
```

### 复古风格 (Vintage/Retro)
```
vintage, retro, heritage, established, classic, nostalgic, weathered,
distressed texture, badge style, hand-lettered, craft, artisan,
sepia tones, muted colors, aged paper effect

(复古、怀旧、传承、历史悠久、经典、沧桑感、做旧质感、徽章风格、手写体、工艺、匠人、深褐色调、柔和色彩、老旧纸张效果)
```

### 奢华/高端 (Luxury/Premium)
```
luxury, elegant, sophisticated, premium, refined, exclusive, high-end,
gold accents, metallic, minimal, tasteful, upscale, prestige,
thin lines, serif typography, foil effect

(奢华、优雅、精致、高端、精炼、专属、顶级、金色点缀、金属感、极简、有品位、高档、声望、细线条、衬线体排版、烫金效果)
```

### 现代/科技 (Modern/Tech)
```
modern, innovative, digital, tech-forward, sleek, futuristic,
gradient colors, geometric, abstract, dynamic, cutting-edge,
clean sans-serif, circuit-like, data visualization

(现代、创新、数字化、前沿科技、圆滑、未来感、渐变色、几何、抽象、动态、尖端、干净的无衬线体、电路样结构、数据可视化)
```

### 趣味/活泼 (Playful/Fun)
```
playful, fun, colorful, friendly, approachable, cheerful, whimsical,
bouncy, rounded shapes, bright colors, cartoon-like, energetic,
bubbly, hand-drawn elements

(趣味、好玩、色彩丰富、友好、亲切、愉悦、奇特、有弹性、圆润形状、明亮色彩、卡通化、充满活力、泡泡感、手绘元素)
```

### 有机/自然 (Organic/Natural)
```
organic, natural, flowing, botanical, eco-friendly, sustainable,
earth tones, leaf elements, hand-drawn, imperfect lines, growth,
green, nature-inspired, biophilic

(有机的、自然的、流动的、植物的、生态友好、可持续、大地色调、叶片元素、手绘、不完美线条、生长、绿色、自然灵感、亲生命设计)
```

## 反向提示词 (Negative Prompts - 需避免的内容)

始终在提示词中包含以下内容以防止产生不理想的效果：
```
NOT: photorealistic, 3D render with realistic textures, photograph,
stock image, clip art, multiple logos, busy background, text watermarks,
low quality, blurry, distorted, complex detailed patterns

(避免：写实照片、带有逼真纹理的 3D 渲染、照片、库存图片、剪贴画、多个 logo 拼合、杂乱背景、文字水印、低质量、模糊、变形、复杂繁琐的图案)
```

## 行业特定提示词示例 (Industry-Specific Prompts)

### 科技初创公司 (Tech Startup)
```
Modern tech company logo, abstract geometric mark, gradient blue to purple,
clean minimal design, innovative feel, scalable vector style,
professional quality, silicon valley aesthetic

(现代科技公司 logo，抽象几何图形，蓝色到紫色渐变，干净极简设计，创新感，可缩放矢量风格，专业品质，硅谷美学)
```

### 医疗健康 (Healthcare)
```
Healthcare medical logo, clean professional design, cross or heart symbol,
calming blue and teal colors, trustworthy appearance, caring feel,
simple scalable mark, HIPAA-appropriate conservative style

(医疗健康 logo，干净专业的设计，十字或心形符号，令人安心的蓝色和青色，值得信赖的外观，关怀感，简单可缩放标记，符合医疗规范的保守风格)
```

### 餐饮/食品 (Restaurant/Food)
```
Restaurant logo, warm inviting colors, appetizing feel, vintage badge style,
chef or utensil iconography, friendly welcoming design, rustic charm,
established look, readable at small sizes

(餐厅 logo，温暖诱人的色彩，食欲感，复古徽章风格，厨师或餐具图标，友好热情的提示设计，乡村魅力，底蕴感，在小尺寸下依然清晰)
```

### 时尚品牌 (Fashion Brand)
```
Fashion brand logo, elegant sophisticated wordmark, luxury aesthetic,
black and gold color scheme, thin refined typography, haute couture feel,
minimal exclusive design, high-end positioning

(时尚品牌 logo，优雅精致的文字标，奢华美学，黑金配色方案，纤细精致的字体排印，高级定制感，极简专属设计，高端定位)
```

### 环保/可持续 (Eco/Sustainable)
```
Eco-friendly sustainable brand logo, organic natural elements, leaf motif,
earth green and brown colors, growth symbolism, environmental awareness,
clean modern yet natural feel, recyclable-look design

(生态友好与可持续品牌 logo，有机自然元素，树叶图案，大地绿和棕色，生长的象征意义，环保意识，干净现代且自然的感觉，可回收外观设计)
```

## 需包含的技术性要求 (Technical Requirements to Include)

### 可缩放性 (Scalability)
```
vector-style, scalable at any size, clear silhouette,
works as favicon, recognizable small scale, simple shapes

(矢量风格、任意尺寸可缩放、清晰的轮廓、可用作网页图标 (favicon)、小尺寸下可识别、简单的形状)
```

### 通用性 (Versatility)
```
works on light and dark backgrounds, single color version possible,
horizontal and stacked layouts, brand mark can stand alone

(可在亮色和暗色背景上使用、支持单色版本、支持横版和堆叠版面、品牌图形标识可独立存在)
```

### 品质保障 (Quality)
```
professional quality, print-ready, high resolution,
crisp edges, balanced composition, centered design

(专业品质、印刷就绪、高分辨率、边缘清晰锐利、构图平衡、居中设计)
```

## 提示词模板 (Prompt Templates)

### 快速生成模板 (Quick Generation)
```
Professional [industry] logo, [style] design, [color] colors,
clean modern aesthetic, scalable vector style

(专业的 [行业] logo，[风格] 设计，[颜色] 色彩，干净现代的美学，可缩放矢量风格)
```

### 详细设计要求模板 (Detailed Brief)
```
Professional logo design for [brand name], a [industry] company.

Visual style: [style keywords]
Primary colors: [hex codes]
Mood: [emotional keywords]
Symbols: [iconography hints]

Technical: Vector-style illustration, scalable, works in single color,
centered on plain background, no text unless specified.

(为 [品牌名称]（一家 [行业] 公司）设计的专业 logo。
视觉风格：[风格关键词]
主要颜色：[十六进制颜色码]
调性：[情感关键词]
符号：[图标线索]
技术要求：矢量风格插画、可缩放、支持单色版本、在纯色背景上居中、除非特别指定否则不包含文字。)
```

### 变体请求模板 (Variation Request)
```
Alternative version of [brand] logo:
Keep: [elements to preserve]
Change: [elements to modify]
Style direction: [new style keywords]

([品牌] logo 的替代版本：
保留：[要保留的元素]
修改：[要修改的元素]
风格方向：[新的风格关键词])
```

## 常见陷阱 (Common Pitfalls)

1. **细节过于繁杂** —— AI 往往会生成复杂的图像；提示词中务必要求 “simple (简单)”。
2. **背景不清晰** —— 明确指定 “plain white background (纯白背景)”。
3. **文本渲染问题** —— AI 渲染文字通常较差；建议单独生成图形标识 (mark)。
4. **宽高比不合要求** —— 明确指定 “1:1 square (1:1 正方形)” 或 “horizontal (横向)”。
5. **过于写实的风格** —— 添加 “illustration, vector-style, not photorealistic (插画、矢量风格、非写实照片)”。
