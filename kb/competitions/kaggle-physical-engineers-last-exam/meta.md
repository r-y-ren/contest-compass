---
id: kaggle-physical-engineers-last-exam
name: "Google - Agent Harness on Physical-Engineering's Last Exam（PLE 工程智能体 harness 大赛，$400k 两阶段 Hackathon）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, CA，rules §B 直抓）；官方全名 'Google - Agent Harness on Physical-Engineering's Last Exam'，Google Cloud AI Research 联合 Mercor 与 Stanford/NYU/UW/UNC Chapel Hill/Harvard/Columbia 学术伙伴出品 PLE 基准（Description 页直抓），配套论文 arXiv:2610.30537（data-description/Acknowledgements 页 BibTeX 直抓）"
award_levels:
  - name: "First Prize"
    count_or_ratio: "$250,000（rules §B 'TOTAL PRIZES AVAILABLE $400,000' 明细直抓）"
  - name: "Second Prize"
    count_or_ratio: "$100,000（rules §B 直抓）"
  - name: "Third Prize"
    count_or_ratio: "$50,000（rules §B 直抓）"
key_dates:
  start:
    date: "2026-11-09"
    verified: true
    note: "Timeline 页 'November 9, 2026 - Start Date' 直抓"
  final_submission_deadline:
    date: "2027-01-05"
    verified: true
    note: "Timeline 页 'January 5, 2027 - Final Submission Deadline'（Writeup + GitHub 仓库含 dev-set artifacts/ 均须在此前提交，23:59 UTC）；CLI 列表卡 deadline 2027-01-05 双源互证（kb/raw/kaggle-list/snapshot-20261125.md）"
  stage1_judging_complete:
    date: "2027-01-19"
    verified: true
    note: "Timeline 页：Stage 1 Writeup 评审完成，Top 100 晋级 Stage 2 隐藏测试集评测"
  stage2_complete_winners:
    date: "2027-01-26"
    verified: true
    note: "Timeline 页：Stage 2 测试集评测完成并公布获奖者"
deliverables:
  - "单一提交制：每队仅 1 份提交、团队上限 5 人（rules §B(1)(2) 直抓）；最终交付 = Kaggle Writeup（≤2000 词）+ GitHub 仓库 40 位 commit SHA（Submission Requirements 页直抓）"
  - "GitHub 仓库根必须含 submission.yaml（model_api 指向 11 个 google-cloud/* 赞助模型之一）、serve.py、harness.py、Apache-2.0 或 MIT LICENSE、eval/run.py 产出的未打包 artifacts/（≤512 MiB、≤10000 文件、无 LFS/符号链接），并过 uv run python -m kit check 与 kit artifacts（Evaluation 页最低门槛直抓）"
  - "Writeup 须覆盖 Stage 1 全部 5 项评分维度 + 封面图 + 3 张必交图：架构图、score-vs-cost 曲线、29 个 dev 任务失败分布（Submission Requirements 页直抓）"
  - "harness 经 WebSocket 驱动任务容器（2 CPU/4GB RAM/网络隔离），单任务 6 小时上限（21600s），动作为 exec/read_file/write_file/http 四类，收尾发 done 帧（data-description 页协议直抓）"
  - "Stage 2 评 56 个隐藏任务×3 次独立运行（168 任务次，0.0–1.0 分）：定量计算/CAD-IFC 几何用验证脚本，开放交付物由 LLM judge（Claude Opus 5.5）评分；获奖 = Stage 2 性能-成本 Pareto 前沿上按平均分取前 3，晋级门槛平均分 ≥0.138（Evaluation 页直抓）"
  - "PLE 基准本体：85 个专家复核长时程工程任务（结构 10/土木 18/电气 27/机械 30），公开 dev 29 + 隐藏 56；任务容器含最多 50 个项目文件（多页 PDF 图纸、IFC4/DXF CAD、荷载表、地勘记录、法规节选、本地 MCP 服务）（data-description 页直抓）"
ai_policy:
  summary: >-
    官方 rules（2026-11-25 经 catalog 实证内容接口全抓，快照 kb/raw/kaggle-physical-engineers-last-exam/pages-api-20261125.md）：①本赛目标即 AI 使用——官方要求参赛者构建开源自主 agent harness 并配对 Google 赞助基础模型（abstract 页原文），AI agent 是赛题本体而非合规风险；②模型硬约束：Stage 2 只准跑 11 个 google-cloud/* 赞助模型（评估代理注入，屏蔽自定义 API key/外部模型服务/web 搜索，Google 免费供评测 key），本地开发可用任意自托管开源权重或个人 API（Evaluation 页直抓）；③外部数据与模型允许（rules §6 'The use of External Data and models is acceptable unless specifically prohibited'），受 Reasonableness Standard 约束（超奖金成本的专有授权不合理）；④AMLT 允许（须持许可，rules §6c）；⑤获奖许可：代码 Apache 2.0/MIT、Writeup 与文档 CC BY 4.0（rules §B WINNER LICENSE TYPE 直抓）；⑥竞赛数据仅限比赛用途（DATA ACCESS AND USE: Competition Use Only）；⑦资格 18+ 全球（制裁地区除外），单账号，团队 ≤5；Hackathon 无榜单，按 Evaluation Rubric 评审。规则未设 AI 辅助开发披露条款。
  url: "https://www.kaggle.com/competitions/physical-engineerings-last-exam/rules"
  checked: "2026-11-25"
credibility: 官网
last_verified: "2026-11-25"
sources:
  - url: "https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=178013"
    title: "Kaggle 官方内容接口全页快照（data-description/Description/Submission Requirements/rules/abstract/tracks-and-awards/Evaluation/Acknowledgements/judges/Timeline 十页全文，原件 kb/raw/kaggle-physical-engineers-last-exam/pages-api-20261125.md；赛 ID 178013 自 SSR 壳 og:image 提取，catalog SPA 绕行通道）"
    accessed: "2026-11-25"
  - url: https://www.kaggle.com/competitions/physical-engineerings-last-exam
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261125.md）：'Featured · 400,000 Usd · 89 队 · deadline 2027-01-05'（列表卡口径；11-19 快照为 55 队，同 ID 已三见）"
    accessed: "2026-11-25"
---

# Google - Agent Harness on Physical-Engineering's Last Exam（kaggle-physical-engineers-last-exam）— meta

## 概况（除标注外均为 2026-11-25 内容接口实抓，原件见信源[1]）

- **赛题本体**：为 PLE 基准（Physical-Engineering's Last Exam）构建开源自主 agent harness——不是问答题，是把真实工程项目文件夹（图纸/CAD/地勘/法规/表格，最多 50 文件）变成可评审工程交付物：抗震剪力墙计算书、黏土沉降备忘录、无碰撞 IFC4 三维模型、25 年冷却塔全寿命成本研究。官方定位：当前顶级前沿模型在该基准上得分 <50%，痛点是误读图纸标注、套错规范条款、单位换算错误、提前放弃（Description 页直抓）。
- **两阶段赛制**：Stage 1 是 Kaggle Writeup 100 分评审 + 资格预筛门槛（Top 100 晋级）；Stage 2 才定名次——56 隐藏任务×3 次独立运行，按平均分与平均成本的 Pareto 前沿取前 3（平均分 ≥0.138 才有获奖资格）。Stage 1 评分维度：洞察与失败分析 25 / 工程推理 25 / 跨模型泛化 15 / 效率与扩展 20 / 表达与可视化 15（Evaluation 页直抓）。
- **关键策略含义**：①Writeup 占 Stage 1 全部分数——"教给 ML 研究者非显然的东西"（真实失败案例+受控消融+失败想法）与跨模型对比表是硬性得分点，纯刷分思路在此赛无效；②赞助模型表 11 个（Gemini 4 Carbon/Neon/Hydrogen 为赛后新增），跨家族双模型对比直接影响 15 分；③每队仅 1 次提交且无榜单——提交前必须用 PLE kit（github.com/google-research/ple）在 29 dev 任务上自验；④获奖条件是"性能-成本前沿"，纯堆 token 不划算，效率与扩展维度（20 分）与 Pareto 判据双重奖励低成本方案。
- **热度（列表卡口径）**：2026-11-25 为 89 队（11-19 快照 55 队，6 日 +34）；绝对值远低于同期 Featured（quantum 3685/enveda 5939 队），叠加单提交制说明参赛摩擦显著（需工程化 harness+GPU 级本地实验）。
- **参与门槛**：需能搭建 WebSocket 服务型 harness、跑 6 小时级容器任务、自费本地 dev（官方明示 Stage 2 评测 key 免费、本地 dev 无需 Google Cloud 账号）；每任务容器仅 2 CPU/4GB RAM，重计算须外包给赞助模型 API。

## 参与状态与窗口（2026-11-25 核对）

- 提交窗口内：终交 2027-01-05（距今约 6 周），Stage 1 评审 01-19，颁奖 01-26。**无中途里程碑奖**（对比 quantum 的 11-20 里程碑设计），唯一节奏点是 01-05 一刀切终交。
- 每队 1 份提交可反复 un-submit/re-submit 至 deadline（Submission Requirements 页直抓）——先提交占位、持续迭代至 01-05 是合规策略。

## 数据缺口与待核验清单

- [ ] Evaluation 页"8 official google-cloud/<id> models"与模型表 11 个存在正文残留矛盾（表侧 Update 注记"bringing the total to 11"为新增后口径）——参赛前以官方论坛/kit 最新文档复核有效模型清单。
- [ ] Stage 1"pre-screened on a small hidden-task subset"的具体子集规模未披露；Stage 2 Pareto 前沿的成本口径（按 Model Garden 定价页计费）具体单价表未抓。
- [ ] ple-bench.com 竞赛指南与 AGENTS.md 编码代理规范、starter harness（pi-opus/hermes-opus/agy-gemini 样例）未深抓——参赛实施层需另开分片。
- [ ] 论坛热度/官方答疑帖未抓；kicker：CLI 列表卡 89 队为列表口径，详情页侧栏数字未核。

- **2026-11-25（建条首验·CLI 列表卡）**：89 队（11-19 同源 55 队）；CLI deadline 2027-01-05 与 Timeline 页终交日一致，双源互证成立。**距终交约 6 周、无里程碑奖**，对参赛者是"一次成型"赛制。（来源：kb/raw/kaggle-list/snapshot-20261125.md ；抓取日期：2026-11-25）
