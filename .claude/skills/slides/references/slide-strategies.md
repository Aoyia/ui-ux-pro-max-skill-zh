# 幻灯片策略

15 种行之有效的演示文稿结构与情感弧线。

## 策略选择

| 策略 | 幻灯片页数 | 目标 | 受众 |
|----------|--------|------|----------|
| YC 种子轮 PPT (YC Seed Deck) | 10-12 | 融种子资金 | 风险投资人 (VC) |
| 盖伊·川崎法 (Guy Kawasaki) | 10 | 20分钟内演示完成 | 投资者 |
| A 轮融资 (Series A) | 12-15 | 融 A 轮资金 | 成长型 VC |
| 产品演示 (Product Demo) | 5-8 | 展示产品价值 | 潜在客户 |
| 销售提案 (Sales Pitch) | 7-10 | 促成交易 | 意向线索 |
| 南希·杜阿尔特波形图 (Nancy Duarte Sparkline) | 视情况而定 | 改变受众视角 | 任何受众 |
| 问题-解决-收益 (Problem-Solution-Benefit) | 3-5 | 快速说服 | 时间紧迫的受众 |
| 季度业务回顾 (QBR) | 10-15 | 汇报给利益相关者 | 领导层 |
| 团队全员大会 (Team All-Hands) | 8-12 | 统一步调 | 员工 |
| 会议演讲 (Conference Talk) | 15-25 | 确立思想领导力 | 参会者 |
| 工作坊 (Workshop) | 20-40 | 教授技能 | 学习者 |
| 案例研究 (Case Study) | 8-12 | 证明价值 | 潜在客户 |
| 竞争分析 (Competitive Analysis) | 6-10 | 做战略决策 | 内部团队 |
| 董事会会议 (Board Meeting) | 15-20 | 汇报给董事会 | 董事会成员 |
| 网络研讨会 (Webinar) | 20-30 | 获取销售线索 | 注册参与者 |

## 常用结构

### YC 种子轮 PPT (10 页)
1. 标题/诱钩 (Title/Hook)
2. 问题 (Problem)
3. 解决方案 (Solution)
4. 业务牵引/数据 (Traction)
5. 市场 (Market)
6. 产品 (Product)
7. 商业模式 (Business Model)
8. 团队 (Team)
9. 财务状况 (Financials)
10. 融资诉求 (The Ask)

**情感弧线：** 好奇 → 沮丧 → 希望 → 信心 → 信任 → 迫切感

### 销售提案 (9 页)
1. 个性化诱钩
2. 他们面临的问题
3. 错失行动的代价
4. 你的解决方案
5. 证明/案例研究
6. 差异化优势
7. 定价/投资回报率 (ROI)
8. 异议处理
9. CTA + 后续步骤

**情感弧线：** 联结 → 沮丧 → 恐惧 → 希望 → 信任 → 信心 → 迫切感

### 产品演示 (6 页)
1. 诱钩/问题
2. 解决方案概述
3. 现场演示/截图
4. 核心功能
5. 收益/定价
6. 行动呼吁 (CTA)

**情感弧线：** 好奇 → 沮丧 → 希望 → 信心 → 迫切感

## 杜阿尔特波形图模式 (Duarte Sparkline Pattern)

在“现状”（当前痛点）与“未来设想”（更美好的未来）之间来回交替：

```
现状 → 未来设想 → 现状 → 未来设想 → 全新极乐状态
(痛点)   (希望)    (痛点)   (希望)     (解决方案)
```

在 1/3 和 2/3 位置打破常规的模式可以制造参与度高峰。

## 检索命令

```bash
# 按目标查找策略
python .claude/skills/design-system/scripts/search-slides.py "investor pitch" -d strategy

# 获取情感弧线
python .claude/skills/design-system/scripts/search-slides.py "series a funding" -d strategy --json
```

## 将策略与上下文匹配

| 上下文 | 推荐策略 |
|---------|---------------------|
| 融资 | YC Seed, Series A, Guy Kawasaki |
| 售卖产品 | Sales Pitch, Product Demo |
| 内部汇报 | QBR, All-Hands, Board Meeting |
| 公开演讲 | Conference Talk, Workshop |
| 证明价值 | Case Study, Competitive Analysis |
| 线索获客 | Webinar |
