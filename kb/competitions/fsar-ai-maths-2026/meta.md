---
id: fsar-ai-maths-2026
name: "SAIR AI for Maths 开放竞赛（Andrews-Curtis / Lean Kernel / Inverse Galois；XTX Markets 资助）"
tier: 学科竞赛
directions:
  - 数模与时序预测
status: active
organizer: "SAIR（The Foundation for Science and AI Research，Fields 奖得主 Terence Tao 与诺贝尔奖得主 Barry Barish 共同创立；公告原文缩写 SAIR，任务包所写 FSAR 系笔误）。分赛共组：ACC = Caltech + SAIR（Lucas Fagan / Sergei Gukov / Terence Tao）；Lean Kernel = Lean FRO + SAIR（Joachim Breitner / Leonardo de Moura / Kim Morrison / Terence Tao）；IGP24 = 与 LMFDB 协作（John Jones / Jen Paulhus / David Roe / Andrew Sutherland / Terence Tao）。资助：XTX Markets（2026-09-16 公告）；赛站部署产物中 ACC 赞助标记 [xtx]、Lean Kernel [sig, xtx]（SIG=Susquehanna International + XTX Markets）"
award_levels:
  - name: "各赛独立 Leaderboard 排名"
    count_or_ratio: "无奖金金额公布"
    note: "三项赛官方规则全文均无奖金节（2026-10-07 核对）；平台通用占位文本 'Prize details will be announced by the organizer.' 存在。IGP24 按 (24Tt,r) 对积分 2^(1-k)·logD0/logD 计总分；LK 每题一榜按内核指令数中位数之和；ACC Discovery 有 Leaderboard 标签页"
  - name: "SAIR Contributor Network 收录与公开署名"
    count_or_ratio: "提交即自动公开（署名 + 时间戳 + 版本史）"
    note: "ACC Proof Track 提交强制勾选共享协议；赛站文本 'All contributions are recognized and cited'"
  - name: "赛后结果与数据集公开发布"
    count_or_ratio: "IGP24 数据集已发布（SAIR Competition Data License）；LK 承诺开源许可发布全部结果与基准数据"
    note: "LK Stage 1 文本：'all results and benchmark data will be released publicly under an open-source license'"
key_dates:
  xtx_grant_announced:
    date: "2026-09-16"
    verified: true
    note: "双源：aimoprize.com 官方公告（2026-10-04 复抓 + 2026-10-07 curl 原件再核）+ updates 索引月度条目"
  igp24_opens:
    date: "2026-06-16"
    verified: false
    note: "单源：官方 igp24.md 'Competition opens: June 16, 2026'；无第二独立官方源"
  igp24_closes:
    date: "2026-08-15"
    verified: false
    note: "单源：官方 igp24.md 'Competition closes: August 15, 2026, AoE'；官方数据集页 'concluded' 表述佐证其已结束（非日期精度第二源）"
  lk_stage1_registration:
    date: "2026-08-26"
    verified: true
    note: "双源：赛站部署文本 + 官方 GitHub rules/overview.md（'Stage 1 registration and team formation open: August 26, 2026'）"
  acc_launch:
    date: "2026-09-11"
    verified: true
    note: "双源：赛站部署文本 + 官方 GitHub pinned revision a0fd6e6（Discovery Track 'September 11, 2026 at 16:00 UTC'；Proof Track 同日）"
  lk_stage1_launch:
    date: "2026-09-15"
    verified: true
    note: "双源：赛站部署文本 + 官方 GitHub（'Stage 1 official launch: September 15, 2026'）"
  lk_stage1_deadline:
    date: "2026-11-20"
    verified: true
    note: "双源：'Stage 1 submission deadline: November 20, 2026, 23:59 AoE (UTC−12)'"
  acc_deadline:
    date: "2026-11-30"
    verified: true
    note: "双源：'Submission deadline for all tracks: November 30, 2026 AoE'"
  lk_stage2_begins:
    date: "2026-12"
    verified: false
    note: "月精度：'Stage 2 begins: December 2026; the exact date will be announced'"
deliverables:
  - "IGP24（已结束）：submission.txt 纯文本，每行一个 monic 整系数 24 次多项式（25 个系数升幂、a24=1、a0≠0）；每队每日 ≤200 次提交、每次 ≤1000 项、文件 ≤1,000,000 字节（2026-07-31 起生效）；Magma 验证 + PARI/GP 判别式评分"
  - "ACC Discovery Track：对官方公布 presentations 找最短 trivialization 初等动作序列（覆盖 AC 与 Stable AC）；ACC Proof Track：平台表单提交——方向（proof/disproof）+ 描述必填 + 可选 Lean 4 形式化（公开 GitHub repo + 完整 commit hash 必填）+ 可选 arXiv 链接 + 强制勾选公开共享协议"
  - "Lean Kernel Stage 1：每题一个 Submission.lean（≤1 MiB，namespace Submission：impl 实现 + impl_correct 全量 ∀ 输入正确性证明）；禁 sorry/admit/native_decide/未批准公理/预计算答案/压缩数据；评分 = pinned Lean 内核 3 次重放的逐用例中位指令数之和（8 题：fib/partition/mertens/primecount/permanent/ca-rule110/sha256/polydisc）"
  - "共同：SAIR 平台注册（账号+资料+同意赛 terms）+ 组队（每主体仅一队、反 sockpuppet 条款）；提交自动进入 SAIR Contributor Network；三项赛均自认 experimental（参赛算力成本自理、组织方不报销）"
ai_policy:
  summary: >-
    分赛三层实抓（2026-10-07）：①IGP24 官方规则明文允许并事实上鼓励 AI——"Participants may use
    computational algebra systems, public databases, papers, preprints, code search, LLMs, agents, and
    collaborative workflows."；"The competition rewards verifiable mathematical output, not the method used
    to find it."；团队节明文欢迎 "AI-assisted workflows"（组队不设上限以支持 "larger groups that combine
    mathematical insight, computation, software engineering, and AI-assisted workflows"）。②ACC 与 Lean
    Kernel 官方文本未见 AI 工具专门条款（已核 overview/proof/rules 全文）：LK 规则 R1–R5 只约束产物形态（人类可读
    代码 + 机器验证证明 + 禁预计算答案），对 AI 生成保持中性——凡能通过内核验证与指令数排名者即为有效；ACC Proof
    Track 要求引用他人工作、GitHub 链接附完整 commit hash（可审计）。③数据许可侧的反向条款（勿与参赛工具政策混同）：
    SAIR Competition Data License 限制将已发布竞赛数据用于商业 AI——"training, fine-tuning, distillation,
    evaluation, improvement of commercial AI models" 等须 SAIR 与共组方书面授权。纲领层（XTX 公告）："All of
    SAIR's competitions are run openly, with public datasets, reproducible evaluation and results that
    reflect the collective contributions of the mathematics community."
  url: https://competition.sair.foundation/competitions/igp24
  checked: "2026-10-07"
credibility: 官网
last_verified: "2026-10-07"
sources:
  - url: https://aimoprize.com/updates/2026-09-16-update-on-xtx-markets-ai-philanthropy
    title: "XTX 公告原件（2026-10-07 curl）：AIMO 关闭、'This grant will fund three state-of-the-art AI for maths competitions: the Andrews-Curtis Conjecture Challenge (Stage 1); the Lean Kernel Challenge (Stage 1); and the Inverse Galois Problem Challenge (Stage 2).'、SAIR 命名与创始人、'All of SAIR's competitions are run openly...'；快照 2026-10-07_aimoprize-closure-announcement.html"
    accessed: "2026-10-07"
  - url: https://competition.sair.foundation/competitions/igp24.md
    title: "IGP24 官方规则+评测全文（任务/评分公式/提交限额/Magma+PARI/GP 验证/AI 原文/时间线 06-16 开 08-15 止）"
    accessed: "2026-10-07"
  - url: https://competition.sair.foundation/competitions/acc
    title: "ACC 赛站页（JS 渲染；正文经官方 bundle 提取并与 GitHub pinned revision 核对）：双轨制、关键日期、共组、反作弊、experimental 条款"
    accessed: "2026-10-07"
  - url: https://github.com/SAIRcompetition/Andrews-Curtis
    title: "ACC 官方仓库（pinned revision a0fd6e6 competition/rules/overview.md）：ACC 日期/共组/任务第二源"
    accessed: "2026-10-07"
  - url: https://competition.sair.foundation/competitions/lean-kernel
    title: "Lean Kernel Challenge 赛站页（JS 渲染；正文经官方 bundle 提取）：Stage 1 规则 R1-R5、8 题、关键日期、Lean FRO+SAIR 共组"
    accessed: "2026-10-07"
  - url: https://github.com/SAIRcompetition/lean-kernel-challenge
    title: "LKC 官方仓库（README + rules/overview.md，main 分支）：Stage 1 日期/8 题清单/提交与评分第二源"
    accessed: "2026-10-07"
  - url: https://sair.foundation/
    title: "SAIR 主站（index.md + llms.txt 官方 markdown 视图）：机构全名与缩写、创始人、Open Math Models/竞赛生态入口"
    accessed: "2026-10-07"
  - url: https://sair.foundation/open-math-model
    title: "Open Math Models 纲领页（JS 渲染，shell 原件入库；正文经 web reader 抓取）：'Math 2.0'、社区共治、开源许可（Apache 2.0/MIT/CC BY 4.0）、数据归属"
    accessed: "2026-10-07"
  - url: https://competition.sair.foundation/llms.txt
    title: "竞赛门户官方 markdown 索引（列 IGP24/Modular Arithmetic/Equational Theories Stage 1+2 四赛；未含 ACC/LK，属构建滞后——门户导航与 bundle 均已含两赛 NEW 标记）"
    accessed: "2026-10-07"
  - url: https://competition.sair.foundation/assets/index-BeSAjzBJ.js
    title: "竞赛门户官方部署 bundle（md5 08f66fcef38fd04f7f3980edaa701aae）：ACC/LKC 页面文本、赞助标记 [xtx]/[sig,xtx]、API 端点与竞赛 id 清单的原始出处"
    accessed: "2026-10-07"

---
# SAIR AI for Maths 开放竞赛（fsar-ai-maths-2026）— meta

## 命名勘误（对任务包线索）

- 任务包与前序记录所写 **"FSAR"（Foundation for Science and AI Research）有误**：XTX 公告与 SAIR 官网原文均为 **"The Foundation for Science and AI Research (SAIR)"**（公告原文："SAIR was co-founded by the Fields Medallist, Terence Tao, and the Nobel Laureate, Barry Barish"）。条目 id 沿用协调者指定的 `fsar-ai-maths-2026` 以保持引用一致，正式名称以 SAIR 为准。
- 另注意 `sair.org` 为同名无关组织（Southern Association for Institutional Research，院校研究团体），检索时勿混淆；本条目所有信源均在 `sair.foundation` / `competition.sair.foundation` / 官方 GitHub org `SAIRcompetition`。

## 与 AIMO 的沿革关系（2026-09-16 XTX 公告，实抓）

- XTX Markets 于 2026-09-16 公告整体关闭 AIMO Prize（含 $5mn Grand Prize 不再推进），理由：前沿与开源权重模型已在 IMO 题集满分，竞赛 "is now unlikely to meaningfully incentivise valuable work"。未支出资金即刻转投：
  - **$10mn → Lean FRO**（覆盖核心运营成本至 2030）；
  - **$10mn → Mathlib Initiative**（同上）；
  - **资助 SAIR 举办三项开放 AI-for-maths 竞赛**：Andrews-Curtis Conjecture Challenge（Stage 1）、Lean Kernel Challenge（Stage 1）、Inverse Galois Problem Challenge（Stage 2）——即本条目三赛。
- 配套关系（区分事实层级）：Lean FRO 获 $10mn 运营资助与 SAIR×Lean FRO 共组 Lean Kernel Challenge 是两条独立事实；IGP24 的协作对象是 LMFDB（非 Mathlib）。公告 stage 标注（ACC=Stage 1 / LKC=Stage 1 / IGP=Stage 2）与 LKC 自身的 multi-stage 序列（其 Stage 1=2026 下半年、Stage 2=2026-12 起）是两套口径，公告的 stage 语义官方未再解释，列入待核验。
- 公告纲领原文（写入 ai_policy 的开放性承诺）："All of SAIR's competitions are run openly, with public datasets, reproducible evaluation and results that reflect the collective contributions of the mathematics community."

## 立条判定（一条目而非三条）

- 三赛**共用同一竞赛程序与平台**（competition.sair.foundation：同一 SAIR 账号注册、同一组队与反 sockpuppet 条款、同一 experimental 免责条款、同一 Zulip 社区、同一 Contributor Network 公开机制），且同属 XTX 2026-09-16 一笔资助计划 → 按任务包判据建一条目；三赛题制差异在分赛节如实记录（ACC=双轨发现+证明；LKC=内核计算优化+机器验证证明；IGP24=多项式发现+判别式评分），后续若 LKC Stage 2 或后续届扩张成独立周期，可再拆分。

## 分赛节（全部为 2026-10-07 实抓）

### 1. Andrews-Curtis Conjecture Challenge（ACC）— status: active

- 定位：对群 presentation 平凡化问题（Andrews–Curtis 猜想及其 stable 版）的开放竞赛——"find short trivializations of group presentations and advance research toward proving or disproving the Andrews–Curtis conjecture"。
- 双轨（各覆盖 AC 与 Stable AC）：**Discovery Track**（找最短初等动作序列，2026-09-11 16:00 UTC 上线）+ **Proof Track**（思想/部分结果/完整证明或反证均可提交，自愿参与但提交须同意公开共享，自动进 Contributor Network）；Proof Track 提交表单字段：方向、描述（必填）、Lean 4 形式化 repo（可选）+ 完整 commit hash（有 repo 则必填）、arXiv 链接（可选）。
- 关键日期：2026-09-11 双轨上线；**2026-11-30 AoE 全轨道截止**。共组：Caltech + SAIR（Fagan/Gukov/Tao）。官方仓库 SAIRcompetition/Andrews-Curtis（问题、示例、验证工具；Lean 形式化定义在 tools/lean/AC.lean）。
- 赛站导航含 Leaderboard 与 Discoveries 标签页（phase: pre-registration 之外可用）。

### 2. Lean Kernel Challenge（Stage 1）— status: active

- 定位：多阶段系列赛，改进 Lean 4 kernel 中验证计算的性能——参赛者对 8 个固定规范问题提交 `Submission.lean`（impl + 全量 ∀ 输入正确性证明），按 pinned 内核 3 次重放的逐用例中位**指令数**之和排名（越低越好；每题独立榜单）。
- 规则 R1–R5：仅交 Submission.lean 且代码人类可读（禁压缩数据/字节码）；只用锁定依赖且实现须 total、kernel-reduce 到输出字面量（禁 partial/unsafe、禁预计算答案与输入特化硬编码）；须证明 ∀ n, impl n = spec n（过测试不够）；禁 sorry/admit/native_decide/未批准公理；只有计算指令数影响排名。
- 8 题：fib、partition、mertens、primecount、permanent（0/1 矩阵积和式）、ca-rule110（Rule 110 元胞自动机）、sha256、polydisc（24 次多项式判别式）。资源限制逐题公布（如 ca-rule110：4 GiB 内存、三组隐藏用例 watchdog 30/60/120s）。
- 关键日期：2026-08-26 注册与组队开放；2026-09-15 官方开赛；**2026-11-20 23:59 AoE (UTC−12) Stage 1 截止**；Stage 2 2026-12 起（日期待公布）。共组：Lean FRO + SAIR（Breitner/de Moura/Morrison/Tao）。Playground Standard 模式每日 2 次运行（00:00 UTC 重置）。

### 3. Inverse Galois Problem Challenge（IGP24）— status: ended（已发放数据集）

- 定位：逆 Galois 问题的 degree-24 显式版——25,000 个 degree-24 传递置换群（24T1–24T25000）×可能签名，共 165,836 个 (24Tt, r) 对；参赛者提交 monic 整系数 24 次多项式，Magma 验证 Galois 群标签与实根数，PARI/GP 算判别式；得分 2^(1-k)·logD0/logD（发现者越少、判别式越小分越高；LMFDB 基线对可被精确 nfdisc 严格改进解锁，LMFDB 计 1 支基线队）。
- 时间线：2026-06-16 开赛 → 2026-08-15 AoE 截止（单源日期）；期内三次规则修订（06-18 基线改进解锁、07-09 mixed discriminant 回退、07-31 提交限额 200 次/日 × 1000 项/次）。与 LMFDB 协作；共组 Jones/Paulhus/Roe/Sutherland/Tao。
- 已结束状态：官方数据集页原文 "The competition has concluded; its mathematical results provide a starting point for further research into degree-24 number fields and their Galois groups."——数据集按 **SAIR Competition Data License** 发布（允许非商业科研教育；商业与营利实体用途含商业 AI 训练须书面授权）。榜单/发现明细在平台动态接口（/api/igp24/leaderboard 等，需 API key），winners 深构待后续分片。
- 背景联动：官方文本提及 degree 23 仅剩 M23（23T5）未实现，并链接为 Epoch AI FrontierMath 的 inverse Galois open problem。

## 奖金情况（verified absence，2026-10-07）

- 三项赛官方规则全文**均无奖金金额**；平台存在通用占位 "Prize details will be announced by the organizer."（隐私条款提及 prize distribution 仅为平台通用措辞）。XTX 公告只说 "fund three state-of-the-art AI for maths competitions"，未承诺奖金。激励结构 = Leaderboard 排名 + Contributor Network 公开署名 + 结果/数据集公开发布（学术信用激励模式）。

## AI 政策原文（2026-10-07 抓取，官网）

- IGP24："Participants may use computational algebra systems, public databases, papers, preprints, code search, LLMs, agents, and collaborative workflows." / "The competition rewards verifiable mathematical output, not the method used to find it." / 团队节："larger groups that combine mathematical insight, computation, software engineering, and AI-assisted workflows"
- SAIR Competition Data License（数据用途限制，非参赛工具条款）："**Commercial AI:** the restrictions include training, fine-tuning, distillation, evaluation, improvement of commercial AI models, generation of training material for them, and support for commercial retrieval systems."（例外须 SAIR + 全体共组方书面授权；"Public availability alone is not authorization."）
- ACC / LKC：官方文本无 AI 工具专门条款（已核全文，如实记录）；约束落在产物可验证性上（commit hash 审计 / 机器验证证明 / 禁预计算答案）。
- Open Math Models 纲领（sair.foundation/open-math-model，2026-10-07 reader 抓取）："building open-source AI models for mathematical research, governed by the mathematical community and open to all"——纲领是开源数学 AI 模型（"Math 2.0"），与各赛对参赛工具的开放态度一致。

## 信源与快照

- `kb/raw/fsar-ai-maths-2026/`（MANIFEST.md 逐文件列 URL 与抓取方式；2026-10-07）
- 关键路径说明：ACC/LKC 页面为 JS 渲染 SPA，官方文本经**部署 bundle 提取**（解析视图，已与官方 GitHub 仓库双源核对）；IGP24 页有官方服务端 .md 视图原件直存；前次 2026-10-04 公告复查在 `kb/raw/kaggle-ai-mathematical-olympiad-progress-prize-3/recheck-20261004-aimo-closure.md`。

## 待核验清单

- [ ] 公告 stage 语义（ACC/LKC=Stage 1、IGP=Stage 2）官方未解释——与 LKC 自身 Stage 1/2 序列的关系待官方后续公告澄清。
- [ ] IGP24 opens/closes 两日期的第二独立官方源（现为官方页单源 verified:false）；IGP24 结果公报/最终榜单官方公告页（blog 未被搜索引擎收录，2026-10-07 检索无）。
- [ ] ACC/LKC/IGP24 奖金是否后续公布（平台有占位文本；建议下轮复查）。
- [ ] ACC Discovery Track 评分细则（discovery.md 全文：官方仓库 competition/rules/discovery.md）与 Leaderboard 计分口径。
- [ ] LKC 8 题逐题资源限额与 config（rules/problems/*.md）；Playground 限额口径（per team vs per team/problem，官方声明将在开赛前澄清）。
- [ ] IGP24 榜单/发现数据深构（/api/igp24/leaderboard 需 API key/登录态——browser-use 路线）→ winners/2026.md 分片入口；同批可深构 LKC 每题榜单与 ACC Discoveries。
- [ ] SAIR 竞赛 terms 与 data_license 全文（/terms、/data_license 路由未直抓）。
- [ ] winners 深构覆盖：本条目暂无 winners/<年>.md（IGP24 已结束有数据，ACC/LKC 赛中）；award_levels 前两级覆盖标准待数据落地后执行。
