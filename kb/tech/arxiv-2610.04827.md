---
id: arxiv-2610.04827
name: "GRAM：图检索'幅度记忆'修正冻结 TSFM——不取相似段未来、只取系统性偏差原型，跨数据集×基础模型一致增益"
field: [time series foundation model, retrieval augmentation, bias correction]
directions: [数模与时序预测]
published: "2026-10-04"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv（2026-10-04 v1；摘要页无 comments、未附代码链接；GitHub 检索未见官方仓）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "小样本时序赛题的免微调增强套路：赛题数据太少不配微调 TSFM 时，用'检索系统性偏差并按视野修正'这一轻量外挂——不碰冻结主干、不需要目标域预训练，修正信号取自**反复出现的模型偏差**而非相似段的随机波动，理论动机（随机波动不可复用、系统偏差可复用）可在论文中作为方法选择依据"
    reuse_cost: 中
  - track: "Kaggle-竞赛"
    edge: "零样本骨干+检索修正的双层 stack 设计：幅度按比例缩放误差聚成可检索原型 + 原型图聚合一致偏差、抑制随机波动——与常见'检索相似历史段拼接上下文'路线正交，可叠加使用；跨多个基础模型一致有效说明可平滑换骨干"
    reuse_cost: 中
sources:
  - url: https://arxiv.org/abs/2610.04827
    title: "GRAM: Correcting Frozen Time-Series Foundation Models via Graph-Retrieved Amplitude Memory（arXiv abs 页，v1 2026-10-04，Xiaoyun Yu/Xiangfei Qiu/Yonggui Huang/Shixiang Tang/Nanqing Dong/Wanli Ouyang/Geguang Pu/Honggang Qi/Jilin Hu/Xi Chen；Comments 未列出；2026-10-16 实抓）"
    accessed: "2026-10-16"
---

# GRAM：冻结 TSFM 的"错题本"——检索偏差原型，按视野修正

> 来源：https://arxiv.org/abs/2610.04827 （arXiv abs 页 v1 2026-10-04，2026-10-16 实抓）。本卡内容出自本次抓取的摘要页，未读 PDF 全文。

## 是什么

一个对**冻结时序基础模型**做免训练修正的外挂模块。核心是两个组件：**幅度记忆模块（Amplitude Memory Module）**——把预测误差按幅度缩放后聚合成可检索的原型（prototype）；**原型图模块（Prototype Graph Module）**——在原型关系图上传播，聚合一致的系统性偏差信息、抑制样本级随机波动。预测时检索相关原型，按预测视野施加修正。

## 解决什么问题

已有检索增强修正路线用"相似历史窗口的**真实未来**"做修正信号——但真实未来里混着样本特有的随机波动，可复用的是其中**反复出现的系统性模型偏差**，而偏差又受尺度差异与噪声干扰难以直接利用。GRAM 要把"偏差"而非"相似段未来"变成可检索、可聚合的修正资产。

## 相比前方法优势

- **修正信号换轨**：从"相似段的真实未来"换成"聚合后的系统性偏差原型"——随机波动被图聚合抑制，系统偏差被放大复用，与检索相似段路线**正交可叠加**；
- **幅度不变性设计**：误差按幅度缩放后再聚合，缓解尺度差异导致的偏差不可比问题；
- **按视野（per-horizon）修正**：不同预测步长的系统偏差分别处理，不一步到位抹平；
- **跨数据集×基础模型一致增益**（摘要表述为 consistent forecasting improvements），不绑定单一骨干。

## 局限（如实标注）

- 摘要页无代码链接，GitHub 检索未见官方仓（reproducibility 低）；"consistent improvements"未给具体数字，增益幅度需读全文；
- 原型库的构建依赖先验误差数据（哪个域的偏差本？），冷启动域的适用性未说明；
- 修正的前提是"系统偏差稳定复现"——强非平稳/域漂移场景下偏差原型可能过期；
- v1 预印本无 venue。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 中）：赛题数据量不足以微调 TSFM 时（数模常态：几百条观测），冻结骨干 + 偏差记忆外挂是性价比路线——可在自留出集上先测"模型系统性偏差是否存在且稳定"，存在则按本文思路建小型偏差原型表按视野修正；论文方法章节用"可复用的是系统偏差而非随机波动"的论证支撑选型。
- **Kaggle-竞赛**（reuse_cost 中）：作为 stack 的一层叠加在 Chronos/TimesFM 类零样本预测之上；跨骨干一致有效意味着换骨干时该层不用重做。

**族内定位**：库内 TSFM 修正位已有 2610.12232（TTA 因果延迟审计：在线更新路线）与本卡（离线检索偏差修正路线）——一个管"要不要在线适应"（结论多为不值得），一个管"离线批修正怎么白拿增益"；两者修正信号（自适应更新 vs 检索偏差原型）互斥可对照选型。
