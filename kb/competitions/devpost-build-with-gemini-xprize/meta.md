---
id: devpost-build-with-gemini-xprize
name: Build with Gemini XPRIZE
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: ended
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
  - name: "Circle Agentic Economy Prize（赞助特别奖）"
    count_or_ratio: "1 名 × $50,000"
    note: "Circle 赞助，25 席 $2M 奖池之外；2026-10-11 获奖公告新发现（得奖 MERGEGATE， USA）"
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
    note: "已发生：PT 09-25 晚于 Moonshots LIVE（洛杉矶）现场公布，公告发布时间戳 2026-09-26T03:35Z（https://www.xprize.org/news/polyfork-wins-the-build-with-gemini-xprize ，2026-10-11 核抓）"
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
last_verified: 2026-10-11
sources:
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
  - url: https://www.xprize.org/news/polyfork-wins-the-build-with-gemini-xprize
    title: XPRIZE 官方获奖公告（全档位名单/国别/类别奖/Circle 赞助奖；档位映射唯一权威源）
    accessed: 2026-10-11
  - url: https://xprize.devpost.com/project-gallery
    title: Devpost 获奖项目画廊（"View the winners" 入口；旧 /winners 路径 404——本行原 /winners 条目据此修正）
    accessed: 2026-10-11
---

# Build with Gemini XPRIZE — meta

## 概况（全部为 2026-08-27 实抓）

- 90 天黑客松（Ideate/Build/Ship/Grow），要求"真实产品、真实收入、真实业务"（Real product. Real revenue. A real business.），总奖金 $2,000,000、共 25 个获奖名额。
- 主办：XPRIZE（Sponsor）× Google（presented）；承办：Devpost（Administrator）。
- 注册规模：26,470 builders/participants（geminixprize.com 首页计数 × devpost 概览页搜索快照，双源一致；devpost 子页计数微增至 26,473–26,477 属计数器时点差异）。
- 当前状态（2026-10-11 复核）：**赛事已终局（ended）**——获奖者 2026-09-25（PT 晚）于 Moonshots LIVE 现场公布，总冠军 Polyfork（$500k）；获奖解构见 `winners/2026.md`。
- 评审标准（等权重）：Business Viability / AI-Native Operations / Category Impact。
- 资格：个人（≥18 岁）、团队、以及 <25 人小型组织的雇员。

## AI 政策原文（geminixprize.com/rules §04，2026-08-27 抓取）

- "Projects that include LLM functionality must use the Gemini API for at least one LLM call in the deployed application. Teams may use additional LLM providers alongside Gemini at their discretion."
- "A Project must use at least one product from Google Cloud."
- Devpost 首页（What to Build）："Your business has to be operated by AI agents and must use at least one product from Google Cloud."

## 奖金结构核对

$500k×1 + $200k×1 + $100k×3 + $50k×15（Runner Up）+ $50k×5（Category）= $2,000,000，与官网 "$2M in prizes across 25 winners" 口径吻合（每 Project 最多获一项 Prize）。**实发核对（2026-10-11 公告）**：25 席足额发出（5 Finalist + 5 Category + 15 Runner Up），另加发 1 名 Circle Agentic Economy Prize $50k（赞助费，25 席之外）——公告口径类别奖授予各类别 highest-grossing（收入最高）项目。

## 信源与快照

- `kb/raw/devpost-build-with-gemini-xprize/2026-geminixprize-ai-policy.md`（原文摘录）
- `kb/raw/devpost-build-with-gemini-xprize/2026-geminixprize-rules.md`（规则全文）
- `kb/raw/devpost-build-with-gemini-xprize/2026-devpost-home.md`（首页要点 + 失败记录）

## 待核验清单

- [x] 2026-09-25 获奖者公布后：核抓 winners 页，派发 winners 深构分片。——**已闭合（2026-10-11 分片）**：实际入口为 project-gallery（/winners 路径 404），主会话预抓 24 卡快照 + 分片深构 8 项目 + 官方公告全档位名单，产物 `winners/2026.md`。
- [ ] devpost /rules、/details 子页直接抓取持续 -302（超 budget 重试上限），当前依赖 geminixprize.com 全文 + 搜索快照；下轮同步时重试直接抓取以补原始快照。（低优先：赛事已终局，规则文本已双源落库）
- [x] Finalist Pitch 名单与流程细节——**已闭合（2026-10-11）**：公告在案，Finalist Pitch 即前 5 名（Polyfork/TICIAN/MyFixam/LaunchBridge/DodoPrep）于 Moonshots LIVE 现场路演定档位。
- [ ] 参赛作品数（entries/projects 数）尚无官方口径，仅有人数 26,470——公告亦只称 "more than 26,000 builders"，获奖率分母缺失，永久缺口。
- [ ] MERGEGATE（Circle Agentic Economy Prize 得主）项目页 slug 未抓取，待下轮补 URL 与页面快照。
- [ ] **watch（新）**：XPRIZE 公告/官网首页提示已启动新一届 $2M（Google 背书）hackathon——未实抓新赛站，待 hunter 分片核抓建档（线索等级：官网首页摘要，中）。

## 重验记录（2026-09-09，K-08 老化重验）

- 公布日期口径**无变更**：geminixprize.com/rules 重抓（https://www.geminixprize.com/rules ，webReader 渲染，抓取 2026-09-09，快照 `kb/raw/devpost-build-with-gemini-xprize/2026-09-09-rules-reverify.md`）§01 仍为 Submission "May 19 – Aug 17, 2026"、Judging "Aug 18, 10:00 AM PT — Sept 15, 2026, 5:00 PM PT"、**"Finalist Pitch & Winners Announced: On or around September 25, 2026, 2:00 PM PT"**；§04 强制 Gemini API / Google Cloud 条款原样（ai_policy 无变化）。
- winners 页（https://xprize.devpost.com/winners ）**未上线且本窗期无法直验内容**：WebFetch 空正文、webReader 网络错误（重试 1 次仍失败）、curl HTTP 202 空响应体（Devpost bot 防护，与 08-27 直抓受限一致）——如实记录，仅可判"无提前上线证据"，9-25 前后需再核。
- `status: active` 维持（评审期 08-18~09-15，今天 09-09 在窗内）。

## 复核记录（2026-10-11，winners 深构分片）

- **赛事终局确认**：XPRIZE 官方公告核抓（https://www.xprize.org/news/polyfork-wins-the-build-with-gemini-xprize ，webReader 全文，发布时间戳 2026-09-26T03:35Z）——总冠军 **Polyfork**（Lucas Martinic · Germany，$500k），TICIAN Cierre $200k，MyFixam/LaunchBridge/DodoPrep 各 $100k，类别奖 5×$50k，Runner Up 15×$50k，另 Circle Agentic Economy Prize（MERGEGATE，赞助费 25 席之外）。status → **ended**，last_verified 滚 2026-10-11。
- **award_levels 扩充**：新增 Circle Agentic Economy Prize（$50k，Circle 赞助，2026-08 updates 页预告、公告落实）——原规则快照未含此赞助奖。
- **路径修正**：xprize.devpost.com/winners 实际 404，获奖入口为 project-gallery（主会话 browser-use 快照 `kb/raw/devpost-build-with-gemini-xprize/winners-gallery-snapshot-20261011.md`，24 张 Winner 徽章卡）；gallery 徽章不分档位，档位以公告为唯一权威源。
- **快照对账**：24 卡 = 25 席 − C2X（类别奖得主，其项目页实抓成功确认在案）——快照渲染缺口已闭合，见 winners/2026.md 数据缺口节。
- 获奖解构产物：`winners/2026.md`（8 项深构 + 25+1 全名单 + 画像分析）；patterns.md 同轮刷新（coverage 首刷 2026）。
