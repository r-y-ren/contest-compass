---
id: arxiv-2610.37585
name: "Timestral：Mistral 开源时序基础模型族（5M-209M 四档）——GIFT-Eval/TIME/fev-bench 三榜 SOTA，解耦视界训练 + 原生协变量支持（971★，Apache-2.0）"
field: [time series foundation model, 概率预测]
directions: [数模与时序预测]
published: "2026-10-27"
maturity: demo
venue_tier: industry
reproducibility_level: high
signal:
  venue: "arXiv + GitHub（2026-10-29 API 实查：mistralai/timestral 971 stars/75 forks，Apache-2.0，Python，2026-10-15 创建同日推送）"
  stars: 971
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "零样本概率预测基线的当前开源天花板：三榜 SOTA 且 123M/209M 包揽每项指标前二，四档尺寸里 5M/28M 可在 CPU 级资源推理——赛题数据少、时间紧时先用 Timestral 出概率区间基线再对比自训模型，'基线含当前开源 SOTA'在评审处是硬差异；概率输出天然适配'预测+区间+情景'的答卷结构"
    reuse_cost: 低
    open_source: "github.com/mistralai/timestral（Apache-2.0）+ huggingface.co/collections/mistralai/timestral（四档权重）"
  - track: "Kaggle-竞赛"
    edge: "时序赛（零售/能源/需求）的快速提交器与融合成员：原生支持已知未来协变量的因果架构（促销/假期/天气类未来已知变量直接吃），解耦视界训练使长视界不掩蔽上下文；按延迟预算选 5M-209M 四档尺寸，零样本分数即可作 blended 提交的稳定成员"
    reuse_cost: 低
    open_source: "同上"
sources:
  - url: https://arxiv.org/abs/2610.37585
    title: "Timestral（arXiv abs 页，v1 2026-10-27，Adrien Petralia/Alexandre Gavaudan/Artjom Joosen 等，Comments 附官网/权重/代码三链接）"
    accessed: "2026-10-29"
  - url: https://github.com/mistralai/timestral
    title: "官方代码仓（GitHub API 实查 2026-10-29：971 stars/75 forks，Apache-2.0，Python，2026-10-15 创建并推送）"
    accessed: "2026-10-29"
---

# Timestral：Mistral 入场时序基础模型，四档小尺寸包揽三榜前二

> 来源：https://arxiv.org/abs/2610.37585 （v1 2026-10-27，Adrien Petralia/Alexandre Gavaudan/Artjom Joosen/Etienne Goffinet/Richard Kurle/Yassine El Ouahidi 等，Comments 附 mistral.ai/news/timestral、HF 权重集合、GitHub 代码三链接；2026-10-29 经 arXiv API 实抓摘要，GitHub API 同日实查 971★/Apache-2.0）。本卡内容出自本次抓取的摘要与 API 元数据，未读 PDF 全文，未运行模型。

## 是什么

Mistral AI 发布的**时序基础模型族 Timestral**：5M/28M/123M/209M 四档参数的**概率预测**模型。三个技术要件：**Decoupled Horizon Forecasting（DHF）**把预测 token 与因果编码的上下文分离，长视界训练无需掩蔽上下文、每个已观测值既是预测目标又是后续预测的上下文；**协变量框架**在因果架构内原生支持"未来已知"协变量；**两阶段管线**先在多样大规模合成语料上预训练、再以扩展上下文在真实+合成混合数据上后训练。作者报告在 GIFT-Eval、TIME、fev-bench 三榜刷新 SOTA，123M 与 209M 包揽每项指标前两名。

## 解决什么问题

通用概率预测"一次训练到处可用"的竞争中，此前缺口是：长视界训练与上下文利用的冲突、未来已知协变量在因果架构里的原生支持。Timestral 以三要件同时处理，并把权重（HF）与推理代码（GitHub，Apache-2.0）全部开放。

## 相比前方法优势

- 榜单广度：三个独立基准（GIFT-Eval/TIME/fev-bench）同时 SOTA，且是包揽式（前二全占），非单点刷榜；
- 尺寸谱实用：5M-209M 意味着从笔记本 CPU 到单卡都有可选项，比赛场景按延迟/算力预算选档；
- 合成预训练 + 真实后训练的两阶段配方与其四档小尺寸组合，暗示低成本部署路线。

## 局限（如实标注）

- 技术报告自报榜单成绩，独立第三方复测尚未出现；ferv-bench/GIFT-Eval 的代表性（是否覆盖比赛常见数据形态）需自查榜单构成；
- 仓库 2026-10-15 创建同日推送后无新提交（API 实查），生态（微调脚本/示例覆盖面）可能仍薄；
- 摘要未报告与 Chronos-2/TimesFM 等具体前代模型的逐项对照数字，需读全文或榜单页核对；
- 未运行验证：本地推理成本、上下文长度限制、协变量接口的实际易用性待实测。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：开赛先用 5M/28M 档零样本出基线与区间，把省下的时间投到特征工程与决策建模；答卷里"基线=当前开源 SOTA"加自训模型对比是标准加分结构；概率输出直接服务不确定性讨论章节。
- **Kaggle-竞赛**（reuse_cost 低）：作为 blend 成员或 start kit 级提交器；未来已知协变量（节假日/促销表）原生输入，免去自构协变量编码管线；注意官方仓目前以推理为主，微调需读全文确认支持路径。

**族内定位**：库内 arxiv-2610.11734（Timer-M1）占"原语式预训练 TSFM"位，arxiv-2608.17299（LiveHouse-TS）占"TSFM 开放世界评测"位；本卡占"工业界开源 SOTA 权重"位——与既有 Chronos-2 相关卡（arxiv-2610.07232、arxiv-2610.08118）构成"用哪家、防什么坑"的选型组合；后续 deep-sync 应跟踪第三方复测与其在协变量 what-if 上的表现（参见 08118 卡揭示的协变量盲区风险）。
