---
id: arxiv-2610.07625
name: "Stateless Language Agents：有状态搜索 + 无状态 agent——harness 持有研究状态，10 亿 token 预算下省 84%"
field: [LLM agents, agent harness, 自动化研究]
directions: [黑客松与数据竞赛]
published: "2026-10-06"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv（32 页，Stanford Kunle Olukotun 组 18 人）+ HuggingFace Papers（18 upvotes）"
  runnable: false
competition_fit:
  - track: "Kaggle-竞赛"
    edge: "自动探索/自动调参管线的 harness 架构范式：研究状态（候选解+实测结果）放 harness、每次调用重建角色化上下文，agent 不背对话史——『无状态化』直接消灭复述历史/重复工作/空转烧 token 三类长程失败；10 亿 token 预算下每个任务最优且以少 84% 的 token 达到最强基线的最终性能，按 token 计费的学生队这是直接的成本差"
    reuse_cost: 中
    open_source: "官方仓 Alex-q-z/stateless-language-agents 为空壳（仅空 assets 目录，API 实查 2026-10-13）；架构模式按论文自实现"
  - track: "黑客松-数据与算法"
    edge: "多 agent 自动化系统的分工结构现成可抄：stateless Advisor 读 harness 证据摘要、跨搜索方向分派具体实验给并行 Worker，Advisor 只消耗 <0.6% token；『短评测预算会误判研究系统』的实证是评审答辩与故障分析框架"
    reuse_cost: 中
    open_source: "无可用官方代码；按论文模式自建 Advisor-Worker harness"
sources:
  - url: https://arxiv.org/abs/2610.07625
    title: "Stateless Language Agents: Scaling Long-Horizon Automated Research（arXiv abs 页，v1 2026-10-06，Qizheng Zhang 等 18 人含 Kunle Olukotun，Comments：32 pages，无代码链接）"
    accessed: "2026-10-13"
  - url: https://github.com/Alex-q-z/stateless-language-agents
    title: "同名 GitHub 仓（GitHub API 实查 2026-10-13：3 stars/0 forks，仅含空 assets 目录，无语言无 license——空壳占位，无可用实现）"
    accessed: "2026-10-13"
---

# Stateless Language Agents：把"状态"从对话里拿出来

> 来源：https://arxiv.org/abs/2610.07625 （v1 2026-10-06，Stanford Qizheng Zhang 等 18 人含 Kunle Olukotun，32 页；HF Papers 18 upvotes，2026-10-13 实抓）+ 官方仓 https://github.com/Alex-q-z/stateless-language-agents （API 实查为空壳）。本卡内容出自摘要页，未读 PDF 全文。

## 是什么

自动化研究系统跑长程任务时，"更多推理"并不自动等于"更多进展"：agent 复述越来越长的历史、彼此重复劳动、实验早已停止而 token 消耗不止。论文把根子追到两个设计选择：**研究状态存在哪里**、**下一步试什么由谁决定**。答案即 Stateless Language Agents（SLA）原则——**有状态的搜索，无状态的 agent**：任何 agent 都不携带对话跨调用；研究状态（候选解与实测结果）由 harness 持有，每次调用为该角色**重建全新上下文**——"每个 agent 看到什么"成为显式设计决策，而非随运行膨胀的历史。实现为 SLA 框架：无状态 Advisor 阅读 harness 汇总的跨方向证据，把具体实验分派给并行 Workers。

## 解决什么问题

长程 agent 系统的三类烧钱失败（复述历史/重复工作/空转）在短预算评测里测不出来。SLA 用架构把这三类失败连根拔掉：状态在 harness 里可去重、可检索、可摘要，agent 上下文每次从零构造，天然无历史包袱。

## 相比前方法优势

- **全面胜出**：软件工程、内核优化、算法设计三类任务、最高 **10 亿 token** 预算、对比三个近期框架——每个任务都是最优最终结果；
- **成本差量化**：以**少 84% 的 token** 达到最强内核优化基线的最终性能——对按量计费的使用者是最硬的卖点；
- **成本结构**：Advisor 只消耗 <0.6% token（协调便宜，预算花在 Worker 实验上）；消融证明"聚焦上下文"与"显式任务分派"各自有效且在全程运行中效果**复合**；
- **方法论贡献**：证明短预算评测会系统性误判研究系统及其组件——对一切"agent 系统对比实验"的预算设计提出警告。

## 局限（如实标注）

- **无可用代码**：官方同名仓是空壳（仅空 assets 目录，2026-10-13 API 实查），复现=按论文自建整套 harness——中等工作量但无现成依赖；
- v1 预印本无 venue（32 页），三个任务域（SWE/内核/算法）偏代码与优化，其他域（写作、数据分析）外推性未证；
- "harness 持有状态"意味着状态管理逻辑（摘要、去重、方向排序）全在框架侧——这些细节摘要未展开，恰是复现难点；
- 对比框架名单与配置摘要未列全，胜出幅度对具体对手的敏感性未知；
- 18 作者大组（Stanford），算力与工程资源远超学生队，直接复现其预算规模不现实。

## 如何用于比赛（比赛映射展开）

- **Kaggle-竞赛**（reuse_cost 中）：搭"自动改代码-跑分-记录"循环时按 SLA 架构：候选方案与实测分数存 harness（一个 JSON/SQLite 就够），每次让 LLM 只看"当前最优解 + 失败教训摘要 + 下一个任务"——上下文恒定大小，长跑不发散；84% token 节省直接等于 API 预算多出 6 倍尝试次数。
- **黑客松-数据与算法**（reuse_cost 中）：Advisor-Worker 分工（便宜模型做协调、贵模型做执行）是可现场搭建的演示结构；"无状态化"叙事（可去重、可审计、可断点续跑）在答辩里是清晰的工程差异化。

**族内定位**：库内 agent harness 卡偏单 agent 运行时或监控（OnTrack 等）；本卡占"长程研究系统的状态所有权"位——与 AgentTune（生命周期底座）互补：一个管状态与分派，一个管训练与审计。
