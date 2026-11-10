---
id: arxiv-2611.07784
name: "EnergyBench：日前电力预测的活体基准——每天 gate 前 30 分钟冻结信息集现场跑模型，18 个 TSFM 对打梯度提升基线（天气协变量降误差 37-51%，TSFM 零样本不敌带协变量 LGBM）"
field: [time series foundation model, 能源预测, benchmark]
directions: [数模与时序预测]
published: "2026-11-05"
maturity: demo
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv（2026-11-10 经 arXiv API 实抓摘要；基准每日实跑运行中；GitHub repo search 未见框架开源代码）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "评测协议设计范本：『gate 截止前冻结信息集并公开 + 逐序列对 seasonal-naive 池化误差 + Bradley-Terry Elo 排名 + day-bootstrap 区间』是一套防泄漏、可复算的活体评测设计，数模论文评估章节与大数据平台评测系统设计可直接引用；其 32 个实跑日的两条实测结论是现成对照弹药——NWP 数值天气协变量让 10 个 TSFM 全部降误差 37-51%（风电 64-73%），TSFM 零样本仍被带协变量的梯度提升模型压制，支撑『基础模型不喂协变量=裸奔』的论证"
    reuse_cost: 低
  - track: "Kaggle-竞赛"
    edge: "电力/新能源类赛道（日前电价、风光功率预测）的实操提示：协变量价值被定量到逐模型（37-51%），说明别裸跑 TSFM、把数值天气预报喂进去是最大的单项增益；Elo 式 Bradley-Terry 配 bootstrap 区间也可用于自建 ensemble 成员选择与稳定性评估"
    reuse_cost: 低
sources:
  - url: https://arxiv.org/abs/2611.07784
    title: "EnergyBench: a live, gate-aligned benchmark of day-ahead forecasts for European power markets（arXiv abs 页，2026-11-05 提交，摘要经 arXiv API 实抓 2026-11-10）"
    accessed: "2026-11-10"
---

# EnergyBench：让日前预测模型每天在真实 gate 期限前现场对打

> 来源：https://arxiv.org/abs/2611.07784 （v1 2026-11-05，摘要经 arXiv API 实抓 2026-11-10）。本卡内容出自本次实抓摘要，未读 PDF 全文；GitHub repo search（2026-11-10）未见框架代码，基准由组织方每日实跑。

## 是什么

欧洲日前电力市场的**活体（live）预测基准**。每个交易日 11:30 CET/CEST（SDAC gate 关闭前 30 分钟），所有参评模型对六个竞价区（BE/NL/FR/DE-LU/DK1/DK2）预测次日的 15 分钟粒度电价、风电、光伏出力与负荷。与既有 live benchmark 的差别：EnergyBench **自己运行所有模型**，在截止时刻冻结并公开同一份信息集（含三套数值天气预报模型），使 TSFM 可以在"带/不带相同天气协变量"两种条件下在真实市场期限下对比。评测：逐序列对 seasonal-naive 基线池化误差，Bradley-Terry Elo 排名配 day-bootstrap 区间。参评阵容：基线、冻结天气上的线性与梯度提升模型、11 个家族 18 个 TSFM、集成、电网运营商官方预测。前 32 个实跑日：天气协变量使 10 个有/无对照 TSFM 全部降误差 **37-51%**（风电 64-73%、光伏 48-61%）。

## 解决什么问题

能源预测模型长期只在回测与固定公开数据集上比较：回测可能用到"预测时刻尚不存在"的信息；固定测试集被反复复用、甚至已进基础模型预训练语料，对 benchmark 过拟合。EnergyBench 用"每天真实 gate 期限 + 冻结信息集"把防泄漏做进评测机制本身。

## 相比前方法优势

- **gate 对齐的活体评测**：所有模型在同一截止线、同一冻结信息集下出预测，回测式信息泄漏被机制性排除；
- **协变量对照是自带的**：同一 TSFM 带/不带 NWP 协变量成对出赛，协变量价值被逐模型定量而非泛泛而谈；
- **排名稳健**：Bradley-Terry Elo + day-bootstrap 区间替代单点指标排名，样本量小、噪声大的逐日对抗也能给出带不确定性的名次。

## 局限（如实标注）

- 框架代码未见开源（GitHub repo search 2026-11-10），团队无法本地复跑整套机制，runnable 如实标 false；
- 覆盖欧洲六个竞价区、日前市场单一任务，其他市场机制/预测任务不能直接套用其结论数字；
- 32 个实跑日样本仍短，Elo 区间宽度与长期稳定性需更多数据；TSFM 阵营是否随更强协变量利用能力翻盘，未见结论。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：两层用法——(1) 评估章节引其协议要素（冻结信息集、对 naive 基线池化、Elo+bootstrap）论证自己评测设计的防泄漏性；(2) 直接引两条实测结论做方法对照："TSFM 零样本 vs 带协变量梯度提升"的差距有权威活体数据背书，凡是自带外生变量（天气/日历）的赛题都应优先把协变量喂饱再谈模型选型。
- **Kaggle-竞赛**（reuse_cost 低）：日前电价/风光功率类赛道（GEF 系、能源竞价类）的可操作结论：数值天气预报是最强单项协变量（风电 64-73% 误差削减），Ensemble 与梯度提升不应因"基础模型时髦"而被放弃；Elo 式成员加权可搬到自己的 stacking/选择环节。
