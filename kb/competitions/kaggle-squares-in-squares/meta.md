---
id: kaggle-squares-in-squares
name: "Squares in Squares（组合几何装箱开问题：n≤1000 单位正方形最小外接方，$50k Playground 长窗口赛）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, CA 94043，rules §B 直抓）；Kaggle Playground 类别（CLI 列表卡口径）"
award_levels:
  - name: "Final Leaderboard 1st Place"
    count_or_ratio: "$12,000（Prizes 页直抓）"
  - name: "Final Leaderboard 2nd Place"
    count_or_ratio: "$10,000（同上）"
  - name: "Final Leaderboard 3rd Place"
    count_or_ratio: "$8,000（同上）"
  - name: "Final Leaderboard 4th/5th Place（各一）"
    count_or_ratio: "各 $5,000（同上）"
  - name: "3rd Month Milestone Prize"
    count_or_ratio: "$5,000——2027-01-17 截止时点公榜最高分（Prizes 页直抓；平分取最早提交者）"
  - name: "6th Month Milestone Prize"
    count_or_ratio: "$5,000——2027-04-18 截止时点公榜最高分（同上）；总池 $50,000（rules §B 'TOTAL PRIZES AVAILABLE'）"
key_dates:
  start:
    date: "2026-10-21"
    verified: true
    note: "Timeline 页 'October 21, 2026 - Start Date' 直抓"
  milestone_3mo:
    date: "2027-01-17"
    verified: true
    note: "Timeline 页 '3 Month Milestone Cut-off Date'"
  milestone_6mo:
    date: "2027-04-18"
    verified: true
    note: "Timeline 页 '6 Month Milestone Cut-off Date'"
  entry_deadline:
    date: "unknown"
    verified: false
    note: "Timeline 页该字段为未渲染模板变量 '${competition.ProhibitNewEntrantsExplicitDeadline}'（catalog 已知现象：模板变量需回退渲染抓取）；报名截止日未定，参赛前须复查页面"
  team_merger_deadline:
    date: "unknown"
    verified: false
    note: "同上，模板变量 '${competition.TeamMergerExplicitDeadline}' 未渲染"
  final_submission_deadline:
    date: "2027-07-18"
    verified: true
    note: "Timeline 页 'July 18, 2027 - Final Submission Deadline'（11:59 PM UTC）；CLI 列表卡 deadline 2027-07-18 双源互证（kb/raw/kaggle-list/snapshot-20261029.md）"
deliverables:
  - "单个 CSV：列 id,n,square_id,x,y,angle——每行一个已放置单位正方形的中心坐标与旋转角（弧度）；**允许部分提交**，缺失题按平凡网格装箱基线计分（Evaluation/data-description 页直抓）"
  - "两目标硬约束：任意两正方形内部交集严格为零 + 最小化轴对齐外接方边长 L；L 不提交、由摆放计算（Description 页直抓）"
  - "评分 score(n) = L/√n − 1（越低越好），全 1000 题求和；metric 公开 notebook kaggle.com/code/metric/squares-in-squares（Evaluation 页直抓）"
  - "每日 10 次提交、仅 1 个 final submission、团队上限 5 人（rules §B(1)(2) 直抓）"
ai_policy:
  summary: >-
    官方 rules（2026-10-29 经 catalog 实证内容接口全抓，快照 kb/raw/kaggle-squares-in-squares/pages-api-20261029.md）：①官方 Description 明示方法谱系——'simulated annealing or gradient descent, evolutionary algorithms, or novel reinforcement learning techniques'，优化算法/AI 方法是赛题本体；②外部数据与模型允许（Reasonableness Standard 条款，与全站统一模板一致）；③AMLT 允许；④获奖许可 Open Source（CC BY 4.0 或 Apache 2.0 二选一，rules §B(5) 原文）；⑤资格 18+ 全球（制裁地区除外），单账号，团队 ≤5。规则未设 AI 辅助开发披露条款。
  url: "https://www.kaggle.com/competitions/squares-in-squares/rules"
  checked: "2026-10-29"
credibility: 官网
last_verified: "2026-10-29"
sources:
  - url: "https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=166661"
    title: "Kaggle 官方内容接口全页快照（rules/Description/Timeline/Evaluation/data-description/abstract/Prizes 七页全文，原件 kb/raw/kaggle-squares-in-squares/pages-api-20261029.md；赛 ID 166661 自 SSR 壳 og:image 提取，catalog SPA 绕行通道）"
    accessed: "2026-10-29"
  - url: https://www.kaggle.com/competitions/squares-in-squares
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261029.md）：'Playground · 50,000 Usd · 1179 队 · deadline 2027-07-18'（列表卡口径；2026-10-19 快照无此赛，与 10-21 开赛日吻合）"
    accessed: "2026-10-29"
---

# Squares in Squares（kaggle-squares-in-squares）— meta

## 概况（除标注外均为 2026-10-29 内容接口实抓，原件见信源[1]）

- **赛题本体**：组合几何经典开问题——把 n 个单位正方形（可旋转）装入最小轴对齐正方形容器，n=1…1000 共 1000 题；绝大多数 n 的最优解未知，1000 题中仅极少数有证明最优，其余皆可改进的上界（Description 页原文 'Only a handful of the 1,000 puzzles have proven optimal solutions'）。属于"打榜即推进数学 SOTA"的开放式进度赛，非固定答案预测赛。
- **赛制结构**：9 个月长跑 + 两个里程碑切点（1-17、4-18，各 $5k 给当时公榜第一）+ 终榜奖 $40k；部分提交允许——低 n（易题）可先拿分，缺题按网格装箱基线计分，天然支持增量迭代策略（Evaluation 页直抓）。
- **热度（列表卡口径）**：开赛一周 1179 队（2026-10-29 CLI；2026-10-19 CLI 列表无此赛，与 10-21 开赛日吻合）。
- **与既有条目差异**：同窗口 Playground 长窗口赛里唯一非预测/非 agent 型——纯优化/搜索题，无数据泄漏担忧，计算资源门槛低（CPU 搜索即可起步），适合作为优化算法（退火/进化/RL）的低成本试验场。

## 参与状态与窗口（2026-10-29 核对）

- 提交窗口内：终交 2027-07-18（约 38 周）；1-17 里程碑（约 11 周后）是第一个变现点。报名/组队截止日字段未渲染（模板变量），**参赛前须重核页面**确认仍可入场。

## 数据缺口与待核验清单

- [ ] Entry Deadline / Team Merger Deadline 模板变量未渲染（本轮内容接口拿不到），需渲染抓取或开赛前复查详情页。
- [ ] 榜单头部分数与社区优化思路帖未抓（退火参数、已刷新的上界纪录散见论坛，参与前值得专项采集）。
- [ ] CLI 列表卡 1179 队为列表口径，详情页侧栏数字未核。
