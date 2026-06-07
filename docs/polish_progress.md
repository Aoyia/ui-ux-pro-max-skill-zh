# UI UX Pro Max Skill 技术文档深度润色进度表

为了彻底消除翻译中的“机翻腔”与“字面死译”，将英文社区的独特术语、黑话与代名词转化为地道、符合中国开发者直觉的专业中文，特制定此润色进度追踪表。

## 润色核心原则
1. **去机翻腔**：摆脱英文语序，采用符合中文技术社区习惯的句式（如“开箱即用”、“底层实现”、“首屏主视觉 (Hero Area)”等）。
2. **中英文混排**：中文字符与英文/数字/行内代码之间必须有且仅有一个半角空格。
3. **保留专有名词与变量**：代码块、命令、参数（如 `--design-system`）、API 及占位符（如 `[Page Name]`）绝对保持原样。
4. **链接格式完整性**：保留所有 Markdown 特殊语法和 `file:///` 格式的本地跳转链接。

## 润色进度追踪

| **P0** | `README.md` | ✅ 已完成 | 核心主文档，消除“英雄区”、“亮色模式”等机翻，润色为地道中文 |
| **P0** | `CLAUDE.md` | ✅ 已完成 | Claude Code 本地技能指南，润色说明与开发规范 |
| **P0** | `src/ui-ux-pro-max/templates/base/quick-reference.md` | ✅ 已完成 | 核心模板：快速参考指南 |
| **P0** | `src/ui-ux-pro-max/templates/base/skill-content.md` | ✅ 已完成 | 核心模板：技能指令内容 |
| **P0** | `.claude/skills/ui-ux-pro-max/SKILL.md` | ✅ 已完成 | 主技能最终指令文件 |
| **P1** | 6 个子技能指令 `SKILL.md` | ✅ 已完成 | 包含 design, brand, design-system 等子技能指令 |
| **P2** | `docs/三个 data-scripts-templates 的区别.md` | ✅ 已完成 | 项目说明文档 |
| **P2** | 各设计指南 Markdown 文档 (docs/references) | ✅ 已完成 | 包含 banner, brand, styling 等模块的参考指南 |

## 更新日志
- **2026-06-08**：深度本土化润色所有技术文档、技能描述、设计指南，完成中英文混排格式优化，彻底消除了所有机翻痕迹，完成此本地化项目。
