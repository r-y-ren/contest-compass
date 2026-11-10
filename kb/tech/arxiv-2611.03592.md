---
id: arxiv-2611.03592
name: "TSFM 概率预测校准评测框架：pooled / horizon-wise / conditional 三级校准诊断 + 后验重校准何者有效——主流 TSFM 存在被标准指标掩盖的系统性误校准"
field: [time series foundation model, 概率预测, 不确定性校准]
directions: [数模与时序预测]
published: "2026-11-02"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv（上轮点名优先评估项，2026-11-10 经 arXiv API 实抓摘要；GitHub repo search 无官方实现）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "区间预测/不确定性量化是数模预测题的常见隐性要求（区间覆盖率、CRPS），本卡提供一套现成的校准检验方法学：把『预测区间可信吗』从单一 pooled 覆盖率提升到 pooled → horizon-wise → conditional 三级，逐 horizon 段定位欠覆盖/过宽，直接当论文『模型评估』小节的检验清单；两条实测结论可直接引用——主流 TSFM 存在标准指标常掩盖的系统性误校准模式，各后验重校准方法只能修复部分校准维度、另一些持续存在，支撑『零样本 TSFM 区间必须做事后重校准并报告分级校准诊断』的方法论证"
    reuse_cost: 低
  - track: "Kaggle-竞赛"
    edge: "概率时序赛（CRPS/quantile 计分）提交前的校准自检管线：分级校准诊断 + 重校准方法对比可当 pipeline 最后一环；『标准指标掩盖误校准』提醒别只盯总 CRPS——分段覆盖检查可能揪出某些 horizon 的系统性偏差，针对性修正即是免费的排名空间"
    reuse_cost: 中
sources:
  - url: https://arxiv.org/abs/2611.03592
    title: "Evaluating Uncertainty Calibration in Probabilistic Time Series Foundation Models（arXiv abs 页，2026-11-02 提交，摘要经 arXiv API 实抓 2026-11-10）"
    accessed: "2026-11-10"
---

# TSFM 校准评测：把『区间可信吗』从一句覆盖率变成三级诊断

> 来源：https://arxiv.org/abs/2611.03592 （v1 2026-11-02，摘要经 arXiv API 实抓 2026-11-10）。本卡内容出自本次实抓摘要，未读 PDF 全文；GitHub repo search（2026-11-10）未见官方实现。

## 是什么

对概率时序基础模型（TSFM）的不确定性校准做系统评测的方法学论文。三个贡献：(1) 给出 TSFM 表达预测不确定性的表示方式分类（taxonomy）；(2) 提出多 horizon 预测的细粒度校准评测框架，区分 **pooled（池化）、horizon-wise（逐 horizon）、conditional（条件化）** 三级递进的校准概念；(3) 用该框架对主流 TSFM 在多数据集上做大规模实证，并逐一分析常见后验重校准方法各自能修复哪些校准形式、哪些持续存在。

## 解决什么问题

TSFM 越来越多地被拿来直接出概率预测（分位数区间），但"区间是否可信"此前缺乏统一且细粒度的检验口径：单一的池化覆盖率指标既看不出偏差出在哪个 horizon 段，也看不出是否只对特定条件子集失效——模型可以在整体覆盖率上"看起来很准"，同时在关键 horizon 上系统性偏窄/偏宽。本文把这个盲区变成可操作的诊断流程。

## 相比前方法优势

- **三级递进口径**：pooled → horizon-wise → conditional，逐级加强，能定位"哪一段 horizon、哪类条件下失准"，而非一个平均数糊过去；
- **覆盖面实证**：跨多数据集的主流 TSFM 对比，结论是存在 distinct and systematic 的误校准模式，且标准指标常常掩盖之——给"TSFM 零样本区间不能拿来就用"提供了成体系的证据；
- **重校准方法画像**：不是泛泛说"做个重校准"，而是刻画每类后验重校准能改善哪一级校准、哪一级修不动，可直接转成操作指南。

## 局限（如实标注）

- 未读 PDF 全文：各 TSFM 的具体误校准数字、数据集清单与重校准方法的逐项对比表以摘要口径为准；
- 无官方开源实现（GitHub repo search 2026-11-10 未见），复现需按论文自行实现指标与重校准流程——指标本身实现成本不高，故 reproducibility 定为 medium；
- 论文评估对象是 TSFM，传统 per-dataset 训练模型的校准问题未覆盖。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：凡赛题要求区间预测、置信带、风险量化（覆盖率、CRPS、VaR 类指标），评估章节直接套三级校准清单：报告 pooled 覆盖率之外补逐 horizon 覆盖与条件化诊断；再用论文结论论证"对零样本基础模型区间做事后重校准"这一步的必要性——评审视角下这比只给一张点预测误差表高一个档位。
- **Kaggle-竞赛**（reuse_cost 中）：CRPS/quantile 计分的概率时序赛，把分级校准诊断做成提交前自检：发现某段 horizon 系统性欠覆盖时按论文重校准方法画像选对应修正手段；"别只看总 CRPS"本身就是对抗排行榜过拟合的免费检查。
