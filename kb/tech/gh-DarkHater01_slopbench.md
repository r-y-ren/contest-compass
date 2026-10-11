---
id: gh-DarkHater01_slopbench
name: "SlopBench：量 LLM agent 写了多少废代码的基准（inflation 代码膨胀率 + 极简提示差值 ponytail Δ）"
field: [LLM agents, 代码生成评测, 软件工程]
directions: [创新创业大赛]
published: "2026-10-10"
maturity: demo
reproducibility_level: high
signal:
  venue: "GitHub（MIT；2026-10-11 API 实抓：10 stars / 1 fork / 当日仍有推送，GitHub Actions 周更快照）"
  stars: 10
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "'AI 研发效能/代码降本'方向产品的现成测量口径与开源基线：inflation = 生成 LOC ÷ 参考解 LOC，且只对通过测试的运行计数（pass@1 ≥ 0.6 才计入，防'两行_obfuscated 过测'与'5 次过 1 次'两种作弊口径，ADR-001 公开可辩）；ponytail Δ 证明'极简系统提示'这个零成本杠杆能砍 LOC——两个数字合起来正好是'AI 代码审查工具'类项目的产品指标定义与市场教育素材；参考解在库内手写、可经 PR 争议，分母公开是刻意设计，申报书的评测方法章节可直接引用这套'可争议基准'范式"
    reuse_cost: "低"
    open_source: "https://github.com/DarkHater01/slopbench（MIT；OpenRouter 驱动，Docker 沙箱 --network none --read-only 非 root 512MB 内存 50s 超时，5 任务×5 重复，scorer 自带自测 test_score.js 无 API 也可跑）"
sources:
  - url: https://github.com/DarkHater01/slopbench
    title: "slopbench 仓库（README+文件树+API 元数据，2026-10-11 实抓：tasks/ 5 个 airtight Python 规格+参考解+pytest，runner/run.js 沙箱执行，runner/score.js 聚合出 data/results.json，index.html 静态榜单）"
    accessed: "2026-10-11"
---

# SlopBench：代码基准都在测"能不能解出来"，它测"浪费了多少行"

> 来源：https://github.com/DarkHater01/slopbench （MIT，JavaScript，2026-10-10 创建，2026-10-11 实抓 README、git trees 与 API 元数据；创建次日即有推送，CI 周更快照到 data/results.json，历史快照存 git）。

## 是什么

一个只回答"模型解出任务时**多写了多少代码**"的基准。每模型每任务跑两遍（vanilla 提示 vs minimal 极简提示），报告三个数：

- `pass@k`：能不能解出来（传统口径）；
- `inflation = 生成 LOC ÷ 参考解 LOC`：12 行任务写 96 行即 8.0×——**只对通过测试的运行计数**，且要求该任务 pass@1 ≥ 0.6 才计入 LOC（防止用失败解污染统计，规则在 docs/adr/ADR-001 公开）；
- `ponytail Δ`：极简提示（"写最少的完全满足规格的 Python，无类无抽象无注释无规格外错误处理"）相对 vanilla 的中位 LOC 差——不换模型就能拉的最低成本杠杆。

当前快照仅 1 个模型有数（poolside/laguna-s-2.1:free：pass@1 1.0，inflation 1.20×，极简提示再省 1.8 LOC），3 个模型快照进行中（2026-10-11 实抓口径）。执行侧：模型代码视为敌意输入，Docker 沙箱断网+只读根+非 root+512MB/1 核/50 秒超时，每任务 5 次重复，5 连不过则 pass@5 记 false 且 LOC 丢弃（"不可依赖的解不值得计数"）。

## 解决什么问题

pass/fail 类代码基准的信号已经饱和（头部模型都能过测），但工程团队的真实痛点是 AI 生成代码的**评审负担**：过了测试的膨胀代码一样要人读人养。SlopBench 把"膨胀"变成一个有防作弊口径、有公开分母、可周更可争议的度量——填补的是评测维度的空白而非又一个 pass@k 榜。

## 相比前方法优势

- 维度独有：库内 nopus 管"编码 agent 回复的散文质量门"、omp-best-of 管"候选择优编排"，均不度量代码量膨胀；既有 pass@k 类基准无此口径；
- 防作弊设计认真：inflation 只在可信通过（pass@1≥0.6 且 5/5）上计数，规则公开可辩（ADR-001）；
- 分母（手写参考解）在库内、可 PR 争议——评测的"可争议性"本身是设计目标；
- 沙箱约束齐全（断网/只读/非root/资源限额），harness 抄来即用于任何 LLM 代码执行评测。

## 局限（如实标注）

- 极早期：5 个任务、1 个模型出数、单维护者、10 stars——尚无统计效力，结论只能当"口径演示"不能当"模型排名"；
- inflation 以手写参考解 LOC 为分母，参考解风格（紧凑 vs 常规）直接左右数值，虽有 PR 争议机制但当前样本无可辩先例；
- "膨胀=评审负担"的因果主张未做下游实证（如评审时长/缺陷率关联）；
- 任务全为 Python 小规格题，对大库重构/多文件场景无覆盖。

## 如何用于比赛（比赛映射展开）

1. **双创-文书与申报（AI 研发效能/代码审查类产品）**：直接复用其指标定义做产品内置度量（"本工具把 AI 生成代码 inflation 从 8.0× 压到 2×"式表述），并用 ponytail Δ 的实证逻辑（提示工程即可省 LOC）做申报书里的低成本方案论证；引用其 ADR-001 防作弊口径展示评测设计的严谨性。reuse_cost 低：scorer/沙箱 runner 是现成 MIT 代码，换成自己任务集即可。
