---
id: gemma-4-dev-agent
name: "Google - The Gemma 4 Developer Agent Competition（Gemma 4 后训练 autonomous coding agent 赛，$65k 主赛 + $35k paper 姊妹赛道）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, California 94043 USA，rules §1.2 直抓）；Kaggle 平台承办（Featured Prediction Competition）"
award_levels:
  - name: "1st Place"
    count_or_ratio: "$37,000（rules §1.5 与 Prizes 页双处直抓）"
  - name: "2nd Place"
    count_or_ratio: "$18,000（同上）"
  - name: "3rd Place"
    count_or_ratio: "$10,000（同上）；主赛小计 $65,000"
  - name: "Paper Submission Award（姊妹赛道，$35,000 池）"
    count_or_ratio: "主赛 Prizes 页：optional paper award 共 $35,000，2026-11-12 11:59PM UTC 截稿，经 paper 赛道（kaggle.com/competitions/gemma-4-developer-agent-paper）提交；2026-10-11 列表卡口径 189 队（列表卡口径）"
key_dates:
  start:
    date: "2026-09-23"
    verified: true
    note: "Timeline 页直抓 'September 23, 2026 - Start Date'"
  paper_deadline:
    date: "2026-11-12"
    verified: true
    note: "Timeline 页 'November 12, 2026 (optional) - Deadline to submit Research Paper'（11:59 PM UTC）"
  entry_deadline:
    date: "2026-11-25"
    verified: true
    note: "Timeline 页 'November 25, 2026 - Entry Deadline'（须在此前接受规则才能参赛；11:59 PM UTC）"
  team_merger_deadline:
    date: "2026-11-25"
    verified: true
    note: "Timeline 页 'November 25, 2026 - Team Merger Deadline'"
  final_submission_deadline:
    date: "2026-12-02"
    verified: true
    note: "Timeline 页 'December 2, 2026 - Final Submission Deadline'（11:59 PM UTC）"
deliverables:
  - "submission.zip（Agent Config）：agent.yaml 必须在根目录，可含 sampling 参数、system prompts、sub_agents（ADK AgentTool）、PEFT LoRA adapters、ADK Skill 目录（SKILL.md+scripts+resources）——遵循 Google ADK Agent Config 规范加沙箱限制（Evaluation 页直抓）"
  - "唯一基模 gemma-4-31b-it-qat-w4a16-ct（Kaggle Models：google/gemma-4）；每个 agent/subagent 都必须用该模型，可配不同 LoRA adapter（Model Selection 节直抓）"
  - "每日 1 次提交、最多 2 个 final submissions、团队上限 5 人（rules §2 直抓）"
  - "agent 在 12 小时总预算内为全部任务产出补丁（含沙箱搭建，不含验证）；9 个预定义工具（run_command/submit_patch/read_file/edit_file/write_file/get_code_neighbors/search_similar_code/get_code_subgraph/get_status）+ 自定义 subagent（Harness Rules 节直抓）"
ai_policy:
  summary: >-
    官方 rules（2026-09-24 经 kaggle CLI 2.2.4 OAuth 全站实抓，存 kb/inbox/gemma-4-dev-agent/）：①外部数据与模型允许——"The use of external data
    and models is acceptable unless specifically prohibited by the Host"，LLM/工具受 Reasonableness
    Standard 约束（Gemini Advanced 级订阅可接受、超奖金成本的专有数据集不合理）；②AMLT 允许（须持许可）；③外部 LLM 蒸馏合规是社区焦点——2026-09-24
    topics 帖 742882-distill（14 票）问蒸馏合规，规则仅有 Reasonableness 条款、无明确禁令，官方未回帖；④获奖许可
    Apache 2.0（Open Source），竞赛数据 Apache 2.0 商用可用；⑤资格 18+ 全球（制裁地区除外），单账号，团队 ≤5。规则未设
    AI 辅助开发披露条款；本赛目标即 agentic AI（后训练 Gemma 4 成 coding agent），AI 使用是赛题本体而非合规风险。
  url: https://www.kaggle.com/competitions/gemma-4-developer-agent/rules
  checked: "2026-09-24"
credibility: 官网
last_verified: "2026-10-19"
sources:
  - url: https://www.kaggle.com/competitions?sortBy=latestDeadline
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261019.md）：主赛卡片 'gemma-4-developer-agent · Featured · 65,000 Usd · 3277 队 · deadline 2026-12-02'、paper 赛道卡 'gemma-4-developer-agent-paper · Featured · 35,000 Usd · 280 队 · deadline 2026-11-12'（列表卡口径）"
    accessed: "2026-10-19"
  - url: https://www.kaggle.com/competitions/gemma-4-developer-agent
    title: "Kaggle 竞赛列表 active 页快照（browser-use 预抓，kb/raw/kaggle-list/snapshot-20261011-active.md）：主赛 2422 队（10-05 快照 1684 队，+738）、2 months to go、$65,000；paper 赛道卡 189 队、A month to go、$35,000；主赛卡片标签 10-05 'Hackathon'→本轮 'Featured'（列表卡口径）"
    accessed: "2026-10-11"
  - url: https://www.kaggle.com/competitions/gemma-4-developer-agent
    title: "全站实抓页面合集（kaggle CLI 2.2.4 OAuth，competitions pages/files/leaderboard/topics）：Description/Timeline/Evaluation/Model&Harness Rules/data-description/Prizes/rules 全文/foundational-rules/abstract/榜单快照/社区帖摘要——原件存 kb/inbox/gemma-4-dev-agent/gemma4-competition-pages.md（抓取通道与 .meta.yaml 同目录，勿移动）"
    accessed: "2026-09-24"
  - url: https://www.kaggle.com/competitions/gemma-4-developer-agent-paper
    title: "paper 姊妹赛道站（主赛 Description/Prizes 节交叉引用直抓）：Submit a Research Paper advancing the state-of-the-art for agentic software engineering；截稿 2026-11-12；$35,000 池"
    accessed: "2026-09-24"
---

# Google - The Gemma 4 Developer Agent Competition（gemma-4-dev-agent）— meta

## 概况（除标注外均为 2026-09-24 kaggle CLI OAuth 实抓，原文快照见信源[2]）

- **赛题本体**：后训练（post-train）Gemma 4 小模型构建自主软件工程 agent——独立导航大型代码库、修真实 GitHub bug/实现 feature request；官方动机直抓："Today's most capable coding agents rely on internet-connected models… puts advanced software engineering out of reach for many developers"（让离线/消费级硬件可用的高级编码助手普及化）。
- **双赛道结构**：$65,000 主赛（prediction competition，1st $37k / 2nd $18k / 3rd $10k）+ **$35,000 paper 姊妹赛道**（研究论文赛道：PEFT/RL 调优、代码理解与图/嵌入、任务与基准、图推理四类主题；Top submissions 将在 Google 主办的学术场合展示（如 NeurIPS expo workshop）；11-12 截稿）。
- **评测机制（Evaluation 页直抓）**：SWE-bench 式 PASS/FAIL——提交补丁应用到 issue 仓库、跑该 issue 验证测试，**得分 = 通过验证测试的仓库百分比**；测试集约 120 任务（public/private 均分），由私有仓库策展；总预算 12 小时跑完全部任务。
- **数据资产（data-description 直抓）**：129 个公开训练任务（fastapi/rich/requests/httpx 四大真实仓库），每任务含 problem_statement、reference patch、test_patch、base_commit 快照 tgz；配套 **AST 调用/依赖图**（NetworkX JSON，256 文件）、**256 维符号嵌入**（npz，支撑 search_similar_code 工具）、124 个离线 wheels、双容器沙箱 Dockerfile；数据管线两阶段验证（Fail-to-Pass + Pass-to-Pass），测试集另加 frontier model 接近饱和的筛选标准。
- **热度（列表卡口径）**：2026-10-11 主赛 2422 队（10-05 1684 队，一周 +738）；paper 赛道 189 队。2026-09-24 榜单快照：12 队上榜、最高 0.10（parthenos）、多数 0.00-0.06——开赛初期分数极低，说明任务难度大、头部空间充足。

## 参与状态与窗口（2026-10-11 核对）

- 当前处于**提交窗口内**（终交 2026-12-02，报名截止 11-25）；距主赛终交约 7 周、paper 赛道截稿约 4 周（自 10-11 起算）。
- HARNESS_README.md（46KB 完整规格，覆盖 swegemma/adk-submission/adk-eval-core 库、双容器沙箱生命周期、上下文压缩、本地 CLI 评测）需接受赛事规则后才可下载——2026-09-24 实抓时未取得（inbox .meta.yaml 注记）。

## 重验记录

- **2026-10-19（滚动重验·CLI 列表卡）**：主赛 2422 → **3277 队**（8 日 +855，10-05→10-11 一周 +738 的高增速延续）、paper 赛道 189 → **280 队**；CLI deadline 字段逐项与既有 key_dates 相符（主赛终交 12-02、paper 11-12），无日期漂移；距主赛终交约 6 周、paper 截稿约 3.5 周（自 10-19 起算）。本轮仅列表层核验，rules/社区帖（蒸馏合规悬置项）未重抓。（来源：kb/raw/kaggle-list/snapshot-20261019.md ；抓取日期：2026-10-19）

## 信源与快照

- **原件位置：`kb/inbox/gemma-4-dev-agent/gemma4-competition-pages.md`**（53KB/518 行，2026-09-24 kaggle CLI 2.2.4 OAuth 全站实抓；抓取通道与说明见同目录 `gemma4-competition-pages.md.meta.yaml`）。**该文件留在 inbox 不移动**，本条目 raw 层引用指此路径（inbox 属本机 gitignore 暂存区，下轮 inbox 跑批消费后如被清理，需先补拷贝至 kb/raw/gemma-4-dev-agent/——已列入待办）。
- 列表卡滚动口径：`kb/raw/kaggle-list/snapshot-20261011-active.md`（2026-10-11）。

## 待核验清单

- [ ] **inbox 原件落 raw**：kb/inbox/ 为本机暂存区，需将 gemma4-competition-pages.md 拷贝至 `kb/raw/gemma-4-dev-agent/2026-09-24-competition-pages.md` 作为持久快照（本轮任务约束为不移动 inbox 文件，拷贝留待下轮跑批）。
- [ ] 外部 LLM 蒸馏合规：社区帖 742882-distill（14 票，0 回复）悬而未决，官方无明文——若参与本赛需赛前向 host 确认蒸馏边界。
- [ ] swegemma harness 未随数据集放出（社区帖 742882，6 票，无 host 回复）：本地评测链路缺失是否已解决待重抓社区确认；数据问题帖 742911（半数 embeddings 空文件 + 图缺 async 函数）修复状态待核。
- [ ] paper 赛道独立规则/奖项明细（$35,000 在主赛 Prizes 节披露，paper 站自身 rules 页未实抓）。
- [ ] 奖项名额是否含 honorable mentions/更多名次（官方仅披露前三名）。
