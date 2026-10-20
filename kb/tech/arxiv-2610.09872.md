---
id: arxiv-2610.09872
name: "LiveMACEBench：活金融市场做演化环境的 Agent 过程感知评测（30 天实测 5 前沿模型，结果-能力差：赚钱≠能力栈健全）"
field: [LLM agents, 评测基准, 金融时序]
directions: [黑客松与数据竞赛]
published: "2026-10-06"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv/HuggingFace Papers"
  runnable: true
competition_fit:
  - track: "Kaggle-竞赛"
    edge: "量化/金融时序类竞赛的能力诊断方法论：其核心发现『结果-能力差』——实现收益常与机制级能力测量背离、相似收益可来自截然不同的机制使用模式——正是排行榜踩坑（赢在行情运气而非方法）的学术版；Tool Use / Persistent Memory / Rule Following / Multi-Agent Collaboration 四机制的 trace 级诊断协议可借来给自家策略 agent 做赛前自检与消融，答辩时区分『赚到了』与『凭什么赚到』"
    reuse_cost: 中
    open_source: "https://github.com/RaymondVoldemortFu/LiveMACE（官方仓，MIT，2026-10-20 实查 README 与论文徽标对应）"
  - track: "黑客松-数据与算法"
    edge: "持续运行 agent 的评测设计模板：活市场作天然演化测试床（环境不可重放、行为与环境闭环互构）+ 完整决策轨迹记录 + 『机制可及性/有效使用/下游绩效』三层分离度量——做演化环境 agent（交易、运维、游戏经济）作品时，这套过程感知评测是相比『只报收益曲线』的清晰答辩差异化；官方评测框架 MIT 可改造成自建环境的诊断层"
    reuse_cost: 中
    open_source: "https://github.com/RaymondVoldemortFu/LiveMACE（Python 3.10+ 后端 + Extension SDK；接真实行情需自备数据源）"
sources:
  - url: https://arxiv.org/abs/2610.09872
    title: "LiveMACE: Process-Aware Evaluation of LLM Agent Capabilities in Evolving Markets（arXiv abs 页，Jun Zhao 等 13 人含 Xuanjing Huang 复旦团队，摘要全文，2026-10-20 实抓）"
    accessed: "2026-10-20"
  - url: https://github.com/RaymondVoldemortFu/LiveMACE
    title: "RaymondVoldemortFu/LiveMACE 官方仓 README（8 stars/MIT/Python 3.10+，论文徽标 arXiv:2610.09872，30 天实测与 outcome-capability gap 口径与论文一致，2026-10-20 实抓）"
    accessed: "2026-10-20"
---

# LiveMACEBench：用活着的金融市场诊断 LLM Agent 的真实能力栈

> 来源：https://arxiv.org/abs/2610.09872 （abs 页摘要，2026-10-20 实抓；Jun Zhao、Leiming Fu 等 13 位作者，含 Xuanjing Huang）。官方代码 https://github.com/RaymondVoldemortFu/LiveMACE （MIT，2026-10-20 README 实读确认与论文对应）。本卡出自本次抓取的摘要页与官方 README，未读全文。

## 是什么

**过程感知**的 LLM agent 评测基准：以**真实演化的金融市场**为测试床，让 5 个前沿 LLM 作为**持久 agent** 沿连续轨迹运行 30 天（收集信息、推理、执行模拟交易），基准记录完整决策轨迹——工具调用、记忆交互、持仓状态。在匹配的四种机制配置下评测：**Tool Use、Persistent Memory、Rule Following、Multi-Agent Collaboration**；评测双轨：实现结果（收益）+ 从完整轨迹导出的机制级诊断。核心发现：**结果-能力差（outcome-capability gap）**——实现收益常与能力测量背离，相似结果可来自迥异的机制使用模式；机制可及性、有效使用、下游绩效三者不可互相替代。定位是把活市场从"排行榜"变成"诊断环境"。

## 解决什么问题

只看结果评 agent 会掩盖产生结果的能力：在演化环境中，结果是 agent 行为与外部环境变化闭环互构的产物——赚钱可能靠行情，亏钱可能靠运气。过程感知评测回答"这个 agent 靠什么能力赚到/亏掉"，并定位各机制的具体瓶颈。

## 相比前方法优势

- **活环境而非重放**：市场自然演化，杜绝静态基准的过拟合与信息泄漏；
- **机制级归因**：四机制配置 + trace 级诊断，能说出"瓶颈在记忆使用而非工具调用"这类结论，结果评测做不到；
- **持久 agent 口径**：连续轨迹上的长期运行，区别于单任务回合制评测；
- **官方开源**：MIT 协议 + Extension SDK，评测框架可迁移到非金融环境。

## 局限（如实标注）

- arXiv 预印本，30 天窗口与 5 模型样本对"市场环境"这一高方差域偏短；结论外推到其他演化环境需谨慎；
- 模拟交易与真实执行的滑点/成本差异未在摘要披露；金融域结论（收益 vs 能力）对非金融赛题的迁移是方法级而非数字级；
- 官方仓 8 stars（2026-10-20 实查），社区复验尚未形成；HF 112 upvotes 信号强但属关注度非质量背书；
- 四机制配置的匹配细节（每机制关什么/开什么）需读全文才能照搬协议。

## 如何用于比赛（比赛映射展开）

1. **Kaggle-竞赛（量化/金融时序）**：赛前用其四机制 trace 诊断协议自检策略 agent——把交易决策轨迹记录下来，对照"机制可及/有效使用/绩效"三层找瓶颈（如：工具都在用但记忆层形同虚设）；比赛叙事从"我的策略收益 X%"升级为"我的 agent 能力栈诊断 + 收益归因"，避开"赢在行情"的评审质疑。reuse_cost 中：协议需读全文后改造，官方代码可跑通其口径。
2. **黑客松-数据与算法（演化环境 agent 作品）**：直接借"过程感知评测"设计模式给作品加诊断层——记录完整决策轨迹、按机制维度做消融、在答辩中展示"结果相同但机制使用更健康"的证据；Extension SDK 支持接自建环境（运维/游戏经济/供应链模拟均可类比"演化测试床"）。reuse_cost 中：框架 MIT 可改，接新环境需自写适配。
