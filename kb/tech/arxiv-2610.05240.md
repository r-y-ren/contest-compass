---
id: arxiv-2610.05240
name: "Pythia：多模态时序的基础世界模型（JEPA 联合嵌入预测架构，MUSE 榜 MASE/WSQL 双降 6.26%/5.00%，暂无代码）"
field: [time series foundation model, 世界模型, 多模态时序]
directions: [数模与时序预测]
published: "2026-10-05"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv（技术报告口径）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "『文本信息怎么进时序模型』的前沿路线图：数模与时序赛题常见『实体描述/事件文本 + 数值协变量 + 序列』混合数据（政策事件、设备工况描述、新闻情绪），Pythia 给出当前最完整的架构答案——JEPA 式联合嵌入预测学上下文条件隐动力学，stop-gradient 数值参考做修正，概率解码器与冻结预测表征解耦；MUSE 榜 Pythia-Tiny MASE 0.6879/WSQL 0.4269，对榜上最强模型错误降 6.26%/5.00%（作者自报）；暂无代码，用途是方案叙事与架构对标，不承诺复现"
    reuse_cost: 高
    open_source: "无官方代码（GitHub 检索未见，2026-10-20 API 实查）；MUSE 基准与被对比模型部分公开，可按论文配方自研小规模验证"
sources:
  - url: https://arxiv.org/abs/2610.05240
    title: "Pythia: Toward Foundation World Models for Multimodal Time Series（arXiv abs 页，Xilin Dai/Hongzhou Chen/Yifan Hu/Yiding Liu/Zewei Dong/Jiang-Ming Yang，摘要全文；Comments 注明 Technical Report，2026-10-20 实抓）"
    accessed: "2026-10-20"
---

# Pythia：文本+协变量+序列一起喂的多模态时序世界模型，MUSE 榜双降错误

> 来源：https://arxiv.org/abs/2610.05240 （abs 页摘要与 Comments，2026-10-20 实抓；Xilin Dai、Hongzhou Chen、Yifan Hu、Yiding Liu、Zewei Dong、Jiang-Ming Yang；Comments 注明 Technical Report）。GitHub 检索未见官方代码（2026-10-20 API 实查）。本卡出自本次抓取的摘要页，未读全文。

## 是什么

面向多模态时序的**基础世界模型**：以联合嵌入预测架构（JEPA 系）跨数据集学习**上下文条件下的隐空间动力学**——文本上下文（实体描述）与辅助观测（事件、协变量）作为条件进入预测表征；用 **stop-gradient 的数值参考**对预测的未来状态做上下文修正；另设**概率解码器**适配冻结的预测表征与观测历史，把"世界模型预训练"与"观测空间预测"解耦。结果（摘要自报）：MUSE 基准上 Pythia-Tiny 的 MASE 0.6879、WSQL 0.4269，比公开 MUSE 榜最强模型错误降 **6.26% / 5.00%**；受控实验支持两点设计结论——预测表征学习与概率读出应当分离；实体描述、事件、协变量的贡献互补。

## 解决什么问题

时序基础模型多为纯数值输入，现实预测任务的上下文里有大量文本（设备是什么型号、发生了什么事件、政策怎么变）。Pythia 探索"可复用的多模态预测表征"：让世界模型先在多域数据上学"给定上下文，隐状态怎么演化"，具体预测任务只训轻量读出头。

## 相比前方法优势

- **多模态进隐动力学而非拼接输入**：文本经联合嵌入进入状态演化，与"文本 embedding 拼特征"的朴素做法机制不同；
- **预训练与读出解耦**：冻结世界模型 + 概率解码器适配，跨任务迁移成本结构与 LLM 微调范式对齐；
- **有公开榜对照**：MUSE 榜相对提升口径（6.26%/5.00%）给了可核查锚点，且是 Tiny 档模型达成。

## 局限（如实标注）

- **无官方代码与权重**（2026-10-20 GitHub 检索无果），复现需从论文配方自研，学生队成本高；
- Technical Report 自述口径：MUSE 榜对比对象、"最强模型"的配置与公平性（上下文长度、输入模态是否对齐）需读全文核实；
- 多模态收益的分解（文本到底贡献几个点）在摘要只有定性"互补"结论；
- 预印本未挂 venue，作者机构 abs 页未列；世界模型叙事的泛化边界（跨域零样本能力）未在摘要给出数字。

## 如何用于比赛（比赛映射展开）

1. **数模-预测与评估（含文本上下文的预测题的方案设计对标）**：当赛题数据带事件/描述文本时，Pythia 是"多模态进预测"的架构参照——可实现的降配版：文本经 LLM/embedding 提取结构化事件特征 + 数值协变量一起进预测模型，论文里引 Pythia 说明该路线的前沿形态与量化潜力（注明预印本作者自报与无代码现状）。reuse_cost 高：作为路线与对标数字引用，不承诺复现；若赛期充裕可按"概率读出与表征分离"思想自建轻量版。
