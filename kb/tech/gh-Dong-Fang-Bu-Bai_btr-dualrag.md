---
id: gh-Dong-Fang-Bu-Bai_btr-dualrag
name: "BTR-dualRAG：生物信息学工具推荐的双路检索增强生成（结构化图谱 + 非结构化知识 → 过滤重排 → 证据接地报告）"
field: [retrieval augmented generation, LLM agents, 工具推荐]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-18"
maturity: demo
reproducibility_level: medium
signal:
  venue: GitHub
  stars: 89
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "垂直领域『工具/方案推荐助手』的完整产品骨架：解析研究对象-操作-预期结果三要素 → 结构化（BTR-MCL 图谱路径，经隔离 HTTP 服务挂 RecBole）与非结构化双路召回 → 过滤重排 → 生成证据接地的推荐报告——四阶段流水线可直接转译为『AI+X 知识服务』类项目的技术方案章节，『每条推荐带证据链』是对 RAG 堆料同行的清晰差异化；随论文同步开源两天 89 星（2026-10-20 API 实查）可作关注度佐证"
    reuse_cost: 中
    open_source: "https://github.com/Dong-Fang-Bu-Bai/btr-dualrag（代码完整含测试与 CLI，但 BTVD/Chroma、BTKG/Neo4j、模型 checkpoints 等大件资产不随仓分发，需按 docs/data-and-models.md 自备；无 license）"
  - track: "黑客松-数据与算法"
    edge: "RAG 赛题的高分模板形态参考：结构化+非结构化双路召回、重排去噪、证据接地输出三件套恰是当前 RAG 评测的关注点组合；其『图谱检索隔离成独立服务』的工程切分（core 运行时与 RecBole 环境分离 + doctor 自检命令）可直接抄作赛期架构，避免依赖打架"
    reuse_cost: 中
    open_source: "https://github.com/Dong-Fang-Bu-Bai/btr-dualrag（架构可裁剪复用；无 license 限制商用复用需联系作者）"
sources:
  - url: https://github.com/Dong-Fang-Bu-Bai/btr-dualrag
    title: "Dong-Fang-Bu-Bai/btr-dualrag 仓库页（API 元数据：89 stars/2026-10-18 创建/2026-10-18 最后推送/无 license/Python）"
    accessed: "2026-10-20"
  - url: https://raw.githubusercontent.com/Dong-Fang-Bu-Bai/btr-dualrag/main/README.md
    title: "README 全文（四阶段方法、仓库布局、大件资产不随仓清单、安装与 doctor 自检用法、作者 Qifan Ma 等 4 人）"
    accessed: "2026-10-20"
---

# BTR-dualRAG：生物信息学工具推荐的双路检索增强生成

> 来源：https://github.com/Dong-Fang-Bu-Bai/btr-dualrag （README 与 GitHub API 元数据，2026-10-20 实抓）。论文《BTR-dualRAG: Bioinformatics Tool Recommendation With Dual Retrieval-Augmented Generation》（Qifan Ma、Biyao Lv、Pingjian Zhang、Deyou Tang）的官方源码仓，2026-10-18 创建并推送，两天 89 stars。

## 是什么

生物信息学工具推荐系统 BTR-dualRAG 的官方实现：用户以自然语言问"哪个工具能对 BAM 文件算 read depth"，系统四阶段作答——(1) 解析查询中的**研究对象、操作、预期结果**三要素；(2) 从结构化知识（BTR-MCL 图谱路径，经隔离 HTTP 服务调用 RecBole 环境）与非结构化知识双路检索候选；(3) 过滤重排；(4) 生成**带证据出处的推荐报告**。工程上切成核心包（`src/btr_dualrag/`，含检索/过滤/生成/评测与单元及工作流契约测试）+ BTR-MCL 服务适配器（`services/btr_mcl_api/`，第三方 RecBole 源码内嵌于 `third_party/`），配 `.env` 配置剖面与 `doctor` 环境自检命令。

## 解决什么问题

生信工具数以万计且更新快，研究者选工具靠口口相传；通用 LLM 直接推荐会幻觉出过时或不存在的工具名。该系统把"选型知识"外置为结构化图谱 + 非结构化语料双路检索，让每条推荐可回溯到证据，模型只负责组织与解释。

## 相比前方法优势

- **双路召回**：结构化图谱路径捕捉工具-任务关联（协同过滤式，BTR-MCL），非结构化路径兜底长尾查询，比单路向量 RAG 覆盖更稳；
- **证据接地输出**：报告逐条带出处，可审计，区别于"一句话推荐"；
- **工程成熟度高于典型论文仓**：依赖锁定文件、双环境隔离、契约测试、doctor 自检、CLI 一应俱全（2026-10-20 README 实读）。

## 局限（如实标注）

- **大件资产不随仓分发**：BTVD/Chroma 向量库、BTKG/Neo4j 图谱、模型 checkpoints、评测数据集均需另行获取（见 docs/data-and-models.md），开箱不可跑全流程，复现成本在数据侧不在代码侧；
- **无 license**：README 未附许可证，复用代码有法律不确定性，只能作架构参考或联系作者；
- 推荐效果数字在论文中，本卡未读论文正文，性能口径不背书；仓库创建与最后推送同日（2026-10-18），后续维护活跃度未知。

## 如何用于比赛（比赛映射展开）

1. **双创-文书与申报（AI+X 知识服务产品）**：四阶段流水线是"垂直领域智能选型助手"的现成方案骨架——把生信域换成任意有"工具/方法/供应商选型"痛点的行业（实验方法推荐、设备选型、政策匹配），架构照搬、语料换域。申报书卖点：(a) 双路检索抗长尾；(b) 证据接地可审计；(c) 结构化服务隔离的工程治理。89 星（2026-10-20）作社区关注度佐证。reuse_cost 中：代码可参考但需自建领域知识资产（这正是项目工作量所在，反而撑得起申报内容）。
2. **黑客松-数据与算法（RAG/知识问答赛题）**：作为 RAG 方案的设计模板——双路召回 + 过滤重排 + 证据接地恰对应当前 RAG 评测的幻觉、覆盖、可审计三大扣分点；其"图谱检索独立成服务 + doctor 自检"的工程切分可在赛期直接套用，避免 RecBole 类重型依赖污染主环境。reuse_cost 中：按赛题数据裁剪两路权重。
