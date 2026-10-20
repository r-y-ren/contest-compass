---
id: arxiv-2610.11213
name: "AliO：长期时序预测的输出对齐训练（同时间戳预测不随输入滞后漂移，TAM 新指标，NeurIPS 2025，官方代码在）"
field: [time series forecasting, 预测可靠性, 训练目标]
directions: [数模与时序预测]
published: "2026-10-05"
maturity: paper
venue_tier: CCF-A
reproducibility_level: high
signal:
  venue: "arXiv（Comments 注明 NeurIPS 2025，46 页）"
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "预测『稳定性/一致性』维度的现成论文章节：SOTA 长期预测模型对同一时间戳的预测会随输入窗口滞后而漂移（output alignment 低），AliO 用时/频域对齐约束训练修复之——TAM 提升 58.2%、精度至多 +27.5%（作者自报）；数模论文写『模型可靠性分析』时 TAM 是现成新指标（比 MSE 多一个评审没见过的口径），AliO 是现成改进手段，NeurIPS 2025 背书引用无压力"
    reuse_cost: 低
    open_source: "https://github.com/eai-lab/AliO（官方仓，11 stars，2026-10-19 仍在推送）"
  - track: "黑客松-数据与算法"
    edge: "长程预测赛题（电力/交通/气象）的防抖动演示点：『同一天的预测值随输入窗口滚动而跳动』是评审可现场复现的痛点，接 AliO 后输出对齐让『同一时刻预测不漂移』可现场可视对比；TAM 数字可直接进答辩页"
    reuse_cost: 低
    open_source: "https://github.com/eai-lab/AliO（官方实现即插即用于主流 LTSF 模型）"
sources:
  - url: https://arxiv.org/abs/2610.11213
    title: "AliO: Output Alignment Matters in Long-Term Time Series Forecasing（arXiv abs 页，Kwangryeol Park/Jaeho Kim/Seulki Lee，摘要全文；Comments：NeurIPS 2025，46 页，2026-10-20 实抓）"
    accessed: "2026-10-20"
  - url: https://github.com/eai-lab/AliO
    title: "eai-lab/AliO 官方代码仓（GitHub 搜索实查：11 stars，描述标注 NeurIPS 2025，2026-10-19 最后推送）"
    accessed: "2026-10-20"
---

# AliO：长期预测模型对同一时刻的答案应该一致——输出对齐训练 + TAM 指标

> 来源：https://arxiv.org/abs/2610.11213 （abs 页摘要与 Comments，2026-10-20 实抓；Kwangryeol Park、Jaeho Kim、Seulki Lee；NeurIPS 2025，46 页）。官方代码 https://github.com/eai-lab/AliO （GitHub API 搜索实查，2026-10-20）。本卡出自本次抓取的摘要页与仓库元数据，未读全文。

## 是什么

长期时序预测（LTSF）的训练改进与评测新维度：作者观察到 SOTA LTSF 模型普遍**输出对齐性差**——同一目标时间戳的预测值，会随输入序列的滞后位置不同而明显波动（模型对"现在几点"过度敏感），损害可靠性。**AliO** 在训练中加入时域与频域的输出对齐约束，压缩同一时间戳跨滞后输入的预测差异；并提出 **TAM（Time Alignment Metric）**量化这种对齐性——现有 MSE 只度量"预测离真值多远"，TAM 度量"预测彼此一致吗"。结果（摘要自报）：TAM 提升至多 58.2%，同时精度保持或提升（至多 +27.5%）。

## 解决什么问题

滚动预测场景（每天用最新窗口重预测未来）中，模型对同一天给出的值反复跳动，业务侧无法信任单次输出；根因是训练目标只对齐"预测 vs 真值"，从不对齐"预测 vs 预测"。AliO 把跨窗口一致性本身变成训练目标。

## 相比前方法优势

- **问题定位新**：LTSF 文献集中在精度，输出对齐（稳定性）是被忽视的独立失败模式，有明确的度量（TAM）与修复（AliO）闭环；
- **即插即用**：作为训练目标补丁叠加在主流 LTSF 模型上，不换架构；
- **双赢口径**：对齐提升不牺牲精度反有增益（作者自报），不是"拿精度换稳定"的折衷。

## 局限（如实标注）

- 对齐约束的收益以滚动重预测场景为前提，单次固定窗口预测（数模提交一次答案的情形）中 TAM 的意义弱化，需改造为"多输入配置一致性"口径；
- 时/频域对齐权重为超参，跨域最优配置需自行调；46 页正文细节（哪些骨干受益最大）未读不背书；
- NeurIPS 2025 为 Comments 自述与官方仓一致（2026-10-20 实查），可信但引用时注明正式版本出处。

## 如何用于比赛（比赛映射展开）

1. **数模-预测与评估（预测类赛题的稳健性章节 + 加分指标）**：两步走——(a) 诊断：对自家模型做 TAM 测量（官方代码有实现），若对齐性差就在论文里展示"同一天预测随窗口漂移"的图，这是评审能直观理解的缺陷证据；(b) 改进：接 AliO 训练目标修复，前后 TAM/精度对照成消融表。比堆模型结构创新的边际收益更高，且"可靠性"叙事契合数模评审口味。reuse_cost 低：官方代码即插即用。
2. **黑客松-数据与算法（长程预测赛题）**：把"输出对齐"做成现场演示——同一目标时刻在不同输入窗口下的预测曲线叠加图，AliO 前后对比，直接回应"你们的预测每次跑都不一样"类质疑。reuse_cost 低。
