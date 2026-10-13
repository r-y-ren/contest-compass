---
id: arxiv-2608.29658
name: 'ButterMamba: Butterworth-Enhanced Spatial-Temporal Mamba for Efficient Traffic Flow Prediction'
field: [time series forecasting, 交通流预测, 时空建模, 信号滤波]
directions: [数模与时序预测]
published: "2026-08-30"
maturity: paper
venue_tier: arXiv
signal:
  venue: "arXiv（comments：9 pages, 6 figures；主分类 physics.soc-ph，交叉 cs.LG 与 physics.data-an；无 venue 与代码信息）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "交通流/人流/共享单车等含噪传感器时序题的'滤波优先'预处理件：Butterworth 谱滤波先剥高频噪声、再上预测模型，且'滤波与建模分离'后滤波带宽可单独调参不重训主干。scipy.signal.butter/filtfilt 数行可移植，与'不做滤波的原始序列'天然构成消融对照，直接区别于'无预处理直接堆 GNN/注意力'的常见答卷；论文据此主张同精度下线性复杂度、更低训练时间与内存"
    reuse_cost: 低
    open_source: "论文无代码；Butterworth 滤波为 scipy 标准件，Mamba 骨干有 state-spaces/mamba 开源生态可自搭（2026-10-13 摘要页实抓）"
  - track: "Kaggle-竞赛"
    edge: "交通流量/拥堵类赛题（Kaggle 有先例题型）的长序列大规模传感器网络场景：并行 Mamba 状态空间混合器以线性复杂度捕获长程时间与空间依赖，相对注意力二次复杂度是时序长度受限赛题的部署级差异点；可只借'谱滤波前端+SSM 主干'的结构分工，不必整架构照搬"
    reuse_cost: 中
    open_source: "无官方实现；完整架构需按论文自建（mamba-ssm 开源骨干起步）"
sources:
  - url: https://arxiv.org/abs/2608.29658
    title: 'ButterMamba: Butterworth-Enhanced Spatial-Temporal Mamba for Efficient Traffic Flow Prediction'
    accessed: "2026-10-13"
---

# ButterMamba：Butterworth 增强的时空 Mamba 交通流预测

> 来源：https://arxiv.org/abs/2608.29658 （arXiv v1 提交于 2026-08-30，主分类 physics.soc-ph，交叉 cs.LG、physics.data-an，作者 Limiao Zhang 等，comments：9 pages, 6 figures，无 venue 与代码链接；抓取日期 2026-10-13）

## 是什么

arXiv 2608.29658 针对交通流预测提出 ButterMamba 框架（以下描述均来自本次抓取的摘要页）：

- **针对两个痛点**：(1) 注意力类架构的二次复杂度阻碍实时、大规模部署；(2) 传感器高频噪声损害预测可靠性（现有 GNN+时序预测方案对二者均未显式处理）；
- **两个组件**：Butterworth 谱滤波模块——建模前剥离高频噪声；空间-时间状态混合器（Spatial-Temporal State Mixer）——并行 Mamba 设计，捕获长程时间与空间依赖；
- **核心主张**：滤波与建模分离的设计带来"更准 + 线性复杂度"，在三个公开数据集上优于 SOTA 且训练时间与内存更省（作者自报摘要口径）。

## 解决什么问题

交通流序列同时是"长程时空依赖"与"高频观测噪声"的叠加体：注意力架构解决前者但代价是二次复杂度，而噪声问题通常被留作不加处理的数据背景。本文把去噪显式前移为独立组件，使复杂度与鲁棒性两个目标解耦。

## 相比前方法优势

- 相对 GNN+注意力的主流时空预测栈：线性复杂度替代二次复杂度，训练时间与内存更低（作者自报），对大规模路网/长时窗场景更可部署；
- 相对库内时序预测族：无一张卡覆盖"频域显式带阻预滤波"这一预处理件——arxiv-2608.25871（CEDAR 残差分解）、arxiv-2608.20052（DecoVAE，仅在叙事中类比 HP 滤波）、arxiv-2610.01765（水文图物理修正）均不占据该先位；本卡的 Butterworth 前端是与骨干无关的即插即用件；
- 相对库内 arxiv-2608.20761（Fuzzy-MoE，交通仅为其应用域举例）：本卡给出交通流主场的完整架构证据链（滤波+时空 SSM），二者正交可叠加。

## 局限

- 无代码、无 venue（9 页 v1 预印本，未经同行评审）；主分类 physics.soc-ph 而非主力 ML 会议，评审强度未知；
- "三个公开数据集优于 SOTA"为作者自报，摘要页未列全对比对象与数据集名称，未经第三方复现；
- Butterworth 截止频率是需要按题调的超参：带宽选择不当可能滤掉真实高频动态（事故、突变），题面含真实突变信号时须做带宽消融；
- 完整架构（并行 Mamba 混合器）复现需自搭，mamba-ssm 生态可用但无现成配方；赛期时间紧时只可移植滤波前端，主干仍需自选成熟模型；
- 结论域限于交通流，向电网/管网等其他传感器网格外推未验证。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**：交通流/人流/共享单车类赛题的数据预处理章节直接落地——"Butterworth 预滤波 → 预测 → 滤波带宽敏感性分析"三段式既是涨点手段也是论文规范性卖点；复用成本为 scipy 标准件级（低）；
- **Kaggle-竞赛**：交通流量类赛题的长序列场景参考其"滤波前端+线性复杂度 SSM 主干"分工；完整架构复现成本中等，先以滤波前端+成熟骨干（PatchTST/iTransformer，见库内 gh-dreamers-laboratory_timeseries-atlas 基线纪律）做 A/B，再决定是否投入自搭 Mamba；
- **纪律提醒**：论文数字全部为作者自报（铁律 4），赛场结论须自测；滤波消融（开/关、带宽扫描）应作为必做实验而非默认开启。
