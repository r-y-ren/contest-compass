---
id: arxiv-2610.36114
name: "Context Is a Pipeline：agent harness 的信息损耗实测——窗口只用 5.75% 却有 1/3 工具结果被截断（字段触达率 4.7% vs 99.3%）"
field: [LLM agents, harness 工程, 可观测性]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-26"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv（5 页）+ Zenodo 复现包（doi:10.5281/zenodo.23614755，2026-10-29 API 实查 open access）"
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "工具调用类赛题的排障清单与诊断框架：把 agent 上下文建模为五阶段管道、每段有可测故障——'先查截断、再怪模型'的排障序可直接搬用；文中实测 11189 条工具结果被 harness 截掉 3827 条且截断全部产生坏 JSON，同一结果里两个字段触达率 4.7% 与 99.3% 天壤之别，可解释大量'模型不行'实为'管道漏数据'"
    reuse_cost: 低
  - track: "双创-文书与申报"
    edge: "'AI+'项目答辩中论证工程可靠性的溯源素材：受控实验显示截断的真实代价先表现为额外功（多 43% 工具调用、双倍计算、yield 0.61→0.31）而非答错——'上下文是管道不是窗口'的完整证据链可支撑技术方案里 harness 工程章节的必要性论证，数字均可溯源至本卡复现包"
    reuse_cost: 低
    open_source: "zenodo.org/records/23614755（Replication Package，open access）"
sources:
  - url: https://arxiv.org/abs/2610.36114
    title: "Context Is a Pipeline, Not a Window: Information Attrition in LLM Agent Harnesses（arXiv abs 页，v1 2026-10-26，Yuvraj Sehgal/Mahsa Panahandeh/Naser Ezzati-Jivan，Comments：5 页，附 Zenodo 复现包）"
    accessed: "2026-10-29"
  - url: https://zenodo.org/records/23614755
    title: "Replication Package（Zenodo API 实查：标题匹配、open access、1 个文件，2026-10-29）"
    accessed: "2026-10-29"
---

# Context Is a Pipeline：窗口没满，数据却在半路漏光了

> 来源：https://arxiv.org/abs/2610.36114 （v1 2026-10-26，Yuvraj Sehgal/Mahsa Panahandeh/Naser Ezzati-Jivan，5 页 1 图 2 表，Comments 附 Zenodo 复现包链接；2026-10-29 经 arXiv API 实抓摘要，Zenodo API 实查复现包 open access）。本卡内容出自本次抓取的摘要与 API 元数据，未读 PDF 全文。

## 是什么

对真实工具调用型 agent 的**上下文信息损耗（information attrition）测量研究**。核心论点：评价 agent 只看"窗口多大"和"答对率"两个数，漏了第三个数——**工具输出在到达模型之前丢了多少**。作者在一个查 Linux 内核 trace 定位注入故障的真实 agent 上测得：720 次运行中最大 prompt 只用了窗口的 5.75%，但 11189 条工具结果里 3827 条（约三分之一）在到达模型前被 harness 截断，且每条被截结果都成了坏 JSON——harness 按固定长度切片 JSON 文本，会把靠尾部的数据整块删掉。

## 解决什么问题

"agent 表现差"的归因普遍朝模型能力去，本文提供第五个嫌疑环节：**harness 管道本身**。贡献有四：(1) 五阶段上下文管道模型，每段附实测故障；(2) 重放 864 条真实工具结果，含一条生产 trace——其中上线版本的截断恰好删掉故障证据的全部 128 条记录；(3) 受控实验证明截断的真实代价先表现为额外功：多 43% 工具调用、双倍计算、yield 从 0.61 跌到 0.31（agent 绕道仍能找到答案，所以不是简单答错）；(4) 调研七个 agent 框架，发现两个用同样的不安全方式截断工具输出。

## 相比前方法优势

- 证据分层清晰：现场测量（5.75% 窗口占用 vs 1/3 结果被截）→ 单例剖析（128 条证据全灭）→ 受控实验（0.61→0.31 yield）→ 框架普查（2/7 中招），四层互相咬合；
- 触达率反差是最锋利的单点证据：同一结果里一个字段只有 4.7% 的调用能到达模型，另一个 99.3%——而哪个字段载有故障证据取决于故障进程在 trace 中的早晚，诊断准确率随之分裂；
- 结论口径诚实：摘要明说"截断是否真导致精度下降仍是开放问题"，不越过相关性下断言。

## 局限（如实标注）

- 5 页短文、单一 agent 场景（内核 trace 排障），管道模型在其他任务域的外推需读全文核对；
- 摘要明示因果性未完全钉死（受控实验显示的是"额外功先恶化"，精度因果仍开放）；
- 复现包为研究工件而非可复用工具，五阶段诊断要自己往自己的 harness 上套；
- 普查只覆盖七个框架且点名但不展开，选型时应自查所用框架的截断实现。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：任何带工具调用的赛题，调试时先给 harness 加"截断审计"——记录每条工具结果的原始长度/送达长度/字段级触达率，再看模型表现；文中字段级 4.7% vs 99.3% 的审计口径可直接照抄成日志 schema，成本一个包装函数。
- **双创-文书与申报**（reuse_cost 低）：申报书/答辩的"工程可靠性"章节引用本卡证据链（复现包 open access 可溯源），论证"优化管道优先于堆模型参数"；43% 额外调用、双倍计算这类数字把"可靠性工程"从口号变成实测账。

**族内定位**：库内 arxiv-2610.00906（ActiveSaddler，harness 自动优化的课程层）与 arxiv-2608.30976（CastClaw，harness 工程）占"harness 怎么建/怎么进化"位，arxiv-2610.07625（Stateless Language Agents）占"上下文预算"位；本卡占"harness 可观测性与故障测量"位——是这条线上第一张"审计工具本身"的卡，其余卡的方法若失效可先用本卡的五阶段模型定位病灶。
