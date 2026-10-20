---
id: gh-cryer_agent-eval
name: "agent-eval：LLM Agent 的统计门禁式 CI（McNemar+bootstrap 显著性、判官校准、对抗模拟用户、OTel 轨迹差分）"
field: [LLM agents, 评测与回归测试, 可观测性]
directions: [创新创业大赛]
published: "2026-10-15"
maturity: demo
venue_tier: other
reproducibility_level: high
signal:
  venue: GitHub
  stars: 10
  runnable: true
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "agent 类赛题作品的验收基建：把『我们测过了』升级为有统计口径的验收——基线 vs 候选两套件回放后用 McNemar 精确检验 + 配对 bootstrap 置信区间判定回归是否显著（pass^k 采样抗噪声），LLM judge 先对人工金标准集算 accuracy/Cohen's kappa/FPR/FNR 校准后才准上岗，规则断言兜底 judge；答辩被问『提升是不是噪声』时这套是现成防线，离线 stub 后端可零成本演示"
    reuse_cost: 低
    open_source: "https://github.com/cryer/agent-eval（MIT，pip install -e . 即用，含离线确定性 toy agent 示例与 GitHub Actions workflow）"
  - track: "双创-文书与申报"
    edge: "AI 产品研发流程成熟度的差异化证据：『prompt/模型版本/工具 schema/循环重构任何一层改动都过同一统计门禁 + OTel 轨迹差分定位行为变化点』可直接写进申报书的工程质量保障与迭代治理章节，对比同行『跑几个例子就说有效』的验收口径；判官校准机制还回应了『用 LLM 评 LLM 是否可信』的常见评审质疑"
    reuse_cost: 低
    open_source: "https://github.com/cryer/agent-eval（MIT；GitHub Actions gate 阻断显著回归的 exit code 2 机制可原样接入团队 CI）"
sources:
  - url: https://github.com/cryer/agent-eval
    title: "cryer/agent-eval 仓库页（API 元数据：10 stars/2026-10-15 创建/MIT/Python，2026-10-20 实查）"
    accessed: "2026-10-20"
  - url: https://raw.githubusercontent.com/cryer/agent-eval/main/README.md
    title: "README 全文（McNemar+bootstrap 统计门禁、pass^k 采样、判官校准指标、对抗模拟用户含提示泄漏攻击、SWE-bench 式 workspace 断言、限速退避）"
    accessed: "2026-10-20"
---

# agent-eval：给 LLM Agent 上统计门禁的 CI 工具

> 来源：https://github.com/cryer/agent-eval （README 与 GitHub API 元数据，2026-10-20 实抓）。Python/MIT，2026-10-15 创建，中英双语 README。

## 是什么

把"这次改动有没有让 agent 变差"变成 CI 里一个有统计依据的是/否门禁：任何改动（prompt、模型版本、工具 schema、agent 循环重构）后，回放评测套件对基线与候选两配置，跑 **McNemar 精确检验 + 配对 bootstrap 置信区间**，只有**显著**回归才阻断合并（GitHub Actions exit code 2），噪声不放行也不误伤。配套：每次运行落 OpenTelemetry 轨迹（LLM 调用、工具调用、token 成本、prompt 版本哈希）到 SQLite 并支持轨迹差分；双层断言（廉价确定性规则：输出内容/工具使用/回合与成本时延预算/工作区终态 + LLM-as-judge 语义层）；**判官先校准再上岗**（对人工标注金标准集测 accuracy/kappa/FPR/FNR）；带隐藏目标的模拟用户做多轮测试（含假意配合实钓系统提示词的对抗 persona，规则断言兜底防泄漏）；编码 agent 场景支持 repo 快照 fixture（SWE-bench FAIL_TO_PASS 模式）；并发 + 429/5xx 指数退避。

## 解决什么问题

agent 行为是概率性、多回合、工具介导的，单元测试覆盖不了"换模型/改工具后的静默退化"；而朴素 A/B 对比又分不清真回归与采样噪声。该工具把统计显著性检验、判官可信度管理、轨迹级归因打包成开箱即用的 CI 组件。

## 相比前方法优势

- **统计门禁而非拍脑袋阈值**：McNemar + bootstrap 只拦显著回归，`--samples` 与 pass^k 控制采样成本；
- **判官也被评**：judge 校准环节（对金标准集的 kappa/FPR/FNR）是多数 LLM 评测工具缺的一环；
- **断言双层兜底**：规则层挡住"宽松 judge/宽松模拟用户放走泄漏"的组合失效；
- **离线可演示**：stub 判官后端 + 确定性 toy agent 让全套流程零 API 成本跑通。

## 局限（如实标注）

- **信号弱且近乎停更**：10 stars，2026-10-15 创建，最后推送同日（2026-10-20 API 实查），无社区验证，作者背景未见披露；
- 判官校准依赖人工标注金标准集，赛期自建该集本身有成本；统计检验的样本量需求（多少 samples 才有功效）README 未给指导；
- OTel 轨迹与 SQLite 存储面向单机本地评测，多机并行聚合一层未见；
- 项目定位是工程工具而非方法创新，无论文背书，机制正确性需自验。

## 如何用于比赛（比赛映射展开）

1. **黑客松-数据与算法（agent 赛题验收）**：赛期把评测基建外包给 agent-eval——用例 yaml 定义 + 离线 stub 演示 + 真模型终验两档跑法；答辩 PPT 直接放"显著性检验 p 值 + 判官 kappa"两行数字，回应"提升是不是波动"与"judge 可信吗"两类必问题。reuse_cost 低：MIT、pip 即装、自带示例。
2. **双创-文书与申报（产品质量与迭代治理）**：技术方案里写"四层变更（prompt/模型/工具/循环）统一过统计门禁 + OTel 轨迹差分归因 + 判官先校准"的验收流水线，是 AI 产品研发成熟度的可核查证据；对比叙述可直接引用其 README 的痛点定义。reuse_cost 低：机制描述与 workflow 文件可转译进申报材料。
