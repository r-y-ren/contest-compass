---
id: arxiv-2611.18199
name: "T2ST：拿'丰富时序数据+冻结 TSFM 蒸馏'喂稀缺时空观测——只用 10% 时空数据训出与全量对打的 STFM，6 长期+12 短期基准成立（匿名审稿仓可跑）"
field: [time series foundation model, spatiotemporal forecasting, data-efficient training]
directions: [数模与时序预测]
published: "2026-11-13"
maturity: paper
venue_tier: arXiv
signal:
  venue: "arXiv（摘要经 arXiv API 实抓，2026-11-25）；官方匿名审稿仓 anonymous.4open.science/r/T2ST-65F3（摘要给出，2026-11-25 记录）"
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "时空赛题的现实困境是站点少/同步观测贵（县级站点、稀疏传感器、短观测期），本卡证明'目标域时空数据可以只要 10%'：用易得的外部纯时序数据增强训练、再从冻结 TSFM 蒸馏时空依赖——小数据赛题（少量交通断面/少数气象站）训练 ST 级模型的成本被压到原来的一成量级，且跨异构架构与时间分辨率迁移，赛题自采数据的规模门槛大幅降低"
    reuse_cost: 中
    open_source: "anonymous.4open.science/r/T2ST-65F3（论文摘要给出的匿名审稿仓）"
sources:
  - url: https://arxiv.org/abs/2611.18199
    title: "T2ST: Data-Efficient Spatio-Temporal Foundation Models via Temporal Data and Knowledge Transfer（arXiv abs 页，摘要经 arXiv API 实抓）"
    accessed: "2026-11-25"
  - url: https://anonymous.4open.science/r/T2ST-65F3/
    title: "官方匿名审稿代码仓（论文摘要给出的链接，2026-11-25 记录；匿名仓无 stars/活跃度可查）"
    accessed: "2026-11-25"
---

# T2ST：时空数据不够，时序数据来凑——10% 时空观测 + 冻结 TSFM 蒸馏

> 来源：https://arxiv.org/abs/2611.18199 （2026-11-13，摘要经 arXiv API 实抓 2026-11-25）；官方匿名审稿仓 https://anonymous.4open.science/r/T2ST-65F3/ （摘要给出，2026-11-25 记录）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

**T2ST**，数据高效的时空基础模型（STFM）训练框架（Yue Xu 等）。出发点：STFM 需要大规模同步观测+空间元数据，采集与整理都贵；而**纯时序数据丰富易得**——每个位置的观测本身就是一条时序。T2ST 用**筛选过的辅助时序数据**扩充有限的时空观测，并**从冻结的时序基础模型（TSFM）向 STFM 蒸馏知识**。关键区分：时间模式的习得可以借外部纯时序，空间依赖必须靠真时空观测学。摘要口径：**只用 10% 原始时空数据**，6 个长期 + 12 个短期预测基准上与全量训练对打或更优；支持跨异构架构与时间分辨率的知识迁移。作者称此为时空基础模型数据高效训练的新范式。

## 解决什么问题

想训/微调时空模型的城市交通、环境监测、气象应用，常卡在"同步观测+空间元数据太贵"——数据稀缺直接把 STFM 路线堵死。T2ST 把"时空数据规模"从硬门槛降为软约束：时间维的知识从海量免费时序里学，空间维只需少量真观测。

## 相比前方法优势

- **问题设定新**：库内现有时空卡稀缺（本库 spatiotemporal 方向此前仅金融报表长预测一张），"用时序数据补时空数据"的数据中心化训练角度此前无人系统化；
- **蒸馏源是现成 TSFM**：不要求自研骨干，冻结 TSFM 当老师即可——与库内 Chronos-2 等基础模型卡直接衔接成流水线；
- **架构与分辨率无关**：跨异构架构/时间分辨率迁移，落地时不必绑定特定 ST 骨干；
- **10% 量级的省数据**：对数据采集成本主导的场景（新增传感器、加密站点）是数量级差异而非百分点差异。

## 局限（如实标注）

- 官方仓是**匿名审稿仓**（anonymous.4open.science），无 stars/commit 活跃度可查，录用后正式仓的维护度未知；
- "辅助时序的筛选"标准与"空间依赖必须真观测"的边界比例（10% 之外还差什么）需读全文，本卡未读 PDF；
- 结论以 6+12 个预测基准为准，极端稀疏（如仅 2-3 个站点）场景的适用性未验证；
- "competitive with or superior to full-data counterparts"中"superior"出现的条件未明，摘要口径按"对打为主"理解更稳妥。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 中）：时空小样本赛题（少量断面交通流、少数站点污染物、稀疏网格气象）直接套两步法——先拿公开时序语料/同城市其他序列把时间模式预训练出来（或直接蒸馏现成 TSFM），再用赛题少量同步观测校准空间依赖；10% 数据对打的结论支撑"我们用有限站点数据训练了 ST 级模型"的方案合法性，匿名仓可当脚手架起点。
