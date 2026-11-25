---
id: kaggle-santa-2026
name: "Santa 2026 - The Elf Calculator（Kaggle 圣诞系列 shortest-program 组合优化赛：48 寄存器算术指令最短程序，$50k，Google 赞助）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, CA 94043, United States，rules COMPETITION SPONSOR 条目直抓）；Kaggle 平台承办（CLI 列表卡 category=Featured）"
award_levels:
  - name: "First Prize"
    count_or_ratio: "$12,000（Prizes 页直抓）"
  - name: "Second Prize"
    count_or_ratio: "$10,000（同上）"
  - name: "Third Prize"
    count_or_ratio: "$10,000（同上）"
  - name: "Fourth Prize"
    count_or_ratio: "$8,000（同上）；名次奖小计 $40,000"
  - name: "Rudolph Prize"
    count_or_ratio: "$10,000——榜单第 1 位累计霸榜时间最长的团队（计榜期起点 Prizes 页口径 2026-11-18 12:00 AM UTC vs rules §B 口径 2027 前文 2026-11-17，两页一日出入照录待核）；终点 2027-01-28 11:59 PM UTC（两页一致）；总池 $50,000（rules §B 'TOTAL PRIZES AVAILABLE'）"
key_dates:
  start:
    date: "2026-11-18"
    verified: true
    note: "Timeline 页 'November 18, 2026 - Start Date' 直抓；⚠ Rudolph Prize 计榜起点在 rules §B 为 'November 17, 2026 12:00 AM UTC'，与 Timeline/Prizes 页的 11-18 一日出入，照录待官方澄清"
  entry_deadline:
    date: "2027-01-21"
    verified: true
    note: "Timeline 页 'January 21, 2027 - Entry Deadline. You must accept the competition rules before this date in order to compete'（11:59 PM UTC）"
  team_merger_deadline:
    date: "2027-01-21"
    verified: true
    note: "Timeline 页 'January 21, 2027 - Team Merger Deadline'"
  final_submission_deadline:
    date: "2027-01-28"
    verified: true
    note: "Timeline 页 'January 28, 2027 - Final Submission Deadline'（11:59 PM UTC）；CLI 列表卡 deadline 2027-01-28 23:59:00 双源互证（kb/raw/kaggle-list/snapshot-20261119.md）"
  writeup_deadline:
    date: "赛事结束后 14 天内"
    verified: true
    note: "Prizes 页直抓 'a Prize winner must provide a detailed write-up on their solution in the competition forums within 14 days of the conclusion of the competition'——获奖者义务节点"
deliverables:
  - "UTF-8 CSV 两列 id,program：id 覆盖 scored_0001…scored_1000 各一行；program 单元格为 JSON 指令数组，每条指令四元组 [\"op\",i,j,d]（op ∈ +/-/*/÷，i/j 为 0–47 号源寄存器，d 为目标寄存器）（Evaluation 页直抓）"
  - "硬约束（data-description 'Calculator rules' 节直抓）：全程正值整数；减法仅限第一操作数大于第二；除法必须整除；任何中间值 ≤ 该题 value_limit（≤10^18）；目标数只需在任意寄存器出现过一次即算覆盖"
  - "规模上限（Evaluation 页直抓）：每题 48 寄存器、每程序 ≤4,096 条指令、program 单元格 ≤128 KiB；所有指令计入总分（含覆盖全部目标后的指令），无部分得分，任一程序非法则整份提交拒收"
  - "获奖者义务（Prizes 页直抓）：赛后 14 天内在赛事论坛发布解法详细 write-up"
ai_policy:
  summary: >-
    官方 rules（2026-11-19 经 catalog 实证内容接口全抓，快照 kb/raw/kaggle-santa-2026/pages-api-20261119.md）：
    ①赛题本体即算法/程序搜索优化（写最短算术指令程序），官方无任何"禁 AI 辅助开发"条款，用 AI/搜索算法求解是赛事本意；
    ②外部数据与模型允许——'The use of External Data and models is acceptable unless specifically prohibited by the
    Competition Host'，受 Reasonableness Standard 约束（公开免费或对全体参赛者'合理低成本'）；③AMLT 允许（须持许可，
    'AMLT may win a Prize'）；④获奖许可 Open Source：CC BY 4.0 或 Apache 2.0 二选一（rules §B(5) 原文，输入数据/预训练
    模型许可证不兼容部分可豁免开源但须申报）；⑤资格 18+、单账号（禁多账号）、团队 ≤5（rules §B 'TEAM LIMITS' 原文
    'maximum Team size is five (5)'）；⑥制裁地区/竞赛实体关联方标准排除条款。规则未设 AI 辅助开发披露条款。
  url: "https://www.kaggle.com/competitions/santa-2026/rules"
  checked: "2026-11-19"
credibility: 官网
last_verified: "2026-11-25"
sources:
  - url: "https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=177055"
    title: "Kaggle 官方内容接口全页快照（rules/Description/Evaluation/Timeline/data-description/Prizes/abstract 七页全文，原件 kb/raw/kaggle-santa-2026/pages-api-20261119.md（JSON 同目录 .json）；赛 ID 177055 自 SSR 壳 og:image 提取，catalog SPA 绕行通道）"
    accessed: "2026-11-19"
  - url: "https://www.kaggle.com/competitions/santa-2026"
    title: "赛站 SSR 壳（og:image content=…/Competitions/177055 直读赛 ID；SPA 正文经官方内容接口取得，等效直抓官网）。快照 kb/raw/kaggle-santa-2026/ssr-shell-20261119.html"
    accessed: "2026-11-19"
  - url: "https://www.kaggle.com/competitions?sortBy=latestDeadline"
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261119.md）：santa-2026 卡片 'Featured · 50,000 Usd · 614 队 · deadline 2027-01-28 23:59:00 · userHasEntered=False'（列表卡口径）；11-13 快照（snapshot-20261113.md）无此赛卡——11-18 开赛窗口内新上榜"
    accessed: "2026-11-19"
---

# Santa 2026 - The Elf Calculator（kaggle-santa-2026）— meta

## 概况（除标注外均为 2026-11-19 官方内容接口实抓，原件见信源[1]）

- **赛题本体**：为 1,000 道谜题各写**最短算术指令程序**——从初始寄存器值出发，用 `+ - × ÷` 四则（除法须整除）在 48 个寄存器上生成全部目标数，得分 = 全部程序指令总数，**越少越好**（abstract 页原文 'write the shortest programs you can for 1,000 puzzles'）。属组合优化/程序合成开问题（指令计数最短化），非预测赛。
- **评测机制（Evaluation 页直抓）**：Score = Σ|program_p|（1,000 题指令数总和，lower is better）；**无 public/private 榜分离**（'There is no public/private leaderboard split'——全程单榜，与多数 Kaggle Featured 赛的双榜防过拟合机制不同；本赛无可过拟合的测试标签，机制自洽）；sample_submission 基线单题最多 2,873 条指令。
- **奖金结构（Prizes 页直抓）**：$50,000 = 名次奖 $40k（1st $12k / 2nd $10k / 3rd $10k / 4th $8k）+ **Rudolph Prize $10k**（计榜期内霸榜第 1 位累计时间最长者，与 verifiable-quantum 的 Longest Leader Prize 同款"早参与早霸榜"激励）。
- **热度（列表卡口径）**：开赛次日 614 队（2026-11-19 CLI）。
- **提交规格**：日 100 次提交（rules §B 'SUBMISSION LIMITS' 原文 'a maximum of 100 entries per day'）、2 个 final submissions、团队 ≤5。
- **数据资产（data-description 页直抓）**：puzzles.csv（1,000 计分题：starting_values/targets/value_limit/registers 五列）+ practice_puzzles.csv（200 非计分题，多给 family 五族（independent/shared/multiplicative/mixed/tiny）、design_tier 三档难度与 **lower_bound**（未在初始值中出现的目标数——单指令至多覆盖一个新目标，是指令数的下界，官方明示"generally loose"）+ sample_submission.csv（合法基线程序）。

## 与既有条目的关系

- 与 `kaggle-squares-in-squares`（几何装箱开问题、同款"无固定答案打榜推进上界"结构 + 里程碑奖）、`kaggle-verifiable-quantum-compilation`（线路压缩 + Longest Leader Prize）同属本库"**开问题优化/最短化**"赛道：无数据泄漏顾虑、CPU 起步、榜单成绩即数学 SOTA 信号；Rudolph Prize 与 quantum 赛 Longest Leader、squares 赛里程碑奖构成三种"早期参与"激励样本。
- 与 `gemma-4-dev-agent`（后训练 coding agent）同为"程序生成"命题，但本赛目标是最短指令计数（可验证、确定性），非自然语言到补丁的泛化。

## 建条理由（本轮分片判据）

- 11-19 CLI 快照窗口内新赛（11-13/11-10/11-07 快照均无此卡，与 11-18 开赛日吻合）；Featured 类 + $50k 池 + 70 天窗口（终交 2027-01-28），任务包"新赛查重建条"直接命中；日 100 次提交 + 单榜即时反馈，迭代成本低，适配"搜索/求解器 + LLM 辅助启发式"的本框架工程栈。

## 数据缺口与待核验

- [ ] **winners/ 未建**：赛事进行中（开赛 2026-11-18，终交 2027-01-28，放榜在其后），无任何获奖名单可抓。按 `award_levels` 前两级（1st $12,000、2nd $10,000）待 Kaggle 放榜公告后补建；**核对维度**：Kaggle 赛站 Leaderboard 页、Discussion 区 winner 公告帖（获奖者须发 write-up 帖，模式库素材入口）。
- [ ] Rudolph Prize 计榜起点一日出入：Prizes 页 'November 18, 2026 12:00 AM UTC' vs rules §B 'November 17, 2026 12:00 AM UTC'（本轮两处均直抓）——对参赛策略影响≈0（首日霸榜者少见），待官方澄清后归一。
- [ ] 榜单头部分数与社区求解思路帖未抓（基线 2,873 条/题被刷到多少、是否有 SAT/ILP/DP 求解器路线讨论——参与前值得专项采集，勿凭记忆预判技术路线）。
- [ ] 614 队为 CLI 列表卡口径（开赛次日），详情页侧栏数字未核。
- [ ] value_limit ≤10^18 下的溢出/中间值剪枝约束对求解器设计的影响属技术分析分片工作，本轮未做。

## 信源与快照

- `kb/raw/kaggle-santa-2026/pages-api-20261119.json`（ListPages API 原始 JSON）+ `pages-api-20261119.md`（7 页渲染视图）
- `kb/raw/kaggle-santa-2026/ssr-shell-20261119.html`（SSR 壳，赛 ID 177055 提取源）
- 抓取通道备注：Kaggle 为 SPA 站点，正文经官方内容接口（competitions.PageService/ListPages，匿名直抓）取得，等效直抓官网（catalog 钦定绕行通道）；本轮无 Timeline 模板变量残留（四行日期全部解析）。

## 重验记录

- **2026-11-19（初建·CLI 列表卡 + 官方内容接口全页）**：按 11-19 快照发现（11-13 快照无此卡），当日内容接口七页全抓建条；CLI deadline 2027-01-28 与 Timeline 页 Final Submission Deadline 逐字一致，无漂移。（来源：kb/raw/kaggle-list/snapshot-20261119.md 、kb/raw/kaggle-santa-2026/pages-api-20261119.md ；抓取日期：2026-11-19）
- **2026-11-25（滚动重验·CLI 列表卡）**：614 → **2940 队**（6 日 +2326，参与数近 5 倍暴增——对比量子赛同期 +331，为当期 kaggle 首屏增速最高，疑平台推荐位/榜单曝光效应，机制未经官方渠道证实仅记现象）；CLI deadline 2027-01-28 与既有口径一致，无日期漂移。列表层核验。（来源：kb/raw/kaggle-list/snapshot-20261125.md ；抓取日期：2026-11-25）
