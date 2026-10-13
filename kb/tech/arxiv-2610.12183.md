---
id: arxiv-2610.12183
name: "AgenticBBO-Bench：LLM agent 黑箱优化跨域基准（五域统一有限预算协议 + 前沿挑战赛，LAMDA 官方 MIT 仓）"
field: [LLM agents, 黑箱优化, 基准评测]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-08"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: "arXiv（南京大学 LAMDA Chao Qian 组 11 人）+ GitHub（lamda-bbo/agentic-bbo，MIT，Python，API 实查 1 star，2026-10-12 仍有推送）"
  stars: 1
  runnable: true
competition_fit:
  - track: "Kaggle-竞赛"
    edge: "『LLM agent 做优化』管线的选型与诊断基准：统一有限预算协议横跨合成函数/HPO/数据库调优/芯片设计/分子设计五域；三条发现直接指导参赛架构——数值工具并非总有用、任务语义普遍有用而更具体的先验不可靠、数值优化器能有效吸收 agent 搜索轨迹的增益（→『agent 出方案、经典求解器收尾』的混合架构有实证背书）"
    reuse_cost: 低
    open_source: "github.com/lamda-bbo/agentic-bbo（MIT）"
  - track: "黑客松-数据与算法"
    edge: "现成的赛题骨架与评分协议：五任务前沿挑战（frontier challenge）+ 统一预算评测可直接改造成黑客松 agent 优化赛道的题目与评分规则；立项论据现成——agentic BBO 家族平均分五域全胜直接 LLM、四域胜最优数值优化器"
    reuse_cost: 低
    open_source: "github.com/lamda-bbo/agentic-bbo（MIT）"
sources:
  - url: https://arxiv.org/abs/2610.12183
    title: "A Closer Look at Agentic BBO: Benchmarking LLM Agents for Black-Box Optimization（arXiv abs 页，v1 2026-10-08，南京大学 LAMDA Ming Chen/Ke Xue/Chao Qian 等 11 人，无 Comments；摘要附官方仓链接）"
    accessed: "2026-10-13"
  - url: https://github.com/lamda-bbo/agentic-bbo
    title: "官方仓（GitHub API 实查：1 star，MIT License，Python，2026-10-06 创建、2026-10-12 推送——论文发布次日仍在更新）"
    accessed: "2026-10-13"
---

# AgenticBBO-Bench：给"LLM agent 跑优化"立一把统一的尺子

> 来源：https://arxiv.org/abs/2610.12183 （v1 2026-10-08，南京大学 LAMDA（机器学习与数据科学研究所）Chao Qian 组 11 人；abs 页 2026-10-13 实抓，附官方仓链接）+ https://github.com/lamda-bbo/agentic-bbo （API 实查 MIT/活跃）。本卡内容出自摘要页与仓库 API 元数据，未读 PDF 全文。

## 是什么

黑箱优化（BBO）出现在目标函数评估昂贵且次数受限的科学工程问题里（调参、调库、芯片、分子）。近期用 LLM agent 做 BBO——把任务语义、计算工具、优化器与反馈决策揉进搜索——势头很猛，但各家任务域与系统配置五花八门，结果不可比、单项设计的效果拆不出来。本文给出 **AgenticBBO-Bench**：跨合成函数、超参优化（HPO）、数据库调优、芯片设计、分子设计五域的统一**有限预算评测协议**，并系统研究三个塑造 agent 表现的因素：优化工具、任务信息与先验知识、LLM 在搜索中的角色。附五任务前沿挑战赛。

## 解决什么问题

"agent 优化"到底比直接问 LLM 强多少、比数值优化器强多少、强在哪一层——此前没有可比的答案。本基准把这个问题变成可在同一协议下回答的实验，并顺带把五个异域任务收进一套代码（MIT 仓已释出）。

## 相比前方法优势

- **五域统一协议**：家族平均分上 agentic BBO 五域全胜直接 LLM 方法、四域胜过最优数值优化器——"agent 有用"第一次有了跨域的受控证据；
- **因素分析可操作**：(a) 额外数值工具**并不**稳定提升表现（别无脑堆工具）；(b) 任务语义普遍有用，更具体的先验反而**不太可靠**（提示词里塞领域知识要克制）；(c) 数值优化器能有效吸收 agent 搜索轨迹的增益——agent 与经典求解器是接力关系而非替代关系；
- **团队与可持续性**：LAMDA 优化组（Chao Qian）出品，仓在论文发布次日仍在推送，基准大概率持续维护；
- **挑战赛现成**：五任务 frontier challenge 是天然的黑客松题目原型。

## 局限（如实标注）

- 仓库极新（1 star，2026-10-06 创建），文档完备度与可复跑性未经社区验证；
- v1 预印本无 venue，数字作者自报；
- "有限预算"的具体预算档位与对比方法名单需读全文——预算档选择会显著影响"谁胜谁"；
- 五域外的 BBO 场景（如真实实验科学）未覆盖；
- agent 框架与 LLM 骨干配置摘要未列全，结论对骨干模型的敏感性未知。

## 如何用于比赛（比赛映射展开）

- **Kaggle-竞赛**（reuse_cost 低）：HPO 域的任务与协议直接可用——用其基准校验自家"LLM 调参 agent"是否真的优于随机/贝叶斯搜索；三因素结论当架构清单用：少塞工具与具体先验、多给任务语义、让 agent 与数值优化器接力。
- **黑客松-数据与算法**（reuse_cost 低）：把 frontier challenge 的五任务裁剪成赛道题目，用其统一预算协议做评分（相同评估次数下比最终目标值）——评测公平性问题被论文预先解决，出题成本低。

**族内定位**：库内优化类卡集中在预测与调度；本卡占"agent×黑箱优化"评测位，与 SLA 卡（自动研究的 harness 架构）形成"架构-基准"互补。
