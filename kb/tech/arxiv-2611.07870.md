---
id: arxiv-2611.07870
name: "FARR：端点差分证据的条件预测残差精炼——冻结预测器的输出层即插即用修正"
field: [时序预测, LLM 预测器, 外生条件建模, 残差修正]
directions: [数模与时序预测]
published: "2026-11-05"
maturity: demo
venue_tier: arXiv
signal:
  venue: "arXiv (cs.AI, Comments: 10 pages, 3 figures, 4 tables)"
  stars: 0
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "外生变量引入的守门组件：数模预测题引入天气/节假日/政策等辅助条件时，'条件选得不对反而增误差'是常见失分点——FARR 用匹配端点差分（同一输入跑'带条件预测'与'预定义空条件预测'，两预测之差即条件影响）显式量化外生条件的贡献，再用共享残差精炼器估计剩余误差、horizon-wise 门控控制修正注入量，全程冻结预测器不改权重；差分门控思路可平移到任意条件预测器（含树模型：跑带条件/空条件两版预测，把差值作为门控特征），四个长程基准上 dataset-average MSE/MAE 最优（论文自报）；官方 MIT 代码仓实核可达（2026-11-09），但数据/权重不分发、需自备冻结骨干生成端点，复现成本中等"
    reuse_cost: "中"
    open_source: https://github.com/blossomrichzyy-star/farr-forecast-aware-residual-refinement
  - track: "Kaggle-竞赛"
    edge: "外生特征增益门控：把'带某特征组 vs 不带'的双预测差分作为特征贡献的训练一致化度量，按 horizon 分段决定注入强度（长程段条件影响通常更不可靠）；与常规 permutation importance 相比不依赖单点打乱、直接在预测输出层量化；需自备骨干与端点生成管线，赛期收益需在自有数据上重验（论文仅四基准自报）"
    reuse_cost: "中"
    open_source: https://github.com/blossomrichzyy-star/farr-forecast-aware-residual-refinement
sources:
  - url: https://arxiv.org/abs/2611.07870
    title: "FARR: Forecast-Aware Residual Refinement with Matched Endpoint Evidence for Long-Horizon Time-Series Forecasting（arXiv:2611.07870 摘要页实抓：端点差分量化条件影响+共享残差精炼器+horizon-wise 门控；四长程基准 dataset-average MSE/MAE 最优；Comments 10 页 3 图 4 表；摘要尾注代码将发布于 blossomrichzyy-star/farr-forecast-aware-residual-refinement）"
    accessed: "2026-11-09"
  - url: https://github.com/blossomrichzyy-star/farr-forecast-aware-residual-refinement
    title: "FARR 官方实现仓库 README 实抓（2026-11-09）：src/farr/（模型/特征/数据加载/训练/评测）+scripts/（端点生成/主实验/评测）+docs/（骨干接口与空条件定义）；ETTh1/Weather/Traffic/ECL × horizon 96-192-336-720；README 明示 Data, weights, configurations, and experiment outputs are not distributed，骨干经本地 factory 加载自备冻结 SE-LLM 预测器"
    accessed: "2026-11-09"
  - url: https://api.github.com/repos/blossomrichzyy-star/farr-forecast-aware-residual-refinement
    title: "GitHub API 仓库快照实抓（2026-11-09）：stars 0 / forks 0 / MIT license / Python / 仓库 83KB / 2026-09-14 创建、2026-10-27 最后 push"
    accessed: "2026-11-09"
---

# FARR：用"带条件 vs 空条件"端点差分修正 LLM 时序预测的残差精炼层

## 是什么

Zhang 等 5 人（2026-11-05 提交 arXiv:2611.07870，cs.AI，Comments 10 页 3 图 4 表，摘要页 2026-11-09 实抓）提出的预测后处理框架：针对"LLM 类预测器用辅助条件（auxiliary conditioning）引入外生信息，但条件与观测时序上下文匹配不佳时反而推高预测误差"的问题，FARR 对同一输入分别获得标准条件下的有效预测与预定义空条件下的零预测，**两者之差即条件对预测的影响**（端点证据）；共享残差精炼器将端点证据与历史特征结合，估计有效预测的剩余误差；horizon-wise 门控逐段控制预测残差注入最终输出的比例。四个长程预测基准上取得对比方法中最优的 dataset-average MSE 与 MAE。官方实现开源（MIT，2026-11-09 仓库页与 API 快照实核可达），但**数据、权重、配置与实验输出不分发**，骨干冻结预测器需经本地 factory 自备加载。

## 解决什么问题

辅助条件（天气、节假日、事件文本等外生信息）被广泛塞进预测模型，但其影响从未被显式度量：条件注入不当时（条件与上下文不匹配），模型被迫在错误的条件下预测，误差不降反升。既有做法要么全盘接受条件、要么干脆不用，缺少"量化条件贡献并按需门控"的中间层。FARR 把这个问题变成可测量的差分：条件影响 = 有效预测 − 空条件预测，再学一个残差精炼器把这个证据转化为修正量。

## 相比前方法优势

- 端点差分是免训练的条件贡献度量：不需要改动或重训预测器（冻结骨干），两次前向即得；
- horizon-wise 门控承认"条件影响随预测步变化"（近程可信、远程存疑），比全局开关更细；
- 输出层插件形态：对任意能跑条件/空条件两次前向的预测器都成立，不绑定特定架构；
- 四基准 dataset-average 最优（论文自报，代码与协议脚本已开源）。

## 局限（如实标注）

- 仓库不分发数据与权重：复现需自备冻结 SE-LLM 骨干并按 docs/backbone.md 实现端点生成接口，赛期复现成本中等；repo stars 0 / 0 fork（2026-11-09 快照），无第三方复现背书；
- 效果数字全部论文自报（四基准），无独立验证；基线阵容与公平性需读全文核查；
- 无 venue（arXiv v1）；
- 骨干是 LLM 型预测器（SE-LLM），对树模型/纯数值骨干的迁移是思路层平移而非代码直接可用——差分门控逻辑要自己重写；
- 与库内 arxiv-2609.23257（CTRL：LLM 控制器读误差分解发控制信号+残差解码）同属"LLM 预测+残差修正"族但不同轴：CTRL 的 LLM 在推理期做控制器、处理非平稳漂移；FARR 的关键件是端点差分量化**条件贡献**并门控，不依赖分解误差的语义分析。

## 如何用于比赛

1. **外生变量预测题的守门组件（数模-预测与评估，主用）**：引入天气/节假日/政策条件前，先跑"带条件 vs 空条件"双预测，看差分是否与真值误差同向——差分大且方向对才让条件参与，否则门控衰减；这能直接避免"塞了一堆外生特征反而掉分"的典型失分，且两次前向的成本远低于特征搜索；官方代码可作为差分-精炼-门控三件套的参考实现；
2. **特征贡献门控（Kaggle-竞赛）**：把端点差分思想用于特征组消融——差值作为该特征组贡献的输出层度量，按 horizon 分段加权，比单一全局特征重要性更能决定"长程段要不要信外生特征"；收益需在自有数据上重验。
