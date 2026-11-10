---
id: arxiv-2611.06254
name: "HarnessFlow：MCTS 搜索完整可执行 agent harness——精炼树 + 可复用机制库，每基准仅 15 次评测预算内平均分 69.48%（+10.89pp，胜 Meta-Harness 3.95pp）"
field: [LLM agents, agent harness 工程, MCTS]
directions: [黑客松与数据竞赛]
published: "2026-11-04"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv（上轮点名优先评估项，2026-11-10 经 arXiv API 实抓摘要；GitHub repo search 无官方实现）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "agent 赛题（SWE-bench 类、web 交互类）模型固定时的提分路线图：把 harness（工具中介/状态管理/控制流）整体当搜索对象，MCTS 维护候选精炼树平衡探索利用，coding agent 借档案代码、执行反馈与**可复用 harness 机制库**改写候选；核心卖点是预算约束——每基准仅 15 次端到端评测就实现 69.48% 平均分，这正是按次计费/限时赛题的现实约束；与库内 ActiveSaddler（arxiv-2610.00906，bandit 调场景臂的课程层）分工不同不重复：ActiveSaddler 管训练场景调度、HarnessFlow 搜 harness 代码本身，两篇可拼成『预算感知 harness 自动化』完整叙事"
    reuse_cost: 高
  - track: "双创-文书与申报"
    edge: "agent 产品『harness 即护城河』叙事的技术背书：引六基准 +10.89pp 且单任务执行成本低于人工基线的实测，论证自动 harness 优化作为 agent 开发平台/工具链类项目的差异化卖点（harness 自动化比 prompt 工程高一层、比模型微调便宜一档）"
    reuse_cost: 中
sources:
  - url: https://arxiv.org/abs/2611.06254
    title: "HarnessFlow: MCTS-Guided Harness Optimization for LLM Agents（arXiv abs 页，2026-11-04 提交，摘要经 arXiv API 实抓 2026-11-10）"
    accessed: "2026-11-10"
---

# HarnessFlow：harness 设计从手工活变成 MCTS 搜索问题

> 来源：https://arxiv.org/abs/2611.06254 （v1 2026-11-04，摘要经 arXiv API 实抓 2026-11-10）。本卡内容出自本次实抓摘要，未读 PDF 全文；GitHub repo search（2026-11-10）未见官方实现。

## 是什么

agent harness 自动优化框架：模型与任务环境固定，优化对象是**完整可执行 harness**。三个组件：(1) 以精炼树组织候选 harness 及其评测历史；(2) MCTS 策略在开放搜索空间中平衡利用与探索，应对端到端评测昂贵的现实；(3) 一个 coding agent 负责改写被选中的候选，改写时可引用存档代码、历史执行反馈与一个**可复用 harness 机制库**。官方口径：六基准（agentic 任务、coding、web 交互）上以每基准 **15 次精炼尝试**取得最高平均测试分 **69.48%**，超初始 harness **10.89pp**、超 Meta-Harness **3.95pp**，且平均单任务执行成本低于人工工程基线。

## 解决什么问题

agent 成绩由模型与 harness 共同决定，但 harness（工具调用中介、状态管理、安全护栏的组织方式）仍以手工设计为主。自动化的障碍是搜索空间开放、每次评估要跑完整任务（贵）。HarnessFlow 把它形式化为"预算受限的树搜索 + 带机制库的代码改写"，让搜索在新颖性与已知好解之间受控地分配有限评测次数。

## 相比前方法优势

- **对象完整**：优化的是整套可执行 harness，而非单个 prompt 或单个超参——搜索空间虽更大，但收益上限也更高；
- **预算感知**：15 次评测/基准的成本量级表明方法在意"评测贵"这一现实约束，与多数无限算力假设的自动化工作不同；
- **机制库复用**：改写不是从零生成，可从验证过的机制库里拼装，搜索效率与结果可复用性同时受益；
- **成本占优**：优化后的 harness 平均执行成本低于人工基线——提分不以推理成本暴涨为代价。

## 局限（如实标注）

- 未读 PDF 全文：六基准的具体构成、与 Meta-Harness 之外基线的逐项数字、机制库初始来源（人工沉淀还是自动提取）以摘要口径为准；
- 无官方开源实现（GitHub repo search 2026-11-10 未见），MCTS + coding agent 改写回路的复现工程量大，reproducibility 定为 low；
- 搜索依赖端到端评测信号，任务评测本身含噪声/不可靠时搜索易被误导；结果是否随基础模型换代稳定迁移未验证。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 高）：agent 类赛题（仓库级 SWE、web 操作、长程任务）模型被锁死时的系统性提分法：按其思路自建简化版——候选 harness 池 + 精炼树 + 按剩余评测预算分配的 MCTS 选点，coding agent 按执行反馈改 harness；"每基准 15 次"的预算设定可直接对齐比赛的提交次数限制，把提交流程从人工迭代升级为受控搜索。
- **双创-文书与申报**（reuse_cost 中）：agent 开发平台/工具链类项目的核心卖点支撑：自动 harness 优化作为"prompt 工程（浅）→ harness 自动搜索（本文）→ 模型微调（贵）"分层叙事的中间层，引其六基准数字与成本占优结论论证工程可行性。
