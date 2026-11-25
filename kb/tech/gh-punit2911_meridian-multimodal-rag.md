---
id: gh-punit2911_meridian-multimodal-rag
name: "Meridian：工业维保文档的'证据接地'多模态 RAG 参考实现——8 检索通道 RRF 融合+图表数字化+声明级幻觉校验+来源冲突仲裁+弃答，默认确定性离线可跑（73★ demo）"
field: [LLM agents, retrieval augmented generation, multimodal RAG]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-11-16"
maturity: demo
venue_tier: industry
reproducibility_level: high
signal:
  venue: "GitHub API 实查（2026-11-25）：punit2911/meridian-multimodal-rag，73 stars（队列快照 52，两日翻倍），2026-11-16 创建、2026-11-17 最后推送，Python；README 实抓，功能清单与 demo 问答样例齐全"
  stars: 73
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "RAG 赛题（文档问答/企业知识库）的工程参考答案：8 检索通道（BM25/LSA/n-gram/实体/数值事实/视觉/PRF/图 PageRank）→加权 RRF→重排→MMR 的融合栈、CRAG 式判分+修正重试+弃答、声明级幻觉校验（单位感知数值/标识符/否定/引用）——这套骨架可直接搬进 48 小时赛程，且默认离线确定性模式意味着断网/无 GPU/无 API key 也能跑通 demo"
    reuse_cost: 低
    open_source: "github.com/punit2911/meridian-multimodal-rag"
  - track: "双创-文书与申报"
    edge: "'人工智能+'赛道的工业维保应用原型样板：PDF 手册/扫描件/服务通报/维保日志/铭牌照片全格式摄入、图表数字化读数、通报对手册的时效性冲突仲裁（provenance-aware）、无证据即拒答——产品故事完整（安全合规叙事强：citations 到页面区域+逐声明校验），技术组件在申报书里可逐条对应；同类项目可用其'确定性离线模式+可选 agent'的分层架构讲成本与安全故事"
    reuse_cost: 低
    open_source: "github.com/punit2911/meridian-multimodal-rag"
sources:
  - url: https://github.com/punit2911/meridian-multimodal-rag
    title: "GitHub 仓库（GitHub API 元数据+README 实抓：73 stars，2026-11-16 创建、2026-11-17 推送，Python）"
    accessed: "2026-11-25"
---

# Meridian：把工业维保 RAG 的"工程完整性"一次做齐的开源样板

> 来源：https://github.com/punit2911/meridian-multimodal-rag （GitHub API 元数据+README 实抓 2026-11-25：73 stars，2026-11-16 创建、2026-11-17 最后推送，Python）。本卡内容出自本次抓取的仓库元数据与 README。

## 是什么

**Meridian**，面向**工业维保文档**的证据接地多模态 RAG 单仓应用（FastAPI + Qdrant + Ollama 可选）。答什么：PDF 手册（文本/表格/图表/警告框）、扫描页、Word 服务通报、CSV/XLSX 维保日志、告警面板照片。每个回答**引用到页面区域**、**逐声明校验**、**无证据即拒答**。工程亮点（README 实抓口径）：布局感知解析（表格→表+行级 chunk+类型化数值事实）；**图表数字化器**（校准坐标轴+OCR 投票刻度，从柱/折线图读值）；**8 检索通道→加权 RRF→late-interaction 重排→学习型排序钩子→MMR**；**CRAG 式判分**+修正重试+弃答（未知模型/语料外词）；**来源感知冲突仲裁**（通报 supersede 手册）+伪前提检测；**声明级幻觉校验**（单位感知数值、标识符、否定、引用）带自动修复；pandas 精确分析工具+单位换算；自带基准 harness（留出集、消融、bootstrap CI、ECE/Brier、幻觉注入）。**默认确定性离线模式**（无 API key/无 GPU/无模型下载），可选 LLM agent（Anthropic/OpenAI 兼容/Ollama）经同一校验器、离线 composer 兜底。

## 解决什么问题

典型 RAG demo 的四个通病——chunk 后图表图像全丢、只有单路向量检索、"永远给答案"（不弃答）、"LLM 说了算"（无校验）——在维保这类**答案必须可追责**的场景是致命的。Meridian 把"证据接地"从口号落成每一步的工程组件。

## 相比前方法优势

- **完整性**：检索融合/多模态/校验/弃答/冲突仲裁/评测 harness 一仓齐备，多数开源 RAG 项目只覆盖其中一两环；
- **离线确定性默认**：不接 LLM 也能出可引用答案（模板 composer），这在无网赛场/内网部署是刚需，也是安全叙事的差异化点；
- **数值可信**：算术交给 pandas 工具而非 LLM、图表读数走校准数字化、数值声明做单位感知校验——工业场景"数字错=事故"的针对性设计；
- **自带评测**：bootstrap CI/ECE/Brier/幻觉注入的 harness 让质量主张可复验，而不是 README 口碑。

## 局限（如实标注）

- 个人仓，创建 2026-11-16 后**自 11-17 起未再推送**（2026-11-25 实查），活跃度存疑；73★ 两日速涨（52→73）但无第三方 issue/讨论佐证实战采用；
- 无配套论文/技术报告，检索融合权重、校验规则的泛化性只能以自建 demo 语料（虚构 Helix Dynamics 语料）为准；
- 图表数字化、OCR（Tesseract）对低质量扫描件的鲁棒性未标定；
- 中文工业文档场景未覆盖（README 全英文示例），中文 OCR/分块需自行适配。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：文档问答/企业知识库赛题直接 fork——换语料、调 8 通道权重即可跑通；离线确定性模式保证无网环境 demo 不翻车；弃答+引用到页面区域是评审最买账的两个特性。
- **双创-文书与申报**（reuse_cost 低）：作为"AI+安全生产/AI+工业维保"选题的原型支撑：申报书的"技术方案"章节可逐条映射其组件（多模态摄入→知识库工程；声明校验→可信 AI；冲突仲裁→知识时效治理），开源实现本身满足"有原型支撑"的评审要求；成本故事好讲——离线模式对应私有化部署与数据不出厂。
