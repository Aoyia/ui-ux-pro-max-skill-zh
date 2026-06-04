# 撰稿公式 (Copywriting Formulas)

25 种用于撰写说服型幻灯片文案的公式。

## 核心公式 (Core Formulas)

### PAS 公式 (问题-煽动-解决)
- **适用场景**：问题页、用户痛点页
- **公式结构**：痛点问题 (Problem) → 情感煽动 (Agitate) → 解决方案 (Solution)
- **模板文案**：“还在受 [痛点] 的困扰？每隔 [时间段]，就会面临 [负面后果]。[解决方案] 能够彻底解决这一难题。”

### AIDA 公式 (引起注意-产生兴趣-激发欲望-促成行动)
- **适用场景**：行动呼吁 (CTA) 页、结语页
- **公式结构**：引起注意 (Attention) → 产生兴趣 (Interest) → 激发欲望 (Desire) → 促成行动 (Action)
- **模板文案**：“[醒目断言]。[核心成效细节]。[社会认同/客户证言]。[行动呼吁 (CTA)]。”

### FAB 公式 (属性-优势-利益)
- **适用场景**：功能特性页、产品展示页
- **公式结构**：产品属性 (Feature) → 竞争优势 (Advantage) → 带来利益 (Benefit)
- **模板文案**：“通过 [产品属性] 可以让您 [竞争优势]，从而实现 [带来利益]。”

### 不采取行动的代价 (Cost of Inaction)
- **适用场景**：痛点煽动页、紧迫感塑造页
- **公式结构**：维持现状 (Status Quo) → 产生损失 (Loss) → 随时间恶化 (Time Decay)
- **模板文案**：“如果不使用 [解决方案]，您将在每 [时间周期] 损失 [金额]。”

### BAB 公式 (之前-之后-桥梁)
- **适用场景**：转型对比页、案例分析页
- **公式结构**：现状痛点 (Before) → 理想愿景 (After) → 达成的桥梁 (Bridge)
- **模板文案**：“[先前的痛点]。[之后的理想状态]。[我们的解决方案] 就是通往该状态的桥梁。”

## 公式与幻灯片类型对应表 (Formula-to-Slide Mapping)

| 幻灯片类型 | 首选公式 | 情感共鸣 |
|------------|-----------------|---------|
| 标题/吸睛点 (Title/Hook) | AIDA, Hook | 好奇 (curiosity) |
| 问题痛点 (Problem) | PAS, Agitate | 沮丧 (frustration) |
| 代价/风险 (Cost/Risk) | Cost of Inaction | 担忧 (fear) |
| 解决方案 (Solution) | FAB, BAB | 希望 (hope) |
| 功能特性 (Features) | FAB | 信心 (confidence) |
| 数据表现/牵引力 (Traction) | Proof Stack | 信任 (trust) |
| 社会认同 (Social Proof) | Testimonial | 信任 (trust) |
| 价格体系 (Pricing) | Value Stack | 信心 (confidence) |
| 行动呼吁 (CTA) | AIDA, Urgency | 紧迫感 (urgency) |

## 标题句式模板 (Headline Patterns)

### 强力词模式 (Power Words)
- “告别/停止 [不好的事物]” (Stop [bad thing])
- “在 [时间周期] 内获得 [渴望的结果]” (Get [desired result] in [timeframe])
- “实现 [行动] 的 [形容词] 方式” (The [adjective] way to [action])
- “为什么 [目标受众] 都在选择 [产品]” (Why [audience] choose [product])
- “实现 [特定目标] 的 [数字] 种方法” ([Number] ways to [achieve goal])

### 对比模式 (Contrast Patterns)
- “[传统方式] 已成过去。来体验 [全新方式]。” ([Old way] is dead. Meet [new way].)
- “不要 [错误行为]，而要 [正确行为]。” (Don't [bad action]. Instead, [good action].)
- “从 [痛点困扰] 跨越到 [核心利益]。” (From [pain point] to [benefit].)

### 社会认同模式 (Social Proof Patterns)
- “超过 [数字] 家 [用户/企业] 正在信赖 [产品]” ([Number]+ [users/companies] trust [product])
- “加入 [知名公司 A] 和 [知名公司 B] 的选择” (Join [notable company] and [notable company])
- “被 [知名媒体/出版物] 报道推荐” (As seen in [publication])

## 检索命令 (Search Commands)

```bash
# 查找适用于特定幻灯片类型的公式
python .claude/skills/design-system/scripts/search-slides.py "problem agitation" -d copy

# 获取契合特定情感的公式
python .claude/skills/design-system/scripts/search-slides.py "urgency cta" -d copy
```

## 快速参考 (Quick Reference)

| 撰写需求 | 选用公式 |
|------|------------|
| 制造紧迫感 | Cost of Inaction (不采取行动的代价), Scarcity (稀缺性) |
| 建立信任度 | Social Proof (社会认同), Testimonial (客户证言) |
| 彰显核心价值 | FAB 公式, Value Stack (价值堆叠) |
| 驱动转化行动 | AIDA 公式, CTA (行动呼吁) |
| 讲述品牌故事 | BAB 公式, Story Arc (故事弧线) |
| Present 数据 | Proof Stack (数据证明堆叠) |
