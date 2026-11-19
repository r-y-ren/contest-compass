---
id: arxiv-2611.19586
name: "SLiDE：外生变量驱动的 Koopman 结构化线性动力学预测——编码与预测共享线性递推，分布外外生输入 MSE -20%（官方仓可跑，轻量 MLP 级开销）"
field: [time series forecasting, exogenous inputs, Koopman operator, dynamics]
directions: [数模与时序预测]
published: "2026-11-14"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv v1（2026-11-14，摘要经 arXiv API 实抓）+ 官方仓 KIT-IAI-DRACOS/slide（GitHub API 实查：0 stars，2026-10-20 创建，Python；README 标题/作者与论文一致（Pütz/Glavas/Schäfer/Oreshkin/Coates），含 Hydra/Lightning 训练管线与逐模型调参配置）"
  stars: 0
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "带外生变量的赛题（电价/负荷/零售需求——数模 C 题经典形态）：SLiDE 的核心卖点是**外生输入分布偏移下的稳健**——超出历史范围的外生值（政策调价、极端天气、促销力度拉满）MSE 仍降 20%，这正是赛题'情景假设'环节最容易翻车的地方；潜空间线性递推的结构也便于做'外生变量如何驱动系统'的机理阐释章节，MLP 级算力本地即可训"
    reuse_cost: 中
    open_source: "github.com/KIT-IAI-DRACOS/slide（官方实现，含数据管线与调参配置）"
  - track: "Kaggle-竞赛"
    edge: "能源/零售类带 future-known 回归量的赛（电价预测、店铺销量）：与梯度提升树路线对比的差异化选项——结构化线性动力学在外生 regime 切换的 private set 上通常比纯相关模型稳；官方仓带 FEV 数据管道与逐数据集调参配置，可直接套赛题数据"
    reuse_cost: 中
    open_source: "github.com/KIT-IAI-DRACOS/slide"
sources:
  - url: https://arxiv.org/abs/2611.19586
    title: "SLiDE: Structured Linear Dynamics for Forecasting with Exogenous Inputs（arXiv abs 页 v1，2026-11-14，摘要经 arXiv API 实抓）"
    accessed: "2026-11-19"
  - url: https://github.com/KIT-IAI-DRACOS/slide
    title: "官方代码仓（GitHub API 实查：0 stars，2026-10-20 创建；README 首行列出论文作者名单，含 SLiDE 消融与基线配置、HuggingFace/FEV 数据管道）"
    accessed: "2026-11-19"
---

# SLiDE：外生变量会变脸的赛题，用"共享线性递推"把机理约束进模型

> 来源：https://arxiv.org/abs/2611.19586 （v1 2026-11-14，摘要经 arXiv API 实抓）；官方仓 https://github.com/KIT-IAI-DRACOS/slide 信号经 GitHub API 实查（2026-11-19，README 与论文作者/标题核对一致）。本卡内容出自本次抓取的摘要与仓库元数据，未读 PDF 全文。

## 是什么

**Koopman 启发的外生输入预测架构**。痛点：现代深度模型在外生输入上容易过拟合**在偏移下不泛化的相关性**。SLiDE 在潜空间对时间动力学施加结构：用学习的**线性算子**近似非线性系统演化——(i) **结构化历史编码器**从过去目标值与输入重建当前潜状态；(ii) **共享线性 rollout** 由未来已知外生变量驱动。关键约束：编码阶段与预测阶段**共用同一线性递推**，让"过去如何被编码"与"未来如何演化"对齐，从而降参数化、阻断对历史输入中伪相关性的依赖。官方口径：电价预测与零售需求等真实基准 SOTA；超范围外生值样本 MSE -20%；同一动力系统被未见外生过程驱动的合成迁移设定 MAE -30%；算力开销与轻量 MLP 相当。

## 解决什么问题

外生回归量驱动的预测有两个失败模式：训练时记住"输入模式→输出"的 spuriously 相关，遇到没见过的外生 regime 就崩；以及编码器与 rollout 各学各的，隐状态语义不一致。SLiDE 用 Koopman 思想把两者锁进同一个线性算子：外生变量只作为线性递推的驱动项进入，系统自身的演化规律保持线性不变——这正是控制论里"外生输入不影响系统矩阵"的结构先验。

## 相比前方法优势

- **偏移稳健是主卖点而非副产品**：-20% MSE（超范围外生）与 -30% MAE（未见外生过程迁移）直接对应赛题情景分析的翻车场景；
- **轻量**：MLP 级开销，无需 GPU 集群，数模队三天算力预算内可训可调；
- **结构可解释**：潜空间线性动力学+外生驱动项的分解，让"外生变量怎么影响系统"有显式机制叙述；
- **与 Koopman 生成线互补**：库内 KGO（2611.04760）用 Koopman 做概率预测的单步流匹配生成，本卡把 Koopman 用于外生回归的稳健化——同一算子家族两种用法。

## 局限（如实标注）

- 0 stars 新仓（建于论文公开前一个月，团队侧研发布局），社区验证不存在；
- "SOTA"为论文自报，摘要只给了电价与零售两个真实域，域覆盖面窄，未提与 TSFM 零样本路线的对照；
- 线性潜动力学的表达力受系统非线性强度限制——强非线性/强 regime 切换系统上线性算子近似误差未量化；
- 未来已知外生变量（future-known）是架构前提：外生变量若只能滞后获得（非 future-known），共享 rollout 的用法要重设计。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 中）：电价/负荷/销量+政策/天气/促销外生量的赛题，用 SLiDE 做主模型或稳健性对照：情景分析环节（"若外生变量超出历史范围会怎样"）恰好打在其 -20% MSE 的优势区；官方仓的逐数据集调参配置给出了从零到结果的完整路径。
- **Kaggle-竞赛**（reuse_cost 中）：能源价格类赛（wind/solar/price）上作为"结构化先验"路线与 LGBM/TSFM ensemble；合成迁移设定（-30% MAE）提示其在 CV 切分不稳定的赛题上风险更低。
