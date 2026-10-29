---
id: arxiv-2610.33209
name: "MAPS：多变量时序任务内在可预测性的 model-agnostic 度量——合成数据与参考可预测性 r=0.963，官方 MIT 代码（0★ 新仓）"
field: [time series forecasting, 任务可预测性, 评测方法]
directions: [数模与时序预测]
published: "2026-10-23"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv + 官方代码仓 ClaudiaShu/MAPS（GitHub API 实查 2026-10-29：0 stars，MIT，Python，2026-10-21 创建，2026-10-24 推送；abs 页 Comments 给出代码链接）"
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "开题阶段'该上多重的模型'的量化判据：MAPS 利用协变量信息在给定 lookback/horizon 下度量任务内在可预测性（模型无关），合成数据上与参考可预测性相关 r=0.963——低分任务直接上简单模型并论证'已接近可预测上限'，高分任务才值得堆深度结构；回应评审'为什么简单模型就够/为什么还差'时有了独立于具体模型的依据"
    reuse_cost: 低
    open_source: "github.com/ClaudiaShu/MAPS（MIT，官方代码）"
  - track: "数模-数据分析与决策"
    edge: "多变量关联数据的探索性分析件：跨 lookback 窗口与预测视界的可预测性画像本身是数据洞察——哪些变量组合、哪个时间尺度携带预测信息，可直接写进'数据分析'章节作为变量筛选与视界选择的论证"
    reuse_cost: 低
    open_source: "同上"
sources:
  - url: https://arxiv.org/abs/2610.33209
    title: "Model-agnostic predictability quantification of multivariable time series（arXiv abs 页，v1 2026-10-23，Yuxuan Shu/Vasileios Lampos，Comments：代码见 github.com/ClaudiaShu/MAPS）"
    accessed: "2026-10-29"
  - url: https://github.com/ClaudiaShu/MAPS
    title: "官方代码仓（GitHub API 实查 2026-10-29：0 stars，MIT，Python，2026-10-21 创建，2026-10-24 推送）"
    accessed: "2026-10-29"
---

# MAPS：先量任务有多可预测，再决定模型上多重

> 来源：https://arxiv.org/abs/2610.33209 （v1 2026-10-23，Yuxuan Shu/Vasileios Lampos，Comments 附官方代码链接；2026-10-29 经 arXiv API 实抓摘要，GitHub API 同日实查 ClaudiaShu/MAPS 0★/MIT/Python）。本卡内容出自本次抓取的摘要与 API 元数据，未读 PDF 全文。

## 是什么

**Multivariable Predictability Score（MAPS）**：度量多变量时序预测任务**内在可预测性**的 model-agnostic 指标。动机：预测精度=模型能力×任务难度，跨基准比精度分不清两者；既有可预测性度量要么抓不住非线性依赖、要么限单变量。MAPS 利用协变量信息，在不同 lookback 窗口与预测视界下评估可预测性，给出"这个任务里到底有多少可用的预测信息"的定量刻画。合成数据上与期望参考可预测性相关 r=0.963，并在真实数据集上对 6 个基线可预测性度量取得更可靠的投影。

## 解决什么问题

"换十个模型都差不多的分数"到底是模型不行还是任务本来就没信息？MAPS 把任务难度从模型能力中剥离出来，让"模型选择"与"上限论证"有独立依据。

## 相比前方法优势

- 多变量 + 非线性：突破既有度量"单变量/线性假设"两个限制，直接面向协变量场景；
- 校准有硬数字：合成实验与参考可预测性 r=0.963，不是只给相关方向的定性结论；
- model-agnostic：分数不依赖某个被评模型，可比、可复用、可先于建模计算；
- 官方代码 MIT 开放（0★ 新仓，2026-10-21 创建），即取即用无授权负担。

## 局限（如实标注）

- 官方仓 0 stars、创建仅一周（2026-10-29 实查），无社区验证；"更可靠的投影（majority of configurations）"措辞留有余地——少数配置下不占优的细节在全文里；
- r=0.963 出自合成数据，真实任务上"分数→该用多重模型"的映射规则需自行标定；
- 可预测性分数解释依赖协变量选择：喂错协变量会低估可预测性，使用时要对协变量集做敏感性检查；
- 作者称适用于"multivariable"场景，纯单变量无协变量任务的适用性摘要未覆盖。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：拿到赛题数据先跑 MAPS 画像（各目标×各视界的可预测性），据此定模型档位并写进模型选择依据；低可预测目标用浅模型+区间（配 DDCI 类校准），高可预测目标再上重模型——"按任务难度分配建模预算"是评审友好的叙事线。
- **数模-数据分析与决策**（reuse_cost 低）：把"哪个视界、哪些协变量组合可预测性最高"的画像做成探索性分析图，直接支撑变量筛选与预测视界选择的论证，一图两用。

**族内定位**：库内 arxiv-2608.14106（Forecast Collapse in TSFMs）记录"强模型在长视界崩"的现象，arxiv-2610.09994（Temporal Predictive Multiplicity）记录"等精度模型轨迹不同"的现象——两者都提示"精度单一口径不够"；本卡占"任务侧难度度量"位，给这两个现象提供事前判据，属同一"评测纪律"簇的补充件。
