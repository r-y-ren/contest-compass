---
id: arxiv-2611.15262
name: "CastWorld：上下文感知 agentic 时序预测基准——8 域 25 数据集 + 49 工具预测原生 harness，模型级/系统级双层评测，'更多交互不必然更准'（官方基准仓可跑）"
field: [time series forecasting, agentic benchmark, LLM agents, evaluation]
directions: [数模与时序预测, 黑客松与数据竞赛]
published: "2026-11-11"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv v2（2026-11-11，摘要经 arXiv API 实抓）+ 官方基准仓 CastWorld-Bench/CastWorld（GitHub API 实查：2 stars，2026-11-13 创建，README 链接 arXiv 2611.15262 与项目页 castworld-bench.github.io，含 leaderboards 与入门文档；中英双语 README）"
  stars: 2
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "为'带上下文的预测系统'提供现成评测协议：8 域 25 数据集统一上下文规范（外生变量/事件/历史案例）+ 49 工具 harness + 预测版本史追踪，可整体搬来评测赛题自建的预测流程——尤其其'过程执行/行为可信度/资源效率'三个非精度维度，正是数模论文区分'好模型 vs 好流程'的评分素材；其 harness 也可拆件复用（预测版本管理、证据缺口提示）"
    reuse_cost: 中
    open_source: "github.com/CastWorld-Bench/CastWorld（官方基准仓，含 harness 与 leaderboards）"
  - track: "黑客松-数据与算法"
    edge: "做'LLM agent 预测'方向的黑客松项目可直接在 CastWorld 上开发与打榜：统一环境免自建数据套件，四维评测（质量/过程/可信度/效率）天然是 demo 评审维度；其发现'交互更多不必然更准、agent 选不中自己最好的预测版本'给项目设计立了两条反直觉的工程红线"
    reuse_cost: 中
    open_source: "github.com/CastWorld-Bench/CastWorld"
sources:
  - url: https://arxiv.org/abs/2611.15262
    title: "CastWorld: Benchmarking Context-Aware Agentic Time Series Forecasting Beyond Predictive Accuracy（arXiv abs 页 v2，2026-11-11，摘要经 arXiv API 实抓）"
    accessed: "2026-11-19"
  - url: https://github.com/CastWorld-Bench/CastWorld
    title: "官方基准仓（GitHub API 实查：2 stars，2026-11-13 创建；README 自述三件套：上下文数据套件/状态自适应 harness/双层评测，含 leaderboards 与 GETTING_STARTED 文档）"
    accessed: "2026-11-19"
---

# CastWorld：给"预测 agent"立考场——不只比准不准，还比过程、可信度和效率

> 来源：https://arxiv.org/abs/2611.15262 （v2 2026-11-11，摘要经 arXiv API 实抓）；官方基准仓 https://github.com/CastWorld-Bench/CastWorld 信号经 GitHub API 实查（2026-11-19）。本卡内容出自本次抓取的摘要与仓库元数据，未读 PDF 全文。

## 是什么

**上下文感知 agentic 时序预测基准**，三件套：(1) **上下文数据套件**——8 域 25 个真实数据集，统一规范覆盖外生变量、事件与历史案例；(2) **预测原生 harness**——49 个核心工具 + 状态自适应循环：追踪预测版本、支持迭代式证据收集与预测修订，中间预测暴露信息缺口，新证据指导后续修订与最终版本选择；(3) **双层评测**——模型级评测考察预测质量、过程执行、行为可信度与资源效率（基于决策轨迹与预测版本史），系统级评测比较预测系统的精度。发现：精度相当的 agent 决策行为差异明显；更多交互不必然改善预测；agent 会选不中自己已生成的最佳预测；允许在修订期采集证据能全面提升三个被评模型的任务感知预测分。

## 解决什么问题

现有 agentic 基准不为预测场景定制：上下文支持零散、没有"修订-选版"的预测特有交互、没有过程级评测。CastWorld 把"预测 agent 该怎么考试"标准化——考的不只是分数，还有拿证据的方式、修订的合理性、选版的判断力和花掉的算力。

## 相比前方法优势

- **预测特化**：版本史追踪+修订循环是时序预测特有的交互形态，通用 agent 基准没有；
- **四维模型级评测**：把"行为可信度""资源效率"纳入评分，能区分"精度相同但乱烧 token/乱改预测"的 agent——与库内 agentic 预测线（CastClaw 的 harness 工程、TSFLab 的工作台）形成"工程-评测"互补；
- **反直觉发现可复用**："不选最优版本"与"多余交互有害"是任何自建预测 agent 都要防的两个坑，其 harness 的版本管理+最终选版机制即对应解法；
- **官方基准仓已开**，含 leaderboards，可直接打榜。

## 局限（如实标注）

- 2 stars 极早期基准仓，榜单上玩家少，"社区标准"地位未成；
- harness 与评测协议绑定：被评 agent 的强弱可能混入 harness 用法熟练度的影响；
- 25 数据集的域覆盖虽广但单域深度有限，特定行业的上下文类型（如监管文本）不在套件内；
- "任务感知预测分"的具体合成方式需读全文/文档才能复刻。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 中）：把其"过程执行/行为可信度/资源效率"评测维度借为赛题预测流程的自检表；官方 harness 的"中间预测暴露信息缺口→采证据→修订→选版"循环可直接套在赛题的预测-修正环节上，产出可解释的版本史供论文引用。
- **黑客松-数据与算法**（reuse_cost 中）：agent+预测方向的参赛项目直接以 CastWorld 为赛道环境：数据套件+harness+四维评分现成，项目叙事可用其发现做差异化设计（如主打"最终选版"环节的可靠性）。
