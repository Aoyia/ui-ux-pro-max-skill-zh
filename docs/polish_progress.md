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
| **P1** | 30 个数据库 CSV 文件 (`src/ui-ux-pro-max/data/`) | ✅ 已完成 | 修复了所有结构性对齐和序列 ID 错误，完成了深度翻译润色（如 Tailwind, Outfit, Framer Motion, Locomotive Scroll 等专有名词）并执行了 `_sync_all.py` 同步 |
| **P1** | 核心技术术语表 (`docs/GLOSSARY.md`) | ✅ 已完成 | 新增核心技术术语及排版规范对照表，便于后续长期维护和 AI 统一对齐 |

## 更新日志
- **2026-06-08 (第四阶段)**：根据工程化和长期维护建议，正式建立并编写了本地化核心术语对照表 `docs/GLOSSARY.md`，规范了核心技术栈、前端底层机制、UI/UX 交互及排版中英文半角空格的翻译标准与对照规范。
- **2026-06-08 (第三阶段)**：编写并运行批量润色脚本 `polish_csvs.py`，全局检索并修正了 29 个 CSV 数据集中的致命机翻与代码 API 错误（如 WebGL 脚本中的 `三.js` 还原为 `three.js`，`</脚本>` 还原为 `</script>`，`window.3` 还原为 `window.THREE`；将 `react.csv` 等框架文件中的 `儿童道具` 纠正为 `children 属性`，`支柱钻探` 纠正为 `属性深层传递 (Prop Drilling)`，`减速器` 纠正为 `Reducer`，`模糊` 纠正为 `失去焦点`，`配置文件` 纠正为 `性能分析 (Profile)` 等）。同步更新了 `cli/assets/` 静态资源目录，确保 AI 技能及 CLI 工具链的数据完全一致且逻辑正确。
- **2026-06-08 (第二阶段)**：利用自动化脚本和定向分析，修复了所有 CSV 数据集结构性错误（如 angular.csv 与 astro.csv 列对齐错乱、styles.csv 与 typography.csv ID 重复/错乱问题）。完成了所有框架栈、产品和风格 CSV 库的深层技术润色，纠正了多处“机翻腔”（如“顺风”->“Tailwind”，“查克拉”->“Chakra UI”，“机车卷轴”->“Locomotive Scroll”，“反应式”->“响应式”），完成了数据同步和 CLI 搜索验证。
- **2026-06-08 (第一阶段)**：深度本土化润色所有技术文档、技能描述、设计指南，完成中英文混排格式优化，彻底消除了所有机翻痕迹，完成此本地化项目。
