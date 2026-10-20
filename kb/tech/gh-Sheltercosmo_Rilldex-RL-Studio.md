---
id: gh-Sheltercosmo_Rilldex-RL-Studio
name: "Rilldex RL Studio：LLM Agent RL 训练可观测台（行为地图、TRL/verl 原生指标、reward hacking 检测、SQL/Python 取证）"
field: [LLM agents, 强化学习, 可观测性]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-16"
maturity: demo
reproducibility_level: medium
signal:
  venue: GitHub
  stars: 16
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "做 agent 强化学习类赛题的稀缺差异化演示：别人只能放训练曲线，你能现场展示行为地图（单元-动作-反馈-计划-重试的关联图）、reward hacking 检测器标记的具体 rollout 及其证据链、训练指标（loss/entropy/KL/clipping）与行为对齐视图——『我们看得见 agent 学了什么、有没有钻奖励空子』在评审处几乎无人能对；采集侧 pip 即装、无 GPU 也能跑（采集与源捕获不需要模型 key）"
    reuse_cost: 中
    open_source: "https://github.com/Sheltercosmo/Rilldex-RL-Studio（pip install git+... 即装；注意无 license，复用代码受限，演示用途自行评估）"
  - track: "双创-文书与申报"
    edge: "agent 产品研发平台叙事的现成素材：『图表数值可下钻到源记录、调查可保存重开、监控以代码定义且带覆盖率检查』的证据链式可观测，支撑申报书里『训练过程可审计、质量可追溯』的工程治理章节；对 TRL GRPO/PPO 回调与 verl logger 的原生接入说明可与主流训练栈叙事衔接"
    reuse_cost: 中
    open_source: "https://github.com/Sheltercosmo/Rilldex-RL-Studio（架构与交互设计可转译进申报材料；无 license 限制直接代码复用）"
sources:
  - url: https://github.com/Sheltercosmo/Rilldex-RL-Studio
    title: "Sheltercosmo/Rilldex-RL-Studio 仓库页（API 元数据：16 stars/2026-10-16 创建/2026-10-19 最后推送/无 license/Python，2026-10-20 实查）"
    accessed: "2026-10-20"
  - url: https://raw.githubusercontent.com/Sheltercosmo/Rilldex-RL-Studio/main/README.md
    title: "README 全文（单元图/计划与尝试/训练总览产品导览、TRL GRPO-PPO 与 verl 接入、reward hacking 检测、SQLite 工作区、Python/SQL 查询导出、示例图注明用 OpenHands 公开轨迹+模拟训练曲线）"
    accessed: "2026-10-20"
---

# Rilldex RL Studio：从训练曲线到 agent 行为的 RL 可观测台

> 来源：https://github.com/Sheltercosmo/Rilldex-RL-Studio （README 与 GitHub API 元数据，2026-10-20 实抓）。Python，2026-10-16 创建、10-19 仍在推送，无 license。

## 是什么

面向 LLM agent 强化学习（GRPO/PPO）的可观测工作台：采集 rollout 与训练器原生指标后，提供四类视图与取证能力——(1) **行为地图**：单元、动作、反馈、 expressed plans、分支与重复尝试的关联图，可下钻每条解读的源记录；(2) **训练总览**：reward、任务成功、复检成功与 loss/entropy/KL/clipping/token 吞吐按同一 cohort 对齐展示，显式标注人群/时钟/单位与缺失数据；(3) **reward hacking 检测**：内置常见行为检查 + 自定义奖励专属检测器，标记后可逐 rollout 溯源；(4) **代码优先分析**：rollout、图节点边、测量与训练日志全量可经 Python/SQL 查询，导出 JSONL/CSV。TRL GRPO/PPO 回调与 verl logger 字典原生接入，保留 objective/版本/writer/重启边界；本地 SQLite 工作区，支持持续采集、中断续传、暂存批量导入。

## 解决什么问题

agent RL 训练的失败大多不在最终 reward 曲线上：agent 可能学会钻奖励空子、陷入重复尝试、或"成功"指标与真实行为脱节。现有训练面板只给标量曲线，行为层面的证据（agent 到底做了什么、为什么拿到这个奖励）无从查起。Rilldex 把行为轨迹与训练信号放进同一可查询工作区，让"为什么变好/变坏"可取证。

## 相比前方法优势

- **行为级而非标量级**：单元图把动作-反馈-重试串成可导航证据链，对比 TensorBoard/W&B 类纯曲线面板；
- **reward hacking 一等公民**：内置检测器 + 证据下钻，多数训练监控方案只能靠人盯 rollout；
- **证据可核查口径诚实**：README 明示示例图用 OpenHands 公开轨迹 + 模拟训练曲线渲染、语义图需配置模型观察、缺失证据保持不可用态；
- **接主流训练栈**：TRL/verl 原生回调，非玩具管线。

## 局限（如实标注）

- **无 license**：16 stars 新仓（2026-10-16 创建），任何代码复用都有授权不确定性，只能作架构参考或自行评估风险；
- **无社区验证**：星数低、创建仅 4 天，稳定性与长期维护未知；
- **示例与实测的边界**：README 图表为保存的应用内容渲染（行为图用 OpenHands 公开轨迹、曲线为模拟数据），真实训练场景下的效果未见第三方报告；
- 语义地图依赖模型观察配置，纯采集模式看不到语义层；训练本身仍需自有 GPU 基建，本工具只覆盖观测层。

## 如何用于比赛（比赛映射展开）

1. **黑客松-数据与算法（agent RL/训练类赛题）**：赛期用它做两件事——(a) 训练现场的可视化证据台：把自家 agent 的 rollout 喂进去，演示行为地图与 reward hacking 检测，形成"我们控制训练过程"的现场说服力；(b) 调试工具：发现重复尝试/奖励钻空子的具体案例改奖励函数。reuse_cost 中：pip 即装但需接自有训练任务，无 license 限制直接改码，赛期按演示目的使用并注明来源。
2. **双创-文书与申报（agent 研发平台/工程治理）**：把"行为地图 + 原生训练指标 + 检测器 + SQL 取证"的观测架构转译为申报书里 agent 研发平台的质量保障章节——对比叙述"传统面板只有曲线，我们能回答 agent 为什么这么做"。reuse_cost 中：设计模式可转译，代码复用受无 license 限制。
