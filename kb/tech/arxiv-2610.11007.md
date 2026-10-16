---
id: arxiv-2610.11007
name: "Always-Loaded Context 的策展理论：AGENTS.md 该装几条规则？——带容量品类模型证明最优文件尺寸有上界、全量追加可任意次优"
field: [LLM agents, context engineering]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-07"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv（2026-10-07 v1，cs.AI/cs.LG/math.Optimization；摘要页无 comments、未附代码）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "agent 项目的系统提示词/AGENTS.md 精简方法论：每个 token 每次会话重复计费、过大固定上下文还伤服从率——本文给出可防守的设计准则（最优文件尺寸有与候选规则数无关的上界；'见过的规则才产生反馈'的删留陷阱：删被忽略的规则可能误删有用规则），48 小时赛程里少走'规则越堆越多'的弯路；实验证实真实上下文文件里的无关规则确实降低模型服从"
    reuse_cost: 低
  - track: "双创-文书与申报"
    edge: "agent 产品的上下文治理叙事与成本模型：把'固定上下文 = 带容量品类问题'写进产品架构章节，直接对应 token 成本与质量双重约束；'需要多少证据才准新增一条指令'的量化框架可支撑企业级 agent 交付的变更管理卖点"
    reuse_cost: 中
sources:
  - url: https://arxiv.org/abs/2610.11007
    title: "Curating Always-Loaded Context for LLM Agents: A Capacitated Assortment Model with Censored Feedback（arXiv abs 页，v1 2026-10-07，Zexuan Liu/Yuning Yang/Tiancheng Zhao，2026-10-16 实抓；无 comments 字段，未见代码链接）"
    accessed: "2026-10-16"
---

# Always-Loaded Context 策展：给 AGENTS.md 瘦身一个数学理由

> 来源：https://arxiv.org/abs/2610.11007 （arXiv abs 页 v1 2026-10-07，2026-10-16 实抓）。本卡内容出自本次抓取的摘要页，未读 PDF 全文。

## 是什么

把 LLM agent 每次会话固定加载的上下文文件（如 AGENTS.md）的维护问题形式化为**带容量的品类选择问题（capacitated assortment problem）**：指令消耗有限"注意力容量"，且新增一条指令不会提升其他指令的服从率。在此模型下推导固定上下文策展的最优策略与 regret 界。

## 解决什么问题

固定上下文文件每个 token 在每次会话重复计费，文件过大还会损害性能；而维护者通常只增不删。核心问题：**该装哪些指令、装多少、何时才值得新增一条？** 反馈是删失的（censored）——已加载指令的效果可观测，缺席指令只有在"缺席造成伤害"时才暴露。

## 相比前方法优势

- **理论结果可直接当工程准则**：证明了最优文件尺寸存在**与候选指令总数无关的上界**；把所有正价值指令全部装上的做法可比最优子集**任意次优**（arbitrarily worse）——给"提示词越全越好"的直觉判了死刑；
- **正面处理删失反馈**：刻画了"删除被忽略的指令可能误删有用指令"的机制，并推导新增一条指令前需要的最少证据量；
- **运营约束入模**：人类审核者每期只能复核有限编辑时的 regret 界——贴合真实团队而非理想化无限审核；
- **实验落地**：用真实上下文文件验证无关规则确实降低模型服从率。

## 局限（如实标注）

- 摘要页未附代码，未见开源实现（reproducibility 低）；理论模型对"指令不互相增强"的假设与真实提示词工程的复杂交互有距离，边界需读全文；
- "服从率"如何度量、实验用的模型与任务规模，摘要未展开；
- 结论适用于"固定加载"型上下文（AGENTS.md/系统提示词），对检索式动态上下文不直接适用。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：任何带 agent 的参赛项目都要写系统提示词——把"文件尺寸上界 + 逐条证据准入"当提示词评审清单用，直接省 token 费用并提升指令服从；"删被忽略规则有风险"提醒别在赛前深夜大扫除。
- **双创-文书与申报**（reuse_cost 中）：申报 agent 类项目时，上下文治理是可写进架构设计的差异化点：以本文框架为依据陈述"我们如何决定提示词装什么、何时扩、成本何时封顶"，比泛谈"提示词工程"更有说服力。

**族内定位**：库内 RAG 类卡（如 RIT-RAG）解决"动态检索什么"，本卡解决"固定加载什么"——上下文供给的两条互补通道。
