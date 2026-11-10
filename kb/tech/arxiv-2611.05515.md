---
id: arxiv-2611.05515
name: "CoCo：LLM 把文本推理蒸馏成预测/置信协变量喂给 TSFM——新闻报告类文本进时序预测的第三条路（Qwen3-4B + Chronos2，MAE 最高 -12%）"
field: [time series foundation model, LLM, 多模态预测]
directions: [数模与时序预测]
published: "2026-11-03"
maturity: paper
venue_tier: arXiv
reproducibility_level: low
signal:
  venue: "arXiv（2026-11-10 经 arXiv API 实抓摘要；GitHub repo search 无官方实现）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "赛题数据带文本协变量（政策新闻、天气预警、舆情通报）而主力预测模型是纯数值时序模型时，CoCo 给出『文本怎么进模型』的成熟答案：不硬拼 prompt、不做端到端多模态大模型，而是让 LLM 把文本推理蒸馏成数值化的 forecast covariate + confidence covariate 去引导 TSFM 骨干——方法选型论证（LLM 数值精度不足、TSFM 不会读文本 → 各自扬长的协变量接口）可直接写进数模论文的方法章节"
    reuse_cost: 中
  - track: "Kaggle-竞赛"
    edge: "带新闻/事件文本的销量、金融、能源类赛道：两阶段配方可拆用——(1) 用 LLM 标注真实时序生成合成配对语料，绕开配对多模态数据稀缺；(2) GRPO 奖励直接绑定『协变量带来的预测改进』做端到端对齐，再用对齐后的 LLM 产出协变量微调 TSFM；官方报 Qwen3-4B-Instruct + Chronos2 组合最高 12% MAE 改进，且合成语料训出的模型在金融/经济/天气/交通/安全多域真实基准泛化。无官方代码，需自建全流程"
    reuse_cost: 高
sources:
  - url: https://arxiv.org/abs/2611.05515
    title: "TSFM Meets LLM: Context as Covariates（arXiv abs 页，2026-11-03 提交，摘要经 arXiv API 实抓 2026-11-10）"
    accessed: "2026-11-10"
---

# CoCo：文本不当 prompt 用，蒸馏成协变量喂 TSFM

> 来源：https://arxiv.org/abs/2611.05515 （v1 2026-11-03，摘要经 arXiv API 实抓 2026-11-10）。本卡内容出自本次实抓摘要，未读 PDF 全文；GitHub repo search（2026-11-10）未见官方实现。

## 是什么

Context as Covariates（CoCo）框架：LLM 读懂新闻/报告/注释类文本后，不做端到端预测，而是输出两个数值化接口——**forecast covariate**（文本蕴含的预测倾向）与 **confidence covariate**（文本带来的置信度调整），由它们引导 TSFM 骨干（实验用 Chronos2）出最终预测。配套两个工程件：(1) 用 LLM 给真实时序数据标注生成大规模合成多模态语料，解决配对数据稀缺；(2) 两阶段对齐——先用 GRPO 微调 LLM（奖励 = 协变量诱导的预测改进），再用对齐后的 LLM 协变量微调 TSFM。官方报告：CoCo（Qwen3-4B-Instruct-2507 + Chronos2）相对 SOTA TSFM/LLM 基线最高 **12% MAE 改进**，合成语料训出的模型在金融、经济、天气、交通、安全多域真实基准上泛化。

## 解决什么问题

真实时序数据普遍携带文本信息（新闻、报告、标注），其中有关键预测信号，但 LLM 数值精度不足、TSFM 读不了文本，两条能力长期接不上；同时大规模"时序+文本"配对数据几乎不存在，端到端多模态方案缺数据。CoCo 把接口定义在"协变量"这一层：LLM 只负责语义推理，数值出力交回 TSFM，配对数据问题用合成语料绕开。

## 相比前方法优势

- **接口轻**：相比把文本塞 prompt 或训统一多模态大模型，协变量接口不动 TSFM 骨干架构、不占长上下文，文本影响被压缩成两个数值通道，可解释（协变量本身可审计）；
- **奖励设计直接对齐目标**：GRPO 奖励绑定"协变量进 TSFM 后预测是否变好"而非"文本摘要好不好"，端到端对齐到预测质量；
- **数据自给**：LLM 标注真实时序造配对语料，另辟一条绕数据稀缺的路，且合成语料训出的模型在真实基准泛化（官方口径）。

## 局限（如实标注）

- 未读 PDF 全文：12% MAE 的具体基准清单、逐域数字、与简单基线（如文本情感打分直接当特征）的对照深度以摘要口径为准；
- 无官方开源实现（GitHub repo search 2026-11-10 未见），GRPO 对齐 + TSFM 微调两阶段复现成本高，reproducibility 定为 low；
- 协变量质量依赖 LLM 文本理解上限，文本与序列相关性弱时协变量可能引入噪声（摘要未给失效分析）。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 中）：带文本辅助信息的预测题（电价+政策新闻、客流+突发事件通报、销量+舆情）的"文本融合"方法选型：与三类常见做法对比论证——文本特征硬编码（信息损失）、端到端多模态（数据不够）、CoCo 式协变量蒸馏（两头扬长）；confidence covariate 还能顺带产出"文本证据强度"分析，写进不确定性讨论。
- **Kaggle-竞赛**（reuse_cost 高）：新闻驱动型销量/金融赛道可拆件复用：合成配对语料生成是独立可用的数据增广思路；GRPO-绑定预测改进的对齐配方可移植到自有两阶段方案；全套自建周期长，适合长周期大赛而非 48 小时黑客松。
