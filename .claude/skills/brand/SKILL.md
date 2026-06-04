---
name: ckm:brand
description: 品牌语气/声量、视觉识别、信息传递框架、资产管理、品牌一致性。在需要品牌化内容、语气语调、营销资产、品牌合规、样式指南时激活。
argument-hint: "[update|review|create] [args]"
metadata:
  author: claudekit
  version: "1.0.0"
---

# 品牌 (Brand)

品牌身份、语气、信息传递、资产管理及一致性框架。

## 使用时机

- 品牌语气 (Voice) 定义与内容调性指导
- 视觉识别 (Visual identity) 标准与样式指南制定
- 信息传递框架 (Messaging framework) 的创建
- 品牌一致性审查与审计
- 资产组织、命名与审批
- 配色方案管理与排版规范

## 快速开始

**向提示词注入品牌上下文：**
```bash
node scripts/inject-brand-context.cjs
node scripts/inject-brand-context.cjs --json
```

**验证资产：**
```bash
node scripts/validate-asset.cjs <asset-path> # 指向要验证的资产路径
```

**提取/对比颜色：**
```bash
node scripts/extract-colors.cjs --palette
node scripts/extract-colors.cjs <image-path> # 指向要提取颜色的图片路径
```

## 品牌同步工作流 (Brand Sync Workflow)

```bash
# 1. 编辑 docs/brand-guidelines.md (或使用 /brand update)
# 2. 同步到设计标记 (design tokens)
node scripts/sync-brand-to-tokens.cjs
# 3. 验证同步结果
node scripts/inject-brand-context.cjs --json | head -20
```

**同步的文件：**
- `docs/brand-guidelines.md` → 单一事实来源 (Source of truth)
- `assets/design-tokens.json` → 标记 (Token) 定义
- `assets/design-tokens.css` → CSS 变量

## 子命令 (Subcommands)

| 子命令 | 描述 | 参考文档 |
|------------|-------------|-----------|
| `update` | 更新品牌身份并同步到所有设计系统 | `references/update.md` |

## 参考文档 (References)

| 主题 | 文件 |
|-------|------|
| 语气框架 (Voice Framework) | `references/voice-framework.md` |
| 视觉识别 (Visual Identity) | `references/visual-identity.md` |
| 信息传递 (Messaging) | `references/messaging-framework.md` |
| 一致性 (Consistency) | `references/consistency-checklist.md` |
| 指南模板 (Guidelines Template) | `references/brand-guideline-template.md` |
| 资产组织 (Asset Organization) | `references/asset-organization.md` |
| 色彩管理 (Color Management) | `references/color-palette-management.md` |
| 排版设计 (Typography) | `references/typography-specifications.md` |
| Logo 使用规范 (Logo Usage) | `references/logo-usage-rules.md` |
| 审批清单 (Approval Checklist) | `references/approval-checklist.md` |

## 脚本 (Scripts)

| 脚本 | 用途 |
|--------|---------|
| `scripts/inject-brand-context.cjs` | 提取品牌上下文以便进行提示词注入 |
| `scripts/sync-brand-to-tokens.cjs` | 将 brand-guidelines.md 同步到 design-tokens.json/css |
| `scripts/validate-asset.cjs` | 验证资产的命名、大小和格式 |
| `scripts/extract-colors.cjs` | 提取颜色并与调色板进行对比 |

## 模板 (Templates)

| 模板 | 用途 |
|----------|---------|
| `templates/brand-guidelines-starter.md` | 新品牌完整的起步模板 |

## 路由 (Routing)

1. 从 `$ARGUMENTS` (第一个单词) 解析子命令
2. 加载对应的 `references/{subcommand}.md`
3. 使用剩余参数执行
