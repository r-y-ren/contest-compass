---
id: arxiv-2610.35767
name: "Free to Look：三个极简 harness 诊断力反超五个人工精雕 RCA agent（PR@1 65-77% vs 16-53%），成本-时间 Pareto 全被简单 harness 占据"
field: [LLM agents, 根因分析, harness 工程]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-26"
maturity: paper
venue_tier: arXiv
signal:
  venue: "arXiv（12 页）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "运维/排障类赛题的 agent 起手式：先用'一次读全证据包'的单调用 harness 起步（三个中档模型上 PR@1 65-77%），打掉'必须造多角色多阶段流水线'的思维定势——被测的五个已发表 RCA agent 反而全部落后（16-53%），且其写死的调用序列会跳过决定性证据；仅在简单 harness 证据不足时才升级多轮"
    reuse_cost: 低
  - track: "双创-文书与申报"
    edge: "技术方案书模型/框架选型论证的三条实测结论：更强模型主要提升可靠性、多轮 harness 主要提升能力上限、更高推理档位精度只动几个点却最高 7 倍耗时——可直接写进选型章节作为'把预算花在哪'的依据，避免评审问'为什么不上多智能体/满血推理'时无数据可答"
    reuse_cost: 低
sources:
  - url: https://arxiv.org/abs/2610.35767
    title: "Free to Look, Free to Reason: Simple LLM Harnesses Outdiagnose Hand-Crafted Root Cause Analysis Agents（arXiv abs 页，v1 2026-10-26，Tingzhu Bi/Xun Zhang/Jinglin Li/Ping Wang/Meng Ma，Comments：12 页）"
    accessed: "2026-10-29"
---

# Free to Look：微服务根因分析里，"让模型自由看"打赢"手把手教模型看"

> 来源：https://arxiv.org/abs/2610.35767 （v1 2026-10-26，Tingzhu Bi/Xun Zhang/Jinglin Li/Ping Wang/Meng Ma，12 页；2026-10-29 经 arXiv API 实抓摘要）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

对微服务故障**根因分析（RCA）LLM agent 的 harness 受控比较**。当前已发表 RCA agent 普遍手工精雕调查流程（标准作业程序、固定阶段、角色分工 agent），且各在自家数据、缺基线下评测——没人验证过这套设计是否真比"让一个强模型自由调查"强。本文在 **RCAtlas**（八个公开数据集的 90 个验证案例）上，对比三种不预设任何模型调用的简单 harness（对证据包的一次性调用、SQL agent、Codex 编码 agent）与五个已发表 RCA agent 及统计/因果方法，跨六个模型、三个推理档位。

## 解决什么问题

回答"**agent 的调查流程该不该由人写死**"：答案是写死的处方在系统性帮倒忙——已发表 agent 把模型十分之一到全部的调用固定在程序里，案例研究显示这些处方会跳过决定性证据。

## 相比前方法优势

- 结论碾压且跨模型一致：简单 harness 在三个中档模型上 PR@1 65-77%，已发表 agent 16-53%，非 LLM 方法 6-39%——凡两族都跑过的模型上简单 harness 全胜；
- 成本-时间 Pareto 被简单 harness 全部占据：在 accuracy 超过最强非 LLM 方法的运行里，每个 Pareto 最优运行都来自简单 harness；
- 把三个杠杆拆开了：更强模型→主要提升**可靠性**；多轮 harness→主要提升**能力上限**；更高推理档→精度只动几个点、耗时最高 7 倍——选型时不必再混为一谈。

## 局限（如实标注）

- 无代码释出（摘要页无链接），RCAtlas 是否公开需读全文确认，复现依赖论文细节；
- 65-77% 出自"三个中档模型"，最强/最弱模型上的表现摘要未给全；
- 场景限于微服务 RCA，"简单 harness 更好"能否推广到证据分散更严重的任务（如长文档审阅）未证——摘要只支持 RCA 域内结论；
- 五个已发表 agent 的复现保真度（是否用其最优配置）需读全文核对。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：排障/巡检/数据分析类赛题的 agent 迭代路线改成"先单调用读全量证据 → 不够再上多轮"，把省下的开发时间花在证据包组装（把对的材料一次性喂进去）而不是流程编排上；"更强模型买可靠性、多轮买上限、推理档别乱加"三条直接当预算分配规则。
- **双创-文书与申报**（reuse_cost 低）：方案书里用本卡数据回应"为何不用多智能体架构"——90 案例、六模型受控比较显示手写流程反落后，引用成本仅一段文字。

**族内定位**：库内 arxiv-2610.36114（Context Is a Pipeline，同队列同日）测的是"harness 把数据弄丢"，本卡测的是"harness 把流程写死"——一软一硬两种 harness 过度工程，搭配 arxiv-2610.11655（Harness Evolution Hits a Ceiling，harness 进化到顶该转权重训练）构成"harness 该建到哪、错在哪、何时停"三件套。
