---
id: arxiv-2610.33330
name: "TempShap：输入格 (t,i) 级 Shapley 归因——同时回答特征何时起作用、影响随 horizon 怎么变"
field: [time series forecasting, 可解释性, Shapley 归因]
directions: [数模与时序预测]
published: "2026-10-23"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv（对照验证三件套：植入时序结构、可精确求解的 cell 博弈、线性预测器闭式归因 oracle）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "数模论文的可解释性章节普遍停留在特征重要度条形图——TempShap 把归因升级为张量（时间×特征×horizon）：能画出'某特征在输入窗哪几天起作用、其影响在预测第几天衰减'的曲线，并配植入结构+闭式 oracle 的验证纪律；这对'模型结论可信度'论证是代差级的差异化素材，且摘要明确给出删除排名实验证明其比 one-at-a-time 更可靠"
    reuse_cost: 中
    open_source: "无（2026-11-07 实抓摘要未附代码链接）"
  - track: "Kaggle-竞赛"
    edge: "错误分析（error analysis）与特征工程的方向盘：cell 级归因定位'预测崩坏的具体时间窗+具体变量'，比全局 feature importance 精一格——对时序赛的 post-mortem（哪段假期/哪个站点拖垮了 CV）和冗余特征识别（substitutable information 会被 one-at-a-time 低估，本文有反例隔离）都有直接操作价值"
    reuse_cost: 中
    open_source: "无（同上）"
sources:
  - url: https://arxiv.org/abs/2610.33330
    title: "TempShap: When and How Much a Feature Matters in Time-Series Forecasting（arXiv abs 页，2026-10-23，摘要经 arXiv API 实抓）"
    accessed: "2026-11-07"
---

# TempShap：把时序预测的 Shapley 归因做到输入格级别

> 来源：https://arxiv.org/abs/2610.33330 （v1 2026-10-23，摘要经 arXiv API 实抓，2026-11-07）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

时序预测器的归因框架。既有 Shapley 解释器把"一个特征"当作一个玩家，等于把两个关键维度压扁了：**特征在输入窗的哪个时刻起作用**（temporal localization）、**其影响随预测 horizon 如何变化**（horizon impact）。TempShap 把玩家细化到**单个输入格 (t,i)**（时刻 t 的特征 i），在回溯式、损失基的 Shapley 博弈上计算，得到归因张量，从中导出时间定位与 horizon 影响两条 profile。验证三件套：植入已知时序结构做 ground truth、构造可精确求解的 cell 博弈、对真实线性预测器推闭式归因 oracle。估计用 permutation sharing 控制扰动成本。

## 解决什么问题

特征级标量归因回答不了"何时、往哪个 horizon 方向"——而这恰是时序决策（何时干预、可信到第几天）真正要问的。同时摘要指出方法学陷阱：**冗余输入下 one-at-a-time 打分会系统性低估可互相替代的信息**，而符号化 Shapley 分解保住总价值，删除排名（held-out deletion ranking）更可靠。

## 相比前方法优势

- **粒度对**：(t,i) 级玩家使"时间定位 + horizon 影响"两条轴同时可问，输出是张量而非标量；
- **验证纪律强**：不是只看直觉合理性——有植入结构、精确可解 toy 博弈、闭式 oracle 三重对照，这在归因文献里少见；
- **成本可控**：permutation sharing 把 cell 级博弈的估计做在局部化扰动成本内；
- **跨族有效**：删除排名优势在多种 Shapley 估计器、多个预测基准、多个模型族上复现（官方口径）。

## 局限（如实标注）

- 摘要未给出具体计算开销数字（cell 数 × 扰动次数的量级），长输入窗+多特征时是否赛程内可跑需读全文/实测；
- 代码释出情况摘要未提及，本轮实抓未见仓库——按 paper 处理；
- 回溯式（retrospective）归因面向已训练模型的解释，不能当训练时的正则用；
- 摘要未说明对极长 horizon（数百步）profile 的分辨率与可读性。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 中）：可解释性章节升级路线：用 TempShap 的归因张量画出"关键驱动变量的作用时段 + 影响衰减曲线"，配合其三重验证叙事回应"黑箱"质疑；若赛题含政策/干预问题，horizon impact profile 直接支撑"干预在预测期内是否持续有效"的论证。
- **Kaggle-竞赛**（reuse_cost 中）：CV 失败片段的归因定位工具——对误差最大的 (时间窗， 变量) 精确归因，指导特征工程与数据清洗的火力分配；冗余特征识别（substitutable information 的低估陷阱）帮助精简特征集。

**族内定位**：库内可解释性家族已有 TSAE（arxiv-2610.04925 类，SAE 内部特征方向，候选池未入）与 Temporal Predictive Multiplicity（等精度模型轨迹分歧）占"内部表征/不确定性"位；本卡占"**输入归因**"位——从输入格扰动出发，与内部方向（SAE）和模型间分歧（multiplicity）三层互补。另注意与 DeFA/TraceBench 等 agent 失败归因卡不同族（那边归因 agent 决策，这边归因预测模型）。
