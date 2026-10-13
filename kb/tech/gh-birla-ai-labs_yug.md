---
id: gh-birla-ai-labs_yug
name: "Yug：271.8M 开箱即用零样本概率时序基础模型（分位数直出+协变量+GluonTS 接入）"
field: [time series forecasting, time series foundation model, 概率预测]
directions: [数模与时序预测]
published: "2026-10-01"
maturity: demo
venue_tier: unknown
reproducibility_level: high
signal:
  venue: "GitHub（Apache-2.0，Python；2026-10-01 创建、2026-10-09 仍有推送，API 实查 58 stars/2 forks）"
  stars: 58
  runnable: true
competition_fit:
  - track: "数模-预测与评估"
    edge: "零样本概率预测开箱即用：单一检查点对未见序列直接出 0.1-0.9 九档分位数，区间预测/风险评估类赛题的置信区间要求免训练满足；271.8M 参数可在免费 Colab/CPU 级算力跑，patch 解码一次前向出整块未来点无逐步循环，竞赛时限内友好；上下文长度 2048 支撑长历史输入"
    reuse_cost: 低
    open_source: "github.com/birla-ai-labs/yug（pip install yug）+ HF 权重 birlaailabs/yug（README 自述）"
  - track: "Kaggle-竞赛"
    edge: "时序赛分钟级 baseline：pip 装即得概率预测，把省下的调参时间投到特征与后处理；可选协变量通道接外生特征，GluonTS predictor 可直接挂进既有基准 harness 做集成/选型对比"
    reuse_cost: 低
    open_source: "github.com/birla-ai-labs/yug + huggingface.co/birlaailabs/yug"
sources:
  - url: https://github.com/birla-ai-labs/yug
    title: "birla-ai-labs/yug（GitHub API 实查：58 stars/2 forks/0 issues，Apache-2.0，Python，2026-10-01 创建 2026-10-09 推送；README：v0.1.1 首个公开发布，271.8M 参数、9 档分位、上下文 2048、patch 直推多步解码、协变量支持、GluonTS predictor、yug-check 自检，权重挂 HF birlaailabs/yug）"
    accessed: "2026-10-13"
---

# Yug：271.8M 开箱即用零样本概率时序基础模型

> 来源：https://github.com/birla-ai-labs/yug （GitHub API + README，2026-10-13 实抓）。Birla AI Labs 出品，v0.1.1 首个公开发布（2026-10）；本卡全部内容出自本次抓取的仓库 API 与 README，未运行实测。

## 是什么

Yug 是一个**预训练时序基础模型**，主打**零样本概率预测**：单一检查点面对从未见过的等间隔数值序列，给定历史上下文与预测步长，直接返回以分位数水平（0.1-0.9 共 9 档）概括的预测分布——无需任务特定训练或逐序列调参。工程形态完整：`pip install yug`、权重挂 HuggingFace（271.8M 参数、上下文 2048）、`yug-check` 环境自检、GluonTS predictor 可接入既有基准 harness。README 列出的要点：patch 解码一次前向输出整块未来点（无逐步生成循环）、概率输出默认自带区间、可选协变量通道。

## 解决什么问题

学生队做预测类赛题的两难：经典统计/GBDT 管线要逐数据集调参，大模型 API 有成本与时延；而多数开源 TSFM 需要自己搭推理环境。Yug 把"零样本 + 概率输出 + 一条命令安装"打包成消费级可用的形态，覆盖"快速拿到带区间的预测基线"这一高频需求。

## 相比前方法优势

- **概率是默认输出而非附加头**：9 档分位数直接可用，区间预测/不确定性分析类赛题要求免改造满足；
- **直接多步解码**：patch 一次前向出整块，无自回归逐步循环——竞赛时限与 CPU 级算力下更稳；
- **工程接入齐全**：PyPI 包 + HF 权重 + GluonTS predictor，接入现有评测管线成本低；
- **协变量通道**：可选外生特征输入，比纯自回归零样本模型多一个信息入口。

## 局限（如实标注）

- **无论文无公开基准数字**：README 未附 GIFT-Eval/MASE 等任何对比结果，模型能力未经第三方验证——"零样本效果如何"完全未知，选型前必须自跑小样本对照；
- 仓库极新（2026-10-01 创建，58 stars/2 forks/0 issues），社区验证缺失，公司背书（Birla AI Labs）无第三方背书；
- README 自述仅支持**等间隔数值序列**，不规则时序、多变量结构化数据不覆盖；
- 协变量支持的具体形态与效果 README 未展开；
- 无关联论文，模型架构/训练细节不透明，出现问题时排查依据有限。

## 如何用于比赛（比赛映射展开）

- **数模-预测与评估**（reuse_cost 低）：C 题类预测赛题开赛后 10 分钟出带 90% 区间的基线预测，置信区间直接支撑"风险评估/区间预测"小问；271.8M 模型免费算力可跑，无 GPU 的队伍可用。与既有卡 Tabby（145M 配方模型）、Chronos 系形成小模型零样本梯队——集成或择优的选型空间。
- **Kaggle-竞赛**（reuse_cost 低）：时序赛作为快速 baseline 与概率集成成员；GluonTS predictor 挂进标准评测后可与其他 TSFM 统一对比；省下的时间投特征工程与后处理。

**入库口径**：demo 级（可装可跑），但能力未经公开基准验证——用于比赛前须自测；若后续放出论文/基准，值得老化重验升级。
