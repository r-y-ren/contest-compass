---
id: arxiv-2610.35013
name: "MPO：长程 LLM Agent 的多尺度策略优化——turn 级锚定优势估计 + turn 级重要性采样（HF 376 赞）"
field: [LLM agents, 强化学习, 长程任务]
directions: [黑客松与数据竞赛]
published: "2026-10-26"
maturity: paper
venue_tier: arXiv
signal:
  venue: "arXiv + HuggingFace Papers（2026-10-29 HF API 实查 376 upvotes，为本次候选队列最高信号；摘要页无代码链接，GitHub 检索未找到官方实现）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "Agent 类赛题（搜索/工具调用/自动化任务）走 RL 微调路线时的信用分配配方：观察到 critic 值主要跨 turn 变化，故把优化锚定在 turn 尺度、token 间再做细粒度分配——Multiscale Advantage Estimation + turn 级重要性采样，在 4B 与 30B-A3B（MoE）两类模型上对搜索/工具/自动化任务一致超过强 RL 基线；无官方代码，需基于 verl/slime 类训练框架自实现，复用成本高，但作为'长程任务别用平铺 token 级优势'的设计原则可直接指导训练方案"
    reuse_cost: 高
sources:
  - url: https://arxiv.org/abs/2610.35013
    title: "Multiscale Policy Optimization for Long-Horizon LLM Agents（arXiv abs 页，v1 2026-10-26，Tao Ren/Hui Yang/Jia Deng 等）"
    accessed: "2026-10-29"
  - url: https://huggingface.co/papers/2610.35013
    title: "HuggingFace Papers 收录页（2026-10-29 API 实查 376 upvotes，publishedAt 2026-10-26）"
    accessed: "2026-10-29"
---

# MPO：长程 agent 的信用分配应该长在 turn 尺度上

> 来源：https://arxiv.org/abs/2610.35013 （v1 2026-10-26，Tao Ren/Hui Yang/Jia Deng/Tingyang Chen/Qiyao Wang/Shuo Tang 等，2026-10-29 经 arXiv API 实抓摘要；HuggingFace Papers 同日 API 实查 376 upvotes）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

面向**长程 LLM agent 的强化学习方法 MPO（Multiscale Policy Optimization）**。出发点是一个观察：长程 agent 以完整 assistant turn 与环境交互、逐 token 生成动作，而 critic 值的变化主要发生在 turn 之间。据此把优化锚定在 turn 尺度、在 token 之间做更细的信用分配：**Multiscale Advantage Estimation（MAE）**提供多尺度优势估计，配合 **turn 级重要性采样**对齐信用分配与策略更新的粒度。

## 解决什么问题

长程 agent 的 RL 训练里，token 级平铺的信用分配与"决策实际以 turn 为单位"错位：一个 turn 内几十个 token 共享同一个决策后果，逐 token 估计优势既贵又噪。MPO 把"在哪个粒度上记账"当作一等问题来解。

## 相比前方法优势

- 粒度对齐：turn 锚定 + token 细分，摘要报告在**搜索、工具使用、自动化任务**三类长程任务上一致超过强 RL 基线；
- 规模验证跨档：4B 稠密模型与 **30B-A3B（MoE）**都做了实验，不是只在单个小模型上成立；
- 社区信号强：HuggingFace Papers 376 upvotes（2026-10-29 实查），为本次候选队列中最高。

## 局限（如实标注）

- v1 预印本，摘要页与 HF 页均无代码链接，GitHub 检索未见官方实现——**结论暂无可运行验证**，引用具体数字前需等权重/代码释出；
- 摘要未给出对哪些 RL 基线（GRPO/PPO 类）、多大优势（具体分值）的量化对照，需读全文；
- 任务域限于搜索/工具/自动化三类，对开放域对话型 agent 的外推未证；
- turn 级锚定依赖"critic 值主要跨 turn 变化"这一观察，若任务结构不同（如单 turn 超长生成）适用性存疑。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 高）：agent 对抗/自动化类赛题若进入"微调自家 agent"环节，MPO 提供**训练配方级**指导——优势估计按 turn 锚定、token 间细分，而不是照搬 token 级 GRPO；当前只能基于开源训练框架自实现（无官方代码），适合有 RL 工程存量的队伍作为差异化训练手段；即使不复现，"先看 critic 值的方差结构再定信用粒度"这条诊断步骤零成本可搬。

**族内定位**：库内 arxiv-2609.03383（TIGPO，时序实例图策略优化）占"轨迹图结构化信用分配"位，本卡占"turn/token 多尺度信用分配"位——两者都在回答长程 agent 的 credit assignment，切分粒度不同（图结构 vs 时间尺度），互补不冲突。
