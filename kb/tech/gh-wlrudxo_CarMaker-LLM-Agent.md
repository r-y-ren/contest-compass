---
id: gh-wlrudxo_CarMaker-LLM-Agent
name: "CarMaker-LLM-Agent：LLM agent 驾驭 IPG CarMaker 整车仿真——触发监控判定 + Claude CLI 决策 + 车辆控制指令闭环（20★ MIT，创建一周内活跃推送）"
field: [LLM agents, 自动驾驶仿真]
directions: [创新创业大赛]
published: "2026-11-04"
maturity: demo
venue_tier: industry
reproducibility_level: high
signal:
  venue: "GitHub API 实查 2026-11-10：wlrudxo/CarMaker-LLM-Agent，20 stars，MIT license，2026-11-04 创建、11-09 推送（活跃维护）"
  stars: 20
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "智能驾驶/ADAS 类双创项目的『LLM + 专业仿真工具』演示底座：仓库给出场景触发监控判定 → Claude CLI 决策 → CarMaker 车辆控制指令注入的完整闭环，MIT 协议 + 活跃维护（创建六天即 20★）可直接改造成项目 demo 或测试自动化模块；ADAS 触发条件（trigger monitoring）自动判定是仿真测试自动化的具体抓手，答辩演示『自然语言指挥整车仿真』辨识度高"
    reuse_cost: 低
sources:
  - url: https://github.com/wlrudxo/CarMaker-LLM-Agent
    title: "GitHub 仓库主页（GitHub API 实查 2026-11-10：20 stars，MIT license，2026-11-04 创建 11-09 推送，描述：LLM agent for autonomous driving simulation in IPG CarMaker）"
    accessed: "2026-11-10"
---

# CarMaker-LLM-Agent：用 LLM 当整车仿真器的"测试驾驶员"

> 来源：https://github.com/wlrudxo/CarMaker-LLM-Agent （GitHub API 实查 2026-11-10：20 stars，MIT，2026-11-04 创建、11-09 推送）。本卡内容出自本次实抓的仓库元数据与描述，未逐文件审读代码实现。

## 是什么

把 LLM agent 接入 IPG CarMaker（商业整车仿真平台）的开源项目：agent 承担三件事——(1) **触发监控**：判定仿真场景中的触发条件（ADAS 类场景验证的核心工序）；(2) **决策**：经 Claude CLI 生成驾驶决策；(3) **执行**：向 CarMaker 注入车辆控制指令完成闭环。MIT 协议，创建一周内 20★ 且持续推送。

## 解决什么问题

整车仿真里的场景触发监控与测试执行历来靠人工配置与观察，场景规模化验证成本高；该项目把"看场景 → 判断 → 操控"这条仿真测试链交给 LLM agent，让自然语言决策层与专业仿真工具直接闭环。

## 相比前方法优势

- **专业工具原生闭环**：不是聊天式 demo，指令直达 CarMaker 车辆控制接口，能跑真实仿真任务；
- **触发监控自动化**：ADAS 仿真验证中判触发是重复劳动，自动化收益具体；
- **工程形态可改**：MIT + 单仓结构，改造成自己的 demo/测试管线门槛低。

## 局限（如实标注）

- 本卡未逐文件审读代码：决策链稳定性、场景覆盖范围、对 CarMaker 版本的依赖以仓库 README 口径为准，复现前需自查；
- 依赖商业软件 IPG CarMaker 授权，无授权环境无法复跑；
- 单作者新仓、20★、无 fork 社区验证，成熟度按 demo 如实标注；LLM 决策在安全攸关仿真中的可复现性/审计性仓库未讨论。

## 如何用于比赛（比赛映射展开）

- **双创-文书与申报**（reuse_cost 低）：智能驾驶/ADAS 方向项目的现成演示底座：以 MIT 仓为起点改造为项目 demo（自然语言指挥仿真、触发判定自动化两个演示点），并在申报书引"LLM agent 闭环驾驶专业仿真工具"作为技术路线证据；需自备 CarMaker 授权，无授权时可引其架构做静态展示并如实标注。
