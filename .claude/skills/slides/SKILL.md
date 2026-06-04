---
name: ckm:slides
description: 创建集成了 Chart.js、设计标记、响应式布局、文案写作公式及上下文幻灯片策略的战略性 HTML 演示文稿。
argument-hint: "[topic] [slide-count]"
metadata:
  author: claudekit
  version: "1.0.0"
---

# 演示幻灯片 (Slides)

具有数据可视化功能的战略性 HTML 演示文稿设计。

<args>$ARGUMENTS</args>

## 使用时机

- 营销展示与商业路演幻灯片 (Pitch decks)
- 使用 Chart.js 绘制的数据驱动型幻灯片
- 使用布局模式进行战略性幻灯片设计
- 经过文案写作优化的演示内容

## 子命令

| 子命令 | 描述 | 参考文档 |
|------------|-------------|-----------|
| `create` | 创建战略性演示幻灯片 | `references/create.md` |

## 参考文档 (知识库)

| 主题 | 文件 |
|-------|------|
| 布局模式 (Layout Patterns) | `references/layout-patterns.md` |
| HTML 模板 (HTML Template) | `references/html-template.md` |
| 文案写作公式 (Copywriting Formulas) | `references/copywriting-formulas.md` |
| 幻灯片策略 (Slide Strategies) | `references/slide-strategies.md` |

## 路由逻辑

1. 从 `$ARGUMENTS` (第一个单词) 解析子命令
2. 加载对应的 `references/{subcommand}.md`
3. 使用剩余参数执行
