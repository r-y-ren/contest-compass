---
id: gh-dolev31_ProactiveInquirer
name: "ProactiveInquirer：LLM Agent 主动提问的水平/垂直度量与 Q&D 后果监督训练"
field: [LLM agents, agent 主动性与澄清提问, agent 评测方法]
directions: [创新创业大赛]
published: "2026-09-26"
maturity: demo
signal:
  venue: GitHub（IBM Research + Weizmann Institute，论文 arXiv:2609.37236）
  stars: 12
  runnable: true
competition_fit:
  - track: 双创-文书与申报
    edge: "产品差异化论据最硬的一档：\"会追问的 AI\"——零训练迁移的客服 agent 任务成功率 13%→34%（τ²-bench retail），主动澄清需求是客服/问诊/需求挖掘类 AI 产品评委可见的行为差异点；Apache-2.0 + HF 权重（LoRA/GGUF/merged 三形态）支持现场演示，论文出自 IBM Research 背书申报书技术叙事"
    reuse_cost: 中
    open_source: "https://github.com/dolev31/ProactiveInquirer（Apache-2.0）；模型 ProactiveInquirer-Qwen3-8B 已上 Hugging Face"
  - track: 黑客松-数据与算法
    edge: "agent 赛道赛题（信息不全需主动澄清的场景）的行为层差异化：Qwen3-8B LoRA 可本地部署，need-graph 无裁判评测协议可直接搬为项目自评方法论——\"不靠 LLM 打分\"的评测叙述在评审问答中天然加分"
    reuse_cost: 中
    open_source: "https://github.com/dolev31/ProactiveInquirer（pi run/pi score CLI，make smoke 离线端到端自检）"
sources:
  - url: https://github.com/dolev31/ProactiveInquirer
    title: "dolev31/ProactiveInquirer: Asking for What Was Never Requested — horizontal and vertical proactivity in LLM agents"
    accessed: "2026-10-04"
---

# ProactiveInquirer：LLM Agent 主动提问的度量与训练

> 来源：https://github.com/dolev31/ProactiveInquirer （GitHub 仓库页，12 stars / 0 forks，Apache-2.0，10 commits，IBM Research + Weizmann Institute 作者：Levy/Yehudai/Shlomov/Adi/Choshen；配套论文 arXiv:2609.37236；抓取日期 2026-10-04）

## 是什么

研究"LLM agent 在**无人要求时主动提问**"的完整开源研究栈（以下均来自本次实抓的仓库页）：论文、训练管线、评测协议、已发布模型权重四件齐。

- **概念框架**：区分两种主动性——水平（horizontal，需求已在当前状态中被点名）与垂直（vertical，需求只在新发现的证据中显现，即"问出从未被要求的东西"）；
- **need-graph 度量**：把 transcript 对照"需求依赖图"（从基准分解恢复）打分，**不使用 LLM judge / 奖励模型**，且在相同提问数下对比 agent；
- **Q&D（Questioner & Drafter）训练**：在决策点 fork 运行、各自续跑，保留"其续跑检索到更多必需证据"的那个提问——即**从提问的后果中学习提问**；训练阶梯为拒绝采样 SFT → 同状态问题对 DPO → 加停止对照的 DPO；
- **架构**：训练出的 questioner 决定"提问或停止" → retriever 回答 → 冻结的 drafter 把证据折进草稿；
- **成果**：ProactiveInquirer-Qwen3-8B（Qwen3-8B 的 LoRA 适配器，HF 提供 GGUF 与合并权重）。留出集上 MuSiQue 必需证据检索 78%（prompted Qwen3-8B）→ 90%；τ²-bench retail 任务成功率 13%→34%（base）与 12%→32%（stop 设定）；三个 QA 基准中两个胜过 prompted GPT-OSS-120B，且在**从未训练过的客服 agent 上任务成功率翻倍以上**；对照实验确认增益来自提问质量而非数量或长度。

## 解决什么问题

Agent 的主动性评估此前依赖 LLM judge（可被操纵、贵、不可复现），且"该问什么"缺乏可训练信号——没有"完美提问"标签。本文给出两个补丁：无裁判的 need-graph 度量，以及把监督信号从提问本身挪到**提问后的检索后果**上。

## 相比前方法优势

- **评测可信度**：need-graph 度量去 LLM judge 化，等提问数对比排除了"多问就赢"的假象；
- **训练信号新颖且可复用**：后果监督（continuation retrieves more required evidence）不需要人工标注提问质量，fork-续跑-保留的流程是通用配方；
- **工程完整度高**：全 CLI（pi data fetch/build、pi run、pi score、pi agg、pi train）、CI、5000+ 测试、`make gate`/`make smoke` 无 API key 离线自检；基准数据 sha256 锁定不重分发；
- **权重已发布**（LoRA + GGUF + merged），demo 可达性在同档研究仓库中属最好一档。

## 局限

- **模型底座绑定 Qwen3-8B**：LoRA 训练/推理需 GPU 或量化运行时，端侧场景需 GGUF 路线自验精度损失；
- **社区极小**：12 stars、5 个 open issue、10 commits，无外部使用背书，踩坑需自己读源码；
- **need-graph 依赖基准分解**：需求依赖图从既有基准的分解中恢复，新领域（如赛题场景）要自建图，度量协议迁移有工程量；
- **数字为论文自报**：78→90、13→34 等均来自仓库 README/论文口径，写入对外材料前须自测复现（铁律 4）；
- 训练阶梯（RS-SFT + 两轮 DPO）复现需中等算力与数据构建，赛期内更现实的路径是直接用已发布权重。

## 如何用于比赛（比赛映射展开）

- **双创-文书与申报**：客服/问诊/需求挖掘类"AI+"项目的核心差异化叙事——"我们的 agent 会主动追问缺失信息"配 τ²-bench 13%→34% 的迁移数字（标注论文自报）与 IBM 系出身；技术路线可直接采用已发布 Qwen3-8B 适配器做产品原型，申报材料强调"无裁判评测"的工程严谨性；
- **黑客松-数据与算法**：agent 赛道中"信息不全"类赛题（需求澄清、多轮信息收集），本地部署 8B 适配器 + 提问行为对比 demo（naive RAG vs 主动追问）形成可见差异；need-graph 协议搬为项目自评方法学；
- **边界提醒**：对数模/Kaggle 类纯建模赛种无自然落点，勿强行映射；directions 按候选继承为创新创业大赛。
