# 图标设计参考指南

使用 Gemini 3.1 Pro Preview 进行 AI 驱动的 SVG 图标生成。提供 15 种风格， 12 个分类，以及多尺寸导出。

## 脚本 (Scripts)

| 脚本 | 用途 |
|--------|---------|
| `scripts/icon/generate.py` | 使用 Gemini 3.1 Pro Preview 生成 SVG 图标 |

## 命令 (Commands)

### 生成单个图标

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "settings gear" --style outlined
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "shopping cart" --style filled --color "#6366F1"
python3 ~/.claude/skills/design/scripts/icon/generate.py --name "dashboard" --category navigation --style duotone
```

### 批量生成变体

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "cloud upload" --batch 4 --output-dir ./icons
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "notification bell" --batch 6 --style outlined --output-dir ./icons
```

### 生成多种尺寸

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --prompt "user profile" --sizes "16,24,32,48" --output-dir ./icons
```

### 列出风格/分类

```bash
python3 ~/.claude/skills/design/scripts/icon/generate.py --list-styles
python3 ~/.claude/skills/design/scripts/icon/generate.py --list-categories
```

## CLI 选项 (CLI Options)

| 选项 | 描述 | 默认值 |
|--------|-------------|---------|
| `--prompt, -p` | 图标描述 | 必填 |
| `--name, -n` | 图标名称 (用于文件名) | - |
| `--style, -s` | 图标风格 (15 个选项) | - |
| `--category, -c` | 图标上下文分类 | - |
| `--color` | 主十六进制颜色 | currentColor |
| `--size` | 以 px 为单位的显示尺寸 | 24 |
| `--viewbox` | SVG viewBox 尺寸 | 24 |
| `--output, -o` | 输出文件路径 | auto (自动) |
| `--output-dir` | 输出目录 (批量) | ./icons |
| `--batch` | 变体生成的数量 | - |
| `--sizes` | 逗号分隔的尺寸列表 | - |

## 可选风格 (Available Styles)

| 风格 | 描边 (Stroke) | 填充 (Fill) | 最适合用于 |
|-------|--------|------|----------|
| outlined | 2px | 无 (none) | UI 界面、Web 应用 |
| filled | 0 | 纯色 (solid) | 移动端应用、导航栏 |
| duotone | 0 | 双色 (dual) | 市场推广、落地页 |
| thin | 1-1.5px | 无 (none) | 奢侈品牌、社论设计 |
| bold | 3px | 无 (none) | 标题头、主视觉区域 |
| rounded | 2px | 无 (none) | 亲和力应用、健康医疗 |
| sharp | 2px | 无 (none) | 科技、金融科技、企业级应用 |
| flat | 0 | 纯色 (solid) | 扁平设计、谷歌风格 |
| gradient | 0 | 渐变 (gradient) | 现代品牌、SaaS |
| glassmorphism | 1px | 半透明 (semi) | 现代 UI、覆盖层 |
| pixel | 0 | 纯色 (solid) | 游戏、复古设计 |
| hand-drawn | 变化 | 无 (none) | 手工艺术、创意设计 |
| isometric | 1-2px | 部分 (partial) | 技术文档、信息图表 |
| glyph | 0 | 纯色 (solid) | 系统 UI、紧凑型界面 |
| animated-ready | 2px | 变化 | 交互式 UI、引导页 |

## 图标分类 (Icon Categories)

| 分类 | 图标内容 |
|----------|-------|
| navigation | 箭头、菜单、主页、折叠箭头 |
| action | 编辑、删除、保存、下载、上传 |
| communication | 邮箱、聊天、电话、通知 |
| media | 播放、暂停、音量、相机 |
| file | 文档、文件夹、归档、云端 |
| user | 个人、群组、资料、设置 |
| commerce | 购物车、购物袋、钱包、信用卡 |
| data | 图表、曲线图、分析、仪表盘 |
| development | 代码、终端、Bug、git、API |
| social | 心形、星星、书签、奖杯 |
| weather | 太阳、月亮、云朵、雨水 |
| map | 大头针、位置、指南针、地球仪 |

## SVG 最佳实践

- **ViewBox**：使用 `0 0 24 24`（标准）或 `0 0 16 16`（紧凑）
- **颜色**：使用 `currentColor` 以便支持 CSS 继承，避免使用硬编码颜色
- **无障碍**：始终包含 `<title>` 元素
- **优化**：使用最少的路径节点，不要嵌入字体或位图图像
- **尺寸**：基于 24px 进行设计，在 16px 和 48px 下测试清晰度
- **描边**：在描边风格中使用 `stroke-linecap="round"` 和 `stroke-linejoin="round"`

## 模型 (Model)

- **gemini-3.1-pro-preview**：最强推理能力、高 Token 效率、极佳的事实一致性
- 纯文本输出（SVG 本质是 XML 文本） —— 无需图像生成 API
- 支持结构化输出，保证 SVG 格式的一致性

## 工作流 (Workflow)

1. 描述图标 → `--prompt "settings gear"`
2. Choose 风格 → `--style outlined`
3. 生成图标 → 脚本输出 .svg 文件
4. (可选) 批量生成 → `--batch 4` 生成多个变体
5. 导出多种尺寸 → `--sizes "16,24,32,48"`

## 环境配置

```bash
export GEMINI_API_KEY="your-key"
pip install google-genai
```
