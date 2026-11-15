---
id: arxiv-2611.06682
name: "SecureGARD：可执行本体把工具型 agent 治理做成确定性的 ready/waiting/forbidden 三值决策——AgentDojo/ASB/AgentDyn 三基准 0% ASR（官方仓 MIT 零依赖可跑）"
field: [LLM agents, agent 安全, prompt injection 防御, 治理本体]
directions: [黑客松与数据竞赛]
published: "2026-11-04"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv v2 + 官方仓 tatra-labs/not-yet（GitHub API 实查：0 stars，MIT，2026-11-10 创建并推送，Python，零依赖零 API key，含离线注入测试 harness 与 CI）"
  stars: 0
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "agent 攻防/安全评审类赛题（含 prompt injection 环节的 agent 竞赛）：SecureGARD 给出可直接抄的治理架构——把异构工具调用落到共享语义表示，用可执行本体+回合级任务状态推出确定性的 ready/waiting/forbidden；'waiting=有未满足但可恢复的义务，允许有界重规划但不扩授权边界'是和其他'一刀切拦截'防线拉开差距的设计点；官方仓零依赖零 API key，赛场上半天可接入自己的 agent 做注入自测（离线 harness 自带）"
    reuse_cost: 低
    open_source: "github.com/tatra-labs/not-yet（MIT，零依赖，含离线 prompt-injection harness）"
  - track: "双创-文书与申报"
    edge: "'人工智能+'项目申报里可信 AI/安全治理一节的现成叙事骨架：本体演化走'离线 LLM 提议公理→只接受修复训练暴露的本体错误→保逻辑一致性与受保护推论→留出集验证后才冻结'的闭环，是比'我们加了安全提示词'高一个等级的治理论证；三基准 0% ASR 且攻击下任务效用还高于基线，可作为指标背书引用（注明为论文自报）"
    reuse_cost: 中
    open_source: "同上官方仓（治理决策器可当演示原型）"
sources:
  - url: https://arxiv.org/abs/2611.06682
    title: "SecureGARD: Dynamic Ontology-Guided Governance for Secure Tool-Using LLM Agents（arXiv abs 页 v2，2026-11-04，摘要经 arXiv API 实抓）"
    accessed: "2026-11-13"
  - url: https://github.com/tatra-labs/not-yet
    title: "官方代码仓（GitHub API 实查：0 stars，MIT，2026-11-10 创建并推送，README 徽章直接标注 arXiv 2611.06682，零依赖设计）"
    accessed: "2026-11-13"
---

# SecureGARD：把 agent 执行安全做成"本体化的三值治理"

> 来源：https://arxiv.org/abs/2611.06682 （v2 2026-11-04，摘要经 arXiv API 实抓）；官方仓 https://github.com/tatra-labs/not-yet 信号经 GitHub API 实查（2026-11-13）。本卡内容出自本次抓取的摘要与仓库元数据，未读 PDF 全文。

## 是什么

面向工具型 LLM agent 的**动态本体引导治理框架**。核心观察：间接 prompt injection 已从"模型输出问题"变成"执行安全问题"，而现有防线（约束工具调用/轨迹/信息流）把动作语义、状态依赖、证据关系都留在隐式层面。SecureGARD 三步走：(1) 把异构调用落到**共享语义表示**；(2) 用**可执行本体 + 回合级任务状态**推出确定性的 **ready / waiting / forbidden** 三值决策——其中 waiting 表示"存在未满足但可恢复的义务"，允许有界重规划而不扩授权边界；(3) 本体**离线演化**：LLM 只提议实例无关的动作-状态公理，且仅当公理修复了训练失败暴露的本体错误、保持逻辑一致与受保护推论、并过留出集验证后才被接受，随后冻结。官方评测：AgentDojo、ASB、AgentDyn 三基准，良性+间接注入设定下 **0% 攻击成功率（ASR）**，且攻击下任务效用优于现有基线。

## 解决什么问题

两个老两难：(a) 拦得死（一刀切禁止）保安全但砍效用，拦得松（模型自判）效用高但不安全；(b) 防线规则跨异构工具不泛化，安全更新（改规则）容易引入新漏洞。SecureGARD 的回答是把"该不该执行"从概率判断搬到**符号层的确定性推理**，并用本体错误驱动的受控演化解决"规则如何安全地长"。

## 相比前方法优势

- **三值而非二值**：waiting 决策给了"暂不可行但可修复"的出口，重规划被限制在授权边界内——既不是放行也不是误杀，这是相对约束类防线的效用增量来源；
- **确定性可审计**：ready/waiting/forbidden 由可执行本体推出，不依赖模型判断，规则变更走"训练失败暴露错误→公理修复→一致性/受保护推论/留出集三道验证"的受控通道，比运行时护栏好审计；
- **0% ASR 三连**：三个异构基准（含动态场景 AgentDyn）全零攻击成功率，且攻击下效用不降反升，说明不是靠无差别拦截换安全；
- **可跑可自测**：官方仓 MIT、零依赖零 API key、带离线注入 harness 与 CI——入场成本在安全类论文里罕见地低。

## 局限（如实标注）

- 摘要未给出与各基线的分项对比表和本体规模/公理条数，0% ASR 的基准覆盖面需读全文核实；
- 本体演化依赖"训练执行"暴露错误——冷启动场景（无历史执行可验证）的公理从哪来，摘要未讨论；
- 0 stars 新仓（创建 2 天），社区验证不存在；三基准之外的泛化（真实生产工具生态）无证据；
- 确定性本体的表达力有边界：语义漂移、工具行为变更时本体失效模式未评估。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：凡是"agent 要调工具完成任务、评审会塞恶意指令"的赛题，官方仓本身就是答案骨架——先跑通其 ready/waiting/forbidden 决策器，再把赛题工具注册进本体；waiting 的"有界重规划"设计点在答辩时是区分度来源（别人的防线要么拦死要么被打穿）。离线注入 harness 可当赛前红队自测器。
- **双创-文书与申报**（reuse_cost 中）：申报书"安全与可信设计"一节的论证模板：语义接地→确定性三值决策→受控本体演化→留出集冻结，四段式比"提示词加固"叙事高一级；引用其三基准 0% ASR 时注明论文自报口径。

**族内定位**：库内 agent 攻防线已有 SARA（arxiv-2608.27146，动作诱导与运行时授权分离）、WebMCP-Phalanx（arxiv-2608.24017，浏览器 agent 信任边界）、Zero-Trust MCP（arxiv-2609.22573，企业 MCP 授权发现）、AttnLocate（arxiv-2608.24022，越权行为定位）、AgentSafeEvo（gh-lalalamdbf，攻防共进化训练）。SecureGARD 占"**本体化三值治理**"位：前述工作都在"谁能做什么"的权限/信任层，本卡在"此刻这个调用在任务语义上处于什么状态"的执行语义层，且是族内少见的**带官方零依赖实现**的治理卡——做攻防赛优先抄它，再做权限层的 SARA/Conflux 组合。
