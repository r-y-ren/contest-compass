---
id: arxiv-2610.07232
name: "协变量不确定性下的 TSFM 负荷预测基准：Chronos-2 领先但怕协变量噪声，TimesNet 更稳（IEEE PES Grid Edge 2027 接收）"
field: [time series foundation model, 负荷预测, 基准评测]
directions: [数模与时序预测]
published: "2026-10-05"
maturity: paper
venue_tier: other
reproducibility_level: low
signal:
  venue: "arXiv（Comments 注明 IEEE PES Grid Edge 2027 接收）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "时序基础模型选型指南：数模队直接上 Chronos-2/TimesNet 已成常规操作，本文给出关键分岔——未来协变量可得且准确时 Chronos-2 零样本/微调双 SOTA，协变量预测噪声变大后性能退化而 TimesNet 更鲁棒；数模题恰常给『部分已知未来协变量 + 需自行预测的协变量』混合场景，其『4 个从头训模型 × 4 个 TSFM × 3 真实数据集 × 协变量质量梯度』的选型矩阵可直接指导建模选型并写进敏感性分析章节（结论引用需注明作者口径）"
    reuse_cost: 低
    open_source: "无代码发布（abs 页无链接，2026-10-20 实抓）；复用=按论文协议用公开模型（Chronos-2/TimesNet 均开源）在自有数据上自测"
  - track: "黑客松-数据与算法"
    edge: "电力/能源负荷预测赛题的 baseline 设计模板：『从头训 vs 基础模型零样本 vs 微调』三档对照 + 协变量质量分层的实验协议可照抄作消融章节，回答评审『为什么不用/为什么用基础模型』的必问题"
    reuse_cost: 低
    open_source: "无代码发布；实验协议可依 5 页正文复刻，模型侧 Chronos-2 与 TimesNet 均有官方开源实现"
sources:
  - url: https://arxiv.org/abs/2610.07232
    title: "Benchmarking Time Series Foundation Models for Load Forecasting Under Covariate Uncertainty（arXiv abs 页，Tomas Kaljevic/Ivan Arzola/Yu Zhang，摘要全文；Comments：5 页 1 图 5 表，IEEE PES Grid Edge Conference & Expo 2027 接收，2026-10-20 实抓）"
    accessed: "2026-10-20"
---

# TSFM 负荷预测选型基准：Chronos-2 赢在协变量好用，TimesNet 赢在协变量烂

> 来源：https://arxiv.org/abs/2610.07232 （abs 页摘要与 Comments，2026-10-20 实抓；Tomas Kaljevic、Ivan Arzola、Yu Zhang；5 页短文，IEEE PES Grid Edge Conference & Expo 2027（Salt Lake City，2027-04-19~22）接收）。abs 页无代码链接。本卡出自本次抓取的摘要页，未读全文。

## 是什么

短期负荷预测（STLF）场景下时序基础模型（TSFM）的系统性对照基准：**4 个从头训练（TFS）模型 vs 4 个 TSFM**（含 Chronos-2、TimesNet），跑 **3 个真实负荷数据集**，按"未来协变量信息的可得性与质量"分层设计运行场景——协变量完整准确、有噪声、逐步退化。结论（摘要自报）：**协变量可得或预测准确时 Chronos-2 在零样本与微调两种设定下均 SOTA**；但**协变量预测噪声加剧时其性能退化，TimesNet 在严重协变量不确定性下更鲁棒**。作者强调协变量建模的鲁棒性是真实场景落地关键。

## 解决什么问题

TSFM 榜单成绩多在"协变量理想可得"的协议下取得；真实电力运营中未来协变量（气象预报、计划检修等）本身是带噪声的预测值。该基准把"协变量质量"作为显式实验维度，回答"什么时候该信基础模型、什么时候该退回传统模型"。

## 相比前方法优势

- **实验维度贴近实战**：协变量质量梯度化，比"单一数据集刷点"的 TSFM 评测更接近落地决策；
- **TFS vs TSFM 同台**：同一协议下回答"从头训还值不值"，学生队算力有限时的直接参考；
- **结论可操作**：不是泛泛"基础模型好"，而是给出随协变量质量切换的选型规则。

## 局限（如实标注）

- **无代码无数据管线发布**（abs 页无链接，2026-10-20 实抓），复现需自行搭协议，reproducibility 低；
- 5 页会议短文，模型档位、微调预算、数据集规模等细节容量有限，负荷域结论向其他时序域外推未证；
- IEEE PES 系会议非 CCF 列表（venue_tier 记 other），影响力以电力行业圈为主；
- "Chronos-2 SOTA / TimesNet 更稳"为摘要自报口径，具体退化曲线与阈值需读正文。

## 如何用于比赛（比赛映射展开）

1. **数模-预测与评估（含未来协变量的预测题）**：选型决策树直接可用——赛题给的"未来已知量"可靠（官方统计、日程表）→ Chronos-2（零样本先跑基线，再试微调）；未来量靠自预测（天气预报、联动指标）→ 把 TimesNet 等鲁棒模型纳入对照，或对协变量做敏感性分析（人为加噪看主模型退化斜率，正是本文实验的缩编版，写进论文的稳健性章节）。reuse_cost 低：无需复现论文，用其结论定选型、借其协议设计自测。
2. **黑客松-数据与算法（能源/负荷预测赛题）**：照抄"TFS/零样本/微调三档 + 协变量分层"的实验设计作作品消融章节，答辩时引用本文口径说明"选型有文献依据"。reuse_cost 低。
