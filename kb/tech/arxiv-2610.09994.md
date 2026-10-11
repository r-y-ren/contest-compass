---
id: arxiv-2610.09994
name: "Temporal Predictive Multiplicity: Equally Accurate Time Series Models Yield Different Forecast Trajectories（等精度模型的轨迹级预测多重性）"
field: [时序预测, 预测多重性, 模型评估]
directions: [数模与时序预测]
published: "2026-10-07"
maturity: paper
venue_tier: arXiv
signal:
  venue: arXiv
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "为答卷的'模型稳健性/敏感性分析'章节提供定量新论据：精度不可区分的多个模型会给出**整条未来轨迹层面**的重大分歧，且轨迹级分歧与逐时刻分歧基本不相关——做检验时除逐点误差表外，应加'多模型轨迹散差图'；这也是答辩时为集成/多模型报告辩护的一手文献（低成本可复现：训练多个等精度模型画轨迹扇形图即可）"
    reuse_cost: "低"
    open_source: "摘要页 2026-10-11 实抓无代码链接；但其度量框架可按论文定义在自训模型上直接复算"
  - track: "数模-数据分析与决策"
    edge: "决策类赛题里'预测驱动决策'的隐患被本文形式化：选哪个等精度模型会改变决策结论（downstream effects）；可把'预测多重性检查'写进决策流程作为模型选型前置步骤，形成方法论差异化"
    reuse_cost: "低"
sources:
  - url: https://arxiv.org/abs/2610.09994
    title: "Temporal Predictive Multiplicity: Equally Accurate Time Series Models Yield Different Forecast Trajectories (arXiv:2610.09994, 摘要页实抓)"
    accessed: "2026-10-11"
---

# Temporal Predictive Multiplicity：等精度模型的整条轨迹可以完全不同

## 是什么

Imperial College London / Siemens 团队（Emanuele Albini、Francesca Toni、Saumitra Mishra、Francesco Leofante，2026-10-07 提交 arXiv:2610.09994，cs.LG，v1，无 venue 标注）提出 **temporal predictive multiplicity（时序预测多重性）**框架：刻画"预测性能近乎相同的模型集合"在**完整预测轨迹**层面的分歧——而非既有预测多重性（Rashomon 效应）研究关注的单点标量输出。实证规模：19 种神经预测架构 × 11 个数据集。

## 解决什么问题

时序预测的多个 horizon 输出共同定义一条轨迹，逐 horizon 比较会掩盖预测行为的差异。已有 multiplicity 研究停在标量输出层，无法回答"两个 MASE 相同的模型会不会给出走向相反的未来"。

## 相比前方法优势（论文实证结论）

- **仅约束预测性能，仍会容纳差异巨大的轨迹族**——精度约束不足以唯一化预测；
- **在单个 horizon 上约束 multiplicity 只能部分压缩、无法消除轨迹级 multiplicity**；
- **轨迹级分歧与逐 horizon 分歧基本不相关**（largely unrelated）——逐点一致性检查发现不了轨迹层面的分歧；
- 由此指出现有多重性研究的空白：性能不可区分 ⇒ 时间轨迹上根本不同，并带下游后果。

## 局限（如实标注）

- 无代码（摘要页 2026-10-11 实抓无链接），复用需按论文定义自实现度量；
- 摘要未给出具体量化幅度（分歧多大、在哪些数据集最严重需读正文核数）；
- 框架性质论文，不提供"降低 multiplicity"的方法解，只提供诊断。

## 如何用于比赛

1. **稳健性章节的定量升级（数模-预测与评估）**：答卷常见"多模型对比表"，可升级为"等精度模型轨迹散带图"——训练 N 个结构不同但精度打平的模型，画轨迹扇形图并报告轨迹级分歧指标；该实验成本极低（复用已训模型）却直接回应"模型选择是否可靠"的评委质疑。
2. **集成与多方案报告的辩护**：若多模型轨迹分歧大，单模型点预测的置信度应下调，给出区间或情景预测——为"为什么交区间预测/多情景"提供文献级理由。
3. **技术脉络定位**：库内首张"模型选型风险"卡——与评测线（tsfm-bench 2609.10357 领域熟悉度、LiveHouse-TS 2608.17299、SimpleTimeBench 2610.02058）互补：那些卡讲"怎么公平测精度"，本卡讲"精度打平之后还剩什么分歧"。
