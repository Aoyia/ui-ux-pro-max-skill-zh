更新品牌颜色、排版与风格 - 自动同步到所有设计系统文件。

<args>$ARGUMENTS</args>

## 概述

此指令会系统地更新：
1. `docs/brand-guidelines.md` - 易于人类阅读的品牌文档
2. `assets/design-tokens.json` - 设计 Token 的唯一真理源 (Source of truth)
3. `assets/design-tokens.css` - 生成的 CSS 变量

## 工作流

### 步骤 1：收集品牌输入

使用 `AskUserQuestion` 收集：

**主题选择：**
- 主题名称（例如 "Ocean Professional" / 海洋专业、“Electric Creative” / 活力创意、“Forest Calm” / 森林宁静）

**主色：**
- 颜色名称（例如 “Ocean Blue” / 海洋蓝、“Coral” / 珊瑚色、“Forest Green” / 森林绿）
- 十六进制代码 (Hex code)（例如 #3B82F6）

**辅助色：**
- 颜色名称（例如 “Golden Amber” / 黄金琥珀、“Electric Purple” / 活力紫）
- 十六进制代码

**强调色：**
- 颜色名称（例如 “Emerald” / 祖母绿、“Neon Mint” / 霓虹薄荷）
- 十六进制代码

**品牌氛围（用于 AI 图像生成）：**
- 氛围关键词（例如 “professional, trustworthy, premium” / 专业、值得信赖、高端，或 “bold, creative, energetic” / 大胆、创意、充满活力）

### 步骤 2：更新品牌指南

编辑 `docs/brand-guidelines.md`：

1. **快速参考表** - 更新颜色名称和十六进制代码
2. **品牌概念版块** - 更新主题名称和描述
3. **调色板版块** - 更新主色、辅助色、强调色及其各阶色调 (Shades)
4. **AI 图像生成版块** - 更新基础 Prompt 提示词、关键词以及氛围描述符

### 步骤 3：同步到设计 Token

运行同步脚本：
```bash
node .claude/skills/brand/scripts/sync-brand-to-tokens.cjs
```

这将：
- 使用新的颜色名称和值更新 `assets/design-tokens.json`
- 重新生成包含正确 CSS 变量的 `assets/design-tokens.css`

### 步骤 4：验证同步

确认所有文件均已更新：
```bash
# 检查品牌上下文提取
node .claude/skills/brand/scripts/inject-brand-context.cjs --json | head -30

# 检查 CSS 变量
grep "primary" assets/design-tokens.css | head -5
```

### 步骤 5：报告

输出摘要：
- 主题：[名称]
- 主色：[名称] ([十六进制值])
- 辅助色：[名称] ([十六进制值])
- 强调色：[名称] ([十六进制值])
- 更新的文件：brand-guidelines.md、design-tokens.json、design-tokens.css

## 修改的文件

| 文件 | 用途 |
|------|---------|
| `docs/brand-guidelines.md` | 易于人类阅读的品牌文档 |
| `assets/design-tokens.json` | Token 定义 (基础 Primitive → 语义 Semantic → 组件 Component) |
| `assets/design-tokens.css` | 供 UI 组件使用的 CSS 变量 |

## 使用的技能

- `brand` - 品牌上下文提取与同步
- `design-system` - Token 生成

## 示例

```bash
# 交互模式
/brand:update

# 带有主题提示
/brand:update "Ocean Professional"

# 快速预设
/brand:update "midnight purple"
```

## 颜色预设

如果用户指定了预设名称，请使用以下默认值：

| 预设 | 主色 | 辅助色 | 强调色 |
|--------|---------|-----------|--------|
| ocean-professional | #3B82F6 海洋蓝 (Ocean Blue) | #F59E0B 黄金琥珀 (Golden Amber) | #10B981 祖母绿 (Emerald) |
| electric-creative | #FF6B6B 珊瑚色 (Coral) | #9B5DE5 活力紫 (Electric Purple) | #00F5D4 霓虹薄荷 (Neon Mint) |
| forest-calm | #059669 森林绿 (Forest Green) | #92400E 暖棕 (Warm Brown) | #FBBF24 阳光黄 (Sunlight) |
| midnight-purple | #7C3AED 罗兰紫 (Violet) | #EC4899 粉色 (Pink) | #06B6D4 青色 (Cyan) |
| sunset-warm | #F97316 橙色 (Orange) | #DC2626 红色 (Red) | #FACC15 黄色 (Yellow) |

## 重要事项

- **务必同步全部三个文件** - 绝不要仅更新 brand-guidelines.md 自身
- **验证提取** - 更新后运行 inject-brand-context.cjs 以确认
- **测试图像生成** - 可选步骤，可生成测试图像来验证品牌风格的应用效果
