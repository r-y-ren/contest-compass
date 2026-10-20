---
id: kaggle-nfl-big-data-bowl-2027
name: "NFL Big Data Bowl 2027（NFL 官方橄榄球数据分析写作赛：Combine 追踪数据 → NFL 赛场表现）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：National Football League（345 Park Avenue, New York, NY 10154，rules §1.2 直抓）；Kaggle 平台承办（Featured，列表卡标 Hackathon 类型）"
award_levels:
  - name: "Open Track Finalist"
    count_or_ratio: "3 名 × 各 $10,000（rules §1.5 直抓：Open Track $45,000）"
  - name: "University Track Finalist"
    count_or_ratio: "3 名 × 各 $10,000（rules §1.5 直抓：University Track $45,000；University 资格细则规则页未载，见待核）"
  - name: "Open/University Track Runner-Up"
    count_or_ratio: "各 3 名 × 各 $5,000（rules §1.5 直抓）"
  - name: "Grand Prize（Combine Presentation Winner）"
    count_or_ratio: "1 名 × $10,000：Open/University 全部 Finalist 受邀在 2027 NFL Scouting Combine 现场展示，其中一队加冕；不可直接提交该赛道（rules §1.5 直抓）"
key_dates:
  start:
    date: "2026-10-06"
    verified: true
    note: "官方 Timeline 页直抓 'October 6, 2026 - Start Date'（列表卡 3 months to go 与之相合）"
  final_submission_deadline:
    date: "2027-01-06"
    verified: true
    note: "官方 Timeline 页直抓 'January 6, 2027 - Final Submission Deadline'（11:59 PM UTC）"
  judging_period:
    date: "2027-01-07 ~ 2027-01-25"
    verified: true
    note: "官方 Timeline 页直抓；注 'subject to change based on the number of submissions received'"
  results_announcement:
    date: "2027-01-26"
    verified: true
    note: "官方 Timeline 页直抓 'January 26, 2027 - Anticipated Results Announcement'"
  entry_deadline:
    date: "unknown"
    verified: false
    note: "Timeline 页未单列 Entry Deadline（Kaggle 惯例为与终交同步，2027-01-06 前接受规则即可；无官方数值，待核）"
deliverables:
  - "分析 Writeup（非模型提交）：≤2,000 词、表格+图合计 <10 个，超出可能受罚（Submission Requirements 页直抓）"
  - "可复现代码：鼓励正文展示关键统计代码，主体代码放附录或链接 Public Kaggle Notebook——Writeup 完整性 gate 要求附公开 Notebook（Evaluation 页直抓）"
  - "必须使用 player tracking 数据：'Any Writeup that doesn't use the player tracking data will not be scored'（Evaluation/Submission Requirements 页直抓）"
ai_policy:
  summary: >-
    官方 rules（2026-10-11 经 Kaggle 官方 ListPages API 直抓全文，competitionId=162982）：①外部数据与模型允许——"The use of external
    data and models is acceptable unless specifically prohibited by the Host"，受 Reasonableness Standard
    约束（Gemini Advanced 级订阅可接受、超奖金成本的专有数据集不合理）；②AMLT 允许（须持许可）；③规则全文未设 AI 工具使用限制或披露条款，本赛交付物为
    分析 Writeup，AI 辅助写作无明文约束（但 2026-01-26 放榜的往届 BDB 未见 AI 披露条款先例可参照——本条仅记录条款缺席事实）；④Winner
    License：Open Source（OSI 认证、不限商用）；⑤**Competition Data：CC BY-NC 4.0（仅限非商业用途**——"non-commercial
    purposes only"，与本库其余 Kaggle 赛的 Apache 2.0 商用可用档不同，注意数据二次使用红线）；⑥资格：全球（制裁地区除外），18
    岁以下可凭监护人同意参赛但不可获奖（rules §7.b 特有条款）；团队 ≤5。
  url: https://www.kaggle.com/competitions/nfl-big-data-bowl-2027/rules
  checked: "2026-10-11"
credibility: 官网
last_verified: "2026-10-19"
sources:
  - url: https://www.kaggle.com/competitions?sortBy=latestDeadline
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261019.md）：nfl-big-data-bowl-2027 卡片 'Featured · 100,000 Usd · 326 队 · deadline 2027-01-06'（列表卡口径）"
    accessed: "2026-10-19"
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=162982
    title: "Kaggle 官方 ListPages API（competitionId=162982）9 页全文直抓：rules 全文（$100,000 三段奖金结构/CC BY-NC 4.0/团队与提交限额/18 岁以下特例）、Timeline（开赛 10-06、终交 2027-01-06、评审 01-07~25、放榜 01-26）、Description（2027 主题 Combine to NFL Performance + 四类示例方向）、Evaluation（双 PASS/FAIL gate + Football 30%/DS 30%/Writeup 20%/Viz 20%）、Submission Requirements（2000 词/10 图表/公开 Notebook/tracking 数据强制）、data-description（510 名新秀 9 个 CSV 约 2.2GiB）、abstract。快照 kb/raw/kaggle-nfl-big-data-bowl-2027/2026-10-11-pages-api.json + 逐页导出 9 件"
    accessed: "2026-10-11"
  - url: https://www.kaggle.com/competitions/nfl-big-data-bowl-2027
    title: "赛站 SSR 壳（og:image 直读赛 ID 162982；SPA 正文经官方 API 取得）。快照 kb/raw/kaggle-nfl-big-data-bowl-2027/2026-10-11-overview-shell.html"
    accessed: "2026-10-11"
  - url: https://www.kaggle.com/competitions?listOption=active
    title: "Kaggle 竞赛列表 active 页快照（browser-use 预抓，kb/raw/kaggle-list/snapshot-20261011-active.md）：nfl-big-data-bowl-2027 卡片 'Uncover non-obvious linkages between Combine sensor tracking and regular-season NFL game performance'、Featured · Hackathon、175 Teams、3 months to go、$100,000（列表卡口径）"
    accessed: "2026-10-11"
---

# NFL Big Data Bowl 2027（kaggle-nfl-big-data-bowl-2027）— meta

## 概况（除标注外均为 2026-10-11 官方 ListPages API 直抓）

- NFL 官方年度数据分析赛（Description 原文印证系列性："As is often the case in **Big Data Bowl** analytics competitions…"），2027 主题 **Combine to NFL Performance**：用 NFL Scouting Combine 的 10Hz 光学追踪数据，解释/预测新秀在 NFL 常规赛的表现——"uncover non-obvious, actionable linkages"。
- **交付物是分析写作而非模型**：≤2,000 词 Writeup + <10 图表 + 公开 Notebook；双 PASS/FAIL gate（①Writeup 显式建立 Combine 追踪数据与 NFL 赛场表现的关联；②格式完整含公开 Notebook）之后进入四维加权评分：**Football 30% / Data Science 30% / Writeup 20% / Data Visualization 20%**。
- 评委（Submission Requirements 页直抓）：**32 支 NFL 球队或与球队合作的追踪数据供应商的 analytics staffers**，按上述权重加权平均——**业界用人方直接评审**， football 可用性（"Would NFL teams be able to use these results on a week-to-week basis?"）占第一问。
- 数据集（data-description 直抓）：2023-2025 年入联盟的 **510 名新秀**，9 个 CSV 约 2.2GiB——players / combine_results（体测+NGS 评分）/ **combine_tracking（10Hz，6,310 次 Combine 试跑）** / player_career_successes / player_play / games / **game_tracking_2023/2024/2025（10Hz 赛场追踪）**。
- 官方示例方向（Description 直抓）：route running & coverage（变向/减速/加速出切 vs in-game separation）、trench play（第一步启动/横向灵活性 vs pass-rush/run-block）、drill translation（传感器指标 vs 传统计时）、position-specific mechanics；官方鼓励聚焦单一小方面/位置组/单项 drill，反对全量评估所有新秀。
- 奖金三段（rules §1.5 直抓）：Open Track $45k + University Track $45k（各 3 Finalist ×$10k + 3 Runner-Up ×$5k）+ Grand Prize $10k（Finalist 受邀 2027 NFL Scouting Combine 现场展示决出）。

## 参与状态与窗口（2026-10-11 核对）

- 提交截止 **2027-01-06**，距今约 13 周；列表卡口径 175 Teams（本周新入 active 池，10-05 快照无此卡）。评审期 2027-01-07~25，放榜 2027-01-26。
- 类型注意：列表卡标 **Hackathon**（写作评审制），rules 内 hackathon 专属条款为"每队 1 次提交"（非 hackathon 默认 5 次/日）——本赛按写作赛语义应适用每队 1 次提交，但规则未逐字点名本赛类型，待核（见下）。

## 重验记录

- **2026-10-19（滚动重验·CLI 列表卡）**：队数 175（10-11 列表卡）→ 205（10-13 CLI）→ **326 队**（10-19 CLI，两周 +87%）；CLI deadline 字段 2027-01-06 与 key_dates 相符，无日期漂移。列表卡口径无核验锚点（详情页团队数不入 API，同 10-11 记录口径）。本轮仅列表层核验。（来源：kb/raw/kaggle-list/snapshot-20261019.md ；抓取日期：2026-10-19）

## 信源与快照

- `kb/raw/kaggle-nfl-big-data-bowl-2027/2026-10-11-pages-api.json`（ListPages API 原始 JSON，9 页）+ 逐页导出 `2026-10-11-page-*.md`（rules/Description/Timeline/Submission Requirements/data-description/abstract/Evaluation/tracks-and-awards/judges）
- `kb/raw/kaggle-nfl-big-data-bowl-2027/2026-10-11-overview-shell.html`（SSR 壳，赛 ID 162982 提取源）
- 抓取通道备注：Kaggle SPA，SSR 壳仅提 ID，正文经官方 ListPages API（competitions.PageService）匿名直抓，等效直抓官网。tracks-and-awards 与 judges 两页为官方占位符文本（"placeholder content"），未据此建任何事实。

## 待核验清单

- [ ] **University Track 资格细则**：rules 仅给奖金段，未定义"University"认定方式（在读学历/学位时限/.edu 验证）——待赛站 Overview/FAQ 页渲染后补抓（SPA 正文页 ListPages 未含）。
- [ ] 提交次数适用档：每队 1 次（hackathon 条款）vs 5 次/日（通用条款）——列表卡标 Hackathon 且评审为 rubric 写作制，倾向前者，但需页面级确认。
- [ ] entry_deadline 官方数值（Timeline 未单列）。
- [ ] 历届（BDB 2021-2026）获奖名单与获奖 writeup 形态——系列赛历届届次存在（Description 原文印证），历届名单未实抓；"往届差异化"分析需另行建分片（Kaggle 历届赛站仍在，可直抓）。
- [ ] 列表卡 175 Teams 为滚动口径，无核验锚点（详情页团队数不入 API），仅记列表卡口径。
