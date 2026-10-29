---
id: kaggle-name-that-llm
name: "Name That LLM - Identify the Model Behind the Text（18 个前沿 LLM 文本指纹归因赛，$50k，Google 赞助）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "Sponsor：Google LLC（1600 Amphitheatre Parkway, Mountain View, CA 94043，rules §1 直抓）；Kaggle 平台承办（Description 原文 'hosted by Kaggle'；Featured 类 Code Competition）"
award_levels:
  - name: 1st Place
    count_or_ratio: "$5,000（rules §1.5 与 Prizes 页双处直抓）"
  - name: 2nd Place
    count_or_ratio: "$5,000（同上）；1st–10th 各 $5,000 共 $50,000，与列表卡 '50,000 Usd' 口径一致"
key_dates:
  start:
    date: "2026-10-14"
    verified: true
    note: "Timeline 页直抓 'October 14, 2026 - Start Date'"
  entry_deadline:
    date: "unknown"
    verified: false
    note: "Timeline 页该行为模板变量（${competition.ProhibitNewEntrantsExplicitDeadline}）未解析；赛事在赛、报名开放中（2026-10-19 CLI 口径 1985 队）"
  team_merger_deadline:
    date: "unknown"
    verified: false
    note: "Timeline 页该行为模板变量（${competition.TeamMergerExplicitDeadline}）未解析"
  final_submission_deadline:
    date: "2027-01-13"
    verified: true
    note: "Timeline 页直抓 'January 13, 2027 - Final Submission Deadline'（11:59 PM UTC）；⚠ 双官方面一日出入：CLI 列表卡 deadline 字段为 2027-01-14 23:59:00.817（毫秒尾数与 gemma paper 赛道同款），date 字段采 Timeline 提交通道页口径，出入待平台/主办方澄清（与 arc-prize paper_deadline 同款情形）"
deliverables:
  - "submission.parquet（Code Competition 经 notebook 提交）：读 /kaggle/input/competitions/name-that-llm/test.csv，逐 id 预测 model 列；缺 id/model 列、null 值、重复 id、预测超出 18 个合法标签任一即拒收（Evaluation 页直抓）"
  - "算力与网络限制（Code Requirements 页直抓）：CPU/GPU notebook 均 ≤9 小时运行；评测期禁网（Internet access disabled）；可带自由公开的外部数据与预训练模型——即 API 型 LLM 评测期不可调用，本地开源模型路线可行"
  - "获奖者义务（rules §2.5/§2.8）：按 Sponsor 规格提供可复现方法说明（架构/预处理/损失/训练细节/超参）+ 完整代码仓链接；获奖提交与源码以 CC-BY 4.0 许可"
ai_policy:
  summary: >-
    官方 rules 与 foundational-rules 全文关键词扫描（2026-10-19 直抓，AI-generat/artificial intelligence/GPT/Claude/generative 等均无禁用条款命中）：①外部数据与模型允许——rules §2.6.b
    原文 "The use of external data and models is acceptable unless specifically prohibited by the Host"，受
    Reasonableness Standard 约束（原文示例：Gemini Advanced 小额订阅可接受，许可费超奖金的私有数据集不可）；②AMLT 允许（须持许可）；③规则中 LLM/Gemini 字样仅出现于外部数据条款与赛题名，无
    "禁 AI 生成提交" 条款——本赛目标即 LLM 作者归因（用模型识别模型），AI 辅助开发是赛事本意而非合规风险；④技术红线在评测环境侧：Code Requirements 明文评测期禁网，API 型模型无法在推理期调用，方案须本地可运行（自带公开预训练模型允许）；⑤许可组合注意：Winner License
    CC-BY 4.0、Competition Data CC BY-SA 4.0（share-alike 档，与本库多数 Kaggle 赛的 Apache 2.0 商用可用档不同，二次使用数据须同方式共享）；⑥资格：Competition Entities 雇员可参赛不可获奖（rules §2.7）；团队 ≤5 人、日 5 次提交、至多 2 个 final submissions（rules §2.1/2.2）。
  url: https://www.kaggle.com/competitions/name-that-llm/rules
  checked: "2026-10-19"
credibility: 官网
last_verified: "2026-10-19"
sources:
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=170484
    title: "Kaggle 官方 ListPages API（competitionId=170484，SSR 壳 og:image 直读）9 页全文直抓：Description（18 模型/6 实验室/约 4000 隐藏测试段落/40–250 词/未见 prompt）、data-description（train 2699 段/150 prompt，test prompt 与 train 不相交）、rules 全文（$50k 十名×$5k/CC-BY 4.0/Data CC BY-SA 4.0/队 5 人/日 5 提交/外部数据 Reasonableness Standard/获奖者义务）、foundational-rules、Timeline（10-14 开赛/01-13 终交；entry/merger 为模板变量）、Evaluation（balanced accuracy + 18 合法标签全表）、Prizes、abstract、Code Requirements（9h/禁网/可带公开预训练模型）。快照 kb/raw/kaggle-name-that-llm/2026-10-19-pages-api.json"
    accessed: "2026-10-19"
  - url: https://www.kaggle.com/competitions/name-that-llm
    title: "赛站 SSR 壳（og:image 直读赛 ID 170484；SPA 正文经官方 ListPages API 取得，等效直抓官网）。快照 kb/raw/kaggle-name-that-llm/2026-10-19-overview-shell.html"
    accessed: "2026-10-19"
  - url: https://www.kaggle.com/competitions?sortBy=latestDeadline
    title: "Kaggle CLI 竞赛列表快照（E-08 通道，kb/raw/kaggle-list/snapshot-20261019.md）：name-that-llm 卡片 'Featured · 50,000 Usd · 1985 队 · deadline 2027-01-14 23:59:00.817'——本条目的发现线索与规模/截止第二口径；该卡为 10-13 快照所无、本轮窗口内新赛"
    accessed: "2026-10-19"
---

# Name That LLM（kaggle-name-that-llm）— meta

## 概况（除标注外均为 2026-10-19 官方 ListPages API 直抓，赛 ID 170484）

- Google 赞助、Kaggle 承办的 Featured 文本分类赛：**LLM 作者归因（authorship attribution）**——判别 ~4,000 个无标签短段落（40–250 词，随机长度）出自 18 个前沿模型中的哪一个；官方动机（Description 原文）：合成文本充斥网络与训练集，"knowing which model wrote a given passage is critical for auditing synthetic data and detecting benchmark contamination"。与常见"人机二分类"检测器不同，本赛要求细粒度到具体模型，且 prompt 未见、长度随机，"character-count shortcuts or topic keywords" 被官方点名不可依赖——各实验室训练数据与后训练选择留下的风格指纹（词汇/措辞/标点）是唯一可靠信号。
- **18 个合法标签**（Evaluation 页全表直抓，6 实验室）：OpenAI `gpt-5.5`/`gpt-5.6-luna`/`gpt-5.6-sol`/`gpt-5.6-terra`/`gpt-6-astra`；Google `gemini-3.1-pro-preview`/`gemini-3.6-flash`/`gemini-3.7-flash`/`gemini-3.8-flash`；Anthropic `claude-fable-5`/`claude-opus-4-6`/`claude-opus-4-8`/`claude-opus-5`/`claude-sonnet-5`；Qwen `qwen3.8-max`；ZAI `glm-5.3`/`glm-5.3-flash`；Moonshot AI `kimi-k3`。段落均为真实自洽回复（仅轻度格式清理），主题覆盖哲学/物理/数学/生物/计算机/创作散文。
- **奖金 $50,000**：1st–10th 各 $5,000（rules §1.5 + Prizes 页双处直抓）。
- **热度**：开赛 5 天 1985 队（2026-10-19 CLI 列表卡口径），为当日列表中除 Getting Started 外最新的 Featured 赛。
- **窗口**：终交 2027-01-13（Timeline 口径；CLI 01-14 有一日出入，见 key_dates 注），在本轮采集窗口内。

## 赛题与数据（data-description 页直抓）

- train.csv：**2,699 段、150 个 prompt**（列 id/prompt_id/text/model）；test.csv：交互期 3 行示例、隐藏复跑约 4,000 段，**test prompt 与 train 不相交**（防 prompt 记忆）；提交 sample_submission.parquet 格式（id, model）。
- 提交为 Code Competition：notebook 评测期对隐藏测试集复跑；产出 submission.parquet（每 id 恰一行）。

## 评测（Evaluation 页直抓）

- **balanced accuracy**（宏平均）：18 类各自 recall 的均值——测试集各模型段落数不相等、公私榜模型构成不同，宏平均给每个模型同等权重；类别不平衡与私榜分布差异是显式考点。

## 规则要点（rules 直抓）

- 团队 ≤5 人；每日 5 次提交；至多 2 个 final submissions；合并队提交配额按天数×日限校验。
- Winner License CC-BY 4.0；Competition Data **CC BY-SA 4.0**（可商用但 share-alike，二次使用注意与 Apache 2.0 档的差别）；外部数据若许可证不兼容获奖开源义务，该部分可豁免开源但须申报（§2.5）。
- 评测环境：CPU/GPU ≤9h、禁网、允许自带自由公开的外部数据与预训练模型（Code Requirements 页）。

## 与既有条目的关系

- 与 `kaggle-enveda-casmi26`（谱图→结构检索/生成）、`gemma-4-dev-agent`（后训练 coding agent）、`kaggle-arc-prize-2026`（推理/程序合成）同属 Kaggle Featured 科学向赛题，但本赛是**纯文本多分类（指纹学习）**，方法论上最接近经典 NLP 分类栈（特征化微调/embedding+分类头/风格计量），为本库新增一个任务形态样本。
- 情报侧注意：本赛的 18 模型名单是 2026-10 时点六大实验室前沿模型的一次性官方盘点（含 gpt-6-astra、claude-opus-5、glm-5.3、kimi-k3 等），与 `kaggle-arc-prize-2026` M1 获奖分析中出现的 Gemma-4/Qwen 世代信号互相印证。

## 获奖情况与缺口声明

- **winners/ 未建**：赛事进行中（开赛 2026-10-14，终交 2027-01-13，放榜在其后），无任何获奖名单可抓。按 `award_levels` 前两级（1st $5,000、2nd $5,000）待 Kaggle 放榜公告后补建；**核对维度**：Kaggle 赛站 Leaderboard 页、Discussion 区 winner 公告帖。**patterns.md 未建**：无获奖作品与评审信号，不臆测。
- 公榜/私榜的段落划分比例与各模型段落数官方未公布（Evaluation 仅明示"不相等"）。

## 信源与快照

- `kb/raw/kaggle-name-that-llm/2026-10-19-pages-api.json`（ListPages API 原始 JSON，9 页全文）
- `kb/raw/kaggle-name-that-llm/2026-10-19-overview-shell.html`（SSR 壳，赛 ID 170484 提取源）
- `kb/raw/kaggle-list/snapshot-20261019.md`（CLI 列表卡：发现线索 + 队数/截止第二口径）
- 抓取通道备注：Kaggle 为 SPA 站点，正文经官方 ListPages API（competitions.PageService）匿名直抓，等效直抓官网（catalog 钦定绕行通道）；Timeline 两行为模板变量未解析（API 局限，与 PTCG 等条目同款）。

## 待核验清单

- [ ] entry_deadline / team_merger_deadline 官方数值（Timeline 模板变量未解析；可经主会话 browser-use 预抓 Overview 渲染页核对后置 verified: true）。
- [ ] 终交日一日出入澄清：Timeline "January 13" vs CLI 字段 2027-01-14 23:59:00.817（毫秒尾数与 gemma paper 赛道同款，疑为平台缓冲/复跑截止口径）。
- [ ] 18 模型名单的版本时效（Gemini 3.x/Claude fable-5 等命名以 Evaluation 页直抓为准，平台若改标签表需滚动核对——标签表变更会直接影响提交合法性）。
- [ ] 训练数据是否存在同 prompt 多段落的组泄漏边界（150 prompt/2699 段≈18 段每 prompt，暗示按 prompt 分组交叉验证的设计空间——推断，勿作事实引用）。

## 重验记录

- **2026-10-29（滚动重验·CLI 列表卡）**：1985 → **3768 队**（10 日 +1783，当期 kaggle 首屏增速最高）；CLI deadline 2027-01-14 与既有口径一致，无日期漂移。列表层核验。（来源：kb/raw/kaggle-list/snapshot-20261029.md ；抓取日期：2026-10-29）
