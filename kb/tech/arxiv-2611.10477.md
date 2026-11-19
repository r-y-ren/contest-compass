---
id: arxiv-2611.10477
name: "PatternBloom：agentic RAG 从'检索内容'转向'检索逻辑'——RL 轨迹蒸馏成图模式记忆（类型抽象推理骨架）+模式增强奖励二段训练，7B 胜 27 基线 +15.0 OOD EM（官方仓可跑）"
field: [agentic RAG, reinforcement learning, knowledge distillation, multi-hop QA]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-11-07"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv v1（2026-11-07，摘要经 arXiv API 实抓）+ 官方仓 EllenYiGe/PatternBloom（GitHub API 实查：0 stars，2026-11-06 创建、2026-11-06 推送，Python；摘要'we release our code at'指向本仓）"
  stars: 0
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "多跳问答/RAG 赛题的涨点路径：把'怎么推理'外化成可检索的模式库而不是每次现场重推——OOD +15.0 EM 的量级在多跳 QA 榜上是从中游到头部的跨度，且增益随推理深度复合（越难的题越吃模式复用）；7B 模型即可，官方仓两段 RL 管线（信息密度奖励→蒸馏→模式增强奖励）齐备可复现"
    reuse_cost: 中
    open_source: "github.com/EllenYiGe/PatternBloom（摘要给出的官方实现仓）"
  - track: "双创-文书与申报"
    edge: "'检索的单元从内容升维到逻辑'是知识库产品申报里辨识度极高的架构叙事：声明性知识（读什么）与程序性知识（怎么读）分库治理——模式库跨模型可迁移，意味着知识资产沉淀在系统而非某个大模型订阅上，正中'自主可控/资产沉淀'类评审关切"
    reuse_cost: 中
    open_source: "github.com/EllenYiGe/PatternBloom"
sources:
  - url: https://arxiv.org/abs/2611.10477
    title: "PatternBloom: Empowering Agentic RAG with Externalized RL-Distilled Graph Patterns（arXiv abs 页 v1，2026-11-07，摘要经 arXiv API 实抓）"
    accessed: "2026-11-19"
  - url: https://github.com/EllenYiGe/PatternBloom
    title: "官方代码仓（GitHub API 实查：0 stars，2026-11-06 创建并推送，Python；README/描述标注为 PatternBloom 论文代码）"
    accessed: "2026-11-19"
---

# PatternBloom：RAG agent 的"推理套路"也能建库检索——逻辑当检索单元，OOD 涨 15 个点

> 来源：https://arxiv.org/abs/2611.10477 （v1 2026-11-07，摘要经 arXiv API 实抓）；官方仓 https://github.com/EllenYiGe/PatternBloom 信号经 GitHub API 实查（2026-11-19）。本卡内容出自本次抓取的摘要与仓库元数据，未读 PDF 全文。

## 是什么

**把推理路由外化为可检索结构先验的 agentic RAG 框架**。诊断：各类 RL 训练的 RAG agent（检索段落/图谱片段/超边、答案级结果奖励）都把推理路线留在模型隐状态里——声明性知识（读什么）与程序性知识（怎么推理）混在一起，内容检索类方法随推理深度增长而触顶。PatternBloom 把检索单元从**内容**换成**逻辑**：一阶段 RL 以冻结 oracle 的信息增益打分（IDR，尺寸归一互信息代理）筛高奖励轨迹，**蒸馏成图模式记忆（GPM）**——类型抽象的推理骨架；二阶段 RL 用模式增强奖励（PAR）把策略与记忆耦合。官方口径：7B 模型胜 27 个基线 +15.0 Avg-OOD EM，增益随推理深度复合。

## 解决什么问题

多跳问答里"同类问题反复现场摸索同一条推理路径"的浪费：每次查询都从头推导"先查 A 的实体→顺边到 B→对照时间线"这类骨架。PatternBloom 让骨架本身成为一等检索对象——查询先匹配"逻辑类型"，复用已蒸馏的推理套路，把程序性知识从"每次重推"变成"一次学习、终身复用"。

## 相比前方法优势

- **检索单元升维**：内容检索（段落/子图）vs 逻辑检索（推理骨架）是正交增益，与库内 RIT-RAG（2610.11370，先定位后阅读）、QueryFlow（2611.04625，查询-证据耦合演化）各占一格；
- **两段 RL 分工清晰**：一段管"哪些轨迹值得留"（信息密度），一段管"记忆如何反哺策略"——管线可拆可换；
- **OOD 增益大且随深度复合**：+15.0 EM 不是微调级抖动，且越难越赚；
- **官方代码同日发布**，7B 规模可训可改。

## 局限（如实标注）

- 0 stars 新仓且仅推送一次（2026-11-06），代码完整度/文档成熟度未知，复现要留排障时间；
- 冻结 oracle 的信息增益打分依赖一个强裁判模型——裁判弱则蒸馏出的模式质量塌方；
- "逻辑类型"的抽象粒度由轨迹聚类决定，跨领域（如法律/医疗问答）迁移时模式库需重建；
- 27 基线对照为论文自报，未见第三方榜单交叉验证。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：多跳 QA/RAG 赛直接在官方仓上改：换赛题数据重建 GPM，7B 底座单卡可训；与"换更强底座模型"路线对比，模式复用路线的增益随题目难度放大，决胜局（最难的一档题）正是其主场。
- **双创-文书与申报**（reuse_cost 中）：知识密集型产品申报用"内容库+模式库"双库架构叙事，程序性知识资产化（不锁在某家模型 API 上）是差异化记忆点。
