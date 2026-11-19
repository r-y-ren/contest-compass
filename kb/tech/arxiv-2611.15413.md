---
id: arxiv-2611.15413
name: "MORA：冻结预测器的免输入残差修正适配器——用结构外推估分段均值再按可靠性分阶段修正，288 例中 96.2% 降 MSE（短期 -28.1%，官方仓可跑）"
field: [time series forecasting, residual correction, model-agnostic adapter]
directions: [数模与时序预测]
published: "2026-11-11"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv v2（2026-11-11，摘要经 arXiv API 实抓）+ 官方仓 hugerli-1/MORA（GitHub API 实查：0 stars，2026-09-23 创建、2026-09-26 推送，Python；摘要'Code repository'指向本仓；仓最后推送早于 v2，对应 v1 代码）"
  stars: 0
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "赛题已有一个'还不错但不够准'的预测结果时，MORA 是最低成本的补刀层：不用新输入、不动冻结骨干、不用 LLM，只从历史输入估分段均值的粗结构再分阶段修正——短期 -28.1% 的量级在 24-72 小时预测题里足以改变名次；其'可预测的粗尺度残差'诊断分析（残差能量集中在少数低频分量）本身就能写进数模论文的误差分析章节"
    reuse_cost: 低
    open_source: "github.com/hugerli-1/MORA（摘要给出的官方实现仓）"
  - track: "Kaggle-竞赛"
    edge: "对已提交管线做 post-hoc 修正的即插即用层：六个骨干（含三个 TSFM）跨上下文长度都吃到收益，意味着无论赛题用 Chronos-2 还是自训模型都能叠一层；与库内修正族互补——CastReasoner（2611.12285）是 LLM 证据驱动的 retain/revise/reconstruct，本卡是纯数值轻量修正，两者构成'有文本协变量 vs 无额外输入'两条修正路线"
    reuse_cost: 低
    open_source: "github.com/hugerli-1/MORA"
sources:
  - url: https://arxiv.org/abs/2611.15413
    title: "MORA: Correcting Time Series Forecasts with Coarse Future Signals（arXiv abs 页 v2，2026-11-11，摘要经 arXiv API 实抓）"
    accessed: "2026-11-19"
  - url: https://github.com/hugerli-1/MORA
    title: "官方代码仓（GitHub API 实查：0 stars，2026-09-23 创建、2026-09-26 推送，Python；仓活跃期早于论文 v2 公开日）"
    accessed: "2026-11-19"
---

# MORA：不给新输入、不动模型，只"修理"已有预测的粗尺度残差

> 来源：https://arxiv.org/abs/2611.15413 （v2 2026-11-11，摘要经 arXiv API 实抓）；官方仓 https://github.com/hugerli-1/MORA 信号经 GitHub API 实查（2026-11-19）。本卡内容出自本次抓取的摘要与仓库元数据，未读 PDF 全文。

## 是什么

**Model-Output Residual Adaptation（MORA）**，模型无关的残差修正适配器。两个先导发现：(1) 各架构预测器的残差能量**集中在少数低频分量**上；(2) 线性探针显示历史输入里仍含有关于**预测均值误差**的可预测信息。据此 MORA 不直接回归骨干特有的残差，而是：对目标序列的分段均值做**结构外推+学习估计**，再把"估计值与骨干预测统计量之差"转成**分阶段修正**，每个更新按估计可靠性缩放。官方口径：12 基准 × 6 骨干，长期 -7.2%、短期 -28.1% MSE，288 例中 96.2% 降 MSE；三个 TSFM 跨上下文长度同享收益。

## 解决什么问题

换架构、调训练都到顶之后，预测误差的"最后一段"是结构性的：低频分段均值估不准。现役修正类方法要么需要额外输入（文本协变量/外部信号），要么直接回归残差（骨干相关、易过拟合）。MORA 证明：**只用已有历史输入，靠估计"粗结构"而不是"残差本身"**，就能稳定吃到修正收益。

## 相比前方法优势

- **免额外输入**：与 LLM 文本修正路线（库内 CastReasoner/CoCo）不同，MORA 不需要任何协变量文本，纯数值闭环；
- **估结构不估残差**：直接回归残差会绑定骨干误差分布，MORA 回归"分段均值应是什么"，跨骨干可移植；
- **可靠性加权**：分段均值估计本身的置信度决定修正幅度——不确定时少修，天然防"越修越坏"；
- **覆盖面大**：288 例 96.2% 降 MSE 的覆盖率比"平均增益"更有工程意义（不是赌某几个数据集）。

## 局限（如实标注）

- 0 stars 低活跃仓，最后推送停在 2026-09-26（早于 v2），v2 若有方法更新代码未必同步；
- 收益主要在短期（-28.1%），长期 -7.2%——长 horizon 赛题的期望要压低；
- "结构性残差可预测"的假设依赖历史输入里确有均值漂移线索；平稳性极强、误差完全随机的序列上修正空间小；
- 分段均值估计的"分段"粒度是超参，不同采样率/周期数据需要重调。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：几乎零成本叠在任何已有预测之后——赛题交论文前拿 MORA 过一遍，若 MSE 再降即可写"残差结构分析与二阶段修正"小节，其低频残差诊断图直接可用；短期预测题（逐小时/逐日）收益最大。
- **Kaggle-竞赛**（reuse_cost 低）：作为 post-hoc ensemble 的替代/补充——不用再训模型，对每个已生成预测文件套修正层；与库内 QUAL（quantile 对齐，2610.41100）构成"均值修正 vs 分位修正"的正交工具对。
