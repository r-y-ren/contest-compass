---
id: arxiv-2611.08175
name: "PCBRouteAgent：全局规划器 + KiCad 原生执行器的多模态 PCB 布线 agent——247 块板 clean-pass 40-100%，真实板超最佳基线最高 36pp（HF 25 赞，官方仓 BSD-3 可跑）"
field: [LLM agents, EDA, 多模态]
directions: [黑客松与数据竞赛]
published: "2026-11-05"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "HuggingFace Papers 25 赞 + 官方仓 chip-ai-agent/PCBRouteAgent（GitHub API 实查 2026-11-10：22 stars，BSD-3-Clause，2026-11-06 创建并推送）"
  stars: 22
  upvotes: 25
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "EDA/硬件设计自动化类赛题（电子设计创新赛、黑客松硬件赛道）的『agent 驾驭专业工具』范式样本：Global Routing Planner 用板卡图像 + 结构化电气几何信息规划拓扑/布线顺序/走廊/换层，Detailed Routing Executor 经 KiCad 原生布线引擎落地并对未解失败做有界局部恢复，失败以结构化反馈回传供定向修订——『全局策略 + 局部执行 + 结构化失败回路』的三段架构可平移到任何专业工具自动化（CAD、仿真器、编译器链）；官方仓 22★ 可跑，PCBWorld-Bench 247 板四分片 clean-pass 100%/94.9%/100%/40%"
    reuse_cost: 低
  - track: "双创-文书与申报"
    edge: "PCB 设计智能化叙事的实证背书：引真实板三分片超最佳基线 13.9/36/10 个百分点的 clean-pass 数据，论证『LLM agent + 原生 EDA 工具链』落地路径；HF 25 赞 + BSD-3 官方仓给出社区与开源双重背书"
    reuse_cost: 低
sources:
  - url: https://arxiv.org/abs/2611.08175
    title: "PCBRouteAgent: How Close Are LLM Agents to Becoming PCB Routing Engineers?（arXiv abs 页，2026-11-05 提交，摘要经 arXiv API 实抓 2026-11-10）"
    accessed: "2026-11-10"
  - url: https://github.com/chip-ai-agent/PCBRouteAgent
    title: "官方代码仓（GitHub API 实查 2026-11-10：22 stars，BSD-3-Clause，2026-11-06 创建并推送）"
    accessed: "2026-11-10"
---

# PCBRouteAgent：把 PCB 布线拆成"工程师式"全局规划 + 原生工具执行

> 来源：https://arxiv.org/abs/2611.08175 （v1 2026-11-05，摘要经 arXiv API 实抓 2026-11-10）；官方仓 https://github.com/chip-ai-agent/PCBRouteAgent 信号经 GitHub API 实查（2026-11-10）。本卡内容出自本次实抓摘要与仓库元数据，未读 PDF 全文。

## 是什么

多模态 PCB 自动布线 agent，模仿人类工程师"全局策略 + 局部执行"的分工：(1) **Global Routing Planner**——综合板卡图像与结构化电气/几何信息，产出连接拓扑、布线顺序、走廊与换层方案；(2) **Detailed Routing Executor**——把规划转成 KiCad 原生布线引擎可执行的指令，对未解失败做**有界局部恢复**；(3) 未解决失败以**结构化反馈**回传，驱动定向修订已接受的布线保持不动。官方口径：PCBWorld-Bench 247 块合成与真实板、四个测试分片，clean-pass 率 **100% / 94.9% / 100% / 40%**；三个真实板子集上超最佳基线 **13.9 / 36 / 10 个百分点**。官方仓 BSD-3-Clause 开源。

## 解决什么问题

布线要求板级连通性决策与几何执行在严格设计规则下协同，现有 agent 虽能调用原生布线工具，但复杂板上可靠性不足——要么全局规划粗糙、要么局部执行失败后无法恢复还污染已完成布线。PCBRouteAgent 把失败处理做成"有界恢复 + 结构化反馈 + 定向修订"，避免一次失败毁掉全局。

## 相比前方法优势

- **人机分工式架构**：全局规划（LLM 擅长的语义/策略层）与几何执行（KiCad 引擎擅长的规则层）各归其位，不让 LLM 直接碰几何；
- **失败可恢复且不扩散**：有界局部恢复限定改动范围，结构化反馈让修订有靶子、已接受布线不被破坏；
- **实测领先幅度大**：真实板上最高 +36pp clean-pass，且最难分片（D3-C 40%）如实暴露当前边界；
- **可跑**：官方仓 BSD-3，HF 25 赞是本周该线关注度最高的 agent 论文之一。

## 局限（如实标注）

- 未读 PDF 全文：基线阵容与消融（图像模态贡献多少、结构化反馈格式敏感性）以摘要口径为准；
- 最难分片 clean-pass 仅 40%，复杂真实板的可靠性边界明确存在；
- 官方仓创建于论文公开次日（11-06）、尚无 fork/社区验证，复现需自证；依赖 KiCad 生态，其他 EDA 工具链需自行适配。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 低）：EDA 自动化类赛题可直接以官方仓为起跑架（KiCad 任务栈现成），赛点有三：换板卡/换规则集的泛化、D3-C 类高难板 clean-pass 提升、失败恢复策略改进；三段架构（规划/执行/结构化失败反馈）可平移到 CAD、仿真器驱动等其他专业工具自动化赛题。
- **双创-文书与申报**（reuse_cost 低）：硬件设计工具智能化项目的实证引用：真实板 +36pp、官方开源、HF 25 赞三件套支撑"agent + 原生工具链"路线的落地叙事，亦可作为项目的对照基线或集成组件。
