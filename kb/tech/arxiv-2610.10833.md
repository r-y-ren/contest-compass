---
id: arxiv-2610.10833
name: "On the Clock：时间预算下的 LLM agent——只看提示守不住 deadline，暴露时钟+硬截止才行（但守时≠用好时间）"
field: [LLM agents, 资源感知, 评测]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-07"
maturity: paper
venue_tier: workshop
reproducibility_level: low
signal:
  venue: "NeurIPS 2026 Workshop on Resource-Aware Agentic AI（接收，Comments 原文 'Accepted at the NeurIPS 2026 Workshop on Resource-Aware Agentic AI. 23 pages'）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "Kaggle/MLE 类赛题天然带硬性运行时限（提交脚本的墙钟上限），论文验证的最小改造恰好是 harness 层可自实现的：把计时信息显式注入 agent 状态 + 硬截止强制机制，即让大模型（Qwen3.6-27B）的时间遵从显著改善、再加截止强制进一步收紧——MLE-Bench Lite 本身就是 Kaggle 竞赛代理基准，'我们的 agent 有时间预算感知'是评审处稀缺且零模型成本的差异化；负结果同样值钱：守住了预算的 agent 会用重复动作填满多余时间（守时≠用时更好），直接校准'多给时间就多跑迭代'的赛期直觉"
    reuse_cost: "低"
    open_source: "无官方代码（abs 页 Comments 仅会议接收信息，2026-10-11 实抓）；harness 机制（时钟暴露+截止强制）自实现门槛低，评测环境 MLE-Bench Lite 与 Jericho（Zork I）均公开可搭"
  - track: "双创-文书与申报"
    edge: "资源感知 agent 产品的成本治理章节论据：'时间遵从（adherence）'与'时间有效利用（productive allocation）'是两个独立能力——提示层预算约束不可靠、harness 层时钟暴露+硬截止可控有效、RL 层（GRPO 预算感知奖励）遵从近满分但任务收益不稳（Zork 近完美泛化到未见预算，MLE-Bench 无增益，多预算训练塌缩到最短预算策略）；这套分层结论给'agent 运行成本可控'的机制设计提供了带实验支撑的论证结构"
    reuse_cost: "中"
    open_source: "无官方代码；方法叙述 arXiv:2610.10833（NeurIPS 2026 Resource-Aware Agentic AI workshop 口径）"
sources:
  - url: https://arxiv.org/abs/2610.10833
    title: "On the Clock: Towards Punctual and Productive Time-Budgeted AI Agents（arXiv abs 页，v1 2026-10-07，Aaron Wang/Neelabh Madan/Vlad Sobal/Matthew Trager/Michael Kleinman/Elman Mansimov/Wei Xia/Stefano Soatto，cs.AI+cs.LG，Comments：NeurIPS 2026 Resource-Aware Agentic AI workshop 接收，无代码链接）"
    accessed: "2026-10-11"
---

# On the Clock：agent 的时间预算感知是 harness 问题，不是提示问题——且守时不等于用好时间

> 来源：https://arxiv.org/abs/2610.10833 （v1 2026-10-07，2026-10-11 实抓摘要页；作者含 Stefano Soatto 团队）。全部实验数字出自本次抓取的摘要口径，未读 23 页全文。

## 是什么

系统研究"小模型 LLM agent 能否在显式墙钟预算下工作"：既尊重运行时限（punctual），又把可用时间用出收益（productive）。评测设两个代理场景：Qwen3.6-27B 跑 MLE-Bench Lite 5 个竞赛任务、Qwen3-4B 玩 Zork I（Jericho）——都是"多给计算时间真能变好"的 agentic 基准。三层发现：

1. **只把预算写进提示 = 守不住**：失败归因三条——时间感知弱、对动作时长的预估差、没有"剩余时间→策略"的映射；
2. **两个干预**：(a) harness 机制（暴露计时信息 + 强制 deadline）使大模型时间遵从显著改善，加硬截止进一步收紧；(b) RL（GRPO 预算感知奖励）在 Zork I 上遵从近满分且泛化到未见预算，但在 MLE-Bench 无性能增益；
3. **核心负结果**：守住了预算的 agent 并不把多余时间转化为更好成绩——用重复动作填满；多预算 GRPO 训练塌缩向最短预算策略。作者把"时间遵从 vs 时间有效利用之间的鸿沟"列为该方向的核心开放问题。

## 解决什么问题

真实部署的 agent 都有墙钟约束（API 预算、赛题时限、生产 SLA），但 agent 研究几乎默认"想到才算完"，没人系统回答"agent 会不会看表、看了表会不会用"。本文给出该问题的第一组分层层级证据与可操作干预清单。

## 相比前方法优势

- 问题提出本身稀缺：资源感知 agent 方向多谈 token/算力成本，墙钟时间维度几乎无人测；
- 干预分层干净：提示层（无效）→ harness 层（有效、零训练成本）→ RL 层（遵从好但任务收益不稳），给实践者一条清晰的采用路径——先做 harness 层就拿到大部分收益；
- 负结果有信息量："守时 agent 用重复动作填时间"是所有时间预算 agent 设计都要规避的坑，多预算训练塌缩是 RL 路线的明确警示。

## 局限（如实标注）

- 无官方代码（abs 页无链接，2026-10-11 实抓）；harness 机制细节需读全文自行实现（好在机制本身简单）；
- 仅两模型（27B/4B）两环境（MLE-Bench Lite/Zork I），向更强模型与生产任务外推未证；
- GRPO 结论在 4B 上取得，赛队不可复现该层；"productive allocation"问题论文自述未解决——本卡价值在诊断与 harness 层干预，不在终解；
- workshop 接收（非主会），23 页 v1 未经主会评审周期。

## 如何用于比赛（比赛映射展开）

1. **黑客松-数据与算法（Kaggle/MLE 型赛题）**：把"时钟暴露+硬截止"写进自己的 agent harness（对齐论文验证过的最小改造），并在技术报告里展示预算遵从曲线（动作数-时间序列图）；同时对"剩余时间"做策略分档（论文证明 agent 自己学不会这个映射，需显式给）。相比"跑到超时被判 0"或"提前躺平"的队伍是实打实的稳定性差异。reuse_cost 低：无需论文代码，MLE-Bench Lite 与 Jericho 环境公开可自测。
2. **双创-文书与申报（agent 产品成本治理）**：申报书"运行成本可控"章节按论文的三层结构写：为什么纯提示限流不可靠（实验归因三条）、为什么 harness 层时钟/截止是可控机制、为什么不上 RL（遵从≠收益的实验证据）。每个论点都有论文实验背书，注明 NeurIPS 2026 workshop 预印本口径。reuse_cost 中：转译为产品机制叙述，不需复现。
