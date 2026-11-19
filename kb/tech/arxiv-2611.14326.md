---
id: arxiv-2611.14326
name: "FGSE：证伪闸门式的 agent 自进化——每条经验教训先当假设做迁移/证伪/回归探针测试再决定入册，有害更新降到 3.6%（无官方实现）"
field: [LLM agents, self-evolution, memory admission, verification]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-11-10"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv v1（2026-11-10，摘要经 arXiv API 实抓）；摘要未附代码链接，GitHub search（'falsification-gated self-evolution agent'/'FGSE falsification lessons agent memory'两组关键词，2026-11-19 实查）无官方实现"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "长程 agent 任务（web/app/工具调用）的经验沉淀守则：FGSE 的'教训=带前提条件+行为变更+预期效果+验证器的结构化假设，先在临时状态试跑迁移/证伪/回归三类探针，再按增益与风险决定 commit/refine/reject'流程，是任何自写 agent 记忆系统都能直接照抄的准入协议——其指标'证伪失败 5.0%、回归损伤 1.3%、有害更新 3.6%'给了工程上的目标线；WebArena 39.8/AppWorld 78.8 的任务面说明协议在真实基准上不掉分"
    reuse_cost: 中
    open_source: "无官方实现（2026-11-19 GitHub search 实查）；准入协议按摘要自实现，探针机制需自行搭验证器"
  - track: "双创-文书与申报"
    edge: "agent 产品的可靠性卖点：'经验教训不是写入即生效，而是先当科学假设证伪后再入册'——把记忆-induced 退化（agent 被坏教训带偏、连本来会做的题都做错）量化到 3.6% 有害更新率，是申报书里'自进化系统的安全机制'一节的现成方法论与数字素材"
    reuse_cost: 中
    open_source: "无官方实现；框架思路可引用论文自述指标"
sources:
  - url: https://arxiv.org/abs/2611.14326
    title: "When Should Agents Remember? Falsification-Gated Self-Evolution for LLM Agents（arXiv abs 页 v1，2026-11-10，摘要经 arXiv API 实抓）"
    accessed: "2026-11-19"
---

# FGSE：agent 的"经验教训"不能写入即生效——先证伪，再入册

> 来源：https://arxiv.org/abs/2611.14326 （v1 2026-11-10，摘要经 arXiv API 实抓）；GitHub search 无官方实现（2026-11-19 实查）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

**Falsification-Gated Self-Evolution（FGSE）**：回答"经验衍生的行为更新何时该进入 agent 持久状态"。核心主张：局部成功不是可复用、安全知识的可靠信号——现役自改进机制把 episode 教训直接写进记忆，坏教训由此混入。FGSE 把每条候选教训表示为**结构化假设**（显式前提条件、行为变更、预期效果、验证器），只在**临时状态**上应用，依次跑三类探针：目标迁移、证伪、归档回归探针，按实测增益与风险决定 commit / refine / reject。官方口径：WebArena 39.8 成功率、AppWorld 78.8 平均完成率、τ-Retail/τ-Airline 0.724/0.487 Pass¹，同时把证伪失败压到 5.0%、回归损伤 1.3%、有害提交 3.6%。

## 解决什么问题

自进化 agent 的隐性债务：**memory-induced 退化**——一条从单次成功提炼的教训，在不满足其隐含前提的新任务上被误用，agent 连本来能做对的任务都做错（库内 2611.13412 "Bursts That Outlast Themselves" 记录了同类退化现象，本卡给出准入侧的解法）。FGSE 把"教训入库"从事后后悔改成事前审查。

## 相比前方法优势

- **准入闸门是探针实测而非启发式规则**：迁移（换个任务还灵吗）、证伪（造反例打破它）、回归（老任务会不会被带坏）三探针直接量化教训的泛化与风险；
- **临时状态试用**：教训先在沙盒状态验证再入持久层，坏教训不污染正式记忆；
- **诚实的风险核算**：有害提交 3.6% 意味着闸门不是 100%，但相比"直接写入"是量级改善；
- **与库内记忆治理卡分工明确**：2610.11188 管的是记忆条目的权限/泄漏准入，本卡管的是行为教训的任务性能准入——两道闸门管两种风险。

## 局限（如实标注）

- 无官方实现（2026-11-19 GitHub search 实查），三类探针需要任务环境自配验证器，复现成本高；
- "验证器"假设任务域可自动判分——开放域任务（无明确对错）上探针机制失效；
- 探针本身消耗任务尝试次数（算力/配额），摘要未报准入流程的额外成本；
- 数字为论文自报单点，无第三方复现。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：自建 agent 的记忆/技能沉淀模块照抄其协议：教训结构化（前提/变更/预期/验证器）→ 临时态试跑三探针 → 按增益风险三选一；评审问"你们怎么防止 agent 被坏经验带偏"时，闸门协议+三条风险数字即是答案。
- **双创-文书与申报**（reuse_cost 中）：agent 产品申报的可靠性章节可直接引用其退化量化口径（证伪失败 5.0%/回归损伤 1.3%/有害提交 3.6%）作为自进化系统安全机制的设计对标。
