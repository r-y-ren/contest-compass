---
id: gh-lalalamdbf_AgentSafeEvo
name: "AgentSafeEvo：攻击者-防御者共进化 RL 训练工具型 agent 安全（Qwen3-8B 五项安全基准 ASR 全线下降，AgentHarm 50.37→6.53）"
field: [LLM agents, agent safety, adversarial training]
directions: [创新创业大赛]
published: "2026-10-14"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv 2610.19422（2026-10-14 v1）+ GitHub lalalamdbf/AgentSafeEvo（API 实查 2026-10-16：27 stars/0 forks，MIT，Python，2026-10-12 创建，隔日仍在推送）+ HuggingFace 三检查点与 SFT 数据集"
  stars: 27
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "『AI+安全』类项目的技术护城河样本：不靠外挂审查框，而是把安全能力训练进 agent 权重——攻击者与防御者 GRPO 共进化 + 可学习性加权任务生成是可申报的创新点叙事；指标可直接引用（Agent-SafetyBench ASR 49.11→17.84，AgentHarm 50.37→6.53，AgentDojo ASR 22.20→6.18，且 BFCL-V3 通用能力不掉、ALFWorld 30.28→43.72 反升）——『安全不牺牲能力』正是评审最常质疑点"
    reuse_cost: 中
    open_source: "github.com/lalalamdbf/AgentSafeEvo（MIT，含 12000 RL seeds 与 200 验证集）+ huggingface.co/collections/lalalamdbf/agentsafeevo（攻击者 SFT/RL 与防御者三个 Qwen3-8B 检查点、20322 条 SFT 数据）"
  - track: "黑客松-数据与算法"
    edge: "agent 安全攻防赛道的完整武器库：六类攻击面（直接/间接提示注入、工具描述注入、虚假信息、有害工具执行、用户查询越狱）×50 场景×约 7000 工具的任务构造器可直接当评测环境用；演化攻击者生成的对抗任务也可用于己方 agent 的红队自测"
    reuse_cost: 中
    open_source: "同上；需 Linux x86_64 + Python 3.12 + NVIDIA GPU（vLLM 0.19.1 栈）"
sources:
  - url: https://github.com/lalalamdbf/AgentSafeEvo
    title: "官方仓库 README 与 GitHub API 元数据（2026-10-16 实抓：27 stars/MIT/Python；方法三步、主结果表、模型与数据清单、安装要求均出自本次抓取）"
    accessed: "2026-10-16"
  - url: https://arxiv.org/abs/2610.19422
    title: "AgentSafeEvo: Adversarial Co-Evolution for LLM Agent Safety（arXiv abs 页，v1 2026-10-14，Wang/Wen/Qi/Zhou/Jin/Lu/Zhang，2026-10-16 实抓；摘要页未附 comments）"
    accessed: "2026-10-16"
---

# AgentSafeEvo：把 agent 安全从"外挂护栏"搬进权重

> 来源：https://github.com/lalalamdbf/AgentSafeEvo （README + GitHub API，2026-10-16 实抓）与 https://arxiv.org/abs/2610.19422 （abs 页 v1 2026-10-14，2026-10-16 实抓）。本卡内容出自本次抓取的 README 与摘要页，未读 PDF 全文。

## 是什么

一个**攻击者-防御者共进化强化学习框架**，训练会调用工具的 LLM agent 在演化攻击下既完成任务又不被劫持。攻击者负责构造含用户查询、工具定义、模拟环境观测的对抗任务；防御者学会在恶意内容环绕下完成正当任务；双方凭防御者执行的安全/效用反馈同步进化。配套释出 arXiv 论文（2610.19422）、MIT 代码、三个 Qwen3-8B 检查点（攻击者 SFT/RL、防御者）与 2 万条 SFT 数据。

## 解决什么问题

多轮工具调用中，恶意内容可藏身于用户查询、工具描述或环境观测三处，把 agent 推向不安全行为。提示词级防御（Spotlighting）、外挂分类器（Prompt Guard 2）对演化攻击收效有限；静态对抗训练（SFT 后固定攻击者）又会被新攻击淘汰。本文要的是**防御能力随攻击分布共同成长**。

## 相比前方法优势

- **三步法**：红队攻击者 SFT 初始化 → 攻击者/防御者联合 GRPO 对抗训练 → 可学习性引导的任务加权（以任务内防御者奖励标准差为可学习性代理，变异大的任务在种子组内获得更大权重）；
- **数字扎实**：Qwen3-8B 上五项安全基准三独立跑均值±标准差全报告；对比静态 AT，Agent-SafetyBench ASR 31.01→17.84、AgentHarm 30.00→6.53；静态 AT 与共进化版通用能力（BFCL-V3 66.73/65.98）基本持平，排除了"安全靠牺牲能力"的解释；
- **判定纪律**：安全与效用判定各 +1/-1，完成有害目标不计入效用；纯有害请求安全拒绝即满足效用——避免"为效用分数暗中纵容"；
- **资产齐全可复跑**：RL 种子（6000 良性+6000 恶意）、验证集、SFT 数据、检查点全公开，任务源取自 TOUCAN，对抗合成用 Gemini 3 Flash Preview。

## 局限（如实标注）

- 防御者仅 Qwen3-8B 单骨干验证；README 自述异构攻防对（攻击者 Qwen3-8B × 防御者 Gemma4-E4B）**结果尚未释出**；
- 仓库 2026-10-12 创建、27 stars/0 forks，无第三方复现；安全判定 +1/-1 的判定器本身未在摘要/README 层面说明其可靠度；
- 训练栈要求 Linux + Python 3.12 + NVIDIA GPU（vLLM/FlashAttention），复现训练有硬件门槛；
- 论文 v1 无 venue；AgentDojo/MSB 等基准外的分布外攻击鲁棒性未报告。

## 如何用于比赛（比赛映射展开）

- **双创-文书与申报**（reuse_cost 中）：申报"AI+安全""可信智能体"类项目时，共进化训练 + 可学习性加权是现成的创新点叙事骨架；论文的三基准对照表是"我们的方法同时改善安全与能力"的证据模板。若自建 agent 产品，可用其演化攻击者对自家系统做红队回归测试（无需重训防御者）。
- **黑客松-数据与算法**（reuse_cost 中）：安全攻防类赛题直接借用其六类攻击任务构造器与评测协议；模型/数据在 HuggingFace 上可直接下载推理，黑客松时间盒内可完成"防御者评估 + 攻击者生成新对抗任务"的演示闭环。

**族内定位**：库内监控/审计路线（如 probes 检测欺骗、轨迹监控类卡）占"部署时发现"位，本卡占"训练时获得鲁棒性"位——外挂护栏与权重内防御互补，攻击面清单（六类）可与其余卡的评测协议互相引用。
