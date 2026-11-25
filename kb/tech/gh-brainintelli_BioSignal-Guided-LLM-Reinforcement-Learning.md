---
id: gh-brainintelli_BioSignal-Guided-LLM-Reinforcement-Learning
name: "类器官电信号当 LLM agent 策略输入的首个全工件开源研究：Godot 生存游戏中 Qwen3.5-0.8B+MEA 重放输入，主结论多为阴性（跨芯片不复现、得分差 84-96% 由动作时长解释），96 checkpoint+18,720 评估回执全公开（141★ 一日）"
field: [LLM agents, reinforcement learning, organoid intelligence, 评测方法论]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-11-24"
maturity: demo
venue_tier: industry
reproducibility_level: high
signal:
  venue: "GitHub API 实查（2026-11-25）：brainintelli/BioSignal-Guided-LLM-Reinforcement-Learning，141 stars，2026-11-24 创建/推送（一日），Python；README 实抓：仓内自带 preprint PDF、游戏与训练源码、96 确认性 checkpoint（optimizer states）、18,720+ 评估回执 release、182 个原始 H5 电生理文件经第三方网盘分发"
  stars: 141
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "'类器官智能（OI）×具身智能'是申报书选题稀缺的差异化题材：本仓给出完整可引的证据链与诚实边界（主结果阴性、跨芯片不复现、审计偏差自曝）——双创文书可引用其'首个 OI 输入 LLM agent 的开源全工件研究'确立选题前沿性，同时借其阴性结果示范'不过度承诺'的合规叙事；附件级证据（checkpoint/回执/原始数据 SHA-256 清单）是答辩时'我们有实证纪律'的现成模板"
    reuse_cost: 低
    open_source: "github.com/brainintelli/BioSignal-Guided-LLM-Reinforcement-Learning"
  - track: "黑客松-数据与算法"
    edge: "游戏 AI/智能体对抗类黑客松的评测设计避坑案例：其核心方法发现——动作占用游戏时长不同，'按决策数配对'与'按真实时间截断'回答的是不同问题、首轮得分差的 84.3-95.9% 可由动作时长解释——直接适用于任何'动作粒度不均'的 agent 对比赛题（大动作 vs 小动作策略），两时钟评测（决策数与时钟各评一次）可写进赛题评分细则或自家 agent 的 ablation 设计"
    reuse_cost: 低
    open_source: "github.com/brainintelli/BioSignal-Guided-LLM-Reinforcement-Learning"
sources:
  - url: https://github.com/brainintelli/BioSignal-Guided-LLM-Reinforcement-Learning
    title: "GitHub 仓库（GitHub API 元数据+README 实抓：141 stars，2026-11-24 创建/推送，Python；含 preprint PDF、checkpoint/回执 release 链接）"
    accessed: "2026-11-25"
---

# 类器官信号驱动 LLM agent：一次"阴性结果也全裸开源"的病毒式研究

> 来源：https://github.com/brainintelli/BioSignal-Guided-LLM-Reinforcement-Learning （GitHub API 元数据+README 实抓 2026-11-25：141 stars，2026-11-24 创建/推送；README 自述含仓内 preprint《Language Model Exploration and Survival Behavior Under Offline Replay of Organoid Neural Signals》）。本卡内容出自本次抓取的仓库元数据与 README，未读 PDF 全文。

## 是什么

Brainintelli（上海）研究仓：把**离线重放的类器官（organoid）微电极阵列（MEA）电信号**作为 LLM agent 的策略输入，在 Godot 生存游戏中测其对探索与生存行为的影响。管线（README 实抓）：1 秒 MEA 窗口提取四个读数（对数发放率、通道激活占比、发放时间集中度、跨通道分布熵），经校准中位数/MAD 归一后进 Qwen3.5-0.8B 的 prompt 与 value 网络；LLM 冻结、PPO 只训 policy adapter；all-zero 控制组在校准后掩零。两个主实验：芯片 22021 首个类器官 16 seeds×48 maps 探索试验；96 个冻结模型×18,432 局的劣境开局试验（intact/shuffled/all-zero 三组）。**主结论诚实为阴性**：首轮 intact vs all-zero 探索均值 +1.99 格/局（95% 区间 1.18-2.73）但中位差为 0；等真实时间口径下区间跨零；**第二块芯片不复现**；劣境开局六个主区间全跨零；首轮得分差的 84.3%（intact）/95.9%（unstimulated）可由**动作时长**解释。审计透明：自曝"设计标识符在评估后更新、注册审计局源不可用、场景校验哈希与注册不符"等偏差并逐条区分。工件：96 checkpoint+optimizer states、182 个原始 H5（第三方网盘+SHA-256 清单）、18,720 评估回执 release。

## 解决什么问题

"生物信号能否增强 LLM agent"此前只有概念演示没有可审计的开源实证。该仓用**阴性结果+全工件**的方式把这个问题第一次放到可复现检验的位置：答案目前是"未见稳健效应"，且给出了为什么容易得出假阳性（两时钟混淆、芯片间生物变异）的机理分析。

## 相比前方法优势

- **配对实验设计**：seed+map 配对、决策数与游戏时间双口径截断——"得分差≠决策更好"的混淆被显式拆解，这是 agent 对比评测里少见的严谨度；
- **全证据链开源**：checkpoint/回执/原始电生理+校验清单，罕见于热点交叉题材；
- **阴性结果自曝+审计偏差自报**：区分设计偏差与重放检查，反炒作风气在 141★ 病毒式传播中尤显稀缺；
- **可复算**：配对明细（exploration.csv/actions.csv）允许读者复算均值与中位差的关系。

## 局限（如实标注）

- **效应主张为阴性**：跨芯片不复现、劣境全跨零——任何"生物信号提升 agent 能力"的引申都不成立，本卡如实按"阴性+方法论"定位；
- 一日新仓（2026-11-24 创建即 141★），病毒式热度未经沉淀，实验室为商业主体（brainintelli.com），preprint 未经同行评审；
- 原始数据经**第三方网盘**（Quark）分发，长期可得性与完整性依赖网盘；
- 自曝的审计偏差（评估后更新设计标识符、注册审计局缺失、哈希不符）削弱预注册效力，作者虽逐条区分，独立复核仍缺失；
- "organoid 重放→agent 输入"的科学意义本身有争议（重放非闭环、无组织反馈），README 亦承认留有"matched 合成输入对照未做"的开放问题。

## 如何用于比赛（比赛映射展开）

- **双创-文书与申报**（reuse_cost 低）：选题差异化引用源——"AI+类器官智能/生物混合智能"题材的申报书引其"首个全工件开源研究"定位前沿，再以其实测阴性引出己方更务实的技术路线（如合成信号对照、闭环反馈），避免评审追问"生物信号到底有没有用"时无据可依；其工件清单（checkpoint/回执/SHA-256）可当"实证纪律"附件模板。
- **黑客松-数据与算法**（reuse_cost 低）：直接借"两时钟评测"设计——凡动作粒度不均的 agent 赛题（游戏 AI、机器人任务规划），评分与 ablation 都应同时报"按决策步"与"按墙钟时间"两口径；84-96% 得分差可由动作时长解释的案例数据，是演示评测陷阱说服力的现成素材。
