---
id: arxiv-2610.11370
name: "RIT-RAG：检索诱导子树让 agentic RAG 先'定位'再'阅读'（284 万页 EntQABench 上领先最强基线 6.8-11.4 点）"
field: [retrieval augmented generation, LLM agents]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-08"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv（2026-10-08 v1，24 页 9 图 16 表；摘要页未附代码链接）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "长文档问答/RAG 赛道的架构升级模板：'检索负责提议去哪看、agent 决定读什么'的分工可直接嫁接到现有 vector RAG 栈——离线从目录/sitemap 建每文档树、在线用命中 chunk 的位置诱导跨文档子树再导航，比 PageIndex 类结构法免去了'提前押注单文档'的失败模式；金融/科研/客服三域基准 + 自建 284 万页基准双重验证"
    reuse_cost: 中
  - track: "双创-文书与申报"
    edge: "企业知识库问答产品的规模化卖点：纯向量检索在超大语料（百万页级）上检索噪声大、纯结构导航又建不全树，'内容检索×结构导航'混合是可写进申报书的架构差异点；EntQABench（284 万技术文档网页）本身可作产品评测背书场景"
    reuse_cost: 中
sources:
  - url: https://arxiv.org/abs/2610.11370
    title: "RIT-RAG: Navigating Document Corpora with Retrieval-Induced Trees（arXiv abs 页，v1 2026-10-08，Pulivarthi/Biswal/Bhushan/Nandwani/Joshi/Raghu，Comments：24 页 9 图 16 表；2026-10-16 实抓）"
    accessed: "2026-10-16"
---

# RIT-RAG：当向量检索遇上目录树，谁提议、谁拍板

> 来源：https://arxiv.org/abs/2610.11370 （arXiv abs 页 v1 2026-10-08，2026-10-16 实抓）。本卡内容出自本次抓取的摘要页，未读 PDF 全文。

## 是什么

一种**内容检索与结构导航配对**的 agentic RAG 架构。离线为每篇文档从目录（TOC）或 sitemap 建树；查询时先做常规内容检索，用命中 chunk 在树中的位置**诱导**出一批可管理的跨文档子树；LLM agent 再在这些子树里导航、读有希望的节点、按需改写查询——检索提出"去哪看"，agent 决定"读什么"。

## 解决什么问题

agentic RAG 让模型迭代检索，但喂给模型的是**脱离文档结构的孤立 chunk**，跨节论证与层级定位弱；PageIndex 类结构感知方法要求对大语料全量建树、且查询时**提前押注单一文档**，押错即失败。RIT-RAG 要在两者之间找到可规模化又不必押注的中间态。

## 相比前方法优势

- **检索诱导子树**：结构信息按需激活——不用全语料预建可导航结构，也不押注单文档，子树由每次查询的检索命中动态圈定；
- **成绩横跨三域**：金融、科研、客服基准上对 vanilla / graph-based / agentic 基线取得最高准确率；
- **超大语料专门验证**：自建 EntQABench（284 万技术文档网页），三个 LLM 骨干上比最强基线高 **6.8-11.4 点**——规模天花板是纯向量 RAG 的软肋，这里是主战场；
- **分工清晰可移植**：现有 RAG 栈的检索器保留不动，增量只在"chunk 位置→子树→agent 导航"一段。

## 局限（如实标注）

- 摘要页未附代码链接，未找到开源实现（reproducibility 低）；树的构建质量依赖文档 TOC/sitemap 的存在与规范度，无目录文档（如扫描件、纯文本堆）的降级路径摘要未说明；
- 每查询多步导航的**延迟与 token 成本**对照未在摘要层给出，生产化成本需读全文；
- EntQABench 为作者自建基准，域偏技术文档；
- v1 预印本无 venue。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：文档问答/RAG 赛题（年报问答、政策问答、技术文档问答）的架构选型——赛题语料若带目录结构（HTML 站点、Markdown 书籍），按本文"离线建树 + 检索诱导子树"改造现有向量栈，是比"换更强 embedding"更结构化的差异化点；评测协议（三域 + 超大语料）可直接借用思路自建小型对照。
- **双创-文书与申报**（reuse_cost 中）：知识库类产品申报的架构章节素材："检索提议、agent 拍板"的混合导航 + 284 万页规模验证，回应"你们的 RAG 和别人有何不同"的必问题。

**族内定位**：库内 RAG 卡群多为 chunking/证据选择/注入防御位（如 2610.10170 结构化切分、2610.11183 误导证据），本卡占"语料级导航结构"位——与结构化切分卡互补：一个管切多细，一个管查完去哪。
