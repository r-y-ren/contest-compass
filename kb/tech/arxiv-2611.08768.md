---
id: arxiv-2611.08768
name: "Conflux：把权限提升正式化为系统级安全目标——ITES 内核取'所有影响主体的权限交集'，附 authority-confinement 定理与 SLED/SLED-V 系统级评估器（研究框架仓可跑）"
field: [LLM agents, agent 安全, 权限提升, 访问控制]
directions: [黑客松与数据竞赛]
published: "2026-11-05"
maturity: demo
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv + 研究框架仓 RayaBuckley/Conflux（GitHub API 实查：0 stars，无 license，2026-07-10 创建、10-23 推送，Python；README 含 ITES 调解内核、SLED 有界验证、序列化求解器模型与运行时适配器）"
  stars: 0
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "多主体信息源（用户文档/网页/第三方 MCP）混入同一 agent 的赛题：Conflux 给出比'提示词隔离'硬一档的答案——把权限提升形式化为系统级目标（一个动作仅当**每个**影响过它的主体都允许才放行），ITES 内核从 provenance 与组织既有访问控制系统取权限**交集**做 fail-closed 调解；仓内自带 SLED 黑盒有界模型检查器，赛场上可以直接给自己的 agent 防线跑一次系统级验证当加分项"
    reuse_cost: 中
    open_source: "github.com/RayaBuckley/Conflux（ITES 内核 + SLED/SLED-V 评估器，注意无 license 条款）"
  - track: "双创-文书与申报"
    edge: "企业级/政务向 agent 项目的安全治理章节：'权限提升=系统级目标、执行在模型判断之外、条件性 authority-confinement 定理'的三段式论证是现成的高规格叙事；如实引用其边界声明（证据有界且部分、无无界部署保证）反而显专业"
    reuse_cost: 中
    open_source: "同上研究框架仓"
sources:
  - url: https://arxiv.org/abs/2611.08768
    title: "Conflux: Preventing Privilege Escalation with Principal Contexts and System-Level Evaluation（arXiv abs 页，2026-11-05，摘要经 arXiv API 实抓）"
    accessed: "2026-11-13"
  - url: https://github.com/RayaBuckley/Conflux
    title: "研究框架仓（GitHub API 实查：0 stars，无 license，2026-07-10 创建、2026-10-23 推送；README 自述 fail-closed ITES 调解内核、有界 SLED 验证、序列化模型与确定性运行时适配器）"
    accessed: "2026-11-13"
---

# Conflux：权限提升是系统级目标，不是模型判断题

> 来源：https://arxiv.org/abs/2611.08768 （v1 2026-11-05，摘要经 arXiv API 实查）；研究框架仓 https://github.com/RayaBuckley/Conflux 信号经 GitHub API 实查（2026-11-13）。本卡内容出自本次抓取的摘要与仓库元数据，未读 PDF 全文。

## 是什么

面向"agent 汇聚多主体信息并对外执行动作"场景的**主体上下文（principal-context）防御**。核心形式化：把权限提升（PE）定义为系统级安全目标——**一个动作仅当每一个影响过它的主体都会允许时才可放行**；由于模型级防御始终是概率性的，强制执行必须放在模型判断之外。Conflux 内核 **ITES** 从 provenance 与组织既有访问控制系统推导权限，对动作取**所有影响主体权限的交集**，fail-closed 调解。论文给出**条件性 authority-confinement 定理**：在完全中介、无洗白 provenance、已知非空决策上下文、新鲜权限检查、动作绑定五条件下，内核不会放行任何相对已记录影响主体的提权动作——但该定理只覆盖"表示出来的价值影响片段"，工具/分支/接收方/计划步选择等控制影响仍是待精化义务。外围扩展：独立策略端口、参数感知授权、披露、同意、委托、限制与暴露规划。系统级评估器两件套：**SLED**（黑盒，对防线的有穷模型做有界穷举）与 **SLED-V**（白盒，对可序列化中间表示检查安全与 provenance 性质）。作者明示：所有证据有界且部分，无任何无界部署保证。

## 解决什么问题

多主体 agent 的经典漏洞链：一封信/一个网页/MCP 返回值（低权限主体）的内容影响 agent，最终动作却以高权限身份执行——间接注入只是它的一个实例。现有防线把"模型别被骗"当目标（概率性），Conflux 把目标上移成"**每个影响者都授权**"（系统级、可判定），并把执行与判断解耦。

## 相比前方法优势

- **目标形式化+定理**：族内多数防线给机制不给性质证明；Conflux 给出带明确前提清单的条件性 confinement 定理，前提不可满足处如实标注为精化义务——这是"可推理的安全"对"可相信的安全"的代差；
- **复用组织既有 ACL**：ITES 权限来自 provenance×现有访问控制系统，不要求为 agent 另建一套权限宇宙，落地摩擦小；
- **系统级评估器可复用**：SLED/SLED-V 是对"防线本身"的验证工具而非对模型的评测集——检查自己的防御设计有无绕路，这个工具位在族内是空缺的；
- **fail-closed 内核可跑**：仓内含调解内核、有界验证与运行时适配器，非纸面设计。

## 局限（如实标注）

- 0 stars、无 license、创建于论文发布前 4 个月（7 月即有框架），主体信息不明——采用前须确认可用条款；
- 定理只覆盖价值影响片段：工具选择、分支、接收方、计划步等**控制影响**不在保证范围内，论文自己承认是精化义务；
- 有界评估：SLED 穷举受模型与界限约束，"证据有界且部分"是作者原话，不能当部署保证引用；
- AgentDojo 等结果放附录且明示局限，主基准数字需读全文核对。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：凡赛题涉及"agent 读了不可信内容后要执行敏感操作"（读网页→发邮件、读文档→写库），ITES 的权限交集模式可以直接架在工具调用层：给每个信息源标主体，动作前求交集，不满足即 fail-closed。SLED 有界检查器可对自建防线跑一次系统级审计，作为答辩的技术深度证据。
- **双创-文书与申报**（reuse_cost 中）：面向企业/政务评审的项目，"系统级安全目标+条件性定理+如实边界声明"的论证结构比"我们做了 prompt 加固"高一个规格；引用时保留其无界保证声明，体现合规素养。

**族内定位**：攻防线已有 SARA（权限层：动作诱导与运行时授权分离）、Zero-Trust MCP（企业 MCP 授权）、WebMCP-Phalanx（浏览器信任边界）、SecureGARD（本批姊妹卡：本体化三值治理）。Conflux 占"**权限提升的形式化+系统级验证**"位：SecureGARD 答"这个调用此刻语义上该不该执行"，Conflux 答"这个动作聚合了谁的影响、他们全都授权了吗"——两层正交，攻防赛可叠用；需要"验证防线本身"时 SLED/SLED-V 是族内唯一系统级评估工具。
