---
competition_id: fsar-ai-maths-2026
last_verified: 2026-10-07
coverage: []            # 尚无 winners 深构：IGP24 已结束但榜单数据未深构，ACC/LKC 赛中
confidence: 中          # 官网信源（规则/评分/政策均官方直抓双源），但零获奖样本——评审偏好只能从规则文本观察
sources:                # 汇总性引用（明细在 meta.md sources 与 kb/raw/fsar-ai-maths-2026/MANIFEST.md）
  - url: https://competition.sair.foundation/competitions/igp24.md
    accessed: "2026-10-07"
  - url: https://competition.sair.foundation/competitions/acc
    accessed: "2026-10-07"
  - url: https://competition.sair.foundation/competitions/lean-kernel
    accessed: "2026-10-07"
  - url: https://aimoprize.com/updates/2026-09-16-update-on-xtx-markets-ai-philanthropy
    accessed: "2026-10-07"
---

# SAIR AI for Maths 开放竞赛（Andrews-Curtis / Lean Kernel / Inverse Galois）模式库（patterns）

> 本文件是 KB-1 条目的解构总结层。**当前零获奖样本**（三项赛均无奖金、无"获奖名单"概念，激励为榜单排名 + Contributor Network 公开署名 + 数据集公开发布），评审偏好仅能从官方规则/评分文本观察，方法论分布无样本支撑——相关节如实留空并声明，宁缺毋滥。

## 一、评审偏好（从章程/评委讲评/获奖名单可观察到的取向）

- **"奖励可验证产出，不问方法"是该赛系的宪法级偏好**。IGP24 官方原文："The competition rewards verifiable mathematical output, not the method used to find it."——LLM/agent/代码搜索全部明文允许，唯一通行证是通过官方验证管道（Magma + PARI/GP / Lean 内核检查）。
- **可复现与可审计强制嵌入**：ACC Proof Track 要求引用他人工作、GitHub 链接必须附完整 commit hash；IGP24 高分提交组织方可要求 provenance；LKC 评分完全由 pinned 内核重放决定。"collective contributions"（社区共建）被明文写为赛事目的（XTX 公告语）。
- **排名逻辑奖励稀缺性与领先度而非绝对量**：IGP24 单队独得一个新 (24Tt,r) 对 = 1 分，多队同得按 2^(1-k) 指数分摊（先发优势显著），判别式更小给 log 比值温和加成；LKC 每题独立榜单、按内核指令数中位数之和（工程优化深度的直接度量）；ACC Discovery 奖励"最短"平凡化序列。
- **公开共享即参赛代价**：ACC Proof Track 提交强制勾选公开共享（进 Contributor Network，带时间戳与版本史）；LKC 赛后全部结果与基准数据开源发布——参赛即贡献公共知识库。

## 二、方法论分布（获奖作品的方法/方案套路）

| 模式 | 出现频次/占比 | 代表年份与条目 | 可迁移性 |
|---|---|---|---|
| （无获奖样本——IGP24 榜单未深构、ACC/LKC 赛中；频次不代表总体，此表待 winners 分片后回填） | | | |

- 规则文本可辨的**方法友好面**（非获奖统计）：IGP24 官方点名可用了方法——计算代数、定向构造、specialization、composita、局部约束、模因子分解模式、resolvents、类域构造；LKC 本质是算法+表示优化赛（官方声明灵感来自 Lean Kernel Arena 但聚焦"algorithms and representations"）。

## 三、往届差异化点（什么样的作品拿到了最高奖）

- 无往届获奖样本（IGP24 为首届已结束、结果公报未检索到；ACC/LKC 为首届赛中）。可观察到的"上榜差异化杠杆"（规则层证据）：IGP24 = 抢先实现无人做过的 (24Tt,r) 对（独得 1 分 vs 分摊）+ 更小判别式；LKC = 单题全用例通过后的内核指令数极致优化（中位数计分压制方差）；ACC = 更短平凡化序列 / 更接近完整的证明贡献。
- 首届效应：三项赛均为 2026 年新设（XTX 2026-09-16 资助公告口径；IGP24 实际 06-16 先行开赛），基线/题目首次公开，先发与搜索工程红利大。

## 四、反面观察（常见失分模式，若有依据）

官方规则原文点名的无效进度/失格模式（信源：官网）：

- IGP24 "Invalid competition progress" 六条：把官方基线对当新发现；刷重复/变号/平移/缩放等平凡等价变体浪费评测资源；在提交中塞自报 24Tt/r/判别式列图绕过验证；利用解析器边界情况/超时/非确定性/验证器实现细节；改基线或验证脚本自报成绩；使用组织方私有数据或泄露的基线更新。
- LKC R1–R5 反面清单：预计算答案查找表与输入特化硬编码（含编码进条件分支）、压缩数据/字节码、partial/unsafe、sorry/admit/native_decide/未批准公理、"attempts to obtain scores through precomputed answers or manipulation of the evaluation process"。
- ACC：coordinated cheating（含 sockpuppet 多队）连带全队 disqualify；引用他人工作不注明（Proof Track 明文要求 cite）。
- 数据合规红线（对生成作品复用该赛数据者）：SAIR Competition Data License 限制商业用途与商业 AI 训练（需 SAIR+共组方书面授权）——"Public availability alone is not authorization."

## 五、赛点检查表（评审标准 → 可执行检查项；快循环验收清单的派生源）

- [ ] **验证优先**：产出是否 100% 通过官方验证器（IGP24=Magma+PARI/GP 管道 / LKC=pinned Lean 内核含全量 ∀ 证明 / ACC=官方验证工具或 Lean 形式化）——任何未验证声明=0 分。
- [ ] **无禁用构造**（LKC 向）：代码人类可读、无预计算答案/输入特化分支、无 sorry/native_decide/未批准公理、只用锁定依赖。
- [ ] **查新与引用**：提交前对照官方基线（IGP24=冻结 LMFDB 基线 CSV；ACC=已公布 presentations 与 Contributor Network 已有提交），引用他人工作并附 commit hash。
- [ ] **稀缺性策略**（IGP24 向）：优先攻无人做的 (24Tt,r) 对（独得 1 分）而非挤已知对；判别式优化作为次级加成。
- [ ] **资源限额内**：LKC 逐题内存/watchdog/1 MiB 文件上限；IGP24 每日 200 次×1000 项提交限额——提交策略按限额规划。
- [ ] **共享义务**：接受提交即公开（Contributor Network）——作品中不得含不愿公开的成分。
- [ ] **AI 工具面**：IGP24 明文可用 LLM/agent；ACC/LKC 无专门条款但产物须可验证可审计——AI 生成产物必须通过同一验证管道并保留出处记录。

## 六、对本框架的启示（喂给 K-02 / 验收报告）

- **方向契合**：该赛系是"数模与时序预测"方向外的数学发现赛，但与我方"AI 辅助原创"产线高度兼容——官方明文欢迎 LLM/agent 工作流（IGP24 原文），评审只认可验证产出，天然适配"AI 生成+机器验证+人工复核"栈。
- **作品工程要点**：交付物是纯文本/单文件（submission.txt / Submission.lean / 表单+repo），无 notebook/算力挂靠（与 Kaggle 系最大差异）；算力成本自理（experimental 条款明文不报销）——战役预算须自筹算力。
- **合规栈**：反 sockpuppet（一主体一队）、共享协议、引用义务、数据许可（商业 AI 用途限制）四层都要进 acceptance 检查表；org 归属 SAIRcompetition GitHub（MiB 级提交文件，无外部 API 依赖）。
- **策略性观察**：三项赛无奖金、以学术署名与公开数据集为激励，适合作为"低成本高信用信号"的练兵战役（尤其 IGP24 数据集已开放=免赛坐条件即可做后续研究型作品）；LKC Stage 2（2026-12）与 ACC（11-30 截止）是 2026-Q4 的两个窗口。
- **KB 后续**：IGP24 榜单深构（winners/2026.md）+ LKC Stage 1 放榜（11-20 后）+ ACC 截止（11-30）后回填第二节方法论分布。
