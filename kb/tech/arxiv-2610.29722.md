---
id: arxiv-2610.29722
name: 'Retrieval Augmented Generation Compositionality'
field: [retrieval augmented generation, 评测方法, 组件组合, 实证研究]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-21"
maturity: demo
venue_tier: arXiv
signal:
  venue: "arXiv v1（comments：103 pages (9 main), 15 figures, 68 tables；作者 Ido Levy, Segev Shlomov, Leshem Choshen，README 标注 IBM / Weizmann）"
  stars: 17
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "RAG 管线组件选型的'防坑表'：论文实测单组件收益不可加——3 个检索技术单独合计预示 +47% 提升、叠加实测仅 +17%，检索质量与答案忠实性偏好不同配置，小语料最优组合到大规模语料会失效（450 配置 × 8 基准 × 5K–200K 文档语料，论文自报）；hackathon 现场搭 RAG 时'要不要上 rerank/查询增强/agentic 验证'的取舍可直接按此先验分配消融预算，避免堆组件白烧 API 费"
    reuse_cost: 低
    open_source: "https://github.com/dolev31/lasagna（Apache-2.0，pip install lasagna-rag，2026-10-25 实测可达：673 commits、17 stars、8 阶段可插拔、55 注册组件、31 基准条目、CLI/REST/MCP 多入口）"
  - track: "Kaggle-竞赛"
    edge: "检索增强类赛题（QA/文档理解）验证'trick 是否真涨分'的规范做法来源：冻结其余阶段单换一组件的 stage-isolation 检验 + 配对符号翻转显著性检验 + Holm-Bonferroni 校正 + 2×2 交互测试，正是 Kaggle 本地 CV 该有的消融纪律；论文'小语料结论不迁移到大语料'的发现提示按规模梯度留出验证集，防本地 CV 与隐藏测试集脱节"
    reuse_cost: 低
    open_source: "https://github.com/dolev31/lasagna（同上；YAML sweep 驱动批量实验，lasagna results significance 直接出显著性）"
sources:
  - url: https://arxiv.org/abs/2610.29722
    title: 'Retrieval Augmented Generation Compositionality'
    accessed: "2026-10-25"
  - url: https://github.com/dolev31/lasagna
    title: 'dolev31/lasagna — LASAGNA: open-source framework for controlled RAG evaluation'
    accessed: "2026-10-25"
---

# RAG 组件组合性：LASAGNA 受控评测框架与"单组件收益不可加"实证

> 来源：https://arxiv.org/abs/2610.29722 （arXiv v1 提交于 2026-10-21，作者 Ido Levy, Segev Shlomov, Leshem Choshen，comments：103 pages (9 main), 15 figures, 68 tables）与 https://github.com/dolev31/lasagna （2026-10-25 实抓）

## 是什么

arXiv 2610.29722 研究现代 RAG 管线各组件（embedding、chunking、retrieval、reranking、query augmentation、context compression、agentic verification）的**组合性**问题，并发布配套开源框架 LASAGNA（以下均来自本次实抓的摘要页与仓库 README）：

- **研究设定**：预声明三条假设——(1) 单组件的孤立收益在组合后是否存活；(2) 检索质量与答案忠实性是否偏好同样的设计选择；(3) 小语料上的结论在大规模是否成立。以 450 个配置、8 个基准、5K–200K 文档语料做受控实验；
- **三个核心发现**：① 收益不可加——3 个检索技术单独合计预示 +47% 提升，叠加实测只有 +17%；② 检索质量与答案忠实性的增益堆叠方向不同，优化一方可能损害另一方；③ 小语料上的最优组合随语料增大不再最优；
- **LASAGNA 框架**：8 个可插拔管线阶段（ingest/chunk/embed/retrieve/rerank/augment/agentic loop/generate，一个配置键或装饰器即可替换），55 个注册组件，6 种向量库后端（Milvus/pgvector/Qdrant/Weaviate/Pinecone/OpenSearch），31 个基准条目（BEIR、RAGBench、KILT、HotpotQA、SQuAD v2 等），内置配对符号翻转显著性检验、Holm-Bonferroni 校正、2×2 交互测试与阶段隔离检查；经 MCP server、REST API、CLI、Python SDK、Docker Compose 多入口可用，复现已发布 BEIR/MTEB 数字误差约 0.004 NDCG@10（README 自述）。

## 解决什么问题

RAG 技术文献几乎都是**单组件孤立评测**：新 reranker、新 chunker 各自报涨分，但实践者把组件叠进真实管线时不知道哪些收益能存活。这导致两类浪费——堆了不涨分的组件（白付延迟与费用），以及在小语料上调出的最优配置直接搬到大语料翻车。本文把"组合后的净收益"变成可预注册、可统计检验的实证问题。

## 相比前方法优势

- 相对库内 arxiv-2608.23252（Laws of Context Allocation：生成式搜索中**上下文分配**的因果测量与闭环编排），本文对象是**整条管线的组件交互**（8 阶段任意组合），且给出现成可跑框架而非测量协议；
- 相对库内 arxiv-2608.24753（RAT：RAG 评测的贝叶斯统一模型——评测的是单系统的输出不确定性），LASAGNA 评测的是**配置空间**（450 配置的交互效应），统计工具是经典假设检验而非贝叶斯建模，二者互补不重叠；
- 相对惯例"ablation 只在自家方法内做"，本文预声明假设 + 冻结其余阶段单换一组件 + 多重比较校正，组合结论有统计背书；
- 工程完成度高：PyPI 可装（`lasagna-rag`，Python 3.10–3.13），speed profile 免密钥（约 92 MB 模型），YAML sweep 批量跑实验——是库内 RAG 族第一张"可直接拿来当实验台"的卡。

## 局限

- **发现是经验性的**：三条结论绑定其 8 基准与语料分布，摘要未点名是哪三个检索技术贡献了"+47%→+17%"，具体组件黑名单需读正文 9 页主文确认，不能当普适定律引用；
- 正文 103 页（主文仅 9 页），细节在附录，赛时提取成本高；
- 框架质量 profile 需下载约 3.2 GB 模型，speed profile 精度有折损；仓库 17 stars、年轻项目（2026-10 实抓时点），API 可能变动；
- 论文与仓库均未给出"最优组合推荐表"，给出的是评测方法论与反直觉实证——拿到手是实验台，不是答案。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**：凡是"文档问答/知识助手"类赛题，开题先按论文先验设消融预算——单组件涨分别急着全上（+47%→+17% 的教训），优先验证检索质量与忠实性两条指标的分离；预算紧张时 token/延迟敏感的 agentic verification 最后再加；
- **Kaggle-竞赛**：把 LASAGNA 的 stage-isolation + 显著性检验流程当本地 CV 纪律模板——任何 trick 上榜前先跑配对检验，防过拟合公共榜；"小语料最优不等于大语料最优"提示做规模梯度验证；
- **成本核算**：reuse_cost=低——pip 即装、免密钥 speed profile 可起跑；论文数字只作先验，赛场结论须在赛题数据上自测（铁律 4）。
