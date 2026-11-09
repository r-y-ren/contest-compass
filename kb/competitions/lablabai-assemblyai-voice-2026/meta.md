---
id: lablabai-assemblyai-voice-2026
name: AssemblyAI - Voice Agent Hackathon（lablab.ai × AssemblyAI，2026-09）
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: ended
organizer: lablab.ai（平台，运营主体 NativelyAI Inc.）× AssemblyAI（协办/API 赞助方，Voice AI 基础设施公司）
award_levels:
  - name: Winner（获奖团队）
    count_or_ratio: 5 组
    note: 每组 $1,000 现金 + $1,000 AssemblyAI API credits（总池 $10,000 = $5k 现金 + $5k credits）
key_dates:
  "开赛/开幕（kick-off）":
    date: 北京时间 2026-09-01 23:00（页面按 CST 本地化显示；publishedTime 元数据 19:00 GMT+0400 与之一致）
    verified: true
  "报名窗口":
    date: 全程开放（2026-09-01~09-30 可随时加入，官方原文"registration stays open for the whole build window"）
    verified: true
  "提交截止":
    date: 北京时间 2026-09-30 23:00
    verified: true
deliverables:
  - 语音代理应用（二选一路线：AssemblyAI Voice Agent API 端到端语音代理；或 Realtime STT API 实时转写应用+自选 LLM/TTS）
  - 提交包（官方清单）：项目标题/短描述/长描述/技术与类别标签、封面图、视频演示、幻灯片演示、公开 GitHub 仓库、demo 应用平台、应用 URL
  - 队伍 1~6 人
ai_policy:
  summary: >-
    强制技术栈条款（赛事页原文"Every participant builds on AssemblyAI"）：所有参赛作品必须构建在 AssemblyAI 平台（Voice Agent API 或 Realtime STT API）之上，报名可得免费 API credits。开源/原创条款（获奖免责节原文）："Submissions must be original and MIT-compliant"——提交须原创并符合 MIT 开源合规。未设生成式 AI 工具使用限制（赛事本身即 AI 应用赛，LLM/TTS 组件自选属比赛内容）。风险条款原文要点：prizes depend on eligibility, availability and third-party sponsors；rules, prizes and terms may change or be canceled at discretion；prize distribution may take up to 90 days。
  url: https://lablab.ai/ai-hackathons/assemblyai-voice-agent-hackathon
  checked: "2026-08-28"
credibility: 聚合站
last_verified: "2026-11-09"
sources:
  - url: https://lablab.ai/ai-hackathons/assemblyai-voice-agent-hackathon/live
    title: 赛事 Live Dashboard 页（SSR HTML 直抓，快照 kb/raw/lablabai-assemblyai-voice-2026/live-page-20261109.html）：**winnersAnnounced:true（放榜）**、winners 数组 5 条均 position=WINNERS（Concierge/SoloRobot、ClauseCatcher、Muninn/High Entropy、Beacon Night Shift/CoffeAndCode、WorkerSaathi/Runtime Terror）、event.status=ended（fetchedAt 2026-11-09T00:59Z）；payload 无 COMMUNITY-CHOICE 独立位次
    accessed: "2026-11-09"
  - url: https://lablab.ai/ai-hackathons/assemblyai-voice-agent-hackathon/live
    title: lablab.ai 赛事 Live Dashboard 页（SSR HTML 直抓，快照 kb/raw/lablabai-assemblyai-voice-2026/live-page-20261025.html）：页面文案"Judges are reviewing every finalist / Results will be published here as soon as judging wrap"+"community voting … community-choice winner"（社区票选开放中）；数据载荷 event.status=ended、**winnersAnnounced:false、winners:[]**（fetchedAt 2026-10-25T01:08Z）、initialLeaderboard 为社区积分榜非获奖名单
    accessed: "2026-10-25"
  - url: https://lablab.ai/ai-hackathons/assemblyai-voice-agent-hackathon
    title: 赛事页（SSR HTML 直抓，快照 kb/raw/lablabai-assemblyai-voice-2026/event-page-20261025.html）：标题加 "[Recap]" 前缀（recap 模板 SEO 文案"Browse winning projects…"，模板性文字非名单）；事件元数据 showWinners:false；"Winner 01~05"卡片为奖金结构区非公告；Results 标签链向 /live 页
    accessed: "2026-10-25"
  - url: https://lablab.ai/ai-hackathons/assemblyai-voice-agent-hackathon
    title: 赛事页（赛程/挑战路线/提交物/评审四维/奖金结构/风险条款/评委名录；2026-10-04 重渲染快照 event-page-20261004.md：赛程无变化、页头现 Results 标签、参赛 3901、获奖未公布）
    accessed: "2026-10-04"
  - url: https://lablab.ai/
    title: lablab.ai 平台首页（运营主体 NativelyAI Inc./合作品牌/往期获奖公布证据；平台可信度评估）
    accessed: "2026-08-28"
---

# AssemblyAI - Voice Agent Hackathon（lablab.ai）

以下正文基于 2026-08-28 实抓（来源编号对应 frontmatter `sources`；快照存于 `kb/raw/lablabai-assemblyai-voice-2026/`：home-lablab、event-page）。

## 定位与组织

- 月度线上赛（2026-09-01~09-30，完全线上、全球可参与、免费报名），lablab.ai 与 AssemblyAI 联办；AssemblyAI 为 Voice AI 基础设施公司（官网自述其模型支撑 Granola、HeyGen、Ashby、ClickUp 等产品）（来源[1]）。
- 当前报名 385 人（2026-08-28 首页卡片显示，来源[2]）。

**2026-09-09 重验**：赛站页渲染重抓（https://lablab.ai/ai-hackathons/assemblyai-voice-agent-hackathon ，webReader，抓取 2026-09-09，快照 `kb/raw/lablabai-assemblyai-voice-2026/event-page-20260909.md`）："Dates: Sep 1–30, 2026"、"Ends Sep 30, 2026"、$10,000 Prize Pool、报名全程开放条款原样（"registration stays open for the whole build window"）→ 赛程**无变化**。**状态变更**：抓取日处于赛期内（09-01 kick-off 已过、09-30 提交未截止），`status` 由 upcoming 更新为 **active**。备注：页面 og:image 引用 AMD 横幅素材（平台模板复用），不影响赛事字段，仅记录。

**2026-10-04 重验（提交截止后 4 天）**：赛站页渲染重抓（同 URL，webReader，抓取 2026-10-04，快照 `kb/raw/lablabai-assemblyai-voice-2026/event-page-20261004.md`）：
- 赛程与截止**无变化**（"Dates: Sep 1–30, 2026"、"Submission deadline Sep 30, 3:00 PM CUT"原样）→ 提交截止（09-30 15:00 UTC）已过，`status` 由 active 更新为 **ended**。
- 参与规模：页面计数 385（08-28）→ **3901**（今日，报名全程开放所致）。
- **放榜 watch 线索**：页头出现 "Live"/"Results" 两枚状态标签，但正文未见获奖名单区块（提交墙百余项目已冻结入墙：Ira、Gogocho Cinema、SignalRoom 等）；官方风险条款 "Prize distribution may take up to 90 days"。获奖公布预期 10 月内（lablab.ai 往期惯例评审约 1-2 周）→ 下轮直接核对本页获奖区块/Results 视图。

**2026-10-25 重验（放榜 watch 第二轮：获奖仍未公布，评审进行中）**：赛事页与 Live Dashboard 双页直抓（SSR HTML，抓取 2026-10-25，快照 `event-page-20261025.html` / `live-page-20261025.html`）：
- **获奖区块未出（重验无变化·放榜维度）**：live 页数据载荷官方字段 `event.status="ended"`、**`winnersAnnounced:false`、`winners:[]`**（fetchedAt 2026-10-25T01:08Z）；live 页明示 "**Judges are reviewing every finalist** — Results will be published here as soon as judging wraps" → 评审仍在进行，未放榜。
- 页面状态微变更：赛事页标题/SEO 加 "[Recap]" 前缀（"Browse winning projects, submissions, and results"——recap 模板文案，正文无名单；事件元数据 `showWinners:false`；页面 "Winner 01~05" 卡片为奖金结构区与首抓一致，非公告）。
- **新机制线索**：live 页载"community voting on the top submissions stays open, every heart counts toward the **community-choice winner**"——社区票选通道开放中（10-04 时未观察到该文案）；`initialLeaderboard`（BULEPOTAN《Soba: Voice AI Emotional Companion》352 分居首等）为社区积分/投票榜，非评委获奖名单。
- 奖金结构、赛程字段无变化；winners 价值评估维持待放榜后执行（官方字段 winnersAnnounced 为最可靠触发器，下轮 watch 优先查该字段与 /live 页 Results 区块）。

**2026-11-09 重验（放榜 watch 第三轮：已放榜）**：live 页 SSR HTML 直抓（抓取 2026-11-09，快照 `live-page-20261109.html`；备注：本机 curl 当日全站 SSL 握手故障，改走 Python urllib 同机直连抓取，原件已入库）：
- **获奖公布（放榜触发器命中）**：官方字段 **`winnersAnnounced:true`**、`winners` 数组 5 条（fetchedAt 2026-11-09T00:59Z）、`event.status="ended"`，条数与 award_levels 5 组一致：
  1. **Concierge**（团队 SoloRobot）——酒店场景物理 AI 语音层：AssemblyAI 代理多语言应答宾客、处理请求并向客房派送机器人（"the voice layer for physical AI, starting with hotels"）；
  2. **ClauseCatcher**（团队 ClauseCatcher）——销售电话实时合规检测：销售承诺与合同冲突时数秒内原文回读对应条款（"quotes the contract word for word and never makes up legal wording"）；
  3. **Muninn: Living Memory System for Technical Work**（团队 High Entropy）——技术工作活记忆伙伴：带轮次时间戳的结构化主张抽取、递归知识图谱、未完成任务与冲突工程决策的主动重现；
  4. **Beacon Night Shift on-call agent you can interrupt**（团队 CoffeAndCode）——可打断的夜间 on-call 语音代理：语音口令批准修复并直接写 AWS，双通道录音即安全凭证（"the transcript is the safety artifact"）；
  5. **WorkerSaathi - Voice-first legal aid navigator**（团队 Runtime Terror）——面向印度 4.5 亿非正规就业者的语音法律援助导航：3 个 AssemblyAI API，印地/英双语，语音转权利研究+证据包+争议信函草稿，零表单。
- payload 无 COMMUNITY-CHOICE 独立位次（5 条均 position=WINNERS；社区票选榜"Top submissions by community vote"与积分榜仍在页内，社区票数统计 909）——10-25 观察到的 community-choice winner 与评委 5 组的关系在数据层仍未显式区分，待获奖公告帖核对，不提前写入 award_levels。
- 参与规模计数 3,181（live 页统计卡；10-04 赛站页曾示 3,901——两页统计口径差异如实记录，不改写其他字段）。
- **winners 建档评估**：建议建 `winners/2026.md`——5 个获奖项目均有站点提交页（slug/封面/短描述已随快照入库），lablab 交付物契约含公开 GitHub 仓库+demo URL+视频+幻灯片（深构原料齐备）；Voice Agent 赛题与黑客松方向强相关，5 个获奖项目覆盖"物理 AI 入口/实时合规/记忆系统/AI 运维/普惠法律服务"五类场景，模式提炼价值高。建议按 winners 分片独立派发深构（四节必备）。

## 赛题（来源[1]）

- 在 AssemblyAI 上构建语音代理，二选一路线：
  1. Voice Agent API 端到端语音代理——Universal-3 Pro 语音识别 + LLM 路由 + 语音输出，turn-taking/VAD，JSON-Schema 工具调用；
  2. Realtime STT API 实时转写应用——WebSocket 亚秒级多语言转录、说话人分离，自选 LLM/TTS 组合。

## 评审与奖励（来源[1]）

- 评审四维：Application of Technology / Presentation / Business Value / Originality。
- 5 组获奖，每组 $1,000 现金 + $1,000 API credits。
- 风险条款（官方免责节）：奖金依赖第三方赞助方资格与可用性；规则与奖金可变更或取消；发放最长 90 天。

## 获奖情况

- **已放榜（2026-11-09 核，live 页官方字段 winnersAnnounced:true + winners 数组）**：5 组获奖——Concierge（SoloRobot）、ClauseCatcher（ClauseCatcher）、Muninn（High Entropy）、Beacon Night Shift（CoffeAndCode）、WorkerSaathi（Runtime Terror），详见上方 2026-11-09 重验记录（含各项目一句话定位）。winners/2026.md 建档待派发。

## 平台可信度评估（任务包前置条件，如实）

- 官方主办方：存在——协办方 AssemblyAI 为具名公司，其 DevRel 工程师 Harnoor Singh 列名开赛演讲者；评委含 Google、PayPal、Hippocratic AI、AI/ML API 等具名公司从业者（来源[1]）。
- 平台运营主体：NativelyAI Inc.（首页页脚，来源[2]）；平台与 AMD/IBM/WeAreDevelopers/TechEx 等品牌有在办/往期合作，页面实见多届已收官事件的获奖公布帖（来源[2]）。
- 往届兑现记录：公开页可证"事件办完+获奖公布"闭环，但奖金实际发放记录不可直证——按任务包口径整体标注：**平台一手（新平台，往届兑现记录待核）**；frontmatter `credibility` 字段枚举无此粒度，取最接近的"聚合站"并在本节显式说明实际等级。

## 对快循环的策略含义（简要）

- 时点优势：9 月赛期与 GOAI 决赛（09-22/23）同窗，Voice Agent 作品可评估"一鱼多吃"（AssemblyAI 强制栈 + MIT 开源与 GOAI 开源要求兼容）。
- 硬约束：必须用 AssemblyAI 技术栈；MIT 合规；提交包含视频+幻灯片+公开仓库——交付物清单可直接映射本框架 Document/Software 角色分工。

## 待办

1. winners：**放榜 watch 已完成（2026-11-09 第三轮：已放榜，winnersAnnounced:true）**——5 组获奖名单已入"获奖情况"节；**winners/2026.md 建档待派发**（深构四节：骨架/亮点/不足与可改进点/可迁移性；提交页 slug 已知：concierge、clausecatcher、muninn-living-memory-system-for-technical-work、beacon-night-shift-on-call-agent-you-can-interrupt、workersaathi-voice-first-legal-aid-navigator）。遗留：community-choice winner 与评委 5 组的关系待获奖公告帖核实。
2. 往届兑现记录待核：可检索往期获奖者公开反馈（社区帖/LinkedIn）佐证奖金发放。
3. 官方 Rules 全文页（独立条款页，赛事页仅摘要免责要点）与 Slack/Discord 细则未抓取，AI 政策以赛事页为准的结论待 Rules 页复核。
4. community-choice winner 与评委 5 组获奖的关系（是否并列加映/计入 5 组）待放榜时核实，勿提前写入 award_levels。
