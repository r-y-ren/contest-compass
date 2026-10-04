---
id: arxiv-2610.01765
name: "Physics-Refined Spatiotemporal Forecasting on Open-Boundary Hydrologic Graphs（开边界水文图的物理修正时空预测）"
field: [spatiotemporal forecasting, 图神经网络, 物理引导机器学习, 水文预测]
directions: [数模与时序预测]
published: "2026-10-01"
maturity: paper
venue_tier: CCF-B
signal:
  venue: "ICDM 2026（arXiv comments：Accepted at the 2026 IEEE International Conference on Data Mining）"
  runnable: false
competition_fit:
  - track: 数模-预测与评估
    edge: "水文/环境类赛题\"边界条件不可观测\"痛点的组件级解法：上下游入流、潮汐等外生驱动在预测时缺失时，ghost node 代理从边界+内部节点学习外部输入近似，双物理修正器（二跳邻居局部一致性对齐 + 物理引导图神经算子抑制长程数值漂移）改善自回归 rollout 的长程稳定性——\"开边界\"框架本身可搬为论文创新点叙述，且代理外生变量的思路可迁移到任何'预测域与未观测外部交换通量'的赛题设定"
    reuse_cost: 高
    open_source: "无（arXiv 页未附代码，两个真实水文图数据集亦未给出公开链接；组件清晰可按摘要在 PyG 上自建复现）"
sources:
  - url: https://arxiv.org/abs/2610.01765
    title: "Physics-Refined Spatiotemporal Forecasting on Open-Boundary Hydrologic Graphs"
    accessed: "2026-10-04"
---

# 开边界水文图的物理修正时空预测（ICDM 2026）

> 来源：https://arxiv.org/abs/2610.01765 （arXiv v1 提交于 2026-10-01，cs.LG，作者 Haoyang Jiang、Zhengui Wang、Shenghan Gao、Y. Joseph Zhang、Xingquan Zhu、Yi He；comments: Accepted at the 2026 IEEE International Conference on Data Mining (ICDM)；DOI 10.48550/arXiv.2610.01765；抓取日期 2026-10-04）

## 是什么

面向**开边界（open-boundary）时空系统**的预测框架：预测域与未观测外部持续交换通量，边界节点接收上游入流、潮汐等外力驱动，而这些信息在预测时通常拿不到——导致自回归 rollout 误差复利放大、长程预测崩坏（以下描述均来自本次实抓的摘要页）。框架两件套：

1. **ghost node 代理**：从边界与内部节点学习"幽灵节点"，近似不可观测的外部输入（回答"边界信息缺失时，什么外力进入了预测域"）；
2. **两个物理修正器（physics refiners）**：其一将 ghost 代理与二跳邻居对齐，强制局部一致性；其二用物理引导图神经算子改善全局稳定性、抑制长程数值漂移（回答"外力应如何传播而不放大误差"）。

在两个真实水文图数据集上，精度与长程稳定性均优于 learning-based 与 physics-informed 基线。ICDM 2026 接收。

## 解决什么问题

图时空预测的既有工作默认预测域封闭（所有输入可观测），而真实水文/沿海/流域系统是开放的：外生边界驱动缺失使纯数据驱动 GNN 在长程 rollout 中系统性漂移。本文把"缺边界条件"显式建模为可学习代理 + 物理约束传播问题。

## 相比前方法优势

- **问题设定新且真实**："开边界"显式化——多数物理引导时空方法只在域内加物理约束，未处理域外通量不可观测这一根因；
- **组件即插**：ghost 代理与物理修正器是骨干无关的附加件（摘要口径），不要求整体架构替换；
- **同时改进精度与长程稳定性**：两个修正器分工（局部一致性 vs 全局抗漂移），直指自回归误差复利这一水文预测常见失败模式；
- 会议背书（ICDM 主会接收）高于库内多数同主题 arXiv-only 条目。

## 局限

- **无代码、无数据链接**：arXiv 页未附实现，数据集亦未给出公开入口，复现只能按摘要描述从零自建（runnable=false 实核）；
- **验证域窄**：仅两个真实水文图数据集，v1 无消融与泛化实验细节（摘要未给量化幅度，引用任何具体数字前必须读正文核实）；
- **水文语境特化**：迁移到非水文开边界系统（交通边界断面、跨区域电网输入等）需自行重推导物理项，摘要未提供迁移实验；
- 物理修正器依赖具体守恒/一致性先验的领域建模能力，赛期引入的建模成本不低。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**：水文/环境/沿海类赛题（水位、流量、污染物扩散、风暴潮）中"外生驱动数据不全"是高频真实痛点——ghost node 代理可作为"缺失外生变量的代理构造"技巧直接写进模型改进章节；"开边界 + 物理修正"叙述框架可升级为论文的创新点陈述（相比裸 LSTM/GNN 基线，长程稳定性对比图是评委可见的差异化证据）；复现路径：PyG 自建，ghost 代理（MLP/小型 GNN）+ 二跳一致性损失 + 图神经算子正则，成本高但组件清晰；
- **与库内卡的关系**：与 TSFM 族（2608.22968/24033/24303/2609.16804，模型选型与评测先验）正交——本卡供的是"物理结构先验 + 图时空"组件，不是基础模型；与已拒的 PIRNN（arXiv-2609.19871，地下水 PINN，域特化且属 PINN 常识延伸）不同：本卡问题设定（开边界外力不可观测）与机制（ghost 代理）更普适，且有 ICDM 主会背书；
- **引用纪律**：摘要未给任何量化数字，对外材料引用前必须读 PDF 正文并自测复现（铁律 4）。
