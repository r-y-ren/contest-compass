---
id: kaggle-kaggriculture
name: "Kaggriculture（Google/Kaggle 农场经营 agent 仿真对抗赛）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, CA）；Kaggle 平台承办（Simulation Competition，无 Private Leaderboard）"
award_levels:
  - name: "1st Place"
    count_or_ratio: "$5,000（官方 Prizes 页/rules §5：1st–10th 名各 $5,000）"
  - name: "2nd Place"
    count_or_ratio: "$5,000"
  - name: "3rd–10th Place"
    count_or_ratio: "8 名 × 各 $5,000；TOTAL PRIZES AVAILABLE: $50,000（rules §5 直抓）。⚠ $60,000 口径为任务包线索与 9 月搜索快照残留——2026-10-11 官方列表卡亦显示 '$50,000'，与 rules 双官方面一致，$60K 口径判定为陈旧/错误数据"
key_dates:
  start:
    date: "2026-07-29"
    verified: true
    note: "官方 Timeline 页直抓 'July 29, 2026 - Start Date'"
  entry_deadline:
    date: "unknown"
    verified: false
    note: "官方 API Timeline 该行为模板变量（${competition.ProhibitNewEntrantsExplicitDeadline}）未解析；赛站 Overview 页为 SPA。2026-10-11 重验：终交 09-30 已过，本字段已无实操意义（moot），仅存档"
  final_submission_deadline:
    date: "2026-09-30"
    verified: true
    note: "官方 Timeline 页直抓 'September 30, 2026 - Final Submission Deadline'（11:59 PM UTC）。2026-10-11 重验：Timeline 逐字未变，终交未延期（列表卡 '3 days to go' 系倒计时至收敛期终点，详见重验记录）"
  ladder_convergence:
    date: "2026-10-01 ~ 约 2026-10-15"
    verified: true
    note: "官方 Timeline 页直抓：截止后继续跑对局至榜单收敛，随后榜单定稿并跑最终 Bradley-Terry 锦标赛（Evaluation 页）。2026-10-11 列表卡倒计时轨迹（10-03 '12 days'→10-15、10-05 '10 days'→10-15、10-11 '3 days'→约10-14）与该窗口吻合——Kaggle 卡片对仿真赛计至赛事结束（榜单定稿）而非 agent 终交日"
deliverables:
  - "自主 AI agent（bot）：Kaggle 官方 Python kit 编写，部署于 /kaggle_simulations/agent/ 路径，与天梯同类评级 bot 对战"
  - "每日至多 5 次提交；仅最近 2 次提交被跟踪并用于最终评估；提交先过 Validation Episode（自博弈跑通校验），失败标记 Error"
  - "可选 2 个最终提交供评审（rules §2b）；团队上限 5 人"
ai_policy:
  summary: >-
    官方 rules（2026-08-28 经 Kaggle 官方 ListPages API 直抓全文）：①外部数据与模型允许——"The use of
    external data and models is acceptable unless specifically prohibited by the Host"，LLM/工具受
    "Reasonableness Standard" 约束（例：Gemini Advanced 级订阅费用可接受、超过奖金成本的专有数据集不合理）；②AMLT（AutoML 等）允许，须持适当许可；③获奖许可 CC-BY
    4.0（Winner License Type），竞赛数据 Apache 2.0——"You may access and use the Competition Data for any
    purpose, whether commercial or non-commercial"（在 Kaggle 仿真赛中最宽松的一档）；④资格：18+ 全球（制裁地区除外）；单账号，多账号报名/提交被禁。未见任何"禁用 LLM/生成式 AI"条款；本赛目标是 agentic
    AI（官方 abstract："design, build, and deploy an autonomous AI agent"）。2026-10-11 重验全页再抓：上述条款逐条在位，无变化。
  url: https://www.kaggle.com/competitions/kaggriculture/rules
  checked: "2026-10-11"
credibility: 官网
last_verified: "2026-10-11"
sources:
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=147734
    title: "Kaggle 官方 ListPages API（competitionId=147734）2026-10-11 重验直抓（12 页）：Timeline 终交 'September 30, 2026' 与收敛窗口 'October 1 to (approx) October 15' 逐字未变；rules/Prizes/Evaluation 关键条款逐条在位——终交未延期，当前赛后收敛期。配合官方 active 列表卡倒计时轨迹（10-03 12d / 10-05 10d / 10-11 3d→约10-14）判定卡片计至榜单定稿"
    accessed: "2026-10-11"
  - url: https://www.kaggle.com/competitions?listOption=active
    title: "Kaggle 官方 active 列表（主会话 browser-use 预抓快照 kb/raw/kaggle-list/snapshot-20261011-active.md，2026-10-11）：kaggriculture 卡 '10148 Teams · 3 days to go · $50,000'——卡片倒计时与奖池徽标口径证据"
    accessed: "2026-10-11"
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=147734
    title: "Kaggle 官方 ListPages API（competitionId=147734）2026-09-16 重验直抓：12 页内容与 2026-08-28 快照逐字节 diff 全部一致——Timeline（开赛 07-29/终交 09-30/收敛 10-01~约10-15）、rules 全文、Prizes（10×$5,000）均无变更；entry deadline 仍为模板变量未解析。快照存 kb/raw/"
    accessed: "2026-09-16"
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=147734
    title: "Kaggle 官方 ListPages API（competitionId=147734）：rules 全文（$50,000/CC-BY 4.0/Apache 2.0）、Prizes（10×$5,000）、Timeline（开赛 07-29、终交 09-30、收敛至约 10-15）、Evaluation（天梯+Bradley-Terry）、How to Play/Foundational Rules（游戏机制全文）—— 2026-08-28 直抓"
    accessed: "2026-08-28"
  - url: https://www.kaggle.com/competitions/kaggriculture
    title: "赛站 SSR 壳（标题 'Kaggriculture'、description 'Create an agent to play in this farming simulation...'、赛 ID 147734）——SPA 正文经官方 API 取得"
    accessed: "2026-08-28"
---

# Kaggriculture（kaggle-kaggriculture）— meta

## 概况（除标注外均为 2026-08-28 官方直抓）

- Google 自办自承办的 **Simulation Competition**：回合制农场经营博弈——两名玩家在各自农场中经营 30 个游戏日（每日 24 回合、共 720 回合），**赛季结束银行存款多者胜**（How to Play 页：'the winner is determined by who has the most money in the bank at the end'）。
- 玩法要素（Description/How to Play 直抓）：种植/浇水/施肥/收获 6 类作物；饲养鹅/牛/羊产蛋奶毛；买地扩张；动态市场（价格随你的出货与小镇需求反应）；雇佣 farm hand 扩大操作规模。官方定位："models the exact same dynamics found in real-world supply chains, dynamic market pricing, and industrial resource allocation under uncertainty"——**agentic RL 风向标赛事**（任务包判断与官方口径一致）。
- 排名机制（Evaluation 页直抓）：Elo 式天梯（胜=加分，净胜金币数不影响评分，只看胜负平）；提交后持续对局；终交后约两周继续跑局降方差，最终跑 **Bradley-Terry 锦标赛**定榜；Simulation 赛无 Private Leaderboard（rules 直抓 'There is no Private Leaderboard in Simulation competitions'）。
- 赛程：2026-07-29 开赛 → 09-30 终交 → 10-01~约 10-15 收敛定榜。**当前（2026-10-11）处于赛后榜单收敛期**：agent 终交已于 09-30 关闭，对局继续跑至约 10-14/15 榜单定稿（列表卡倒计时轨迹与之一致，见重验记录），随后 Bradley-Terry 锦标赛定榜。
- 关键机制红线（How to Play 直抓，供赛点检查表）：作物两天不浇水变杂草；动物两天不喂（小麦）会逃跑不可找回；番茄/草莓为有限次产出（4 次）后衰败成杂草；西瓜加肥 8 天达产上限。

## 奖金口径（任务包双口径核验结论）

- **$50,000**：官方 rules §5 "TOTAL PRIZES AVAILABLE: $50,000" + Prizes 页（1st–10th 各 $5,000）**双处直抓证实**——采信口径。**2026-10-11 收口**：官方 active 列表卡（主会话 browser-use 预抓快照）奖池徽标亦显示 "$50,000"，rules 与列表卡双官方面一致。
- **$60,000**：任务包线索；9 月搜索快照显示列表页标 "$60,000"——与 2026-10-11 列表卡实抓（$50,000）不符，判定为陈旧/错误数据，不再并存（除非出现新证据）。
- 二手线索（搜索快照级，未直抓）：Reddit r/reinforcementlearning 称首周 2k+ 队伍参赛、有 Kaggle 员工参与规则制作——仅作热度参考。

## AI 政策原文（rules 直抓，2026-08-28）

- "The use of external data and models is acceptable unless specifically prohibited by the Host."（外部数据/模型默认允许）
- "a small subscription charge to use additional elements of a large language model such as Gemini Advanced are acceptable if meeting the Reasonableness Standard"（LLM 使用按费用合理性标准放行）
- "Individual Participants and Teams may use automated machine learning tool(s) ('AMLT') ... provided that ... they have an appropriate license"（AMLT 放行）
- Winner License Type: CC-BY 4.0；Data Access and Use: Apache 2.0（商用亦允许）
- "You cannot sign up to Kaggle from multiple accounts and therefore you cannot enter or submit from multiple accounts."

## 获奖情况

- 当届未放榜：终交 2026-09-30 已过，榜单收敛至约 10-15（10-11 仍在收敛期），无任何名单。winners/2026.md 已建并声明数据缺口。官方页面未见历届记录，按首届处理（待核）。

## 信源与快照

- `kb/raw/kaggle-kaggriculture/2026-kaggle-pages-api.json`（全页官方 JSON：rules/foundational-rules/how-to-play/prizes/evaluation/timeline/description/FAQ 等 12 页）
- `kb/raw/kaggle-kaggriculture/2026-kaggle-page-*.md`（逐页导出 12 件）
- `kb/raw/kaggle-kaggriculture/2026-kaggle-overview-shell.html`（SSR 壳）
- `kb/raw/kaggle-kaggriculture/2026-09-16-kaggle-pages-api.json`（2026-09-16 重验快照：与 08-28 全页 diff 一致，无变更）
- `kb/raw/kaggle-kaggriculture/2026-09-16-kaggle-overview-shell.html`（重验 SSR 壳，与旧壳一致）
- ⚠ 2026-10-11 盘点：上述 `kb/raw/kaggle-kaggriculture/` 路径在本机已不存在（kb/raw 未入主库 git，历史快照疑被清理/未同步）；历史引用保留存档价值，复取走下方 API URL（匿名可访问）。
- 抓取通道备注：Kaggle SPA，正文经 Kaggle 官方 ListPages API（competitions.PageService）匿名直抓，等效直抓官网。

## 重验记录

- **2026-09-16（老化重验·滚动批）**：官方 12 页与 08-28 快照逐字节一致——关键日期（终交 09-30、榜单收敛至约 10-15）、规则、奖金口径（10×$5,000）均无变更；重验无变化。待核项（$50K/$60K、entry_deadline）维持原状。
- **2026-10-11（老化重验·海外 Kaggle 线）**：**终交疑点定谳——未延期**。①官方 ListPages API（competitionId=147734）Timeline 页再抓，"September 30, 2026 - Final Submission Deadline" 与收敛窗口 "October 1 to (approx) October 15" 逐字未变；②任务包矛盾（终交 09-30 已过 vs 列表卡 "3 days to go"）解释为**卡片口径差异**：官方 active 列表卡倒计时轨迹 10-03 "12 days"→10-15、10-05 "10 days"→10-15、10-11 "3 days"→约 10-14，连续指向收敛期终点而非 09-30——Kaggle 对 Simulation 赛的卡片计至赛事结束（榜单定稿），非 agent 终交日；③09-30 终交已关闭，当前为赛后收敛定榜期，status: active 维持（仍在官方 active 列表），预计约 10-15 榜单定稿后翻 ended；④rules 关键条款（$50,000/CC-BY 4.0/Apache 2.0/no Private Leaderboard/Gemini Advanced 合理性标准/外部数据允许）逐条在位，AI 政策无变化；⑤列表卡队数 10-03 10246 → 10-11 10148（微降 98，疑清理，无官方说明，仅记录）；⑥列表卡奖池徽标 $50,000 与 rules 一致，$60K 口径收口为陈旧数据。本轮抓取载荷按任务包约束未写入 kb/raw，原件经 API URL 可复取（见 sources）。

## 待核验清单

- [x] 奖池 $50K vs $60K——2026-10-11 收口：官方列表卡与 rules 双面一致 $50,000，$60K 判定为陈旧/错误数据。
- [x] entry_deadline 官方数值——终交已过，字段 moot，存档不再追。
- [ ] "首届"判断（未见历届，但未做穷尽检索旧届记录）。
- [ ] Reddit "首周 2k+ 队伍"热度口径（二手，未直抓）。
- [ ] agent 运行环境资源限额（FAQ 页 HDD/RAM/vCPU 字段均为模板变量未解析；Docker 基镜像 github.com/Kaggle/kaggle-environments 已知）。
- [ ] 约 10-15 榜单定稿/Bradley-Terry 锦标赛后：最终榜单与获奖名单跟踪（winners 分片输入）；届时卡片应翻 ended，同步翻本条 status。
