---
competition_id: devpost-build-with-gemini-xprize
last_verified: 2026-10-11
coverage: ["2026"]      # 2026-10-11 winners 分片首刷：官方公告全档位名单 + 8 项目深构（winners/2026.md）
confidence: 中           # 名单/档位/国别=官网公告单源（高）；深构=项目页一手全文（高）；类别分布/评审内幕=官方未公开（缺口）；无评委打分细节
sources:
  - url: https://www.xprize.org/news/polyfork-wins-the-build-with-gemini-xprize
    title: XPRIZE 官方获奖公告（全档位名单/国别/类别奖=各类别收入最高者/Circle 赞助奖）
    accessed: "2026-10-11"
  - url: https://xprize.devpost.com/project-gallery
    title: Devpost 获奖画廊快照（24 张 Winner 徽章卡，kb/raw/devpost-build-with-gemini-xprize/winners-gallery-snapshot-20261011.md）
    accessed: "2026-10-11"
  - url: https://devpost.com/software/polyfork
    title: Polyfork 项目页（1st place，webReader 全文）
    accessed: "2026-10-11"
  - url: https://devpost.com/software/tician-cierre
    title: TICIAN Cierre 项目页（2nd place，webReader 全文）
    accessed: "2026-10-11"
  - url: https://devpost.com/software/c2x
    title: C2x 项目页（Professional Services Access 类别奖，webReader 全文）
    accessed: "2026-10-11"
  - url: https://www.geminixprize.com/rules
    title: Official Rules — Build with Gemini XPRIZE（章程层：评审三准则/强制条款，2026-08-27 实抓）
    accessed: "2026-08-27"
---

# Build with Gemini XPRIZE 模式库（patterns）

> 快照存 `kb/raw/devpost-build-with-gemini-xprize/`（章程层：2026-08-27 实抓；获奖层：winners-gallery-snapshot-20261011.md + XPRIZE 公告 2026-10-11 核抓）。
> 状态声明：**首届已出奖（2026-09-25 公布，10-11 深构分片闭合）**——第二、三节已按实证首刷；获奖解构明细见 `winners/2026.md`（8 项深构：全部 5 Finalist + 2 类别奖 + 1 Runner Up）。

## 一、评审偏好（章程 × 2026 实证）

**章程层**（规则原文，等权重三准则，信源：官网，高）：Business Viability / **AI-Native Operations** / Category Impact。

**实证层**（2026-10-11 公告 + 项目页深构，详见 winners/2026.md）：

- **总冠军反"垂直行业"共识**：$500k 给了 Polyfork——3D 资产即可编程物、agent 工厂量产（周产 175 模型）、交付面同时供人与 agent 消费（llms.txt/REST/MCP）。主会话 08 月"垂直行业 Agent 是最大公约数"的赛前画像只兑现到 2-4 名（墨西哥 VAT/尼日利亚工匠/弗州创业服务）；**登顶靠 AI-native 纯度 + 收入证据链质量 + 平台级想象力**（终席评委含 Cathie Wood、Palmer Luckey、Logan Kilpatrick——投资人/ Builder 视角，公告名单）。
- **收入证据分层兑现**：公告口径类别奖授予各类别 **highest-grossing（收入最高）项目**——收入决定类别奖；但总冠军首月收入仅 $4,428（54 付费客户）——**顶层比的不是收入绝对值，而是证据链质量与叙事可扩展性**；同时存在无收入证据进 top5 的先例（DodoPrep 第 5 名，页面无付费证据）——"证据驱动"不等于"收入门槛"，但 Runner Up/类别奖层面收入密度显著（TRAMA 付费客户+三档定价+Delaware C-Corp；MyFixam 370+ 用户+10% 抽成）。
- **新兴市场密度约 6 成**：25 席国别（公告口径）——LatAm 6（Colombia×2/Mexico×2/Venezuela/Argentina）、非洲 3（Nigeria 单籍 1 + Uganda 1 + MyFixam 尼/美双籍）、南亚 5-6（India×3/Pakistan×2 + Ability Bazaar 印/美双籍）、中东 1（UAE）≈ 15-16 席；美国单籍 4（另 2 席双籍含美）；欧洲 4（Germany×2/France/Spain）——**为低连接/低信任市场做交付面适配（WhatsApp/离线端侧/移动支付）是高频形态**，但只见于 Runner Up/类别奖层。
- **单人/微型团队主导**：Polyfork、TICIAN、C2X、MyFixam、Teluma、Enamel 均单人 founder，TRAMA 4 人兼职、LaunchBridge 2 名大学生——agent 舰队把单人产能抬到小团队量级，25 席过半 ≤2 人。
- **跨赛连胜选手现象**：Olva（Runner Up）署名 Zelong Wang——与 devpost-gitlab-ai-2026 条目中横扫 4 奖的同一人；Devpost 高频单人选手跨赛复用工程底盘是可观察策略。

## 二、方法论分布（2026 首刷，样本=8 项深构 + 17 项列表级）

| 模式 | 出现频次/占比 | 代表年份与条目 | 可迁移性 |
|---|---|---|---|
| 确定性内核 + LLM 只做判断（"模型不做数字"） | top5 中 ≥3 例独立收敛 | 2026：TICIAN（Python 做算术/C2X（数字必带 {value,tag,source,vintage}）/Polyfork（harness 实测再信） | 强：财税/法务/工程文档类 agent 的默认架构（成本：中） |
| 独立评审 agent + 打回率留痕 | 2 例 | 2026：Polyfork（新会话 judge 打回 2/3）、C2X（66/66 harness 绿） | 强：生成类产品的质检层（成本：低-中） |
| agent 舰队按职能分工 | 深构 8 项中 6 项 | 2026：C2X 六内阁、Teluma 五级管线、TRAMA 模块化+agent_log | 中：分工命名/日志表可照搬 |
| WhatsApp 作为 agent 交付面 | 2-3 例（Runner Up/类别奖层） | 2026：TRAMA、EsencIA | 强：LatAm/非洲/东南亚 B2B 渠道（成本：低-中） |
| 端侧小模型（隐私/离线） | 1 例（全场唯一） | 2026：Enamel（Gemma 3+MedGemma@Ollama，PHI 不出设备） | 强：医疗/法律数据默认架构（成本：中） |
| 收入证据工程化（把证据做成系统组件） | 2 例 | 2026：LaunchBridge（Evidence Layer）、Polyfork（关联方收入零声明+Stripe 拆户诚实披露） | 强：证据驱动型比赛通吃（成本：低） |
| LLM+浏览器自动化填官方表格 | 1 例 | 2026：LaunchBridge（Playwright+Claude 填 SCC/IRS 表单） | 中：工商/税务代办类（成本：中） |

## 三、往届差异化点（2026 = 首届，即历届答案）

- **$500k 与 $50k 的形态分野**：总冠军 = "AI-native 基础设施/平台想象力"（资产即程序、agent 双向消费）；类别奖 = "垂直深域 + 收入第一"（公告口径 highest-grossing per category）；Runner Up = "垂直行业 agent + 早期商业化证据"。冲顶与保类别是两条不同的作品形态路线（与规则"每项目限一奖"互斥条款互相印证）。
- **25 席类别分布不可统计**（官方只披露 5 名类别奖得主的类别）；5 个类别奖国别：India/USA/Colombia/Uganda/Colombia——Small Business Services 与 Professional Services Access 两席均归 Colombia。
- **收入量级实况**：可核的冠军收入 $4,428/首月——该赛"真实收入"口径的实际门槛远低于字面想象，**证据形态（付费客户数、支付通道轨迹、定价页、C-Corp 注册）比金额更被看重**。

## 四、反面观察（失分模式，实证仍薄）

章程红线层（2026-08-27 规则原文，仍然有效）：
- 技术栈资格红线（§04）：部署应用无 Gemini API 调用 / 无任何 Google Cloud 产品 = 资格不符（可并用其他 LLM——LaunchBridge 用 Claude 填表单、TICIAN 引擎在 VPS，均合规佐证）。
- 提交物完整性红线：收入/费用/产品证据 + GitHub 共享双邮箱 + ≤3min 视频 + 500-1000 词叙事（Customer Evidence 之外均为必备表述）。
- 资格红线（§07）：<25 人组织；时区红线（§02）PT；奖项策略红线（§06）每项目限一奖。

实证层（2026 首届观察，样本小、置信中）：
- **"纯技术炫技型"缺席 top 层**：8 项深构无一以模型/算法创新为主卖点（DodoPrep 的 Monte Carlo 掌握度是唯一算法自研，也排在第 5）——把 gemini 调用当功能点缀、无业务闭环的作品在本赛无席位样本。
- **无收入证据进 top5 是少数派**（DodoPrep 一例）：不能反推"收入证据可有可无"——类别奖按收入高低分配的公告口径决定了大多数席位仍是收入敏感的。
- 待核验条款：协调者任务包提示的"窗口期外开发无效"类条款，在现有规则快照提取正文中无原文对应（快照章节跳号）——维持待核验，不作为结论引用。

## 五、赛点检查表（评审标准 → 可执行检查项；快循环验收清单的派生源）

- [ ] 部署应用中存在 ≥1 次 Gemini API LLM 调用且留有调用记录（§04 强制；可与其他 LLM 并用）
- [ ] 使用 ≥1 个 Google Cloud 产品并在叙事中明示（§04 强制）
- [ ] 业务流程由 AI agents 运营，agent execution logs + API usage records 归档可查（AI-Native Operations 准则 × 产品证据）
- [ ] 收入证据格式合规：Stripe dashboard 导出或银行对账单 + P&L（提交清单原文）
- [ ] 费用证据齐备（提交清单）
- [ ] GitHub repo 已共享 testing@devpost.com 与 judging@hacker.fund，部署态可被实测（提交清单 + 推断）
- [ ] 视频 ≤3 分钟且公开托管（提交清单硬指标）
- [ ] Written Narrative 500–1000 词（提交清单硬指标）
- [ ] 五分类择一，叙事逐条对齐 Category Impact（评审准则）
- [ ] 商业可行性量化呈现：收入/费用/单位经济口径一致（Business Viability 准则 × 收入/费用证据交叉）
- [ ] 截止时间按 PT 换算自查（§02）
- [ ] 奖项策略自查：每项目限一奖（§06），冲总冠军/保类别奖二选一

## 六、对本框架的启示（喂给 K-02 / 验收报告）

- **~~第一 watch 项 = 9-25 winners 深构分片~~（已闭合 2026-10-11）**： winners/2026.md 落盘（8 项深构 + 25+1 全名单），本文件二、三节已首刷。**新 watch**：XPRIZE 已启动新一届 $2M（Google 背书）hackathon（官网首页摘要线索，待 hunter 建档核抓）。
- **首届获奖画像对本框架的三条硬启示**（依据 winners/2026.md）：
  1. **证据工程 > 冲高收入**：$4,428 首月收入可夺 $500k——评审买的是"付费客户数 + 支付轨迹 + 定价页 + 公司注册"的证据链形态，作品期应把证据采集做成系统组件（LaunchBridge Evidence Layer 模式）；
  2. **"确定性内核 + LLM 判断层"是跨场景收敛解**：top5 中 ≥3 项独立收敛到该纪律（TICIAN/C2X/Polyfork）——我方任何 agent 类作品应默认采用"数字不出模型"架构并把审计留痕当提交物；
  3. **单人 + agent 舰队是可行的参赛形态**：25 席过半 ≤2 人， Polyfork 单人夺 $500k——资源假设应按"1 人 + agent 流水线"校准，而非默认组队。
- **本队 Gemini API 经验评估（如实）**：库内（kb/tech/）**无本队直接使用 Gemini API / Google Cloud 的工程经验档案**；唯一相关记录是第三方项目 Cybermes（kb/tech/gh-Zyrexnn_Cybermes.md，2026-08-28 实抓）提及其 MCP 服务器"面向 Claude Code/Cursor/Gemini 等 AI 客户端"——属客户端兼容性旁证，非本队开发经验。结论：该赛技术栈（Gemini API + GCP）对本队为**未验证栈**，任何参赛/复用决策前须先由 K-02 结合团队画像补栈评估。
- **"证据驱动"赛制对作品工程的提示**：该赛把 agent 运营日志、API 用量记录、收入凭证作为提交物——获奖作品的工程核心是**可审计的运营留痕**而非 demo 完成度；此取向与本框架验收清单"评审标准 × 可验证动作"的派生思路同构，可反哺赛点检查表设计（第五节已按此结构落地）。
- **竞争密度参考（粗算，低置信）**：25 席 / 26,470 注册人 ≈ 0.09% 获奖率（注册口径，参赛项目数无官方口径，实际按项目计的获奖率会更高但无法核算）——用于同类赛的投入产出预期校准，不用于决策。
