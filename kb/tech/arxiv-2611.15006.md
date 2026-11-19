---
id: arxiv-2611.15006
name: "EvoX：把 agent harness 当运行时策略——Rust 多模型运行时的三机制（动作落地/执行连续性/结果接地）+ Contrast 审计框架，691 任务-模型对 56.2% 最高成功率（无官方实现）"
field: [LLM agents, agent harness, runtime, evaluation]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-11-11"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv v1（2026-11-11，摘要经 arXiv API 实抓）；摘要未附代码链接，GitHub search（'EvoX agent runtime rust harness'等两组关键词，2026-11-19 实查）无官方实现（注意与同名进化计算库 EvoX 区分）；评测面 5 基准 × 6 基础模型 × 6 harness，含 GLM-5.3 与 Kimi K3"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "agent 工程的分层补丁思路：模型决策靠谱但执行翻车（工具调用错参、流程中断、明明没做完却宣称完成）——EvoX 主张把这三类问题从 prompt 层下沉到 runtime 层做确定性控制（动作落地、执行连续性、结果接地），赛题里 agent 输出不稳时先查'语义策略 vs 运行时策略'两层责任而不是死磕 prompt；其 Contrast 审计框架（公平约束+供应商边界请求验证+基于证据的裁定）可整体借为自建评测的防作弊层"
    reuse_cost: 中
    open_source: "无官方实现（2026-11-19 GitHub search 实查）；三机制按摘要自实现为运行时包装层"
  - track: "双创-文书与申报"
    edge: "'harness 是与模型并列的第二策略'的产品架构叙事：691 任务-模型对的证据显示 harness 增益是模型依赖的（GLM-5.3 +10.7、Kimi K3 +7.9）——申报书可据此主张'运行时层适配多家模型'的供应商解耦优势，且'无记忆、无进化、无扩展'的纯运行时收益口径在成本表里干净可核"
    reuse_cost: 中
    open_source: "无官方实现；指标口径可引用论文自述"
sources:
  - url: https://arxiv.org/abs/2611.15006
    title: "EvoX: Rethinking the Agent Harness as a Runtime Policy（arXiv abs 页 v1，2026-11-11，摘要经 arXiv API 实抓）"
    accessed: "2026-11-19"
---

# EvoX：harness 不是脚手架，是第二策略——模型管"想什么"，运行时管"落地成不成"

> 来源：https://arxiv.org/abs/2611.15006 （v1 2026-11-11，摘要经 arXiv API 实抓）；GitHub search 无官方实现（2026-11-19 实查，与同名进化计算库 EvoX 区分）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

**"运行时策略（Operational Policy）"定位的 agent 运行时**。诊断：模型决策貌似合理，执行却翻车——工具调用错配、流程中断、未完成却宣称完成。EvoX（Rust 实现、多模型）主张 harness 是与基础模型"语义策略"互补的**第二策略**，用三个机制把模型意图落到确定执行：**动作实现（Action Realization，修工具调用错配）**、**执行连续性（Execution Continuity，接住中断的工作流）**、**结果接地（Outcome Grounding，验证完成声明）**。配套 **Contrast** 审计框架：显式公平约束、供应商边界的请求验证、基于证据的裁定——评测 harness 时不压制其原生行为。官方口径：5 基准 × 6 模型 × 6 harness，691 个共同任务-模型对上 56.2% 最高成功率，较其余五个 harness 均值 +3.0pp；对 GLM-5.3 +10.7、Kimi K3 +7.9；且零记忆、零进化、零扩展。

## 解决什么问题

harness 评测的方法学混乱（各家 harness 在不同模型上表现颠簸，且评测时容易顺手优化）+ 执行层的系统性失败没有归属层。EvoX 给出两个贡献：把执行可靠性工程定位到 runtime 层（不靠 prompt 补丁、不靠记忆/进化魔法），以及 Contrast 的公平 harness 对比协议。

## 相比前方法优势

- **层次定位清晰**：库内 harness 线已有搜索式（HarnessFlow 的 MCTS 搜索、MetaCaster 的元 harness 优化、ActiveSaddler 的课程调度）与工程经验式（CastClaw），本卡占"运行时=固定确定性策略"一格——搜索答案 vs 直接给定运行时规则，正交；
- **模型依赖性证据**：+10.7（GLM-5.3）对 +7.9（Kimi K3）的分化直接回答"harness 值不值得为特定模型调"；
- **Contrast 可独立复用**：公平约束+边界验证+证据裁定的三件套是任何 agent 横评的自查清单；
- **归因干净**："无记忆/进化/扩展"前提把增益单独归给运行时控制。

## 局限（如实标注）

- 无官方实现（2026-11-19 GitHub search 实查），Rust 运行时三机制需从零自建；
- +3.0pp 的总体均值增益中等，主卖点在特定模型上的大幅增益——换模型后收益未知；
- Rust 栈对赛题队伍门槛偏高，机制思想需翻译成 Python 包装层；
- 56.2% 的绝对成功率说明执行翻车仍是常态，runtime 策略是减损不是根治。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：把三机制当自建 agent 管线的运行时清单——工具调用包装层（参数校验+重试落地）、断流续跑（检查点+恢复）、完成声明核验（对照任务产物而非模型自述）；Contrast 三件套借为队内评测协议防"评测时偷偷优化"。
- **双创-文书与申报**（reuse_cost 中）：多模型接入的产品申报用"语义策略+运行时策略"双层架构叙事，引用其模型依赖性分化数字论证运行时层的必要性。
