# 幻灯片演示策略 (Slide Strategies)

15 种经过验证的、带有情感曲线 (Emotion arcs) 的幻灯片结构。

## 策略选择 (Strategy Selection)

| 演示策略 | 幻灯片数 | 目标 | 受众 |
|----------|--------|------|----------|
| YC 种子轮 Pitch | 10-12 | 融种子轮资金 | 风险投资人 (VC) |
| 盖伊·川崎 (Guy Kawasaki) | 10 | 20 分钟内路演宣讲 | 投资者 |
| A 轮路演 | 12-15 | 融 A 轮资金 | 成长型 VC |
| 产品演示 (Demo) | 5-8 | 展示核心价值 | 潜在客户 |
| 销售路演 (Sales Pitch) | 7-10 | 达成交易 | 精准意向客户 |
| 南希·杜阿尔特 (Nancy Duarte) 折线图 | 视情况而定 | 转化思维视角 | 任何受众 |
| 问题-解决-成效 (Problem-Solution-Benefit) | 3-5 | 快速说服 | 时间紧张的人群 |
| 季度业务回顾 (QBR) | 10-15 | 向利益相关者汇报更新 | 领导层 |
| 团队全员大会 (All-Hands) | 8-12 | 统一团队目标 | 员工 |
| 大会演讲 (Conference Talk) | 15-25 | 确立思想领袖地位 | 参会者 |
| 工作坊 (Workshop) | 20-40 | 教授技能 | 学习者/学员 |
| 案例研究 (Case Study) | 8-12 | 证明价值 | 潜在客户 |
| 竞品分析 (Competitive Analysis) | 6-10 | 制定战略决策 | 内部团队 |
| 董事会会议 (Board Meeting) | 15-20 | 汇报董事会更新 | 董事会成员 |
| 网络研讨会 (Webinar) | 20-30 | 获取销售线索 | 注册用户 |

## 常见结构 (Common Structures)

### YC 种子轮路演 (10 页)
1. 标题/吸睛点 (Title/Hook)
2. 痛点问题 (Problem)
3. 解决方案 (Solution)
4. 业务数据/牵引力 (Traction)
5. 目标市场 (Market)
6. 核心产品 (Product)
7. 商业模式 (Business Model)
8. 团队介绍 (Team)
9. 财务预测 (Financials)
10. 融资需求 (The Ask)

**情感曲线：** 好奇 (curiosity) → 沮丧 (frustration) → 希望 (hope) → 信心 (confidence) → 信任 (trust) → 紧迫感 (urgency)

### 销售路演 (9 页)
1. 个性化吸睛点 (Personalized Hook)
2. 客户痛点 (Their Problem)
3. 不采取行动的代价 (Cost of Inaction)
4. 您的解决方案 (Your Solution)
5. 数据证明/案例研究 (Proof/Case Studies)
6. 差异化优势 (Differentiators)
7. 定价/投资回报率 (Pricing/ROI)
8. 疑虑解答 (Objection Handling)
9. 行动呼吁 + 下一步规划 (CTA + Next Steps)

**情感曲线：** 建立连接 (connection) → 沮丧 (frustration) → 担忧 (fear) → 希望 (hope) → 信任 (trust) → 信心 (confidence) → 紧迫感 (urgency)

### 产品演示 (6 页)
1. 吸睛点/痛点问题 (Hook/Problem)
2. 解决方案概述 (Solution Overview)
3. 实时演示/截图展示 (Live Demo/Screenshots)
4. 核心功能 (Key Features)
5. 核心成效/定价 (Benefits/Pricing)
6. 行动呼吁 (CTA)

**情感曲线：** 好奇 (curiosity) → 沮丧 (frustration) → 希望 (hope) → 信心 (confidence) → 紧迫感 (urgency)

## 杜阿尔特折线图模式 (Duarte Sparkline Pattern)

在“现状”（当前痛苦）与“愿景”（更好未来）之间来回交替：

```
现状 (What Is) → 愿景 (What Could Be) → 现状 (What Is) → 愿景 (What Could Be) → 崭新未来 (New Bliss)
（痛点）           （希望）                 （痛点）           （希望）                 （解决终局）
```

在 1/3 和 2/3 位置打破这种模式可以创造出互动的峰值。

## 检索命令 (Search Commands)

```bash
# 根据目标查找策略
python .claude/skills/design-system/scripts/search-slides.py "investor pitch" -d strategy

# 获取情感曲线
python .claude/skills/design-system/scripts/search-slides.py "series a funding" -d strategy --json
```

## 按上下文场景匹配策略 (Matching Strategy to Context)

| 上下文场景 | 推荐策略 |
|---------|---------------------|
| 融资路演 | YC Seed, Series A, Guy Kawasaki |
| 产品销售 | Sales Pitch, Product Demo |
| 内部汇报 | QBR, All-Hands, Board Meeting |
| 公开演讲 | Conference Talk, Workshop |
| 证明价值 | Case Study, Competitive Analysis |
| 线索获取 | Webinar |
