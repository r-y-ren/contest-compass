---
id: gh-huynguyengl99_agent-graph-engineering
name: "Agent Graph Engineering：LLM agent 生产级参考实现（声明式图流 + 生成式契约 + 不可逆动作人工审批门）"
field: [LLM agents, 软件工程, human-in-the-loop]
directions: [创新创业大赛]
published: "2026-10-08"
maturity: demo
reproducibility_level: high
signal:
  venue: "GitHub（MIT；2026-10-11 API 实抓：11 stars / 4 forks / 2026-10-09 仍有推送）"
  stars: 11
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "'AI+' 类项目从 demo 走向可申报产品的架构底座与论证模板：流程声明为 LangGraph 图而非 if/else 链（图可从编译后对象导出 Mermaid，架构图与代码永不失配——申报书/答辩架构图可直接生成）；服务边界全部用生成的 OpenAPI/AsyncAPI 契约（改形状跑 just gen，编译器点名哪里断）；不可逆动作（退款/外发消息）调用前强制停靠人工审批、审批字段直接由工具参数 schema 渲染（评审者不会批准一个没见过字段的调用）；每图节点级 tracing 带成本核算、LLM 在 HTTP 层 mock 使全管线测试零花费。这四件事正是评审问'工程可行性/安全可控性'时的标准答案，README 的'每条过度谨慎都来自一次真实事故'叙述可直接转译为风险控制章节"
    reuse_cost: "低"
    open_source: "https://github.com/huynguyegl99/agent-graph-engineering（MIT；just setup && just up 即起三服务，无 API key 时内置脚本模型驱动全流程，just e2e 真浏览器端到端）"
sources:
  - url: https://github.com/huynguyengl99/agent-graph-engineering
    title: "agent-graph-engineering 仓库（README+文件树+API 元数据，2026-10-11 实抓：Django 5.2 业务记录 / FastAPI+LangGraph+Pydantic AI agent / React 19 前端三服务，Postgres checkpoint 可恢复，OpenTelemetry 兼容导出）"
    accessed: "2026-10-11"
---

# Agent Graph Engineering：把 agent 生产化的四个工程决策做成可跑参考实现

> 来源：https://github.com/huynguyegl99/agent-graph-engineering （MIT，Python/TypeScript，2026-10-08 创建，2026-10-11 实抓 README、git trees 与 API 元数据）。作者自述从一套五服务生产系统蒸馏而来（约五年实时基础设施与 agent 系统经验），配套系列文章 https://huynguyengl99.github.io/series/agent-graph-engineering/ 逐决策解释；自述出处未经独立核实，如实标注。

## 是什么

一个"AI 客服工位"完整参考实现（工单双通道：客户看过程、团队看内部，一个 agent 服务两条通道），核心价值不在业务而在**四个可复用的工程决策**：

1. **流程即声明图**：agent 的行为是 LangGraph 编译出的执行图（状态/节点/条件边/中断/恢复），不是意图分类器上的 if/else 链；`GET /graphs/support.mermaid` 直接从编译对象渲染架构图——图与代码不可能不一致；
2. **边界即生成契约**：Django(业务)↔FastAPI(agent)↔React(前端) 三服务之间，REST 用生成 OpenAPI、WebSocket 用生成 AsyncAPI，`just gen` 后 TS/Python 客户端由编译器保证类型一致；
3. **不可逆动作人工门**：工具调用运行前一律停靠待审批（重启不丢、换 socket 可恢复——Postgres checkpoint）；普通问答不停（"永远要人点头的客服台没有客服"）；审批表单字段直接来自工具参数 schema，杜绝"批准了没见过的字段"；
4. **可观测且零花费可测**：每图节点一个 span（模型调用嵌套其中，含单次运行成本），可转发任意 OTLP collector；LLM 在 HTTP 层 mock，SSE 解析/工具装配/流式/校验全管线可测，evals 按需打真 provider。

模型无关：节点写用途不写模型名，哪个模型服务哪个用途是配置项（防路由漂移到贵的）。

## 解决什么问题

赛队/小团队的 agent demo 普遍停在"prompt + 循环"形态，走向产品时缺的不是模型能力而是**工程化模式**：流程改动牵一发动全身（if/else 链）、前后端契约靠口头约定、不可逆操作没有闸门、出问题无法回答"agent 当时为什么这么做"。本仓把这四个失败模式各给了一个机制化答案，且每个设计都附"它在生产里怎么坏的"（同一线程双运行互相覆盖导致已批准回复消失、重启丢回复等），继承的是失败模式而非代码风格。

## 相比前方法优势

- 与库内 Rome（agentic OS）、Agents Universe（多角色平台）、Jixu（TS 事件溯源单 agent harness）相比，定位不同：它是**教学级完整度的生产架构参考**（三服务 + 契约生成 + 审批流 + tracing + evals + e2e 全套），且强调"图声明式 + 契约生成式"这一对组合在库内无同款；
- "审批表单从工具 schema 渲染"是库内 SARA/WebMCP-Phalanx 等授权研究论文的工程落地最小版——不是论文而是能直接抄的代码；
- 自可视化（Mermaid 从运行时对象导出）解决了"架构图腐烂"这个所有申报材料的老问题。

## 局限（如实标注）

- 仓库极年轻（2026-10-08 创建）、11 stars、单维护者，无第三方生产使用背书；"蒸馏自五服务生产系统"为作者自述；
- 场景绑定客服工位（工单/退款/升级），换域要重写业务节点——抄的是模式不是产品；
- Python/TS 双栈三服务 + Postgres，对纯算法赛队是重量级底座，48 小时黑客松内从零吃透偏重（适合作为双创产品迭代期骨架）；
- 无论文无基准数字，工程主张（契约生成降缺陷等）无量化实证。

## 如何用于比赛（比赛映射展开）

1. **双创-文书与申报（"AI+"项目管理类/服务类产品）**：三条直接可用——(a) 申报书架构图从 `/graphs/*.mermaid` 生成并附"图即代码"说法；(b) 安全可控章节引用其审批门机制（工具参数 schema 渲染审批字段 + Postgres checkpoint 恢复 + 节点级成本 tracing），每条都对应一个可演示的界面截图；(c) 软件著作权/技术实现材料可直接以三服务契约为骨架。reuse_cost 低：`just setup && just up` 无 key 可跑，一天内可改域换皮成自己项目的原型。
