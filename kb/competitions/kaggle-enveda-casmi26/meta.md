---
id: kaggle-enveda-casmi26
name: "Enveda CASMI 2026 - Molecule ID From Mass Spectra（CASMI 社区挑战赛复活版：MS/MS 谱图→分子结构 SMILES 识别，$50k）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Enveda Therapeutics, Inc.（5700 Flatiron Parkway, Boulder, CO 80301，rules §1.3 直抓）；CASMI 名称经创始人 Emma Schymanski 与 Steffen Neumann 许可由 Enveda 复活（CASMI 背景页直抓）；Kaggle 平台承办"
award_levels:
  - name: 1st Place
    count_or_ratio: "$16,000（Prizes 页直抓）"
  - name: 2nd Place
    count_or_ratio: "$12,000（同上）"
  - name: 3rd Place
    count_or_ratio: "$9,000（同上）"
  - name: 4th Place
    count_or_ratio: "$7,000（同上）"
  - name: 5th Place
    count_or_ratio: "$6,000（同上）；合计 $50,000，与列表卡 '50,000 Usd' 口径一致"
key_dates:
  start:
    date: "2026-09-14"
    verified: true
    note: "Timeline 页直抓 'September 14, 2026 - Start Date'；CLI 列表卡同赛同窗互证（kb/raw/kaggle-list/snapshot-20261013.md）"
  entry_deadline:
    date: "2026-12-07"
    verified: true
    note: "Timeline 页 'December 7, 2026 - Entry Deadline. You must accept the competition rules before this date to compete.'（11:59 PM UTC）"
  team_merger_deadline:
    date: "2026-12-07"
    verified: true
    note: "Timeline 页 'December 7, 2026 - Team Merger Deadline'"
  final_submission_deadline:
    date: "2026-12-14"
    verified: true
    note: "Timeline 页 'December 14, 2026 - Final Submission Deadline'（11:59 PM UTC）；CLI 列表卡 deadline 2026-12-14 23:59:00 互证"
deliverables:
  - "submission csv：表头 molecule_id,smiles；每个 molecule_id 恰好一行，smiles 列为至多 25 个候选结构（分号分隔，最优在前）；少于 25 个允许，错猜除占位外无额外惩罚；缺列/空值/重复 molecule_id/超 25 个候选均判拒收（Evaluation 页直抓）"
  - "获奖者义务（rules §2.8）：按 Sponsor 规格提供可复现方法说明（架构/预处理/损失/训练细节/超参）+ 完整代码仓链接（rules 直抓）"
ai_policy:
  summary: "允许使用 LLM 与外部数据/模型：rules §2.6.b 明文外部数据与模型可用（须公开可得、对全体参与者'合理可得且低成本'，Reasonableness Standard；规则原文示例：Gemini Advanced 小额订阅属可接受，许可证价格超奖金的私有数据集不可）；基础规则禁人工标注/预测 test data；外部数据若为预训练模型须许可证兼容获奖开源义务（§2.5）；开源代码须 OSI 许可且不限制商用；禁队伍外私下共享代码。无'禁止 AI 生成'条款——本赛即机器学习建模赛。"
  url: "https://www.kaggle.com/competitions/enveda-CASMI26-molecule-id-mass-spectra/rules"
  checked: "2026-10-13"
credibility: 官网
last_verified: "2026-10-13"
sources:
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=143318
    title: "Kaggle 官方 ListPages API（competitionId=143318，og:image 直读）11 页全文直抓：overview×2（任务/数据/三档新颖性分级/训练集 11 库明细/碰撞能规约）、data-description（MS/MS 原理科普）、rules×2（Official Rules：$50k 奖金表/5 人队/每日 5 提交/外部数据 Reasonableness Standard/获奖者代码义务）+ Foundational Rules（禁人工标注/公私榜/取消资格条款）、evaluation（MRR@25 + InChIKey14 匹配）、timeline、prizes、CASMI 背景、kernel 规范页。快照 kb/raw/kaggle-enveda-casmi26/2026-10-13-pages-api.json + 逐页导出 11 件"
    accessed: "2026-10-13"
  - url: https://www.kaggle.com/competitions/enveda-CASMI26-molecule-id-mass-spectra
    title: "赛站 SSR 壳（og:image 直读赛 ID 143318；SPA 正文经官方 API 取得）。快照 kb/raw/kaggle-enveda-casmi26/2026-10-13-overview-shell.html"
    accessed: "2026-10-13"
  - url: https://www.kaggle.com/competitions?sortBy=latestDeadline
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261013.md）：enveda-CASMI26 卡片 'Featured · 50,000 Usd · 3169 队 · deadline 2026-12-14'（列表卡口径）"
    accessed: "2026-10-13"
---

# Enveda CASMI 2026 - Molecule ID From Mass Spectra（kaggle-enveda-casmi26） — meta

## 概况（2026-10-13 详情页实抓）

- **赛事定位**：CASMI（Critical Assessment of Small Molecule Identification）社区挑战赛的复活版。CASMI 由 Emma Schymanski 与 Steffen Neumann 创立（2012），2012~2022 由各学术团队轮办；本次由 Enveda Therapeutics 经创始人许可在 Kaggle 平台复活（CASMI 背景页直抓，附 PubMed 沿革文献链接）。
- **任务**：从串联质谱（MS/MS）谱图预测未知分子 2D 化学结构。每分子提交至多 25 个候选 SMILES（最优在前）；**按分子而非按谱图**预测——同一分子多张谱图（不同碰撞能/加合离子，1~16 张，中位 3）须聚合成一个排序表（overview 直抓）。
- **奖金**：$50,000（1st $16k / 2nd $12k / 3rd $9k / 4th $7k / 5th $6k）。
- **体量**：列表卡 3169 队（2026-10-13 CLI 口径）。
- **窗口**：终交 2026-12-14，在本轮采集窗口（2026-11~2027-02）内。

## 赛题与数据（本赛核心事实）

- **测试集**：约 1,500 张谱图、约 400 分子，全部 Bruker timsTOF 平台；单同位素质量 157~1159 Da（中位 348）；10 种加合离子。公私榜分离，隐藏测试集复跑替换（overview）。
- **三档新颖性分级**（每分子必属其一，归属隐藏）：Class 1 有公开参考谱图（谱库相似性可解）；Class 2 已知结构但无公开谱图（PubChem/COCONUT 可检索）；Class 3 全新结构（不在 PubChem，须 de novo 预测）——官方明确按难度递增排序。
- **训练集**：~250 万谱图、~27.6 万结构，为 11 个公开谱库的聚合（enveda-180 115 万张同仪器合成分子、GNPS 22 万张天然产物、RIKEN/MassBank/MoNA 等）；官方另放 `enveda-np-examples`（250 个常见天然产物，与测试集同仪器同管线，最接近测试分布的域适配锚点）。允许一切公开可得外部数据（rules §2.6）。
- **碰撞能量规约**：三列设计（orig 原始记录 / 单位标注 / best-effort eV 换算），官方提示"模型若消费碰撞能量，用 `collision_energy_ev` 列"。
- **谱图仅轻度清洗**：只剔除前体质量矛盾、基峰 <1000 counts、前体+2Da 以上噪声峰；其余清洗自主决定（官方给常见方法清单：相对强度阈值/去同位素/强度变换/top-N 峰保留等）。

## 评测（Evaluation 页直抓）

- **指标 MRR@25**：每分子取首个正确候选的倒数秩，均值。第 1 位猜中得 1.0，第 2 位 0.5，第 25 位 0.04。
- **匹配标准**：SMILES 经 RDKit 互变异构规范化（钉在 2026.03.3）后取 InChIKey 第一块（InChIKey14）比对——**立体中心与互变形式错误不扣分**（骨架对即得分）。官方提供 metric notebook。
- 公私双榜：私榜定名次（Foundational Rules §3.7）。

## 规则要点

- **队伍上限 5 人**；每日 5 次提交；合并队伍时提交配额按天数×日限校验（rules §2.1/2.2）。
- **外部数据与 LLM**：可用，须"合理可得且低成本"（Reasonableness Standard，原文示例 Gemini Advanced 小额订阅可、超奖金价私有数据集不可）；AMLT 自动化 ML 工具可用（rules §2.6）。
- **获奖者义务**：可复现方法说明 + 完整代码仓（§2.8）；预训练模型许可证须兼容获奖开源义务，不兼容部分可豁免开源但须申报（§2.5）。
- 合规红线：禁人工标注/预测测试数据；禁队伍外私下共享代码（论坛公开共享允许且须 OSI 许可）；单账号参赛（多账号取消资格）。

## 与既有条目的关系

- 与 `kaggle-ai-mathematical-olympiad-progress-prize-3`、`kaggle-arc-prize-2026` 同属 Kaggle Featured 科学发现向赛题，但本赛是**谱图→结构的检索+生成混合任务**，评测为排序指标而非准确率/程序正确性——方法论与 ARC（推理/程序合成）、NFL（时序特征工程）均不同源。
- 官方资源页点名 MIST-CF、SIRIUS、matchms、GeMS/DreaMS 预训练谱图嵌入、MassIVE 语料——这是官方背书的外部工具清单，参赛可直接消费。

## 数据缺口与待核验

- [ ] **winners/ 未建**：赛事进行中（终交 2026-12-14，放榜在其后），无任何获奖名单可抓。按 `award_levels` 前两级（1st $16k、2nd $12k）待 Kaggle 放榜公告后补建。**核对的维度**：Kaggle 赛站 Leaderboard 页、Discussion 区 winner 公告帖。
- [ ] **CASMI 历届（2012~2022）优胜方法谱系未消费**：背景页仅给沿革与 PubMed 文献链接（pubmed.ncbi.nlm.nih.gov/24958137 等），历届挑战赛各方法成绩与胜出方案属独立深构分片工作量（外置文献抓取+解构），本轮未做，勿凭记忆补写。
- [ ] 公榜/私榜划分比例官方未公布（隐藏测试集复跑机制，规模"approximately the same size"）。
- [ ] ListPages 中 kernel 规范页（841696）为通用 Kernel Award 说明模板，与本赛是否挂钩未逐一核对（本赛 award_levels 无 kernel 奖，判定不挂钩，未写入 frontmatter）。
- [ ] rules §3.18 defined terms 节为模板法务全文，未逐条消费（与本赛特异性事实无关）。
