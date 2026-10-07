---
id: arxiv-2610.07232
name: 'Benchmarking Time Series Foundation Models for Load Forecasting Under Covariate Uncertainty'
field: [time series foundation model, 负荷预测, 模型选型, 协变量鲁棒性]
directions: [数模与时序预测]
published: "2026-10-05"
maturity: paper
venue_tier: industry
signal:
  venue: "2027 IEEE PES Grid Edge Conference & Expo（arXiv comments：5 pages, 1 figure, 5 tables, Accepted，Salt Lake City, 2027-04-19/22）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "电力/能耗类赛题（短期负荷预测是电工杯等赛事常设题型）的 TSFM 选型先验，且占据库内空白的'协变量不确定性'轴：3 个真实负荷数据集上 4 个从头训练模型 vs 4 个 TSFM 的梯度实验——未来协变量可得且较准时 Chronos-2 零样本与微调均 SOTA；协变量预测变噪时 Chronos-2 退化，TimesNet 在严重协变量不确定性下更稳。直接回答赛题最现实的追问：'天气预报/温度等未来协变量本身不准时该用哪个模型'，与库内 arxiv-2608.20024（供热热负荷×TabPFN-TS 单模型实证）、arxiv-2608.18675（智能电表深度模型基准）互补不重叠"
    reuse_cost: 低
    open_source: "基准脚本与数据未随论文发布（arXiv 页未附代码）；但复现路径全开源——Chronos-2（HF amazon/chronos-2，2026-10-07 实测可达，Apache-2.0）与 TimesNet（thuml/Time-Series-Library，2026-10-07 实测可达，12,934 stars）"
sources:
  - url: https://arxiv.org/abs/2610.07232
    title: 'Benchmarking Time Series Foundation Models for Load Forecasting Under Covariate Uncertainty'
    accessed: "2026-10-07"
---

# 协变量不确定性下时序基础模型负荷预测基准

> 来源：https://arxiv.org/abs/2610.07232 （arXiv v1 提交于 2026-10-05，cs.LG/eess.SY，作者 Tomas Kaljevic、Ivan Arzola、Yu Zhang，comments：5 pages, 1 figure, 5 tables, Accepted to the 2027 IEEE PES Grid Edge Conference & Expo；抓取日期 2026-10-07）

## 是什么

arXiv 2610.07232 针对短期负荷预测（STLF）给出 TSFM 在真实运行条件下的系统基准（以下描述均来自本次抓取的摘要页）：

- **实验矩阵**：4 个从头训练（trained-from-scratch）模型 vs 4 个 TSFM，3 个真实负荷预测数据集，在**未来协变量的可得性与质量梯度**（可用/准确 → 噪声预测 → 严重不确定）下对比；
- **核心发现**：协变量可得且较准时，**Chronos-2 在零样本与微调两种设定下均持续取得 SOTA**；但其性能随协变量预报变噪而退化；**TimesNet 在严重协变量不确定性下表现出更强的鲁棒性**；
- 作者结论：鲁棒的协变量建模（robust covariate modeling）是实际部署的关键。

## 解决什么问题

TSFM 在通用预测基准上表现亮眼，但在"未来协变量本身就是预报值、不可靠"的真实负荷场景下该不该用、用哪个、退化多快，此前缺乏系统证据——这恰是负荷类赛题与实际电网运行共同的真实条件（天气预报必然有误差）。

## 相比前方法优势

- 相对库内负荷类卡片的差异化：arxiv-2608.20024 是 TabPFN-TS 在区域供热热负荷上的单模型零样本实证、arxiv-2608.18675 是智能电表上从头训练深度模型的基准——都未做"协变量质量梯度 × TSFM vs 监督模型"的对照，本文首次给出该轴上的可引用结论（Chronos-2 准时最强 / TimesNet 噪声下更稳）；
- 相对通用 TSFM 基准（GIFT-Eval 等）：固定一个高价值应用域（电力负荷），结论对赛题更可迁移；
- 有正式接收 venue（IEEE PES Grid Edge 2027），证据层级高于同期纯 arXiv 预印本。

## 局限

- 5 页短文（1 图 5 表），实验矩阵的粒度有限，"严重不确定性"的具体噪声设定需回原文核对后才能定量搬用；
- 基准脚本与数据未随论文发布，复现需自找数据集；
- 仅覆盖电力负荷域，结论向其他能耗/需求预测外推未验证；Chronos-2/TimesNet 之外的 TSFM（如 TabPFN-TS、Moirai）不在"更稳"结论内；
- 论文未附开源实现（runnable=false 为论文自身资产而言；两个被比模型的实现开源，2026-10-07 实测可达）。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**：电力/能耗/需求预测赛题的选型论证章节直接引用——协变量可信时以 Chronos-2 零样本为强基线（微调再抬一档）；协变量预报噪声大（常见于天气依赖型赛题）时以 TimesNet 类监督模型兜底，或两者并行按协变量质量切换；"鲁棒协变量建模"本身可作为论文的方法论卖点；
- **成本核算**：reuse_cost=低——Chronos-2（HF 权重公开）与 TimesNet（thuml/Time-Series-Library，12.9k stars）均开箱可跑，自备任一负荷数据集即可复现对照；论文数字只作选型佐证，赛场结论须自测（铁律 4）。
