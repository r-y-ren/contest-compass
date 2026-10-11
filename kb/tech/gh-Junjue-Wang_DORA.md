---
id: gh-Junjue-Wang_DORA
name: "DORA：灾害应急响应 LLM agent 基准（NeurIPS 2026 E&D oral，515 专家任务 + 108 工具 MCP 地理空间库）"
field: [LLM agents, 评测基准, 遥感地理空间]
directions: [创新创业大赛]
published: "2026-09-25"
maturity: demo
venue_tier: CCF-A
reproducibility_level: medium
signal:
  venue: "NeurIPS 2026 Evaluations & Datasets Track oral（README News 自述 2026-09-25 接收）+ GitHub API 实抓：33 stars / Apache-2.0 / 2026-10-10 仍有推送；论文 arXiv:2605.11633"
  stars: 33
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "'AI+应急/灾害响应'选题（高教主赛道社会价值向）的三件套底座：(a) 需求框架直接引用其五维运营分类（灾情感知评估/空间关系分析/行动规划/时序演化推理/多模态报告合成），每维锚定 UNOSAT、Copernicus EMS、FEMA Hazus/US&R、UN OCHA 等真实业务协议——申报书的业务理解章节即有国际协议背书；(b) 108 工具 MCP 库（建筑损毁分割/洪水制图/最短路径/损毁地图/态势报告页生成，统一 JSON-RPC+类型化 schema）可直接挂任意 MCP 兼容 agent 框架搭应急原型；(c) 立项依据用其榜单：13 个 agent 最优 53.74%（Gemini-3.0-Flash）对专家金轨迹 80.48%，任务远未解决且开源可复现"
    reuse_cost: "中"
    open_source: "https://github.com/Junjue-Wang/DORA（Apache-2.0；2026-09-29 已释出代码+108 工具 MCP 库+数据准备脚本+评估器；README 自述数据集与感知 checkpoint 'coming soon'，2026-10-11 实抓口径）"
sources:
  - url: https://github.com/Junjue-Wang/DORA
    title: "Junjue-Wang/DORA 仓库（README+文件树+API 元数据，2026-10-11 实抓：515 任务/45 真实灾害事件/10 灾种/5 大洲，3500 步专家验证金轨迹，NeurIPS 2026 E&D oral，作者含 Stefano Ermon（Stanford）/Naoto Yokoya）"
    accessed: "2026-10-11"
  - url: https://arxiv.org/abs/2605.11633
    title: "DORA 论文 arXiv 页（README 所引官方链接，2026-10-11 记录；本卡事实以仓库 README 实抓为准）"
    accessed: "2026-10-11"
---

# DORA：把"agent 能不能做灾害应急"做成 515 个专家任务的 NeurIPS oral 基准

> 来源：https://github.com/Junjue-Wang/DORA （Apache-2.0，Python，2026-09-25 创建，2026-10-11 实抓 README、文件树与 API 元数据）。论文 arXiv:2605.11633（2026-05-12 挂出，2026-09-25 NeurIPS 2026 Evaluations & Datasets Track oral，README News 自述）；作者 Junjue Wang/Weihao Xuan（共同一作）等，含 Stefano Ermon、Naoto Yokoya。本卡事实出自本次 README 实抓，论文正文未读。

## 是什么

灾害运营响应 agent 基准：**515 个专家撰写任务，覆盖 45 个真实灾害事件、10 种灾型、5 大洲**，配专家验证、可回放的金轨迹共 3,500 个工具调用步骤。三个设计特征：

1. **Operational**：五维任务沿灾害响应业务管线展开——T1 灾情感知与评估（132 任务，UNOSAT Rapid Mapping/Copernicus EMS 协议）、T2 空间关系分析（108，FEMA Hazus）、T3 灾害行动规划（100，FEMA US&R）、T4 时序演化推理（61，Copernicus EMS Monitoring）、T5 多模态报告合成（114，UN OCHA SitRep/IFRC）；
2. **Heterogeneous**：光学/SAR/多光谱影像（单/双/多时相，0.015–10m GSD）+ DEM/坡度/地表温度/POI/路网/人口/设施足迹矢量层；
3. **Agentic**：108 工具 MCP 库（感知 31/栅格 18/矢量 31/逻辑 15/可视化 11/摘要 2，统一 JSON-RPC 与类型化 schema），任意 MCP 兼容框架零改造接入；同时评工具调用轨迹与最终答案。

榜单（13 个 LLM agent，ReAct 式循环）：最优 Gemini-3.0-Flash 53.74%，开源最优 Qwen3.5-397B-A17B 53.45%，专家金轨迹 80.48%。

## 解决什么问题

灾害应急是"agent 能力真实有用"的高价值试炼场，但既有遥感/地理空间评测要么是单张影像分类、要么无工具调用语义；没有按真实业务协议组织、可回放金轨迹、多模态异构数据齐备的 agent 级基准。DORA 把业务协议（联合国/政府应急体系怎么实际干活）直接编译成评测维度与金轨迹。

## 相比前方法优势

- 协议锚定：五维全部映射到 UNOSAT/Copernicus/FEMA/OCHA 真实运营规程，评测维度即业务需求文档——这不是学术合成任务；
- 轨迹级评测：3,500 步专家金轨迹 + 最终答案双口径，可诊断"答案对但过程错"；
- MCP 工具库本身是可复用工件（108 个地理空间工具含实现），独立于基准数据也有用；
- NeurIPS E&D Track oral + Stanford/NASA 系背景团队，信号在同类新基准中属头部。

## 局限（如实标注）

- **数据集与感知模型 checkpoint 尚未释出**（README News 自述 coming soon，2026-10-11 实抓）——当前可复用的是代码、MCP 工具库、数据准备脚本与评估器；复跑 515 任务全基准需等数据；
- 遥感数据管线有真实门槛（影像下载/算力/多光谱处理），赛队复现 T1/T4 类任务成本不低；
- 33 stars 早期仓库，社区与维护延续性未经验证；
- NeurIPS 2026 尚未开会（oral 为接收口径），camera-ready 与论文正文本卡未读，任务细节以 README 为准。

## 如何用于比赛（比赛映射展开）

1. **双创-文书与申报（"AI+应急"高教主赛道/社会价值向项目）**：三段式采用——需求分析章引其五维协议分类（每个协议名都是可检索的真实权威规程）；技术方案用 108 工具 MCP 库搭最小应急 agent 原型（损毁评估→路径规划→报告生成一条线，库已释出可跑）；立项必要性引"最优 agent 53.74% vs 专家 80.48%"的缺口数字（注明 NeurIPS 2026 E&D oral 与 README 榜单口径）。reuse_cost 中：工具库接入轻，全量数据集未放出前不要承诺复跑完整基准，原型选 T3（行动规划）或 T5（报告合成）等工具链依赖重、影像依赖相对轻的维度切入。
