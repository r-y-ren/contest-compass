---
id: gh-qybaihe_bla
name: "BLA（Blind LLM Agents）：对 AI 逆向工程的对抗盾——Poison→Exhaust→Hallucinate 三段防御，覆盖二进制/Electron/JS/Python/WASM（204★，MIT）"
field: [LLM agents, 对抗安全, 软件保护]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-25"
maturity: demo
venue_tier: other
reproducibility_level: high
signal:
  venue: "GitHub（2026-10-29 API 实查：204 stars/57 forks，MIT，TypeScript，2026-10-25 创建，2026-10-28 仍有推送，活跃）"
  stars: 204
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "安全赛道（AI 攻防/逆向对抗）的现成防御件：以 Poison→Exhaust→Hallucinate 三段流程对抗 REA 类 AI 逆向 agent，MIT 协议、覆盖 binary/Electron/JS bundle/Python/WASM 五类产物，可直接集成进参赛作品做'抗 AI 逆向'现场演示——选手间几乎无人带防御件，差异化显性"
    reuse_cost: 低
    open_source: "github.com/qybaihe/bla（MIT，2026-10-29 API 实查 204★）"
  - track: "双创-文书与申报"
    edge: "'AI 时代的软件保护'选题支撑：204★/MIT/五类产物覆盖/针对具名攻击 agent（REA）的对抗叙事，可作安全类双创项目的核心组件或竞争壁垒论据；'防御 AI 逆向'切口在双创申报里尚属少见位"
    reuse_cost: 低
    open_source: "同上"
sources:
  - url: https://github.com/qybaihe/bla
    title: "qybaihe/bla 官方仓（GitHub API 实查 2026-10-29：204 stars/57 forks/MIT/TypeScript/2026-10-25 创建 10-28 仍推送；README：对抗 REA 类 AI 逆向 agent 的 Poison→Exhaust→Hallucinate 防御盾）"
    accessed: "2026-10-29"
---

# BLA：当逆向工程师换成 AI agent，防御也该换打法

> 来源：https://github.com/qybaihe/bla （2026-10-29 GitHub API 实抓：204 stars/57 forks，MIT，TypeScript，2026-10-25 创建、2026-10-28 仍有推送；README 自述为对抗 REA 等 AI 逆向 agent 的防御盾，流程 Poison→Exhaust→Hallucinate，覆盖二进制/Electron 应用/JS bundle/Python/WASM）。本卡基于本次实抓的仓库元数据与自述，未运行验证防御效果。

## 是什么

**BLA（Blind LLM Agents）**是一个开源对抗防御盾，目标是让 AI 逆向工程 agent（README 点名 REA 类）对受保护软件"看不清、耗尽、产生幻觉"：**Poison → Exhaust → Hallucinate** 三段流程。保护对象覆盖五类产物：二进制、Electron 应用、JS bundle、Python、WebAssembly。TypeScript 实现，MIT 协议。

## 解决什么问题

AI 编码/逆向 agent 让"读懂一个闭源产物"的成本骤降，传统混淆/加壳对人有效、对会推理会调工具的 agent 未必。BLA 把防御对象从"人"换成"agent"，针对 agent 的工作方式（读元数据→枚举→构造理解）逐段设障。

## 相比前方法优势

- 定位新：针对 **agent 逆向**这一新攻击面，而非传统人工逆向；
- 覆盖面宽：五类产物一套盾，比赛里不必按技术栈分别找方案；
- 工程可用：MIT 协议无授权负担，创建四天内 204★/57 forks（2026-10-29 实查）且持续推送，社区接纳速度快。

## 局限（如实标注）

- **防御效果无第三方验证**：README 自述为主，未附论文或基准评测，"对抗 REA 有效"的具体数字需自查仓库实验记录；
- 创建仅四天的新仓，API 变动与维护风险高；
- 对抗是一场比赛：防御针对 REA 类 agent 的已知模式，换攻击策略可能绕过；
- 作者背景与机构未在仓库元数据中体现，引用时注明"社区项目"。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：AI 安全/攻防赛道直接集成进作品链路做"攻击者用 REA 类 agent 逆向，防御后产物仍是盲盒"的现场对比演示；也可反向用作红队素材——研究其 Poison 段落即知道 agent 逆向的软肋在哪。
- **双创-文书与申报**（reuse_cost 低）：安全类项目以"上游开放组件 + 自研场景适配"叙事起步，204★ 的社区信号可写进"生态与认可度"论据；注意如实标注项目成熟度（四天新仓）。

**族内定位**：库内暂无 AI 逆向攻防卡（既有安全卡偏 prompt 注入与 RAG 投毒方向），本卡占"agent 逆向对抗防御"新位；与本次同队列未入库的 arxiv-2610.36108（Log-To-Leak，MCP 注入攻击）分属攻击/防御两端。
