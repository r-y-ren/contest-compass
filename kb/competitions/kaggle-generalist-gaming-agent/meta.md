---
id: kaggle-generalist-gaming-agent
name: "Generalist Gaming Agent（普林斯顿通用游戏智能体赛，实时浏览器游戏 Code Competition，$50k）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：The Trustees of Princeton University（Office of Technology Licensing, 34 Chambers Street, Princeton, NJ 08542，rules §B 直抓）；赛事名 'Generalist Gaming Agent'，定位为实时交互基准——测 AI 智能体玩从未见过的游戏（data-description 页直抓）"
award_levels:
  - name: "1st Place"
    count_or_ratio: "$16,000（rules §B 与 Prizes 页双处直抓）"
  - name: "2nd Place"
    count_or_ratio: "$12,000（同上）"
  - name: "3rd Place"
    count_or_ratio: "$9,000（同上）"
  - name: "4th Place"
    count_or_ratio: "$7,000（同上）"
  - name: "5th Place"
    count_or_ratio: "$6,000（同上）；总池 $50,000（rules §B 'TOTAL PRIZES AVAILABLE'）"
key_dates:
  start:
    date: "2026-11-23"
    verified: true
    note: "Timeline 页 'November 23, 2026 - Start Date' 直抓"
  final_submission_deadline:
    date: "2027-03-01"
    verified: true
    note: "Timeline 页 'March 1, 2027 - Final Submission Deadline'（23:59 UTC）；CLI 列表卡 deadline 2027-03-01 双源互证（kb/raw/kaggle-list/snapshot-20261125.md）"
  entry_deadline:
    date: null
    verified: false
    note: "Timeline 页为模板变量 ${competition.ProhibitNewEntrantsExplicitDeadline}（catalog 已知事项：Timeline deadline 偶为模板变量需回退渲染抓取）——报名截止日期未实抓，参赛前须回查页面"
  team_merger_deadline:
    date: null
    verified: false
    note: "Timeline 页为模板变量 ${competition.TeamMergerExplicitDeadline}，同上待回查"
deliverables:
  - "Notebook Code Competition：提交须过 notebook（CPU/GPU 均 ≤9 小时运行、rerun 断网、NVIDIA RTX Pro 6000 96GB GPU 可用），每日 5 次提交、最多选 2 个 final submissions、团队 ≤5（Code Requirements 页与 rules §B(1)(2) 直抓）"
  - "单一离线 agent（/kaggle/working/agent.py 定义 Agent 类 + GGAInferenceServer 启动）连玩 32 个浏览器游戏×10 分钟游戏时间：只收像素帧 + 目标/操作简报，输出鼠标/键盘 11 类动作；启动（含模型服务）≤15 分钟、单决策 ≤90 秒（data-description 页直抓）"
  - "实时约束：游戏 20 FPS 不等 agent，每 4 帧（200ms）一个决策点，慢回复延迟生效不丢弃；异常回放 skip（data-description 页 Timing 直抓）"
  - "评分：每游戏 0–1 归一（floor=不动作 0 分，human baseline=1 分，上限 1）；公榜 = 16 游戏（含 4 样例）均值，私榜 = 其余 16 游戏均值并决定最终名次；提交后约 6 小时出分（data-description/Evaluation 页直抓）"
  - "数据集含评估 harness（gga/）、4 个样例游戏、starter 模板与两个官方 baseline notebook（LLM agent 与 decision model 各一）；其余 28 个隐藏游戏从不分发，agent 只见像素（data-description 页直抓）"
ai_policy:
  summary: >-
    官方 rules（2026-11-25 经 catalog 实证内容接口全抓，快照 kb/raw/kaggle-generalist-gaming-agent/pages-api-20261125.md）：①本赛目标即 AI 智能体使用——构建离线通用游戏 agent 是赛题本体；②推理环境硬约束：notebook rerun 断网（Internet access disabled），不得调用外部 LLM API——LLM 路线须自带权重在 notebook 内起本地服务（vLLM/llama.cpp，计入 15 分钟启动），或用官方 decision-model baseline；③外部数据允许：Freely & publicly available external data 含预训练模型（Code Requirements 页直抓），rules §6 外部数据/模型默认允许除非明令禁止，受 Reasonableness Standard 约束；④AMLT 允许（rules §6c）；⑤获奖许可与数据许可均为 MIT（rules §B WINNER LICENSE TYPE / DATA ACCESS 直抓），数据可用于商业/学术用途（rules §B4a）；⑥资格 18+ 全球（制裁地区除外），单账号，团队 ≤5；⑦标准公私双榜赛制（rules C7），平局先交者胜。规则未设 AI 辅助开发披露条款。
  url: "https://www.kaggle.com/competitions/generalist-gaming-agent/rules"
  checked: "2026-11-25"
credibility: 官网
last_verified: "2026-11-25"
sources:
  - url: "https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=165501"
    title: "Kaggle 官方内容接口全页快照（data-description/Description/Evaluation/rules/abstract/foundational-rules/Getting Started/Timeline/Prizes/Code Requirements 十页全文，原件 kb/raw/kaggle-generalist-gaming-agent/pages-api-20261125.md；赛 ID 165501 自 SSR 壳 og:image 提取，catalog SPA 绕行通道）"
    accessed: "2026-11-25"
  - url: https://www.kaggle.com/competitions/generalist-gaming-agent
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261125.md）：'Research · 50,000 Usd · 187 队 · deadline 2027-03-01'（列表卡口径；11-19 快照无此赛，11-23 开赛后新上榜）"
    accessed: "2026-11-25"
---

# Generalist Gaming Agent（kaggle-generalist-gaming-agent）— meta

## 概况（除标注外均为 2026-11-25 内容接口实抓，原件见信源[1]）

- **赛题本体**：通用游戏智能体——一个离线 agent 连玩 32 个未见过的实时浏览器游戏（10 个类型：平台/射击/解谜/竞速等），只凭像素帧+目标简报，用鼠标键盘动作边玩边学。官方动机：现有模型在会暂停等回复的文本/视觉基准上表现好，但"时钟不停"的实时场景下常常行动过迟或原地打转；此赛推进"边行动边规划"的 agent 架构（Description/abstract 页直抓）。
- **信息不对称设计**：4 个样例游戏可见可练，28 个隐藏游戏只有 game_id 不下发、开局才见像素与简报——考察规则学习与泛化，硬编码样例必败于私榜（16 个私榜游戏全为隐藏池）（data-description 页直抓）。
- **评测机制**：每游戏相对人类基线 0–1 归一，公榜均值（含样例）供过程参考、私榜均值定名次；每决策 ≤90s、启动 ≤15min、notebook ≤9h 实时预算内完成全部 32 局；同动作同延迟=同分，模型采样随机性典型带来 0.001–0.01 波动（data-description 页直抓）。
- **热度（列表卡口径）**：开赛两天 187 队（2026-11-25 CLI；11-19 快照无此赛，与 11-23 开赛日吻合）。
- **参与门槛**：需在 Kaggle notebook 内自托管模型推理（断网 rerun），RTX Pro 6000 96GB 赞助 GPU 可用；实时 200ms 决策节奏对推理延迟敏感，大模型路线须做量化/本地小模型或混合决策模型。

## 参与状态与窗口（2026-11-25 核对）

- 提交窗口内：终交 2027-03-01，距本轮约 14 周，窗口为当前 Kaggle 在役赛最长之一。**报名截止（Entry Deadline）为 Timeline 模板变量未实抓**——参赛前必须回查页面确认（见缺口清单）。
- 每日 5 次提交 + 2 个 final 选择额度宽裕，公榜含 4 样例游戏可作开发信号。

## 数据缺口与待核验清单

- [ ] **Entry Deadline / Team Merger Deadline 为 Timeline 模板变量**（${competition.ProhibitNewEntrantsExplicitDeadline}/${competition.TeamMergerExplicitDeadline}），需回退渲染抓取确认具体日期（catalog 已知事项）。
- [ ] 两个官方 baseline notebook（LLM agent / decision model）实现细节未读；28 个隐藏游戏的类型分布未披露。
- [ ] kicker：CLI 列表卡 187 队为列表口径，详情页侧栏数字未核。

- **2026-11-25（建条首验·CLI 列表卡）**：187 队；CLI deadline 2027-03-01 与 Timeline 页终交日一致，双源互证成立。（来源：kb/raw/kaggle-list/snapshot-20261125.md ；抓取日期：2026-11-25）
