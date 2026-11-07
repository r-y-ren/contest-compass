---
id: arxiv-2611.06500
name: "Coca-Cola：工具观测压成隐 token 喂给 agent——token 省 70-89%、端到端提速 24-56% 且任务反升"
field: [LLM agents, 上下文压缩, latent space]
directions: [黑客松与数据竞赛]
published: "2026-11-04"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv + 官方仓 THU-Agent/Coca-cola（GitHub API 实查：3 stars，2026-11-04 刚创建，无 license 信息——代码在但社区验证为零）"
  stars: 3
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "agent 赛道普遍按 token/成本计分或设上下文硬限——Coca-Cola 把工具返回的原始观测（网页/搜索结果）压缩进 agent 输入嵌入空间的连续隐 token，跳过'离散文本'这个表示瓶颈：官方数字 token 消耗降 70-89%、端到端运行时降 24-56%，四个 QA 基准上任务表现不降反升；长程多步 agent 的上下文膨胀问题从此有'表示层'解法，而非只在文本层做剪枝/摘要"
    reuse_cost: 中
    open_source: "github.com/THU-Agent/Coca-cola（刚建仓，3 stars，无 license——使用前核查）"
  - track: "Kaggle-竞赛"
    edge: "凡评分含成本/延迟项（token 预算赛、效率加权榜）的 agent 赛道，压缩率 70-89% 直接换算成榜上分数；Action-Preserving Training（对齐压缩前后 next-action 分布）是可复用的训练配方——若赛道允许微调，可为赛道专训压缩器"
    reuse_cost: 中
    open_source: "同上官方仓"
sources:
  - url: https://arxiv.org/abs/2611.06500
    title: "Tools Need Not Speak in Text: Latent Context Compression for Agents（arXiv abs 页，2026-11-04，摘要经 arXiv API 实抓）"
    accessed: "2026-11-07"
  - url: https://github.com/THU-Agent/Coca-cola
    title: "官方代码仓（GitHub API 实查：3 stars、1 fork，2026-11-04 创建并推送，无 license 与描述）"
    accessed: "2026-11-07"
---

# Coca-Cola：工具观测不必说人话——隐 token 上下文压缩

> 来源：https://arxiv.org/abs/2611.06500 （v1 2026-11-04，摘要经 arXiv API 实抓）；官方仓 https://github.com/THU-Agent/Coca-cola 信号经 GitHub API 实查（2026-11-07）。本卡内容出自本次抓取的摘要与仓库元数据，未读 PDF 全文。

## 是什么

挑战"agent 必须以离散文本 token 消费工具输出"这一默认假设。提出 **Coca-Cola**：把工具观测压缩成连续隐 token、直接注入 agent 的输入嵌入空间。配套 **Action-Preserving Training**：约束 agent 在"完整观测"与"压缩观测"下的 next-action 分布一致，迫使压缩器只保留决策充分信息（action-sufficient）。实测（web-search agent，4 个 QA 基准 × 2 个模型族）：token 消耗降 **70.01%-89.24%**，端到端运行时降 **24.45%-55.97%**，任务表现**一致提升**。代码已释出（github.com/THU-Agent/Coca-cola）。

## 解决什么问题

多步 agent 把原始工具输出一路堆进上下文：token 账单膨胀、注意力被噪声稀释。文本层剪枝/摘要受"离散 token"表示上限约束，压不干净还丢信息。Coca-Cola 把瓶颈从表示层移走——观测以连续向量进模型，压缩比不再受词表离散度限制，且训练目标直接对齐"决策够用"而非"文本还原"。

## 相比前方法优势

- **压缩比上一个量级**：70-89% 对比文本摘要类方法（通常 30-60% 且有损任务信息）；
- **任务反升**：不是"压缩后勉强不掉点"，而是四个基准一致提升——噪声稀释注意力的问题被顺带解决；
- **训练目标可迁移**：Action-Preserving 的对齐思路不绑定网页搜索场景，任何"观测→动作"管线都能套；
- **有代码**：官方仓已释出（虽然极新），2 模型族的实验证据说明不是单模型巧合。

## 局限（如实标注）

- **成熟度极低**：官方仓 2026-11-04 创建（论文发布当天），3 stars、无 license、无 README 描述——复现风险自担，接入前先核对许可证；
- 需要训练压缩模型（对每个 agent 主干各配一次），零训练场景不可用；摘要未报告训练成本与数据需求；
- 实验域限于 web-search QA agent，代码/具身/长程规划任务的迁移未证；
- 隐 token 与 agent 主干嵌入空间绑定——换主干需重训压缩器，跨模型复用性存疑。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：token 计分/预算受限赛道的结构性优势项——但注意其训练前提：hackathon 时限内只适合直接用官方发布的压缩器（若有配套权重）或赛道主干恰好匹配的场景；纯推理期替代方案仍是文本层剪枝。License 未明，商用赛道慎入。
- **Kaggle-竞赛**（reuse_cost 中）：效率加权 agent 榜的候选武器；更稳的用法是借其 Action-Preserving 思路自训轻量压缩器（用赛道环境轨迹当训练数据），把"压缩率-动作一致率"曲线画进方案说明。

**族内定位**：库内上下文家族已有 Context Is a Pipeline（harness 信息损耗**诊断**）、QRAE 类检索压缩（候选池未入）与 oc（网站→CLI 文本压缩）占不同层——本卡占"**观测→隐空间的表示层压缩**"位，是目前压缩率上限最高的一档；诊断卡（Pipeline）的"工具结果被截断"证据恰好是本卡方法的问题来源，两卡连用构成"诊断→处方"叙事。
