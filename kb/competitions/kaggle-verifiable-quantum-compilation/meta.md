---
id: kaggle-verifiable-quantum-compilation
name: "Google Quantum AI - Verifiable Quantum Circuit Compilation（kickmix 可验证量子线路压缩赛，$150k）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, CA 94043，rules §B 直抓）；赛事名为 'Google Quantum AI - Verifiable quantum circuit compilation'，配套论文 arXiv:2610.23832（Description 页直抓）"
award_levels:
  - name: "1st Place"
    count_or_ratio: "$50,000（rules §B 与 Prizes 页双处直抓）"
  - name: "2nd Place"
    count_or_ratio: "$25,000（同上）"
  - name: "3rd Place"
    count_or_ratio: "$10,000（同上）"
  - name: "4th/5th/6th Place（各一）"
    count_or_ratio: "各 $5,000（rules §B 直抓）"
  - name: "Mid-Competition Milestone Prize"
    count_or_ratio: "$10,000——2026-11-20 23:59 UTC 公榜最高分且 notebook 公开（Prizes 页直抓）"
  - name: "Longest Leader Prize"
    count_or_ratio: "$10,000——开赛至 2027-01-04 间霸榜时间最长的公开 notebook 团队；多 notebook 霸榜时长可累加（Prizes 页直抓）"
  - name: "Single Task Performance Prizes"
    count_or_ratio: "3 任务各 $10,000，共 $30,000——单任务最优提交（Prizes 页直抓）；总池 $150,000（rules §B 'TOTAL PRIZES AVAILABLE'）"
key_dates:
  start:
    date: "2026-10-22"
    verified: true
    note: "Timeline 页 'October 22, 2026 - Start Date' 直抓"
  milestone_prize_deadline:
    date: "2026-11-20"
    verified: true
    note: "Timeline 页：Mid-Competition Milestone Prize 截止（该时点公榜最高分获胜，notebook 须公开）"
  longest_leader_period_end:
    date: "2027-01-04"
    verified: true
    note: "Timeline 页：Longest Leader Prize 计榜期终点，合格 notebook 及其数据集须在此前公开"
  entry_deadline:
    date: "2027-01-13"
    verified: true
    note: "Timeline 页 'January 13, 2027 - Entry Deadline'（此前须接受规则）"
  team_merger_deadline:
    date: "2027-01-13"
    verified: true
    note: "Timeline 页 'January 13, 2027 - Team Merger Deadline'"
  final_submission_deadline:
    date: "2027-01-20"
    verified: true
    note: "Timeline 页 'January 20, 2027 - Final Submission Deadline'（11:59 PM UTC）；CLI 列表卡 deadline 2027-01-20 双源互证（kb/raw/kaggle-list/snapshot-20261029.md）"
deliverables:
  - "提交 zip 三任务：invsqrt.kmb/.kmx、dqi.kmb/.kmx、dfthcsos/ 目录（angle_k_0…angle_k_<n-1> 无缺口编号 + submission.npz 含因式分解 U/W/H2_I/H1_I/Hsym_lower 与 Givens 树 tree_edges）（Evaluation 页直抓）"
  - "每日 5 次提交、最多 2 个 final submissions、团队上限 5 人（rules §B(1)(2) 直抓）；评分约 45 分钟（Evaluation 页）"
  - "得分 = 三任务相对基线改进的几何均值 ∏(cost_ref/cost)^(1/3)；三任务异构损失：invsqrt=Q×C（Toffolis+T/4）、dqi=R(ε+)×Q²×T（失败率重复因子）、dfthcsos=λ_eff×T×Q（>128 量子比特拒收）（Evaluation 页直抓）"
  - "无传统训练集：闭环验证——用 kickmix 库（Qualtran 开源，github.com/quantumlib/Qualtran）fuzz-test 数千万门级线路；verifier 按提交哈希+密盐播种生成测试（data-description 页直抓）"
ai_policy:
  summary: >-
    官方 rules（2026-10-29 经 catalog 实证内容接口全抓，快照 kb/raw/kaggle-verifiable-quantum-compilation/pages-api-20261029.md）：①本赛目标即 AI 使用——官方 Description 原文 'you will use AI coding agents, classical optimization, and algorithmic insights in a closed verification loop'，无需量子物理背景、无量子硬件；②外部数据与模型允许（§6 'The use of External Data and models is acceptable unless specifically prohibited by the Competition Host'），受 Reasonableness Standard 约束（超奖金成本的专有授权不合理）；③AMLT 允许（须持许可）；④获奖许可 Apache 2.0（Open Source），竞赛数据 Apache 2.0 商用可用；⑤资格 18+ 全球（制裁地区除外），单账号，团队 ≤5。规则未设 AI 辅助开发披露条款；AI agent 参赛是赛题本体而非合规风险。
  url: "https://www.kaggle.com/competitions/google-verifiable-quantum-circuit-compilation/rules"
  checked: "2026-10-29"
credibility: 官网
last_verified: "2026-10-29"
sources:
  - url: "https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=161954"
    title: "Kaggle 官方内容接口全页快照（rules/Description/Evaluation/Timeline/data-description/Prizes/abstract/Domain Context 八页全文，原件 kb/raw/kaggle-verifiable-quantum-compilation/pages-api-20261029.md；赛 ID 161954 自 SSR 壳 og:image 提取，catalog SPA 绕行通道）"
    accessed: "2026-10-29"
  - url: https://www.kaggle.com/competitions/google-verifiable-quantum-circuit-compilation
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261029.md）：'Featured · 150,000 Usd · 1505 队 · deadline 2027-01-20'（列表卡口径；2026-10-19 快照无此赛，10-22 开赛后新上榜）"
    accessed: "2026-10-29"
---

# Google Quantum AI - Verifiable Quantum Circuit Compilation（kaggle-verifiable-quantum-compilation）— meta

## 概况（除标注外均为 2026-10-29 内容接口实抓，原件见信源[1]）

- **赛题本体**：压缩三个容错量子计算瓶颈子程序的线路规模——不训模型，用 AI coding agent + 经典优化 + 算法洞察在**可验证闭环**里找更小线路编译（含精度界内的聪明近似）。官方动机：手工优化一篇论文一小步，kickmix 结构让数千万门线路在经典输入上秒级 fuzz 验证，从而把"不可验证的一般量子线路"问题变成"可机器验证的特定结构"问题（Description 页 + 配套论文 arXiv:2610.23832）。
- **三任务（对应三篇应用论文）**：①invsqrt 聚变能——定点逆平方根线路（等离子体 α 粒子阻止功率，PNAS 2024）；②dqi 组合优化——RS(4095,4025) 可逆 Reed–Solomon 综合征解码器（DQI，Nature 2025）；③dfthcsos 量子化学/清洁能源——FeMoCo 固氮催化剂哈密顿量块编码（化肥占全球能耗约 2%，PRX 2025）（Description 页直抓）。
- **评测机制**：几何均值改进分（基线 sample_submission 记 1.0）；metric 公开 notebook（kaggle.com/code/metric/google-quantum-ai-metric）；dfthcsos 全块编码计成本、angle 线路 >128 量子比特直接拒收（Evaluation 页直抓）。
- **热度（列表卡口径）**：开赛一周 1505 队（2026-10-29 CLI；2026-10-19 CLI 列表无此赛，与 10-22 开赛日吻合）。
- **参与门槛**：官方明确"无需量子物理背景"并附 Domain Context 量子线路 60 秒入门页；starter kit 数据集可从基线三步构建完整 dfthcsos 提交（data-description 页直抓）。

## 参与状态与窗口（2026-10-29 核对）

- 提交窗口内：终交 2027-01-20，报名截止 2027-01-13；距终交约 12 周。**近期利益点**：11-20 里程碑奖（$10k，公榜最高分+公开 notebook）距本轮仅 3 周；Longest Leader Prize 激励尽早公开长期霸榜 notebook——两类附加奖都奖励"早参与、早公开"，与纯终榜赛策略不同。

## 数据缺口与待核验清单

- [ ] 榜单/社区帖未抓（是否有 host 官方答疑、kickmix PyPI 迁移进度——data-description 已预告将从赛数据集迁至 PyPI，metric 随之切换，参赛前需复查）。
- [ ] kicker：CLI 列表卡 1505 队为列表口径，详情页侧栏数字未核。
