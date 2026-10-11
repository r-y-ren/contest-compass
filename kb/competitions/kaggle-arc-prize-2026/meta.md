---
id: kaggle-arc-prize-2026
name: "ARC Prize 2026（ARC-AGI-2 / ARC-AGI-3 / Paper Track 三赛道）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "ARC Prize, Inc.（非营利主办方，官网口径 'ARC Prize is a nonprofit'；赛道经 Kaggle 承办）"
award_levels:
  - name: "ARC-AGI-3 Grand Prize"
    count_or_ratio: "解锁制 $700,000：授予首个在 ARC-AGI-3 评测得 100% 的合格 agent；未颁出滚存下届年度赛"
  - name: "ARC-AGI-2 Bonus Prize"
    count_or_ratio: "$150,000：首个私榜 ≥85% 的合格方案；未颁出滚存 2027"
  - name: "ARC-AGI-2 Grand Prize"
    count_or_ratio: "$275,000：按 Solution Writeup 六项等权标准（各 0–5 分取均值）评审"
  - name: "Paper Top Paper"
    count_or_ratio: "$75,000（1st $50K / 2nd $20K / 3rd $5K，保底，横跨 AGI-2 与 AGI-3 两赛道评）"
  - name: "ARC-AGI-3 Top Score Award"
    count_or_ratio: "$75,000（1st $40K / 2nd $15K / 3rd $10K / 4th $5K / 5th $5K，保底）"
  - name: "ARC-AGI-3 Milestone Prizes"
    count_or_ratio: "$75,000（M1 与 M2 各：1st $25K / 2nd $10K / 3rd $2.5K；须在节点截止前开源方有资格）"
  - name: "ARC-AGI-2 Progress Prizes"
    count_or_ratio: "$275,000，8 档：$75K/$50K/$40K/$35K/$25K/$20K/$15K/$15K"
  - name: "Paper Outstanding Papers Pool"
    count_or_ratio: "$375,000：rubric >4.5 分者由主办方裁量分润，多名可同时获奖"
key_dates:
  competition_start:
    date: "2026-03-25"
    verified: true
    note: "双源达成（2026-10-11）：arcprize.org 总览 'March 25, 2026 — Competition starts' + Kaggle 三赛道 Timeline 直抓 'March 25, 2026 - Start Date'"
  agi3_milestone_1:
    date: "2026-06-30"
    verified: true
    note: "双源：arcprize.org 总览 + AGI-3 赛道页（'Milestone #1 — June 30, 2026'）；Kaggle Timeline 标注 '(optional)'（里程碑为可选节点）"
  agi3_milestone_2:
    date: "2026-09-30"
    verified: true
    note: "双源：arcprize.org 总览 + AGI-3 赛道页（'Milestone #2 — September 30, 2026'）；Kaggle Timeline 标注 '(optional)'。2026-10-11 已过，官方博客尚无 M2 放榜公告"
  entry_deadline_code_tracks:
    date: "2026-10-26"
    verified: true
    note: "新增（2026-10-11 Kaggle Timeline 直抓）：ARC-AGI-2 与 ARC-AGI-3 均为 'October 26, 2026 - Entry Deadline'，同日 Team Merger Deadline——新参赛/合队须在此前完成（此前该字段官方页缺失）"
  final_submission_deadline:
    date: "2026-11-02"
    verified: true
    note: "三源（2026-10-11 起三源）：arcprize.org 总览 'November 2, 2026 — Submissions due' + Kaggle ARC-AGI-3 Timeline 直抓 'November 2, 2026 - Final Submission Deadline' + ARC-AGI-2 Timeline 同文"
  paper_deadline:
    date: "2026-11-09"
    verified: true
    note: "⚠ 双官方面一日出入（2026-10-11 定谳记录）：Kaggle Paper Track Timeline 直抓 'November 9, 2026 - Final Submission Deadline'（11:59 PM UTC，提交通道权威）vs arcprize.org 总览 'November 8, 2026 - Papers due'。date 字段采 Kaggle 通道口径；11-08 疑为总览页时区/口径简化，待主办方澄清"
  results_announced:
    date: "2026-12-04"
    verified: true
    note: "双源：arcprize.org 总览 'December 4, 2026 — Results announced' + Kaggle 两代码赛道 Timeline 直抓 'December 4, 2026 - Winners announcement'"
deliverables:
  - "Kaggle code competition notebook（两阶段：Save & Run All 验证可运行 + Competition Rerun 跑隐藏集；评测期无互联网）"
  - "开源解决方案：自有代码/方法须以 CC0、MIT-0 等公有领域/宽松许可开源；第三方代码须允许公开共享（Apache-2.0、GPLv3 等）；获官方私榜分数前必须完成开源。Kaggle rules（2026-10-11 直抓）加固：获奖者以 CC-BY 4.0 许可获奖提交与源码；AGI-3 另要求 open source system/model/weights/parameters（对齐 OSI Open Source AI 定义 checklist）"
  - "ARC-AGI-2 Grand Prize 参评：提交截止后 7 日内附官方 Solution Writeup 并开源全部 artifacts"
  - "Paper Track：Writeup（必含 Abstract/Intro/Prior work/Approach/Results/Conclusion），必须关联同届 ARC-AGI-2 或 ARC-AGI-3 的 Kaggle code 提交（分数不限高低）；Writeup ≤1,500 词（超限可能受罚，Submission Requirements 页直抓）；须附公开 notebook，截止时未提交的草稿不予评审"
  - "团队上限（Kaggle rules 2026-10-11 直抓）：ARC-AGI-2 五(5)人；ARC-AGI-3 八(8)人；Paper Track 八(8)人且须与 ARC-AGI-2/AGI-3 提交团队一致"
  - "算力限额（Kaggle Code Requirements/Upgraded accelerators 页 2026-10-11 直抓，此前'待公布'已落地）：AGI-2 CPU/GPU notebook ≤12h（submission.json），L4x4 加速器（96GB 显存，配额 2 倍计费）；AGI-3 CPU/GPU ≤9h，RTX 6000 专属机器（g4-standard-48，他用可封号）；全部加速会话禁网"
ai_policy:
  summary: >-
    官方页面实得三组硬条款：①评测环境禁 API 型 LLM——总览页原文 "Internet access is not
    available during Kaggle evaluation (no API-based systems like GPT/Claude/etc.)"，AGI-2 与
    AGI-3 赛道页均有 "No internet access during evaluation"，即 GPT/Claude 等 API 系统在评测期不可用（方案本身可以基于本地预训练模型/agent）；②强制开源——"Participants
    must open source their solutions before receiving official private evaluation
    scores"，自有代码 CC0/MIT-0、第三方须 Apache-2.0/GPLv3 等，未开源者被移除奖金资格；③验证榜 Testing
    Policy——单次评测成本上限 "$10,000 USD"、不跨次平均、明确不开 web search、不默认挂工具（"tool
    use should be opt-in, not opt-out"，任何工具使用必须声明）。任务包所称"AI 生成代码/方案专门条款"未见于本次实抓的任一官方页面（总览/三赛道/policy/terms/docs）。**2026-10-11 收口**：Kaggle 三赛站 Rules 全文经官方 ListPages API 直抓成功（SPA 问题绕开），全文检索 AI-generat/artificial intelligence/GPT/generative/Claude 等——**无"禁 AI 生成代码"专门条款**；LLM/外部数据按 Kaggle 通用 "Reasonableness Standard" 放行（原文与 PTCG/RSNA 同款："a small subscription charge to use additional elements of a large language model such as Gemini Advanced are acceptable"），该待核项关闭。
  url: https://arcprize.org/competitions/2026
  checked: "2026-10-11"
credibility: 官网
last_verified: "2026-10-11"
sources:
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=133468
    title: "Kaggle 官方 ListPages API（ARC-AGI-3 赛道，赛 ID 133468）2026-10-11 直抓（9 页）：Timeline（03-25 开赛/06-30 M1 optional/09-30 M2 optional/10-26 Entry+Merger/11-02 终交/12-04 Winners）、rules 全文（团队 8 人/CC-BY 4.0/Open Source AI checklist）、Code Requirements（9h 断网）、Upgraded accelerators（RTX 6000 g4-standard-48 专属）"
    accessed: "2026-10-11"
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=133469
    title: "Kaggle 官方 ListPages API（ARC-AGI-2 赛道，赛 ID 133469）2026-10-11 直抓（9 页）：Timeline（10-26 Entry+Merger/11-02 终交/12-04 Winners）、rules（团队 5 人/Progress Prizes $275,000/85% 目标）、Code Requirements（12h 断网，submission.json）、Upgraded Accelerators（L4x4 96GB，配额 2 倍）"
    accessed: "2026-10-11"
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=133724
    title: "Kaggle 官方 ListPages API（Paper Track，赛 ID 133724）2026-10-11 直抓（10 页）：Timeline（仅 03-25 开赛 + 11-09 终交两节点）、Submission Requirements（Writeup ≤1,500 词/须附公开 notebook/草稿不评审）、rules（团队 8 人且与代码赛道同队/CC-BY-4.0）、tracks-and-awards/Bonus Prize/judges 页"
    accessed: "2026-10-11"
  - url: https://arcprize.org/competitions/2026
    title: "arcprize.org 2026 总览页 2026-10-11 重验直抓（trafilatura 抽正文）：timeline 六节点与 09-16 逐字一致（M1 06-30/M2 09-30/提交 11-02/论文 11-08/放榜 12-04）——注意 'November 8 — Papers due' 与 Kaggle Paper Track 'November 9 Final Submission Deadline' 一日出入，两官方面并存"
    accessed: "2026-10-11"
  - url: https://arcprize.org/blog
    title: "ARC Prize 官方博客索引 2026-10-11 直抓：最新帖仍为 07.06.26 'ARC-AGI-3 Milestone Prize #1'——M2（09-30 截止）后无放榜公告"
    accessed: "2026-10-11"
  - url: https://arcprize.org/competitions/2026
    title: "ARC Prize 2026 总览 2026-09-16 重验直抓：timeline 六节点逐字与 08-27 快照一致（M1 06-30/M2 09-30/提交 11-02/论文 11-08/放榜 12-04），页面无变更记录。快照 kb/raw/2026-09-16-arcprize-refetch-extract.md"
    accessed: "2026-09-16"
  - url: https://arcprize.org/blog/arc-prize-2026-milestone-1
    title: "官方博客 'ARC Prize 2026: ARC-AGI-3 Milestone Prize #1'（索引日期 07.06.26，2026-09-16 webReader 全文直抓）：M1 前三公布——1st Tufa Labs 'The Duck'（Qwen 3.6 27B FP8 本地、REPL 写码 agent）、2nd Reki（Gemma-4-31B 本地视觉 LLM 策略）、3rd Md Boktiar Mahbub Murad 'forge'（Gemma-4-31B，GPT-OSS-120B 官方模板）；首笔 $37.5K；文末明示 'The second (and final) milestone prize will end September 30th'。全文快照 kb/raw/2026-09-16-arcprize-milestone1-blog.md"
    accessed: "2026-09-16"
  - url: https://arcprize.org/competitions/2026
    title: "ARC Prize 2026 总览（$2M 总池、三赛道、时间线、无互联网/API 条款、开源要求）"
    accessed: "2026-08-27"
  - url: https://arcprize.org/competitions/2026/arc-agi-2
    title: "ARC-AGI-2 赛道页（$700K 拆分、85% 目标、Bonus/Grand/Progress 评法、2 outputs 规则）"
    accessed: "2026-08-27"
  - url: https://arcprize.org/competitions/2026/arc-agi-3
    title: "ARC-AGI-3 赛道页（$850K 拆分、Grand 解锁条件、M1/M2 金额、Kaggle 提交通道）"
    accessed: "2026-08-27"
  - url: https://arcprize.org/competitions/2026/paper
    title: "Paper Prize 赛道页（$450K 拆分、六项 rubric、须关联 Kaggle 提交）"
    accessed: "2026-08-27"
  - url: https://arcprize.org/policy
    title: "ARC Prize Verified Testing Policy（$10K/次评测上限、无 web search、工具 opt-in、开源方可验证）"
    accessed: "2026-08-27"
  - url: https://arcprize.org/terms
    title: "站点通用条款（无竞赛 AI 条款，仅原创性担保；已核）"
    accessed: "2026-08-27"
  - url: https://docs.arcprize.org/arc-prize-2026
    title: "ARC Prize 2026 Starter Kit 文档（code competition 两阶段提交流程、RTX 6000 限 AGI-3、加速会话禁网）"
    accessed: "2026-08-27"
  - url: https://www.kaggle.com/competitions/arc-prize-2026-arc-agi-2
    title: "Kaggle ARC-AGI-2 赛站（SPA；标题与描述经直抓，日程经搜索索引快照交叉）"
    accessed: "2026-08-27"
  - url: https://www.kaggle.com/competitions/arc-prize-2026-arc-agi-3
    title: "Kaggle ARC-AGI-3 赛站（SPA；'November 2, 2026 - Final Submission Deadline / December 4, 2026 - Winners' 经搜索索引快照取得）"
    accessed: "2026-08-27"
  - url: https://www.kaggle.com/competitions/arc-prize-2026-paper-track
    title: "Kaggle Paper Track 赛站（SPA；'Writeup documenting the submission... for either' track 经搜索索引快照取得）"
    accessed: "2026-08-27"

---
# ARC Prize 2026（kaggle-arc-prize-2026）— meta

## 概况（全部为 2026-08-27 实抓）

- ARC Prize, Inc. 主办的年度 AGI 奖金赛（非营利），2026 届总池 **$2,000,000、三赛道**：ARC-AGI-3（交互式推理，AI agent）、ARC-AGI-2（静态推理）、Paper Prize（论文）。三赛道奖池 $850K + $700K + $450K = $2M，与总览口径自洽。
- 赛程：2026-03-25 开赛 → 06-30 AGI-3 M1 → 09-30 AGI-3 M2 → 11-02 提交截止 → 11-08 论文截止 → 12-04 公布结果。当前（2026-08-27）处于赛中，M2 将近。
- AGI-2 目标："Reach 85% accuracy on the ARC-AGI-2 private evaluation dataset within the Kaggle efficiency limits"；评测无互联网、仅 notebook 提交；每任务对每个 test 输入预测恰 2 个输出，任一精确匹配即该任务得 1 分。
- AGI-3 Grand Prize 解锁条件："Awarded to the first eligible agent that scores 100% on the ARC-AGI-3 evaluation"。
- Starter Kit（docs.arcprize.org）：提交为 code competition notebook，Kaggle 跑两阶段；加速器选项 cpu/t4/p100/rtx6000，"RTX 6000 is reserved for ARC-AGI-3 notebooks"；"All accelerated Kaggle sessions have internet disabled"。
- 硬件/算力限额：赛道页原文 "Hardware and compute limits will be announced with the competition launch"（08-27 表述）；**2026-10-11 已在 Kaggle Code Requirements/Upgraded accelerators 页落地**（AGI-2 ≤12h+L4x4 96GB、AGI-3 ≤9h+RTX 6000 g4-standard-48，加速会话禁网），数值详见 deliverables。

## 线索纠错（对任务包线索，2026-08-27 复核）

- "AGI-2 在赛至约 2026-11-09"：**不成立**。总览页与 Kaggle ARC-AGI-3 快照双源均为 **2026-11-02** Final Submission Deadline。
- "AGI-3 总池 $850K + 解锁 $700K"：口径修正为 **$850K 总池（内含 $700K 解锁制 Grand Prize）**，非两笔叠加。
- "Paper Track 论文截止 2026-11-08/09、$75K"：$75K 实为 Top Paper（保底）一档，Paper 赛道总池 **$450K**（另含 $375K Outstanding Papers Pool）；截止日实抓仅得 11-08（单源），11-09 未证实。
- "Milestone 2 截止 2026-09-30"：双源确认。

## AI 政策原文（arcprize.org，2026-08-27 抓取）

- "Internet access is not available during Kaggle evaluation (no API-based systems like GPT/Claude/etc.)"（总览）
- "No internet access during evaluation"（AGI-2 / AGI-3 赛道页）
- "All code and methods must be open sourced to be eligible for prizes." / "Participants must open source their solutions before receiving official private evaluation scores."（总览与赛道页）
- Testing Policy："We cap our evaluations at $10,000 USD per run." / "we do not average scores across runs" / "We specifically do not enable web search, because that could leak Semi-Private data to the web." / "tool use should be opt-in, not opt-out, so any tool use will always be declared"
- 注：Kaggle 各赛站 Rules 全文为 SPA 渲染，直抓与 r.jina.ai 代理均未取得；"AI 生成代码专门条款"未在已抓官方页面出现，不臆测。

## 获奖情况

- 全赛结果 2026-12-04 公布，winners 深构分片待 12 月后启动。
- **Milestone #1 已放榜（官方博客 2026-07-06 发布，2026-09-16 直抓）**：1st Tufa Labs "The Duck"（小参数开源 LLM Qwen 3.6 27B FP8 本地跑，REPL 内写 Python 操作游戏，唯一"agent 写码"路线）；2nd Reki（Gemma-4-31B 本地，视觉 LLM 逐帧出 JSON 动作+反思记忆）；3rd Md Boktiar Mahbub Murad "forge"（Gemma-4-31B，官方 GPT-OSS-120B 模板改造的可配置框架）。首笔里程碑奖 $37.5K，作品全部开源（Kaggle notebook 可查）。共性信号：全部本地小模型、零 API、官方模板起步——与"评测期无互联网"条款呼应。

## 重验记录

- **2026-09-16（老化重验·滚动批）**：①总览页 timeline 六节点逐字一致，重验无变化（提交截止 11-02、论文 11-08、放榜 12-04 均维持）；②**任务包"M2 9-30 已过"前提有误**——今日 2026-09-16，M2（09-30）尚未到，官方博客 M1 文末原文 "The second (and final) milestone prize will end September 30th" 证实 M2 仍在进行中，无 M2 结果可公告；③**新增情报**：M1 结果已于 07-06 官方博客放榜（前三名单见获奖情况节）；④官方博客 09-03 新帖 "OpenAI's GPT-6 Astra on ARC-AGI-3"（模型热度信号，未下钻）；⑤Verified 榜页为动态渲染，本轮未取到榜单条目。
- **2026-10-11（老化重验·海外 Kaggle 线）**：arcprize.org 总览重抓六节点逐字未变，**Kaggle 侧三赛道 Timeline 经官方 ListPages API 首次直抓成功**（赛 ID：AGI-2=133469、AGI-3=133468、Paper=133724，从 SSR 壳 og:image 提取）。①**无日期翻转**：两代码赛道终交 11-02、放榜 12-04 与总览一致；官方列表卡倒计时自洽（AGI-3 "22 days to go"→11-02、Paper "A month to go"→11 月上旬）；②**新日期**：两代码赛道 Entry/Team Merger Deadline 均为 **10-26**（此前官方页缺失该节点）；Kaggle Timeline 将 M1/M2 标注 "(optional)"；③**paper_deadline 定谳存疑点**：Kaggle Paper Track Timeline 直抓 "November 9, 2026 - Final Submission Deadline"（11:59 PM UTC）vs 总览 "November 8 — Papers due"，双官方面一日出入，date 字段改采 Kaggle 通道口径 11-09（verified: true），出入待主办方澄清；④**待核项批量关闭**：Kaggle Rules 全文首获（无"禁 AI 生成代码"条款，LLM 按合理性标准放行）；团队上限落地（AGI-2 五人/AGI-3 八人/Paper 八人同队）；算力限额落地（AGI-2 ≤12h+L4x4、AGI-3 ≤9h+RTX 6000 g4-standard-48）；competition_start 03-25 获第二官方源；⑤**M2 放榜未出**：官方博客索引最新仍为 07-06 M1 帖，M2（09-30 截止）结果公告待发；⑥队数（列表卡）：AGI-3 3676→4135、AGI-2 2730、Paper 246；⑦本轮载荷按任务包约束未写 kb/raw，经 API URL 可复取。

## 信源与快照

- `kb/raw/kaggle-arc-prize-2026/2026-arcprize-overview.html`
- `kb/raw/kaggle-arc-prize-2026/2026-arcprize-arc-agi-2.html`
- `kb/raw/kaggle-arc-prize-2026/2026-arcprize-arc-agi-3.html`
- `kb/raw/kaggle-arc-prize-2026/2026-arcprize-paper.html`
- `kb/raw/kaggle-arc-prize-2026/2026-arcprize-testing-policy.html`
- Kaggle 三赛站为 SPA，无有效静态快照可存；其日程/描述事实经搜索索引快照交叉后引用。

## 待核验清单

- [x] Kaggle Rules 全文（三赛站 /rules）——2026-10-11 经官方 ListPages API 直抓收口：**无"AI 生成代码/方案专门条款"**，LLM/外部数据按 Reasonableness Standard 放行；获奖许可 CC-BY 4.0；AGI-3 开源对齐 OSI Open Source AI 定义。
- [x] competition_start 2026-03-25 的第二官方源——2026-10-11 Kaggle 三赛道 Timeline 直抓 "March 25, 2026 - Start Date"。
- [x] paper_deadline 第二官方源——2026-10-11 Kaggle Paper Track Timeline 直抓 11-09（与总览 11-08 一日出入，见 key_dates 注）。
- [x] 算力限额数值——2026-10-11 Kaggle Code Requirements/Upgraded accelerators 页落地（AGI-2 ≤12h+L4x4；AGI-3 ≤9h+RTX 6000 g4-standard-48）。
- [x] 团队人数上限——2026-10-11 Kaggle rules 直抓（AGI-2 五人/AGI-3 八人/Paper 八人且与代码赛道同队）。
- [ ] 11-08（arcprize.org 总览 "Papers due"）vs 11-09（Kaggle Paper Track 终交 23:59 UTC）一日出入的主办方澄清。
- [ ] M2（09-30）结束后：Milestone #2 获奖公告跟踪（官方博客索引 10-11 仍未发布）→ winners 分片启动时的首选输入。
- [ ] Verified 榜页条目（动态渲染）与 09-03 "GPT-6 Astra on ARC-AGI-3" 博客下钻。
