---
id: devpost-build-with-gemini-xprize
name: Build with Gemini XPRIZE
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: ended  # 2026-10-01：获奖者已公布（2026-09-25），赛事终局；winners 深构见 winners/2026.md
organizer: "XPRIZE（Sponsor，Culver City, CA）× Google（presented by Google / Google Cloud 背书）；Devpost, Inc.（Administrator）"
award_levels:
  - name: "1st place"
    count_or_ratio: "1 名 × $500,000"
    note: 总冠军现金奖（USD）
  - name: "2nd place"
    count_or_ratio: "1 名 × $200,000"
    note: USD
  - name: "3rd–5th place"
    count_or_ratio: "3 名 × $100,000 each"
    note: USD
  - name: "Category Prize（5 类：Education & Human Potential / Entrepreneurship & Job Creation / Small Business Services / Money & Financial Access / Professional Services Access）"
    count_or_ratio: "5 名 × $50,000"
    note: 每类别 1 名
  - name: "Runner Up"
    count_or_ratio: "15 名 × $50,000"
    note: USD
key_dates:
  submission_open:
    date: 2026-05-19
    verified: true
    note: "Submission Period 起 2026-05-19 10:00 PT（geminixprize.com/rules 全文 × devpost /rules 搜索快照双源）"
  submission_close:
    date: 2026-08-17
    verified: true
    note: "Submission Period 止 2026-08-17 13:00 PT（双源同上）"
  judging_start:
    date: 2026-08-18
    verified: true
    note: "Judging Period 起 10:00 PT"
  judging_end:
    date: 2026-09-15
    verified: true
    note: "Judging Period 止 17:00 PT"
  winners_announcement:
    date: 2026-09-25
    verified: true
    note: "官方口径 'On or around September 25, 2026 (2:00 pm PT)'，含 Finalist Pitch；尚未发生，关注节点"
deliverables:
  - "GitHub 仓库（须共享给 testing@devpost.com 与 judging@hacker.fund）"
  - "3 分钟视频（公开托管）"
  - "Written Narrative（500–1000 词）"
  - "收入证据（Stripe dashboard export 或银行对账单 + P&L）"
  - "费用证据（expenses）"
  - "产品证据（agent execution logs、API usage records）"
  - "客户证据（early customer interactions / testimonials，如有）"
ai_policy:
  summary: "强制 Gemini：含 LLM 功能的项目必须用 Gemini API 完成部署应用中至少一次 LLM 调用（可并用其他 LLM 提供商）；必须至少使用一个 Google Cloud 产品；业务须由 AI agents 运营（'Your business has to be operated by AI agents and must use at least one product from Google Cloud.'）。评审含 AI-Native Operations 维度。"
  url: https://www.geminixprize.com/rules
  checked: 2026-08-27
credibility: 交叉验证
last_verified: 2026-10-04
sources:
  - url: https://www.xprize.org/news/polyfork-wins-the-build-with-gemini-xprize
    title: XPRIZE 官方获奖公告（25 席全名单 + Agentic Economy Prize + 评委/颁奖细节；curl 原件 + extract sidecar）
    accessed: 2026-10-01
  - url: https://gxp.moonshots.com/project/<slug>（25 席逐席）
    title: 官方展示站 Top 100 项目页（Built by / Problem / Category；curl 原件 ×25 + 汇总 extract）
    accessed: 2026-10-01
  - url: https://xprize.devpost.com/submissions/{1126044-polyfork,1124454-tician-cierre,1041321-myfixam,1118450-launchbridge,1127092-dodoprep-the-autonomous-learning-os}
    title: 前五名 Devpost 提交页全文（webReader 渲染；curl 被 AWS WAF 拦截）——winners 深构材料
    accessed: 2026-10-01
  - url: https://xprize.devpost.com/
    title: Build with Gemini XPRIZE（Devpost 赛站首页：奖金块/提交物/AI 运营要求）
    accessed: 2026-08-27
  - url: https://www.geminixprize.com/rules
    title: Official Rules — Build with Gemini XPRIZE（主办方官网规则全文：日期/奖金表/Gemini 条款）
    accessed: 2026-08-27
  - url: https://www.geminixprize.com/
    title: Build with Gemini XPRIZE 官网首页（26,470 builders registered）
    accessed: 2026-08-27
  - url: https://xprize.devpost.com/rules
    title: Official Rules - Build with Gemini XPRIZE - Devpost（直接抓取失败，事实经搜索快照交叉，详见正文降级说明）
    accessed: 2026-08-27
  - url: https://xprize.devpost.com/winners
    title: Winners 页（获奖者 2026-09-25 公布后启用，winners 深构分片入口）
    accessed: 2026-08-27
---

# Build with Gemini XPRIZE — meta

## 概况（全部为 2026-08-27 实抓）

- 90 天黑客松（Ideate/Build/Ship/Grow），要求"真实产品、真实收入、真实业务"（Real product. Real revenue. A real business.），总奖金 $2,000,000、共 25 个获奖名额。
- 主办：XPRIZE（Sponsor）× Google（presented）；承办：Devpost（Administrator）。
- 注册规模：26,470 builders/participants（geminixprize.com 首页计数 × devpost 概览页搜索快照，双源一致；devpost 子页计数微增至 26,473–26,477 属计数器时点差异）。
- 当前状态（2026-08-27）：提交已截止（08-17），处于评审期（08-18 ~ 09-15），获奖者定于 2026-09-25 前后公布 → 本条目 status 取 active（赛事未终局，关注节点临近）。
- 评审标准（等权重）：Business Viability / AI-Native Operations / Category Impact。
- 资格：个人（≥18 岁）、团队、以及 <25 人小型组织的雇员。

## AI 政策原文（geminixprize.com/rules §04，2026-08-27 抓取）

- "Projects that include LLM functionality must use the Gemini API for at least one LLM call in the deployed application. Teams may use additional LLM providers alongside Gemini at their discretion."
- "A Project must use at least one product from Google Cloud."
- Devpost 首页（What to Build）："Your business has to be operated by AI agents and must use at least one product from Google Cloud."

## 奖金结构核对

$500k×1 + $200k×1 + $100k×3 + $50k×15（Runner Up）+ $50k×5（Category）= $2,000,000，与官网 "$2M in prizes across 25 winners" 口径吻合（每 Project 最多获一项 Prize）。获奖者未公布。

## 信源与快照

- `kb/raw/devpost-build-with-gemini-xprize/2026-geminixprize-ai-policy.md`（原文摘录）
- `kb/raw/devpost-build-with-gemini-xprize/2026-geminixprize-rules.md`（规则全文）
- `kb/raw/devpost-build-with-gemini-xprize/2026-devpost-home.md`（首页要点 + 失败记录）

## 待核验清单

- [x] 2026-09-25 获奖者公布后：核抓 winners 页，派发 winners 深构分片。（2026-10-01 完成：devpost /winners 聚合页仍被 WAF 拦截，改以 XPRIZE 官方公告 + 官方展示站 25 席逐页为事实源；winners/2026.md 已落盘）
- [ ] devpost /rules、/details 子页直接抓取持续 -302（超 budget 重试上限），当前依赖 geminixprize.com 全文 + 搜索快照；下轮同步时重试直接抓取以补原始快照。
- [x] Finalist Pitch 名单与流程细节（规则提到 top finalists 现场路演，具体名单待公布）。（2026-10-01：五强名单已由获奖公告确认；但路演内容本身无公开记录，列入 winners/2026.md 缺口声明）
- [ ] 参赛作品数（entries/projects 数）尚无官方口径，仅有人数 26,000+。

## 重验记录（2026-09-09，K-08 老化重验）

- 公布日期口径**无变更**：geminixprize.com/rules 重抓（https://www.geminixprize.com/rules ，webReader 渲染，抓取 2026-09-09，快照 `kb/raw/devpost-build-with-gemini-xprize/2026-09-09-rules-reverify.md`）§01 仍为 Submission "May 19 – Aug 17, 2026"、Judging "Aug 18, 10:00 AM PT — Sept 15, 2026, 5:00 PM PT"、**"Finalist Pitch & Winners Announced: On or around September 25, 2026, 2:00 PM PT"**；§04 强制 Gemini API / Google Cloud 条款原样（ai_policy 无变化）。
- winners 页（https://xprize.devpost.com/winners ）**未上线且本窗期无法直验内容**：WebFetch 空正文、webReader 网络错误（重试 1 次仍失败）、curl HTTP 202 空响应体（Devpost bot 防护，与 08-27 直抓受限一致）——如实记录，仅可判"无提前上线证据"，9-25 前后需再核。
- `status: active` 维持（评审期 08-18~09-15，今天 09-09 在窗内）。

## 重验记录（2026-10-01，winners 深构分片）

- **获奖者已公布**（2026-09-25 美西，洛杉矶 Moonshots LIVE 现场宣布；XPRIZE 官方新闻 datePublished 2026-09-26T03:35Z）：25 席全名单 + Circle 加分奖（Agentic Economy Prize $50k → MERGEGATE）已获官方原件。事实源：XPRIZE 官方公告（https://www.xprize.org/news/polyfork-wins-the-build-with-gemini-xprize ，curl 原件 101KB + .extract.md sidecar）+ 官方展示站 gxp.moonshots.com 逐席项目页 ×25（curl 原件）双源一致。
- 前五名：1st POLYFORK [Lucas Martinic · 德国，$500k]（3D 模型作为程序售卖，agent 工厂 175/周，首月 $4,428/54 付费客户）；2nd TICIAN CIERRE [墨西哥，$200k]（墨西哥 VAT 退税关账，builder/validator 双 agent）；3rd MYFIXAM [尼日利亚/美国，$100k]（尼日利亚手艺人市场 + escrow）；4th LAUNCHBRIDGE [美国，$100k]（$350/72h 公司注册一体化，弗州）；5th DODOPREP [印度/美国双源歧义，$100k]（多模态 AI 家教）。评审：Cathie Wood/Palmer Luckey/Mark Pincus/Logan Kilpatrick；Ansari 颁奖。
- **devpost /winners 聚合页仍被 AWS WAF 拦截**（curl 得 challenge 桩页；WebFetch 空体）——但**提交子页可经 webReader JS 渲染全文获得**（5/5 成功），与 09-09 记录的"/winners 索引页不可得"不矛盾；子页渲染快照已存 kb/raw/.../winners/。
- `status` → **ended**（赛事终局；schema 枚举值）；winners 深构产物：`kb/competitions/devpost-build-with-gemini-xprize/winners/2026.md`（25 席名单 + 前五全深构 + 缺口声明）。

## 重验记录（2026-10-04，K-08 老化重验·轻核）

- 官方获奖公告页可达性核对（https://www.xprize.org/news/polyfork-wins-the-build-with-gemini-xprize ，curl HTTP 200、101,296 字节，抓取 2026-10-04）：与 2026-10-01 原件（101KB）体量一致，页面在线未失效。**轻核无变化**，`status: ended` 维持，本条目无待办 watch 节点。
