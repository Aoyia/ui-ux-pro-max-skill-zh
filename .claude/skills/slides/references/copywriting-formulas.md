# 撰稿公式

25 种用于撰写具说服力的幻灯片文案的公式。

## 核心公式

### PAS (Problem-Agitate-Solution / 问题-煽动-解决)
**适用场景：** 问题页幻灯片、痛点阐述
**构成要素：** 问题 (Problem) → 煽动 (Agitate) → 解决方案 (Solution)
**模板：** "[痛点]？每隔 [时间段]，就会 [后果]。[解决方案] 可以解决这一问题。"

### AIDA (Attention-Interest-Desire-Action / 注意-兴趣-欲望-行动)
**适用场景：** 行动呼吁 (CTA)、收尾页幻灯片
**构成要素：** 注意 (Attention) → 兴趣 (Interest) → 欲望 (Desire) → 行动 (Action)
**模板：** "[大胆的声明]。[详细收益]。[社会认同]。[行动呼吁 CTA]。"

### FAB (Features-Advantages-Benefits / 特性-优势-收益)
**适用场景：** 功能页幻灯片、产品展示
**构成要素：** 特性 (Feature) → 优势 (Advantage) → 收益 (Benefit)
**模板：** "[特性] 能让您 [优势]，从而实现 [收益]。"

### 错失行动的代价 (Cost of Inaction)
**适用场景：** 痛点煽动页幻灯片、建立迫切感
**构成要素：** 现状 (Status Quo) → 损失 (Loss) → 时间流逝 (Time Decay)
**模板：** "如果不使用 [解决方案]，您每隔 [时间段] 就会损失 [金额]。"

### 桥接对比 (Before-After-Bridge / 之前-之后-桥梁)
**适用场景：** 转型页幻灯片、案例研究
**构成要素：** 之前 (Before) → 之后 (After) → 桥梁 (Bridge)
**模板：** "[之前的痛点]。[之后的理想状态]。[我们的解决方案] 就是两者之间的桥梁。"

## 公式与幻灯片类型映射

| 幻灯片类型 | 首选公式 | 触发情感 |
|------------|-----------------|---------|
| Title/Hook (标题/诱钩) | AIDA, Hook | 好奇 |
| Problem (问题) | PAS, Agitate | 沮丧 |
| Cost/Risk (代价/风险) | Cost of Inaction | 恐惧 |
| Solution (解决方案) | FAB, BAB | 希望 |
| Features (功能) | FAB | 信心 |
| Traction (牵引力/数据) | Proof Stack | 信任 |
| Social Proof (社会认同) | Testimonial | 信任 |
| Pricing (定价) | Value Stack | 信心 |
| CTA (行动呼吁) | AIDA, Urgency | 迫切感 |

## 标题模式

### 强力词汇
- "Stop [bad thing]"（停止 [不好的事情]）
- "Get [desired result] in [timeframe]"（在 [时间段] 内获得 [理想结果]）
- "The [adjective] way to [action]"（以 [形容词] 的方式进行 [行动]）
- "Why [audience] choose [product]"（为什么 [受众] 选择 [产品]）
- "[Number] ways to [achieve goal]"（[数字] 种实现 [目标] 的方法）

### 对比模式
- "[Old way] is dead. Meet [new way]."（[旧方式] 已死。迎来 [新方式]。）
- "Don't [bad action]. Instead, [good action]."（不要 [坏行为]。相反，应该 [好行为]。）
- "From [pain point] to [benefit]."（从 [痛点] 到 [收益]。）

### 社会认同模式
- "[Number]+ [users/companies] trust [product]"（[数字]+ 用户/公司信赖 [产品]）
- "Join [notable company] and [notable company]"（加入 [知名公司] 和 [知名公司] 的行列）
- "As seen in [publication]"（见于 [出版物/媒体] 报道）

## 检索命令

```bash
# 查找特定幻灯片类型的公式
python .claude/skills/design-system/scripts/search-slides.py "problem agitation" -d copy

# 获取适合特定情感的公式
python .claude/skills/design-system/scripts/search-slides.py "urgency cta" -d copy
```

## 快速参考

| 需求 | 适用公式 |
|------|------------|
| 建立迫切感 | Cost of Inaction, Scarcity (稀缺性) |
| 建立信任 | Social Proof, Testimonial (证言) |
| 展示价值 | FAB, Value Stack (价值堆叠) |
| 驱动行动 | AIDA, CTA |
| 讲故事 | BAB, Story Arc (故事弧线) |
| 呈现数据 | Proof Stack (证据堆叠) |
