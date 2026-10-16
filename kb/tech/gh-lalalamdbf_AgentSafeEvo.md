---
id: gh-lalalamdbf_AgentSafeEvo
name: "AgentSafeEvo：LLM Agent 安全的攻防对抗共同演化框架（攻击者-防御者 GRPO 联合训练）"
field: [LLM agents, agent 安全, 对抗鲁棒性, 强化学习]
directions: [创新创业大赛]
published: "2026-10-12"
maturity: demo
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: GitHub
  stars: 27
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "AI 安全赛道的红蓝攻防演示与红队压测底座：官方已发三个 Qwen3-8B 权重（HF 公开，2026-10-16 API 实查），vLLM 起服务即可把 Attacker-RL 当自适应红队对自己队伍的 agent 作品做多轮攻击压测，现场展示『共同演化攻击者 vs 静态攻击』的 ASR 对比（作者自报 Agent-SafetyBench 50.37→6.53、AgentDojo ASR 22.20→6.18）——多数队只演示功能，演示『用持续演化的红队测自己的作品并给出加固前后数据』是评审可感知的安全维度代差；六类攻击×50 场景×约 7000 工具的任务构造器可直接搬来当赛题评测集"
    reuse_cost: "中"
    open_source: "https://github.com/lalalamdbf/AgentSafeEvo（MIT；HF lalalamdbf/AgentSafeEvo-{Defender,Attacker-SFT,Attacker-RL}-Qwen3-8B 公开可下）"
  - track: "双创-文书与申报"
    edge: "『AI 安全自演化攻防』选题的技术底座与叙事背书：攻防共同演化（攻击随防御进化而持续升级）是申报书里自洽且有方法论门槛的技术主线，论文（arXiv 2610.19422）+开源框架+可下载权重三件套构成可行性证明；learnability-guided task weighting（按任务内 defender 奖励方差加权任务贡献）可包装为训练效率创新点，对比普遍的『提示词过滤/护栏』类项目有代际区隔"
    reuse_cost: "中"
    open_source: "https://github.com/lalalamdbf/AgentSafeEvo（MIT，捆绑 veRL 运行时与训练脚本）"
sources:
  - url: https://github.com/lalalamdbf/AgentSafeEvo
    title: "lalalamdbf/AgentSafeEvo: An Adversarial Co-Evolution Framework for LLM Agent Safety"
    accessed: "2026-10-16"
  - url: https://arxiv.org/abs/2610.19422
    title: "AgentSafeEvo: Adversarial Co-Evolution for LLM Agent Safety（2026-10-14 v1，cs.AI）"
    accessed: "2026-10-16"
  - url: https://huggingface.co/api/models?author=lalalamdbf
    title: "HF 权重可达性实查（Defender/Attacker-RL/Attacker-SFT 三权重公开，2026-10-16）"
    accessed: "2026-10-16"
---

# AgentSafeEvo：把 agent 安全做成"攻击者与防御者共同进化"的博弈

## 是什么

2026-10-12 开源的攻防共同演化强化学习框架（MIT，Python 3.12，Linux x86_64 + NVIDIA GPU；2026-10-16 实抓 GitHub API + README），配套论文 arXiv 2610.19422（2026-10-14 v1，cs.AI，Wang et al.，无 venue 标注）。核心设定：attacker 在多轮工具交互中构造对抗性任务暴露防御者弱点，defender 学习在攻击下仍完成合法任务，双方用 GRPO 联合训练，配 learnability-guided task weighting（以任务内 defender 奖励方差衡量可学性、据此加权任务贡献）。攻击面覆盖六类（直接/间接提示注入、工具描述注入、误信息、有害工具执行、越狱），任务空间 50 个 agent 场景、约 7000 工具。仓库实抓结构：`agentsafeevo/`（任务构造/trainer/agent 循环/配置）+ 捆绑 `verl/` 运行时 + `data/`（12000 训练种子、200 验证）+ 两阶段训练脚本（LLaMA-Factory SFT 攻击者 → veRL GRPO 联训，默认 8×GPU、120 步）+ 消融启动器（Static-AT/无加权/单侧加权）；README 附快速评测路径（vLLM 起已发布 defender + 捆绑 AgentDojo 评测）。HF 已公开三个 Qwen3-8B 权重（Defender / Attacker-SFT / Attacker-RL）与 20322 条 SFT 数据集（2026-10-16 HF API 实查确认可达）。

## 解决什么问题

静态安全训练（SFT 对固定攻击集）的防御是"对昨天的攻击免疫"：攻击者一旦适应即失效。本工作把 agent 安全训练建成攻防共同演化博弈——防御者面对的攻击分布随自身进化而持续升级，缓解安全训练的分布过拟合；learnability weighting 则解决联训中任务贡献不均（对防御者过易/过难的任务几乎不产生梯度信号）的问题。评测同时看安全与通用能力两头，回应"安全对齐牺牲能力"的老矛盾。

## 相比前方法优势

- **对比静态防御架构**（库内 WebMCP-Phalanx/SARA/PlanFence 等推理时防线）：这是训练时方法，产出权重级鲁棒性，与架构层正交、可叠加——防线挡注入，权重抗诱导；
- **对比静态红队评测**：攻击者与防御者共同演化，训练与评测都不依赖一次性的固定攻击集，防"攻击分布过时"；消融脚本可直接复现 Static-AT 等对照；
- **安全-能力双赢口径**（作者自报）：Agent-SafetyBench ASR 50.37→6.53、AgentHarm 53.64→6.18、AgentDojo ASR 22.20→6.18，同时 ALFWorld 30.28→43.72、ToolHop 21.84→48.04、BFCL-V3 基本持平——多数安全训练以通用能力为代价，此处反而提升。

## 局限（如实标注）

- **极年轻、零第三方验证**：2026-10-12 创建、2 commits、27 stars，论文为 arXiv v1 无 venue，全部数字为作者自报未经独立复现；
- **完整复训门槛高**：GRPO 联训默认 8×GPU×120 步，比赛期间重训不现实；开箱可跑的是推理侧（vLLM 起 HF 权重 + AgentDojo 评测）；
- 权重仅 Qwen3-8B 一系，跨模型家族泛化未验证；异构 attacker-defender 配对"pending release"；
- Linux + NVIDIA 硬依赖，Windows 赛队需 WSL2 或云 GPU；
- 训练出的攻击者/防御者绑定其 50 场景任务分布，迁移到自建场景需重做任务构造。

## 如何用于比赛

1. **AI 安全赛道黑客松：自适应红队压测（主用）**——不重训，只做推理侧：vLLM 起 Attacker-RL 权重当红队，对自己作品（任何 LLM+工具链 agent）跑多轮攻击，对比静态攻击提示与共同演化攻击者的 ASR 差；再叠一层库内静态防御卡（如 WebMCP-Phalanx 权限分离）展示"攻击升级→架构加固"的闭环叙事。评测集可直接用其六类攻击任务构造器生成。
2. **双创申报：『AI 安全自演化攻防』项目主线**——技术故事自洽（对抗持续升级、防御共同进化）、有三件套可行性背书；演示视频可录"Attacker-RL 攻击未加固 agent 成功 → Defender 权重替换后抵御"，视觉冲击直接。
3. **成本提示**：云租 8×GPU 复训约千美元级，赛队一般不必要；把预算花在推理侧演示与评测集复用上，性价比最高。
