---
id: arxiv-2610.41100
name: "QUAL：免标签分位数对齐——拿模型池当概率参照系互救，GIFT-Eval 成员 MASE -7.4%/CRPS -9.8%"
field: [time series foundation model, ensemble, 概率预测校准]
directions: [数模与时序预测]
published: "2026-10-30"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv（GIFT-Eval 基准；摘要称代码发布于 github.com/junhyeokkang/QUAL，本轮 GitHub API 实查 404 未找到——仓库未上线或链接失效）"
  runnable: false
competition_fit:
  - track: "数模-预测与评估"
    edge: "零样本组合多个 TSFM（Chronos-2/TimesFM/…）时没有目标域标签可供加权——QUAL 用模型池自身做概率参照系：把每个成员的分位数预测向池参照对齐，再 Huber 聚合 + rearrangement 出最终分布，全程免训练免标签；对'赛题数据一到手就要交区间'的数模场景，这是把手上 3-4 个现成基座白嫖成更强集成的 10 行级后处理"
    reuse_cost: 低
    open_source: "无可用官方仓（摘要链接 github.com/junhyeokkang/QUAL 经 GitHub API 实查 404）"
  - track: "Kaggle-竞赛"
    edge: "概率时序赛（CRPS 计分）的 ensemble 增益来源：官方报告对齐使成员平均 MASE/CRPS 降 7.4%/9.8%，且池中混入弱模型也稳健（无需事先验证成员质量）——刚好对上 Kaggle 常态'手里的 checkpoint 良莠不齐'; 与成员间简单平均相比是更优的合并层"
    reuse_cost: 低
    open_source: "无可用官方仓（同上，404）"
sources:
  - url: https://arxiv.org/abs/2610.41100
    title: "QUAL: Quantile Alignment Improves Zero-Shot Time-Series Foundation Models（arXiv abs 页，2026-10-30，摘要经 arXiv API 实抓）"
    accessed: "2026-11-07"
---

# QUAL：零样本 TSFM 集成的免标签合并层

> 来源：https://arxiv.org/abs/2610.41100 （v1 2026-10-30，摘要经 arXiv API 实抓，2026-11-07）。本卡内容出自本次抓取的摘要，未读 PDF 全文。

## 是什么

针对零样本场景的 TSFM 集成框架。出发点：多个基础模型能降低单模型在各数据集上的方差，但零样本部署没有目标标签，无法选择或加权成员。作者发现模型池有第二个用法——**当作概率参照系**：把每个成员的分位数预测向"池相对参照"变换对齐， aggregate 上每个成员都被改善。落地为 QUAL 三步：成员分位数对齐 → **Huber 聚合**（稳健合并）→ **rearrangement**（保证分位数单调），全程免训练、不改成员模型。GIFT-Eval 上：成员平均 MASE 降 **7.4%**、CRPS 降 **9.8%**；候选池混入弱预测器时框架依然稳健。

## 解决什么问题

零样本集成没有标签就没有权重——传统 stacking/验证集加权全部失效。QUAL 的答案是不要权重：让成员互为参照，把各自的系统性分位偏差向池中心拉齐后再稳健合并。弱成员不毁局（Huber 抗污染），这是"不知道手里模型好坏"时的安全选项。

## 相比前方法优势

- **免标签免训练**：纯推理期后处理，不改任何成员模型，与零样本前提自洽；
- **"对齐"先于"合并"**：先让成员分布可比，再做聚合——比直接平均/中位数合并多吃一层增益（成员级 -7.4% MASE 是对齐本身的贡献）；
- **对池污染稳健**：弱成员在场仍有效，适配"模型质量无法事先验证"的真实工作流；
- **方法简单**：分位数变换 + Huber + rearrangement 三件事都是标准件，无新算力需求。

## 局限（如实标注）

- **官方代码仓本轮实查 404**（摘要给的 github.com/junhyeokkang/QUAL 不存在或未上线）——论文存在≠可直接复用，落地需按摘要自实现（方法本身简单，但 rearrangement 与对齐的具体实现细节需读全文）；
- 数字全部来自官方摘要口径（GIFT-Eval 单基准），跨基准外推未证；
- 对齐以池为参照：池内成员高度同质（例如全是 Chronos 系）时参照系退化，增益预期缩水；
- 与简单平均/中位数的逐项对照数字摘要未给出，增益净额需读全文核对。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：开赛先把 2-4 个 TSFM 零样本跑一遍（Chronos-2/TimesFM 等，见基座卡），QUAL 合并出最终区间——为论文提供"多模型集成 + 免标签稳健合并"的方法学段落；实现成本一次性的后处理脚本。
- **Kaggle-竞赛**（reuse_cost 低）：CRPS/分位数赛道的合并层选型：比 weighted blend 少一个需要验证集的超参层；"弱成员混入仍稳健"意味着 checkpoint 池可以贪心收，不必先做成员筛选实验。

**族内定位**：库内概率校准线已有"TSFM 不确定性校准评测"类证据与 FreshCast（闭式权重校准修正冻结预测器）占"检索增强修正"位；本卡占"**多模型免标签合并**"位——上游可接任何成员集合（含 Chronos-2 基座卡与 KGO 的采样输出），与 time-wise/series-wise 验证卡（arxiv-2611.08252）正交：那边管选型，这边管合并。
