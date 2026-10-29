---
id: arxiv-2610.11655
name: "Harness Evolution Hits a Ceiling：按失败构成分流——过程失败归 harness（4B 0.16→0.30），内容失败归权重（LoRA 内化 +0.13，placebo adapter 反而掉到基座之下）"
field: [LLM agents, harness 工程, 参数高效训练]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-08"
maturity: paper
venue_tier: arXiv
signal:
  venue: "arXiv（21 页 7 图 15 表；摘要页无代码链接）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "长程 agent 赛题的迭代预算分配规则：按首个触发信号给失败轨迹分类——过程失败（调用被阻断/死循环/步数耗尽）交给 harness 进化修复，内容失败（交付的方案本身差）才动权重；两步'先诊断后干预'法则避免在 harness 已到天花板后继续空转迭代，Qwen3.5-4B/9B × DeepPlanning 与 WebArena-Lite 的交叉实验给出可引用的量化依据"
    reuse_cost: 中
  - track: "Kaggle-竞赛"
    edge: "agent 类 Kaggle 赛（工具调用/游戏 AI）的训练数据质检模板：placebo 对照设计（用答案打乱的轨迹训 adapter 反而低于基座）可直接搬为自检——若自家微调增益在 placebo 下不消失，说明增益可能来自数据里的伪线索而非能力；WebArena-Lite 上'增益住在模型看到的东西里时 adapter 无增益'的发现提示先定位增益位置再投算力"
    reuse_cost: 中
sources:
  - url: https://arxiv.org/abs/2610.11655
    title: "Harness Evolution Hits a Ceiling: When Weight Training Should Begin（arXiv abs 页，v1 2026-10-08，Yuan Tian/Bing Hu/Hao Wang/Binghang Lu/Fang Wu，Comments：21 页 7 图 15 表）"
    accessed: "2026-10-29"
---

# Harness Evolution Hits a Ceiling：harness 修到几时该改练权重？看失败构成说话

> 来源：https://arxiv.org/abs/2610.11655 （v1 2026-10-08，Yuan Tian/Bing Hu/Hao Wang/Binghang Lu/Fang Wu，21 页 7 图 15 表；2026-10-29 经 arXiv API 实抓摘要）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

研究长程 LLM agent 的两条改进路线——**冻结模型进化 harness** vs **训练权重**——各自管什么、何时切换。方法是把 agent 的失败轨迹按"首个触发信号"分成两类：**过程失败**（调用被阻断、死循环、步数预算耗尽）与**内容失败**（交付了但方案本身差）。核心发现构成一条用两次的"先诊断后干预"法则：先读失败构成决定上 harness 还是上权重；再看 harness 已接受的修改改了什么，决定哪些增益值得训练进去。

## 解决什么问题

self-evolving harness 类工作只演示"harness 能涨分"，不回答"harness 涨到头了吗、剩下的问题是不是权重的事"。本文用交叉实验（种子/进化 harness × 基座/训练权重）把两条路线的增益归属拆开。

## 相比前方法优势

- 增益归属有数字：DeepPlanning 上自进化 harness 把 Qwen3.5-4B 持出分 0.16→0.30、9B 0.32→0.44；4B 持出交付率 55%→90%，而内容失败留给权重；
- 训练进权重的可行性与边界都有：在进化 harness 轨迹上训 LoRA，原 harness 下两尺寸 +0.13；4B 上 adapter 与 harness 叠加超翻倍，9B 上 adapter 单独追平完整进化线（内容失败从四分之一轨迹降到二十分之一）；
- 有阴性对照：答案打乱轨迹训的 placebo adapter 低于基座——增益确实来自轨迹质量而非数据量；
- 跨基准检验切换条件：WebArena-Lite（117 个未见任务）+0.09，且该基准上增益"住在模型看到的东西里"、adapter 无增量——恰好演示了"增益位置决定该用哪个杠杆"。

## 局限（如实标注）

- 摘要页无代码链接，21 页细节未读，LoRA 训练超参与进化循环实现不可直接复用；
- 实验以 Qwen3.5 家族为主（共八模型六家族两基准），家族外推需读全文；
- 分数是四次 rollout 均值（除标注外同夜对照），长程任务方差下样本量偏小的风险需读正文评估；
- "失败构成"分类依赖首个触发信号的启发式，分类误差如何传导到决策未在摘要说明。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：agent 赛迭代时先做失败构成审计（把坏轨迹按首信号分两桶）——两桶比例就是"harness 还要不要继续磨"的量化答案；过程失败占主导时继续改 harness 零训练成本，内容失败占主导再考虑微调，避免把马拉松预算花在天花板上。
- **Kaggle-竞赛**（reuse_cost 中）：placebo adapter 设计（答案打乱训练应掉回基座）作为微调实验的标准自检位，防"增益来自泄漏或伪线索"；WebArena-Lite 的教训迁移为"先确认增益住在哪（输入内容 or 行为策略）再决定 LoRA 还是改检索/改提示"。

**族内定位**：库内 arxiv-2609.24972（RRSI，harness 正则化递归自改进）占"harness 进化方法"位，arxiv-2610.00906（ActiveSaddler）占"harness 自动优化课程层"位；本卡占"harness vs 权重的切换判据"位——是这条线的"停止规则"，与前两者方法卡互补。
