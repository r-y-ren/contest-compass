---
id: gh-shakewingo_Tadpole
name: "Tadpole：从零手写并持续演化的 LLM agent 教学仓——45 星 MIT，双创团队的 agent 原型脚手架"
field: [LLM agents, agent 教学/脚手架]
directions: [创新创业大赛]
published: "2026-10-26"
maturity: demo
venue_tier: other
reproducibility_level: high
signal:
  venue: "GitHub（shakewingo/Tadpole，GitHub API 实查：45 stars、3 forks、MIT license，2026-10-26 创建、11-03 仍有推送，8 open issues）"
  stars: 45
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "'人工智能+'类双创项目的两用底座：(1) 团队从零到一搭 agent 原型的教学路径——'build from scratch and continuously evolve'的定位正好覆盖申报书里'核心技术自研'叙事需要的理解深度（不是套框架，是懂原理）；(2) 演化式设计的叙事素材——把'持续演化 agent 能力'作为产品迭代故事写进商业计划书的技术路线节"
    reuse_cost: 低
    open_source: "github.com/shakewingo/Tadpole（MIT，可自由改作项目底座）"
sources:
  - url: https://github.com/shakewingo/Tadpole
    title: "仓库主页（GitHub API 实查：45 stars、3 forks、MIT、2026-10-26 创建 11-03 推送、8 open issues；描述：Build an LLM agent from scratch and continuously evolve it）"
    accessed: "2026-11-07"
---

# Tadpole：从零构建、持续演化的 LLM agent 学习仓

> 来源：https://github.com/shakewingo/Tadpole （GitHub API 实查 2026-11-07：45 stars、3 forks、MIT、创建于 2026-10-26、最近推送 2026-11-03、8 open issues）。本卡出自本次抓取的仓库元数据与描述，未逐文件审读代码。

## 是什么

GitHub 教学型仓库：引导使用者**从零开始手写一个 LLM agent 并持续演化它**（官方描述：Build an LLM agent from scratch and continuously evolve it）。定位是"造轮子式"学习路径——与调用 LangChain/LangGraph 类框架的项目相反，强调对 agent 内部件（循环、工具调用、记忆、演化机制）的第一性理解。MIT 许可，创建两周 45 星、维护活跃（11-03 仍有推送）。

## 解决什么问题

想入门 agent 开发的团队面临两难：直接上框架，快但对内部机制黑箱，出问题不会修；纯读论文，懂原理但没有可跑的落点。Tadpole 占"从零手写+持续演化"的中间位：以可运行代码为载体逐步搭出 agent，并把"演化"（而非一次性搭建）作为仓库的组织主线。

## 相比前方法优势

- **演化主线**：不以"搭完即止"为目标，而是持续迭代 agent 能力——这与自进化 agent 研究潮流（库内 FASE/RRSI 卡）同频，学到的组织方式可直接迁移到自进化项目；
- **活跃且轻量**：两周 45 星、双周内有推送，MIT 无法律负担；从零手写的代码量通常远小于框架栈，读得动改得动；
- **双创叙事友好**："自研"与"持续演化"两个申报书高频词都能在仓库实践中找到实物支撑。

## 局限（如实标注）

- 45 星社区规模小、无权威背书（非知名作者/机构），代码质量未经大规模检验，8 个 open issues 待处理；
- 单人维护的仓库，断更风险真实存在——引用/依赖前先看最近提交；
- "从零手写"路线在生产环境的工程完备性（并发、缓存、观测）必然不及成熟框架，原型阶段适用；
- 本卡未逐文件审读：仓库具体覆盖哪些 agent 部件（工具/记忆/RAG/多智能体）需克隆后核验，勿直接引用未核验的功能清单。

## 如何用于比赛（比赛映射展开）

- **双创-文书与申报**（reuse_cost 低）：作为团队内训与原型脚手架——赛程前期全员跟仓搭一遍，建立对 agent 循环/工具/记忆的共识词汇；原型阶段直接在其代码基座上改，省掉框架选型内耗；申报书技术路线里"从零构建并持续演化"的开发过程本身可写成工程能力证据。注意：衍生作品需遵守 MIT 保留版权声明，且"基于开源教学仓二次开发"在申报中应如实标注，避免自研表述越界。

**族内定位**：库内 agent 工程家族此前偏研究/组件卡（harness、记忆、编排），教学/脚手架位稀疏——本卡是双创方向"团队 agent 起步"位的候选锚点；与研究卡的关系是**消费方**：Tadpole 类仓库的手写循环与 FASE/RRSI 的演化机制可对接，作为把研究卡落成课程化实践的载体。
