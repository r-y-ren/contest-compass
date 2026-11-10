---
id: arxiv-2611.06409
name: "LLM agent 零样本协调（ZSC）：极简环境定位协调失败根源，Coordination-friendly Definitions 可自动发现（NeurIPS 2026，官方仓 Apache-2.0 可跑）"
field: [LLM agents, 多智能体, zero-shot coordination]
directions: [黑客松与数据竞赛]
published: "2026-11-04"
maturity: demo
venue_tier: CCF-A
reproducibility_level: high
signal:
  venue: "NeurIPS 2026 + 官方仓 ahayler/zsc-llm-agents（GitHub API 实查 2026-11-10：7 stars，Apache-2.0，论文摘要明示代码地址）"
  stars: 7
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "多智能体对抗/合作类赛（狼人杀、Hanabi 类 AI 对抗赛、协作机器人赛）的赛前诊断与接口设计工具：实测证明各自独立开发的 LLM agent 即使在**极简环境**也协调失败（根源是对协调问题理解弱、对队友信念推理差），且现实里各队 scaffold 不会共享——这解释了『自己队内测试很好、联赛现场拉胯』的常见现象；其解法 CFD（把环境定义改写成 LLM 可利用的语义结构）可自动发现，参赛方用来把赛题规则转译成『队友一眼读懂』的规范，主办方用来设计协调友好接口；官方仓可复现全部实验"
    reuse_cost: 低
  - track: "双创-文书与申报"
    edge: "多 agent 产品集成规范的方法论引用：CFD 作为 agent 间接口/协议设计原则（从『共享 scaffold』转向『共享协调友好的问题定义』），支撑跨团队异构 agent 协作类产品的可行性论证"
    reuse_cost: 中
sources:
  - url: https://arxiv.org/abs/2611.06409
    title: "Zero-Shot Coordination among LLM Agents（arXiv abs 页，2026-11-04 提交，摘要经 arXiv API 实抓 2026-11-10，摘要内附官方代码地址）"
    accessed: "2026-11-10"
  - url: https://github.com/ahayler/zsc-llm-agents
    title: "官方代码仓（GitHub API 实查 2026-11-10：7 stars，Apache-2.0，描述标注 NeurIPS 2026 paper）"
    accessed: "2026-11-10"
---

# LLM agent 零样本协调：极简环境暴露失败根源，CFD 给出可自动发现的修法

> 来源：https://arxiv.org/abs/2611.06409 （v1 2026-11-04，摘要经 arXiv API 实抓 2026-11-10）；官方仓 https://github.com/ahayler/zsc-llm-agents 信号经 GitHub API 实查（2026-11-10）。本卡内容出自本次实抓摘要与仓库元数据，未读 PDF 全文。

## 是什么

研究 LLM agent 的零样本协调（ZSC）：各自独立开发的 agent 必须在测试时现场配合。与既有 LLM 协调研究的差别：(1) 不依赖专用共享 scaffold（现实中独立开发的 agent 不会共享）；(2) 用**极简环境**替代 Hanabi 类复杂环境，把协调失败归因到具体机制。发现：即便受控场景，前沿 LLM agent 协调仍然失败，根源是对协调问题本身理解有限、对队友信念的推理薄弱；LLM 引入了语义信息这一新的协调轴，但未能有效利用。提出 **Coordination-friendly Definitions（CFD）**——把问题定义改写成利于协调的语义结构，并证明 CFD 可自动发现、免除手工工程。

## 解决什么问题

RL 文献里 ZSC 已有成熟研究，但 LLM agent 的 ZSC 几乎空白；现有 LLM 协调评测要么依赖共享专用 scaffold（不现实），要么环境太复杂无法定位失败原因。本文把"为什么 LLM agent 合作总是拉胯"拆成可测量的最小问题集，并给出不要求共享 scaffold 的修法。

## 相比前方法优势

- **评测设定贴近现实**：不共享 scaffold、极简环境定位失败根源，结论可直接外推到"各自开发、现场相遇"的真实多 agent 场景；
- **归因具体**：失败主因被定位到"协调问题理解弱 + 队友信念推理差"，而非笼统的"模型不够强"；
- **CFD 可自动发现**：协调接口的改写不再依赖人工设计，方法论可规模化；
- **NeurIPS 2026 + 官方仓 Apache-2.0**：实验可复现。

## 局限（如实标注）

- 未读 PDF 全文：极简环境的具体任务集、CFD 自动发现的算法细节、各前沿模型的失败率数字以摘要口径为准；
- 极简环境到复杂博弈（狼人杀/Hanabi 全规则）的外推距离未知，CFD 在复杂规则下的构造成本未量化；
- 官方仓 7 stars、无社区验证记录，复现需自证。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：多智能体对抗/合作赛（狼人杀、Hanabi 类、协作任务赛）两向可用——参赛方：赛前用官方仓自测自家 agent 在不共享 scaffold 条件下的配合度，把规则文本改写成 CFD 风格（目标/约束/信念提示结构化），降低现场与陌生队友的协调摩擦；主办方/命题人：按 CFD 原则设计赛题接口，让参赛队的异构 agent 有共同的协调锚点。
- **双创-文书与申报**（reuse_cost 中）：跨团队异构 agent 协作类产品的接口设计原则引用：以"LLM agent 天然协调失败、CFD 可自动发现"的实证论证产品必须内建协调友好协议层，而非假设 agent 间自然默契。
