---
id: arxiv-2610.26987
name: "DDCI：时序预测的双反馈 conformal 推断——实际误覆盖反馈 + oracle 阈值估计反馈，区间更窄更稳且近名义覆盖（NeurIPS 2026）"
field: [time series forecasting, 不确定性量化, conformal prediction]
directions: [数模与时序预测]
published: "2026-10-19"
maturity: paper
venue_tier: CCF-A
reproducibility_level: medium
signal:
  venue: "arXiv（Comments：Accepted by NeurIPS 2026）+ 官方代码仓 sdu1998/DDCI（GitHub API 实查 2026-10-29：0 stars，Python，无 license，2025-09-24 创建，最后推送 2026-05-05）"
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "区间预测题的不确定性外套：在线 conformal 只靠'真值是否落在区间内'的误覆盖反馈会过度膨胀/收缩，DDCI 加入来自 oracle conformal 的经验阈值作为估计反馈来阻尼——序列相关+分布漂移下区间更窄更稳且保持近名义覆盖；方法 model-agnostic，套在任何点预测器外即可，数模答卷'点预测+区间'的标准结构直接受益"
    reuse_cost: 低
    open_source: "github.com/sdu1998/DDCI（0★ 无 license，使用前核查许可）"
  - track: "Kaggle-竞赛"
    edge: "概率/分位数赛道的后处理校准层：以误覆盖指标与经验阈值双信号在线调预测区间宽度，适配时序赛常见的分布漂移（COVID 段、政策切换段），比固定分位数偏移更抗漂移；官方仓可直接改造成验证器管道的一环"
    reuse_cost: 低
    open_source: "同上"
sources:
  - url: https://arxiv.org/abs/2610.26987
    title: "Dynamic Dual-feedback Conformal Inference for Time Series Forecasting（arXiv abs 页，v1 2026-10-19，Songlin Du/Ling Luo/Uwe Aickelin，Comments：Accepted by NeurIPS 2026）"
    accessed: "2026-10-29"
  - url: https://github.com/sdu1998/DDCI
    title: "官方代码仓（GitHub API 实查 2026-10-29：sdu1998/DDCI，0 stars，Python，无 license，2025-09-24 创建，最后推送 2026-05-05，早于论文 v1）"
    accessed: "2026-10-29"
---

# DDCI：给在线 conformal 加第二个反馈信号，区间不再"一惊一乍"

> 来源：https://arxiv.org/abs/2610.26987 （v1 2026-10-19，Songlin Du/Ling Luo/Uwe Aickelin，Comments 注明 Accepted by NeurIPS 2026；2026-10-29 经 arXiv API 实抓摘要；官方仓 sdu1998/DDCI 同日 GitHub API 实查）。本卡内容出自本次抓取的摘要与 API 元数据，未读 PDF 全文。

## 是什么

时序预测的**在线 conformal 推断**改进方法 DDCI（Dynamic Dual-feedback Conformal Inference）。现有在线 conformal 只用**实际反馈**（每步真值是否落在区间内的误覆盖指示）调整预测阈值，忽视**估计反馈**（由 oracle conformal 方法导出的经验预测阈值）。DDCI 双反馈并行：实际反馈驱动区间的主调节，估计反馈在更新时阻尼过度的膨胀或收缩。作者报告在序列设置下获得更稳定、更窄的预测区间，同时保持近名义覆盖。NeurIPS 2026 接收。

## 解决什么问题

时序数据时间相关且分布易漂移，单反馈在线 conformal 对单步误覆盖事件过敏——一次 miss 就大幅扩区间、连击命中又过度收窄，区间宽度震荡且平均偏宽（信息量低）。DDCI 用"理论该在哪"的经验阈值给"实际在哪"的误覆盖信号装阻尼器。

## 相比前方法优势

- 反馈结构升级是主贡献：不是新覆盖目标函数，而是修正更新信号的构成，方法层面 model-agnostic、即插即用；
- 双目标兼得：更窄（信息量）与近名义覆盖（合规性）同报，而非牺牲一头；
- 有同行评议背书：NeurIPS 2026 接收（Comments 注明），在本批 arXiv 候选里证据等级最高；
- 有官方代码仓（0★、Python），方法体量小，按论文自实现门槛低。

## 局限（如实标注）

- 官方仓 0 stars、无 license、最后推送停在 2026-05-05（早于论文 v1 三个月）——代码可用性未经社区验证，授权状态需联系作者确认；
- "近名义覆盖"是实证报告而非理论保证，摘要未给有限样本覆盖界；
- 基线覆盖面（对比哪些在线 conformal 方法、哪些数据集）摘要未列，需读全文；
- oracle conformal 的经验阈值在实践中如何近似得到（oracle 本身不可得），实现细节决定成败，需读全文。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：赛题要"预测+置信区间/预测区间"时，把 DDCI 套在任意点预测器（自训模型或 TSFM）外层，以滚动验证报告区间覆盖率与平均宽度两个指标——比"±1.96σ 假设正态"的土法区间有方法论卖点；双反馈机制的直觉（一个信号管方向、一个管幅度）也好写进模型叙述。
- **Kaggle-竞赛**（reuse_cost 低）：分位数/区间类提交（如需求区间、电价区间）用 DDCI 做在线校准后处理；漂移段（赛题后期分布变化）是它的主场，可作为针对"后期区间失准"的定向修复件。

**族内定位**：库内 arxiv-2608.17333（SPACE，多元时序的自适应 conformal 椭球）占"多变量联合预测集"位；本卡占"单变量在线区间宽度的双反馈调节"位——SPACE 管"多元形状"，DDCI 管"在线宽度稳定性"，组合可用于多元区间题的两层校准；另可与时序 TTA 审计卡（arxiv-2610.12232）配套使用：先按其因果延迟协议搭管道，再上 DDCI 出区间。
