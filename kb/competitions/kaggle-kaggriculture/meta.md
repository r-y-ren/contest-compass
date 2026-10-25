---
id: kaggle-kaggriculture
name: "Kaggriculture（Google/Kaggle 农场经营 agent 仿真对抗赛）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: ended
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, CA）；Kaggle 平台承办（Simulation Competition，无 Private Leaderboard）"
award_levels:
  - name: "1st Place"
    count_or_ratio: "$5,000（官方 Prizes 页/rules §5：1st–10th 名各 $5,000）"
  - name: "2nd Place"
    count_or_ratio: "$5,000"
  - name: "3rd–10th Place"
    count_or_ratio: "8 名 × 各 $5,000；TOTAL PRIZES AVAILABLE: $50,000（rules §5 直抓）。$60,000 系 Kaggle 列表页口径，2026-10-25 官方 API reward=50,000 USD 与 rules 双证 $50K，列表页口径废弃"
key_dates:
  start:
    date: "2026-07-29"
    verified: true
    note: "官方 Timeline 页直抓 'July 29, 2026 - Start Date'"
  entry_deadline:
    date: "2026-09-23"
    verified: true
    note: "2026-10-25 赛站 Overview 页 Timeline 区（Browser Use JS 渲染直抓）：'September 23, 2026 - Entry Deadline. You must accept the competition rules before this date in order to compete.'；同日 Team Merger Deadline 亦为 09-23。此前 API 模板变量待核项就此解决"
  final_submission_deadline:
    date: "2026-09-30"
    verified: true
    note: "官方 Timeline 页直抓 'September 30, 2026 - Final Submission Deadline'（11:59 PM UTC）"
  ladder_convergence:
    date: "2026-10-01 ~ 2026-10-15"
    verified: true
    note: "官方 Timeline 页直抓：截止后继续跑对局至榜单收敛，随后榜单定稿并跑最终 Bradley-Terry 锦标赛（Evaluation 页）。2026-10-25 确认收敛期已结束：Overview 头部 Close=Oct 15, 2026；官方 API deadline=2026-10-14 23:59 UTC；榜单已定稿（终榜≠天梯榜，Bradley-Terry 重排生效）"
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
    AI（官方 abstract："design, build, and deploy an autonomous AI agent"）。
  url: https://www.kaggle.com/competitions/kaggriculture/rules
  checked: "2026-08-28"
credibility: 官网
last_verified: "2026-10-25"
sources:
  - url: https://www.kaggle.com/competitions/kaggriculture/leaderboard
    title: "Kaggle 赛站 Leaderboard 页（Browser Use JS 渲染直抓）2026-10-25 定榜核对：'This competition has completed. This leaderboard reflects the final standings.' + Prize Winners Top 10（各 $5,000，终榜分 5890.3~5334.0）；冠军 M & M & P & Q；7/10 名奖金队挂官方 solution writeup；Late Submission 按钮禁用。快照摘录存 kb/raw/kaggle-kaggriculture/2026-10-25-kaggle-leaderboard-final-top12.txt（配合 API 通道）"
    accessed: "2026-10-25"
  - url: https://www.kaggle.com/api/v1/competitions/leaderboard/download/kaggriculture
    title: "Kaggle 官方 API（鉴权通道，kaggle CLI）2026-10-25 直抓：competitions/list 显示 deadline=2026-10-14 23:59 UTC、reward=50,000 USD（$50K/$60K 双口径就此定分：官方 API 与 rules 均为 $50K，列表页 $60K 系列表页口径废弃）、teamCount=10148；leaderboard --show 前 12 行=终榜名次（快照 2026-10-25-kaggle-leaderboard-final-top12.txt）；天梯全量 CSV 快照 2026-10-25-kaggriculture-publicleaderboard-ladder.csv（10,148 行，天梯口径，与终榜名次差异即 Bradley-Terry 重排证据）。注：匿名 ListPages API 本轮起被 reCAPTCHA 挑战页拦截（GET/POST 均拦），鉴权 API 通道取代之"
    accessed: "2026-10-25"
  - url: https://www.kaggle.com/competitions/kaggriculture/overview
    title: "Kaggle 赛站 Overview 页（Browser Use JS 渲染直抓）2026-10-25：Timeline 区补出 Entry Deadline 2026-09-23 与 Team Merger Deadline 2026-09-23（此前为 API 模板变量待核项）；头部 Start Jul 31, 2026 / Close Oct 15, 2026；7 tab 无 Timeline tab（原 Timeline 为论坛帖页）。SSR 壳快照 2026-10-25-kaggle-overview-shell.html"
    accessed: "2026-10-25"
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=147734
    title: "Kaggle 官方 ListPages API（competitionId=147734）2026-10-07 重验直抓：12 页与 09-16 快照 diff 仅 Timeline 页 postId 变化（46423765→50263813，帖被重存）、全部正文逐字一致——终交 09-30/收敛 10-01~约10-15 未改。终交已过 7 天，官方口径处收敛期，无获奖公告；Leaderboard 匿名接口 403（需鉴权）。快照存 kb/raw/2026-10-07-kaggle-pages-api.json"
    accessed: "2026-10-07"
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
- 赛程：2026-07-29 开赛 → 09-23 报名/组队截止 → 09-30 终交 → 10-01~10-15 收敛定榜。**已定榜收官（2026-10-25 核，status: ended）**。
- 关键机制红线（How to Play 直抓，供赛点检查表）：作物两天不浇水变杂草；动物两天不喂（小麦）会逃跑不可找回；番茄/草莓为有限次产出（4 次）后衰败成杂草；西瓜加肥 8 天达产上限。

## 奖金口径（任务包双口径核验结论）

- **$50,000**：官方 rules §5 "TOTAL PRIZES AVAILABLE: $50,000" + Prizes 页（1st–10th 各 $5,000）**双处直抓证实**——当前采信口径。
- **$60,000**：任务包线索；另搜索快照显示 Kaggle 竞赛**列表页**对同描述赛事标 "$60,000"（列表页为 SPA，ListCompetitions API 匿名不可访问，未直抓证实）。可能为奖池上调后的列表页新口径或列表页数据不一致。**双口径并存，标待核**——建议主会话 Browser Use 预抓 https://www.kaggle.com/competitions 列表页与赛站 Overview 头部奖池徽标核对。
- 二手线索（搜索快照级，未直抓）：Reddit r/reinforcementlearning 称首周 2k+ 队伍参赛、有 Kaggle 员工参与规则制作——仅作热度参考。

## AI 政策原文（rules 直抓，2026-08-28）

- "The use of external data and models is acceptable unless specifically prohibited by the Host."（外部数据/模型默认允许）
- "a small subscription charge to use additional elements of a large language model such as Gemini Advanced are acceptable if meeting the Reasonableness Standard"（LLM 使用按费用合理性标准放行）
- "Individual Participants and Teams may use automated machine learning tool(s) ('AMLT') ... provided that ... they have an appropriate license"（AMLT 放行）
- Winner License Type: CC-BY 4.0；Data Access and Use: Apache 2.0（商用亦允许）
- "You cannot sign up to Kaggle from multiple accounts and therefore you cannot enter or submit from multiple accounts."

## 获奖情况

- **已定榜（2026-10-25 官方直抓）**：Leaderboard 页 "This competition has completed. This leaderboard reflects the final standings."，Prize Winners Top 10 各 $5,000：1st M & M & P & Q（5890.3）、2nd Victor @ Tufa Labs（5823.4）、3rd DSM（5580.3）……10th KawattaTaido（5334.0）；总参赛 10,148 队。**终榜名次与天梯榜不同**（Bradley-Terry 终赛重排：Farmcore 7→4、CDE 4→6、DECEM 5→7），与 Evaluation 页定榜机制吻合。7/10 名奖金队挂官方 solution writeup（3rd/4th/5th/6th/7th/9th/10th）。完整名单与 writeup 链接见 `winners/2026.md`。官方页面未见历届记录，按首届处理（待核）。

## 信源与快照

- `kb/raw/kaggle-kaggriculture/2026-kaggle-pages-api.json`（全页官方 JSON：rules/foundational-rules/how-to-play/prizes/evaluation/timeline/description/FAQ 等 12 页）
- `kb/raw/kaggle-kaggriculture/2026-kaggle-page-*.md`（逐页导出 12 件）
- `kb/raw/kaggle-kaggriculture/2026-kaggle-overview-shell.html`（SSR 壳）
- `kb/raw/kaggle-kaggriculture/2026-09-16-kaggle-pages-api.json`（2026-09-16 重验快照：与 08-28 全页 diff 一致，无变更）
- `kb/raw/kaggle-kaggriculture/2026-09-16-kaggle-overview-shell.html`（重验 SSR 壳，与旧壳一致）
- `kb/raw/kaggle-kaggriculture/2026-10-07-kaggle-pages-api.json`（**2026-10-07 重验快照**：与 09-16 快照 diff 仅 Timeline 页 postId 变化（46423765→50263813，帖重存），全部页面正文逐字一致 → 重验无变化；同轮 LeaderboardService/GetLeaderboard 匿名 POST 返回 403 PERMISSION_DENIED，榜单条目不可匿名取）
- `kb/raw/kaggle-kaggriculture/2026-10-07-kaggle-overview-shell.html`（重验 SSR 壳，标题/description 与 08-28 一致）
- `kb/raw/kaggle-kaggriculture/2026-10-25-kaggle-leaderboard-final-top12.txt`（**2026-10-25 定榜快照**：官方 API leaderboard --show 前 12 行=终榜名次）
- `kb/raw/kaggle-kaggriculture/2026-10-25-kaggriculture-publicleaderboard-ladder.csv`（2026-10-25 天梯全量 CSV，10,148 行——天梯口径，与终榜差异为 Bradley-Terry 重排证据；含成员名列）
- `kb/raw/kaggle-kaggriculture/2026-10-25-kaggle-overview-shell.html`（2026-10-25 SSR 壳；Overview 正文经 Browser Use JS 渲染直抓）
- 抓取通道备注：Kaggle SPA。2026-10-25 起匿名 ListPages API 被 reCAPTCHA 挑战页拦截，改走 Kaggle 官方鉴权 API（kaggle CLI，本机 OAuth 凭据）+ Browser Use JS 渲染，等效直抓官网。

## 重验记录

- **2026-09-16（老化重验·滚动批）**：官方 12 页与 08-28 快照逐字节一致——关键日期（终交 09-30、榜单收敛至约 10-15）、规则、奖金口径（10×$5,000）均无变更；重验无变化。待核项（$50K/$60K、entry_deadline）维持原状。
- **2026-10-07（老化重验·09-16 批到期）**：重验无变化——官方 12 页正文与 09-16 逐字一致（仅 Timeline 论坛帖指针 postId 变化）。**阶段推进**：终交 09-30 已过 7 天，当前处官方口径收敛期（10-01~约 10-15，期间继续跑对局降方差），`status` 维持 active（榜单未定稿、无获奖公告）；榜单条目与 "status: ended" 官方终态标识需渲染抓取（本轮匿名通道不可及：Leaderboard API 403、SSR 壳薄壳无状态字段）。**下一个 watch 点：约 10-15 收敛截止后**——定榜 + Bradley-Terry 结果公告 → status 转 ended 与 winners/2026 深构分片的首选输入。
- **2026-10-25（老化重验·10-07 批到期）→ 有变更（定榜收官）**：① `status` active→**ended**——Leaderboard 页官方明示 "This competition has completed. This leaderboard reflects the final standings."，Overview 头部 Close=Oct 15, 2026；② **Prize Winners Top 10 公布**（冠军 M & M & P & Q，10×$5,000，总 10,148 队），终榜经 Bradley-Terry 重排与天梯榜名次不同；7/10 队挂官方 solution writeup——winners/2026.md 名单已落盘，深构分片高价值待派（两届watch闭环）；③ **entry_deadline 补出 = 2026-09-23**（Overview Timeline 直抓，原 API 模板变量待核项解决）；④ 奖金双口径定分 = **$50,000**（官方 API reward + rules 双证，列表页 $60K 口径废弃）；⑤ 通道变更：匿名 ListPages API 被 reCAPTCHA 拦截，改官方鉴权 API + Browser Use 渲染。遗留：1st/2nd/8th 无 writeup（深构分片补抓 Discussion）；"首届"与 Reddit 热度口径维持待核。

## 待核验清单

- [x] 奖池 $50K vs $60K：**2026-10-25 已定分 = $50,000**（官方 API reward=50,000 USD + rules §5 双证；$60K 系列表页口径，废弃）。
- [x] entry_deadline 官方数值：**2026-10-25 已补 = 2026-09-23**（Overview 页 Timeline 直抓）。
- [ ] "首届"判断（未见历届，但未做穷尽检索旧届记录）。
- [ ] Reddit "首周 2k+ 队伍"热度口径（二手，未直抓；官方 teamCount=10,148 可作官方热度口径替代引用）。
- [ ] agent 运行环境资源限额（FAQ 页 HDD/RAM/vCPU 字段均为模板变量未解析；Docker 基镜像 github.com/Kaggle/kaggle-environments 已知）。
- [ ] 1st/2nd/8th 名方案 writeup 缺（深构分片经 Discussion 区补抓）。
