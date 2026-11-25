---
id: arxiv-2611.29467
name: "Beyond Accuracy：假设驱动实验规划的诊断基准——把 agent 推理拆成信念更新/假设判别/判别性实验设计/干预下预测四步分别打分，10 个 LLM agent 暴露'认得出假设≠写得出对比预测'"
field: [LLM agents, scientific discovery, benchmark, 实验规划]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-11-22"
maturity: paper
venue_tier: arXiv
signal:
  venue: "arXiv（摘要经 arXiv API 实抓，2026-11-25）；基准网站 schwallergroup.github.io/beyond-accuracy（摘要给出）；GitHub 官方代码仓未检索到（2026-11-25 实查）"
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "数据分析类赛题的评审正在从'最终精度'转向'过程质量'，本卡提供了现成的过程诊断框架：把探索行为量化为设计空间中的 space-filling vs corner-seeking 模式、把推理拆成四步分别打分——自建赛题 agent 的评测环节照搬这套分解，就能回答'agent 是真在做假设检验还是瞎试'；四步分解同样是调试自家数据分析 agent 的检查表（哪一步掉分修哪一步）"
    reuse_cost: 中
    open_source: "schwallergroup.github.io/beyond-accuracy（基准网站，摘要给出）"
sources:
  - url: https://arxiv.org/abs/2611.29467
    title: "Beyond Accuracy: A Diagnostic Benchmark for Hypothesis-Driven Experiment Planning in LLM Agents（arXiv abs 页，摘要经 arXiv API 实抓）"
    accessed: "2026-11-25"
  - url: https://schwallergroup.github.io/beyond-accuracy/
    title: "基准网站（论文摘要给出的链接，2026-11-25 记录）"
    accessed: "2026-11-25"
---

# Beyond Accuracy：别只看 agent 答对没有，看它会不会"做实验"

> 来源：https://arxiv.org/abs/2611.29467 （2026-11-22，摘要经 arXiv API 实抓 2026-11-25）；基准网站 https://schwallergroup.github.io/beyond-accuracy/ （摘要给出，2026-11-25 记录）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

**Beyond Accuracy**（Ryo Kuroki 等），面向**假设驱动自适应实验规划**的基准+诊断评测框架，实例化为闭世界系统辨识中的**动力学机理辨识**（kinetic mechanism identification）。超越最终精度的两刀：(1) **探索行为量化**——agent 的实验设计在空间中呈 space-filling 还是 corner-seeking 模式；(2) **推理过程四步分解**分别打分：信念更新、假设判别、判别性实验设计、干预下的预测推理（基于推理轨迹）。10 个 LLM agent 的实测发现：专家标注支持"干预下预测推理"环节的判定标准，"判别性实验设计"证据正面但不一致；核心 gap 是**"认得出合理假设"与"把假设转写成尖锐对比预测"之间的断裂**，实验设计瓶颈有初步证据。

## 解决什么问题

用最终精度评测科学任务 agent，会掩盖推理在哪一步成功/崩坏——一个瞎试碰对的 agent 和一个假设驱动的 agent 可能同分。要改进 agent 或评选 agent，都需要把"科学过程质量"变成可测的分项。

## 相比前方法优势

- **过程可测化**：探索模式（space-filling vs corner-seeking）是行为级的量化指标，不依赖人工读轨迹；
- **四步分解可定位**：belief update → hypothesis discrimination → discriminative design → predictive reasoning 的链条让"哪一步弱"有答案，区别于端到端 accuracy 类科学 agent 基准；
- **专家标注背书**：预测推理环节的判定标准有独立专家标注支撑，不是纯 LLM-judge 自说自话；
- **闭世界实例**：动力学机理辨识有 ground truth，假设判别可严格判分。

## 局限（如实标注）

- 单一实例域（动力学机理辨识）：四步框架向其他科学域（实验化学/生物）迁移需重新设计任务与判分，摘要未给迁移实验；
- "判别性实验设计"证据不一致——框架自身最核心的一步，评测可靠性尚存疑；
- 官方代码仓未检索到（2026-11-25 GitHub 实查），仅有基准网站，复现依赖网站资源；
- arXiv 预印本，基准的社区采用度未经过检验。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：两层复用——(1) 评测设计：为"AI 数据分析"类赛题（如智能体数据分析挑战）设计评分细则时，把四步分解+探索模式指标直接搬为 rubric，避免"只看 final 分数"； (2) 自家 agent 调试：数据分析 agent 在赛题上表现差时，按四步打分定位短板（常见断点：认得出假设但写不出对比预测→重点改实验设计 prompt）。
