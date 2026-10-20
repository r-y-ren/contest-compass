---
id: arxiv-2610.24087
name: "OR-License：用真实付费运筹项目评测 LLM Agent（31 实例/10 工业场景/380 万美元合同额，DAQ 指标下无模型达到专家基准）"
field: [LLM agents, 运筹优化, 基准评测]
directions: [黑客松与数据竞赛]
published: "2026-10-15"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv/HuggingFace Papers"
  runnable: true
competition_fit:
  - track: "数模-数据分析与决策"
    edge: "运筹优化是数模核心题型（排产/调度/选址/资源分配），OR-License 第一次给出『LLM agent 直接吃原始业务材料→产出方案』的可行性标尺：11 个前沿 LLM 挂 coding-agent 框架，最强 Claude Code 配置严格可行率 88.39%、DAQ 0.87（专家参考解为 1，不可行记零；作者自报口径）——条件目标质量能超专家、端到端交付质量达不到，这个『最后一公里差距』结论可直接支撑数模论文里『AI 辅助建模需人工把关交付质量』的论证；其 31 个去标识真实实例是现成的高难度练手题库"
    reuse_cost: 低
    open_source: "https://github.com/NineAbyss/OR-License（官方代码与数据，2026-10-20 实查活跃）"
  - track: "黑客松-数据与算法"
    edge: "自研优化 agent 的防作弊验收协议模板：ORSim 客户模拟器只披露业务事实不授运筹专长 + 隐式评估（可行性检查 + 对客户验收过的专家解比目标质量）+ DAQ（不可行交付记零分）——三层设计堵死『预先知道答案』与『交付不可行方案』两类作弊，可直接借来给 hackathon 的优化类作品做评测设计"
    reuse_cost: 中
    open_source: "https://github.com/NineAbyss/OR-License（基准协议代码公开；ORSim 与评估器可改造复用）"
sources:
  - url: https://arxiv.org/abs/2610.24087
    title: "OR-License: Evaluating LLM Agents as Real-World Operations Research Practitioners（arXiv abs 页，Peisong Wang 等 19 人含 Jie Fu/Zuo-Jun Max Shen/Yong-Hong Kuo，摘要全文与 Code and Data 链接，2026-10-20 实抓）"
    accessed: "2026-10-20"
  - url: https://github.com/NineAbyss/OR-License
    title: "NineAbyss/OR-License 官方代码仓（API 元数据：2 stars/2026-10-20 仍有推送）"
    accessed: "2026-10-20"
---

# OR-License：LLM Agent 能否当真·运筹咨询师——380 万美元真实项目的端到端基准

> 来源：https://arxiv.org/abs/2610.24087 （abs 页摘要，2026-10-20 实抓；Peisong Wang、Feixue Liu 等 19 位作者，含 Jie Fu、Zuo-Jun Max Shen、Yong-Hong Kuo）。代码与数据见 abs 页链接 https://github.com/NineAbyss/OR-License （2026-10-20 GitHub API 实查确认存在且活跃）。本卡内容出自本次抓取的摘要页与仓库元数据，未读全文。

## 是什么

端到端运筹优化（OR）agent 基准：**31 个实例、10 个工业场景，全部来自累计 380 万美元的真实付费 OR 项目**，去标识后保留原始需求文档、输入数据、交付格式与信息边界——不从"自包含题目描述"起步，考的是把原始客户材料翻译成专业方案的全链路。配套两个机制：**ORSim** 受控客户模拟器（只披露业务事实、不提供 OR 专长，逼 agent 自己做信息获取）；**隐式评估**（自动查可行性 + 与客户此前验收过的专家解比对目标质量）；评分用 **DAQ（Deployment-Adjusted Quality）**：各实例相对专家解的质量均值，不可行交付记零。结果（摘要自报）：11 个前沿 LLM 挂 coding-agent 框架，若干模型**条件目标质量超过专家参考解**，但**无一达到专家的 DAQ**；最强 Claude Code 主配置严格可行率 88.39%、DAQ 0.87。轨迹分析显示客户信息获取延伸到方案开发与验证阶段。

## 解决什么问题

现有 OR 基准都从"整理好的题目"开始，回避了真实咨询里最难的一段：从原始、不完整、互相矛盾的业务材料里提炼出正确的优化问题。OR-License 把这段纳入评测，并给出防泄漏的受控模拟与不可行记零的严格口径。

## 相比前方法优势

- **生态效度**：实例来自真实付费交付（客户验收过的专家解作参考锚），不是竞赛题或教科书题；
- **评测防作弊三层**：ORSim 控信息流、隐式评估免人工判卷、DAQ 对不可行零容忍；
- **结论有区分度**：条件质量 vs 端到端 DAQ 的分离直接定位"问题翻译与交付完整度"是 agent 短板，而非求解能力本身。

## 局限（如实标注）

- arXiv 预印本（venue_tier arXiv），评测细节与实例覆盖面需读全文与数据集核实；31 实例规模对泛化结论偏小；
- 数字全部为作者自报口径；官方仓 2 stars、发布极新（2026-10-20 仍有推送），社区复验尚未形成；
- "coding-agent 框架"配置细节（预算、工具集、迭代上限）未读全文不背书；最强结果绑定 Claude Code 配置，模型-框架耦合度未知。

## 如何用于比赛（比赛映射展开）

1. **数模-数据分析与决策（运筹/优化类赛题）**：两用——(a) 论证素材：数模论文的"AI 辅助与人工把关"讨论章节可引用其核心数字与"条件质量可达、端到端交付不及专家"的结论（注明 arXiv 作者自报），支撑"模型出方案、人审交付质量"的工作流设计；(b) 训练题库：31 个去标识真实实例是超纲练手材料，模拟"从模糊业务材料到模型"的真题难度。reuse_cost 低：代码与数据公开。
2. **黑客松-数据与算法（优化类 agent 作品的评测设计）**：把 ORSim + 隐式评估 + DAQ 三层协议借来自建赛题评测或自测作品——尤其"不可行记零"口径能倒逼方案交付的完备性（可行性检查先行），比"跑通就行"的松口径在评审处更有说服力。reuse_cost 中：协议需按赛题改造，评估器实现可参考官方代码。
