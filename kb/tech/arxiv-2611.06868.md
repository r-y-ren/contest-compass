---
id: arxiv-2611.06868
name: "Turn-Level Best-of-N：每轮生成 N 个候选动作、选择器模型挑一个——长程任务精度 +5~10%，重试次数下降"
field: [LLM agents, 推理时扩展, inference-time scaling]
directions: [黑客松与数据竞赛, 创新创业大赛]
published: "2026-11-04"
maturity: paper
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv（generator-selector 双模型框架；长程 terminal 任务实测；强调用 off-the-shelf 开源权重模型当选择器，不训 reward model）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "agent 类赛题（长程多步任务、SWE-bench 式环境）里最便宜的性能杠杆：不改模型不加训练，每轮让小模型生成 N 个候选动作、另一个现成开源模型直接对比挑一个——精度 +5~10% 且多次重跑的一致性提升；官方对照证明不需要专门训练的 critic，现成 open-weight 模型就能胜任比较，48 小时 hackathon 内可落地"
    reuse_cost: 低
    open_source: "无官方仓（2026-11-07 实抓摘要未附代码链接；方法两行 prompt 工程即可自建）"
  - track: "Kaggle-竞赛"
    edge: "LLM agent 赛道（如 agent 性能榜）的推理时 scaling 基线：turn-level 粒度比终局 best-of-N 省 N 倍 rollout 成本——错误在发生当轮就被拦截，而不是整条轨迹跑完再挑；轨迹分析显示任务指令遵循、调试与测试行为增加，这些恰是 agent 赛评分的行为项"
    reuse_cost: 低
    open_source: "无官方仓（同上）"
sources:
  - url: https://arxiv.org/abs/2611.06868
    title: "On Turn-Level Best-of-N Sampling for Scaling LLM Agents（arXiv abs 页，2026-11-04，摘要经 arXiv API 实抓）"
    accessed: "2026-11-07"
---

# Turn-Level Best-of-N：把推理时扩展的粒度从"轨迹"降到"回合"

> 来源：https://arxiv.org/abs/2611.06868 （v1 2026-11-04，摘要经 arXiv API 实抓，2026-11-07）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

对 LLM agent 的**回合级 best-of-N 采样**做系统评估：generator-selector 框架下，每一回合由 generator 生成 N 个候选动作、selector 模型比较后择一执行。与既往"critic 引导搜索"工作的差异点：不训练专门的评判模型，直接检验**现成开源权重 LLM 能否有效比较候选动作**。在长程 terminal 任务上：精度提升 **5-10%**，多次尝试间的**一致性**显著改善；轨迹分析显示行为向良性迁移——解题尝试次数减少、指令遵循与调试/测试行为增多。

## 解决什么问题

outcome-reward 式的终局 best-of-N 要把 N 条完整轨迹跑到底再挑最好的，成本 O(N×轨迹长) 且反馈来得太晚；每轮只有一次机会的 agent 则一步走错满盘输。turn-level 粒度把选择前移到每个动作发生前，用"当轮比较"替代"终局挑选"。

## 相比前方法优势

- **无训练依赖**：选择器就是现成 open-weight LLM——不训 reward model、不加 rollout，部署面只有 prompt/编排改动；
- **成本结构优**：每轮 N 个单步候选 << N 条全程轨迹，同样的算力预算下可用更大的 N；
- **一致性是隐形加分**：多次重跑稳定性提升，对"以最好一次/平均成绩计分"两类赛制都友好；
- **行为证据**：不止分数涨，调试/测试等过程性行为可见增加——在评分含过程项的赛道是直接收益。

## 局限（如实标注）

- 选择的可靠性受限于现成模型"看动作猜好坏"的能力——摘要未报告 selector 在哪些任务类型上失灵（如需要环境状态才能判断的动作）；
- N 与 generator/selector 规模组合的预算-收益曲线摘要未给出，需读全文；
- 实验域为 terminal 类长程任务，游戏/具身/网页任务外推未证；
- 无官方代码释出（本轮实查），复现按摘要自建——方法简单但选择器 prompt 设计细节在全文里。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：agent 赛道的"最后一晚提分件"——generator 用主力模型、selector 用另一个开源模型，每轮 3-5 候选；由于不动权重、不动环境，可以赛前几小时内叠加到任何现成 agent 框架上 A/B 验证。
- **Kaggle-竞赛**（reuse_cost 低）：agent 赛 or LLM 工程赛的推理预算规划：turn-level BoN 与 self-consistency/终局 BoN 组成 scaling 菜单，按"单步可判 vs 终局才可判"分配预算；轨迹行为改善（指令遵循/调试）在含 rubric 评分的赛道直接兑现。

**族内定位**：库内推理时扩展家族已有 omp-best-of（Best-of-N + LLM verifier 的编码 agent 编排插件，repo 卡）占"候选级+工具化"位、零样本协调（ZSC）卡占多 agent 协作位；本卡占"**回合级粒度的系统评估**"位——与 omp-best-of 的差异是粒度（每轮 vs 每次产出）与证据形态（评测论文 vs 可跑插件），实操可互相借 selection prompt。
