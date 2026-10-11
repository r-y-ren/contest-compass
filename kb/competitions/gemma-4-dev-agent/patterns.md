---
competition_id: gemma-4-dev-agent
last_verified: 2026-10-11
coverage: []
confidence: 中
sources:
  - url: https://www.kaggle.com/competitions/gemma-4-developer-agent
    title: "全站实抓（kaggle CLI OAuth 2026-09-24）：Evaluation/rules/Prizes/data-description/榜单/社区帖——原件 kb/inbox/gemma-4-dev-agent/gemma4-competition-pages.md"
    accessed: "2026-09-24"
---

# Google - The Gemma 4 Developer Agent Competition 模式库（patterns）

> 本文件是 KB-1 条目的解构总结层：供 K-02 赛道评分（"获奖模式重叠"维度）、验收分析报告与赛点检查表消费。
> 当届未放榜（终交 2026-12-02），本版基于**官方评测文件与开赛初期榜单/社区观察**建库，无获奖样本——方法论分布节留空，宁缺毋滥。

## 一、评审偏好（从章程/评测文件可观察到的取向）

- **客观指标压倒一切**（Evaluation 页直抓）：得分 = 通过验证测试的仓库百分比，PASS/FAIL 无部分分、无评委主观分——评审偏好完全可由 public 129 任务离线复现（test_patch 随训练集公开）。
- **双阶段验证即质量定义**：数据管线 Fail-to-Pass/Pass-to-Pass（data-description 直抓）——"解得对"被定义为**测试从红变绿且全绿**，与 SWE-bench Verified 同构。
- **paper 赛道主题偏好**（Prizes 节直抓）：PEFT/RL 调优、代码图生成与嵌入、新任务与基准、大图推理四类主题——官方明确把"代码结构理解（图/嵌入）"列为奖励方向，与本赛数据资产（AST 图+256 维嵌入）强绑定。
- 信源等级：官网（kaggle CLI OAuth 直抓）。

## 二、方法论分布（获奖作品的方法/方案套路）

| 模式 | 出现频次/占比 | 代表年份与条目 | 可迁移性 |
|---|---|---|---|
| （当届未放榜，无获奖样本；下表留待 winners 深构后回填） | — | — | — |

注：2026-09-24 榜单 12 队、最高 0.10——开赛初期样本无代表性，禁止据早期榜单推"获奖模式"。

## 三、往届差异化点（什么样的作品拿到了最高奖）

- 首届在赛（官方页面未见历届记录，待核），无往届名单可考。官方信号（abstract/Prizes）指向的"高分行区间"特征：小型开源模型（31B QAT）在受限 12h 预算内的**补丁通过率**——预算分配与代码库导航效率是硬约束下的分水岭（推断自评测条款，非获奖实证）。

## 四、反面观察（规则原文可证的失分点与合规红线）

- 提交格式硬伤即零分风险：agent.yaml 不在 zip 根目录、引用不存在的 adapter、路径穿越（../、symlink）出 submission root（Harness Rules 直抓沙箱红线）。
- 基模替换违规：仅允许 gemma-4-31b-it-qat-w4a16-ct，任何 agent/subagent 换基模即违规（Model Selection 直抓 "You *must* choose this model for every agent and subagent"）。
- 每日 1 次提交限额（rules §2 直抓）：调试性提交成本极高，需离线验证成熟再提交。
- 12 小时全局预算超时：跑不完所有任务 = 未跑任务按 0 计（PASS/FAIL 未运行即 FAIL）。
- 私下跨队共享代码禁令（foundational-rules §6 直抓）；公开分享代码即视为 Apache 2.0 授权。
- 外部 LLM 蒸馏边界未明（社区帖 742882-distill 14 票 0 回复）：蒸馏前必须向 host 书面确认，否则存在获奖后取消风险（Reasonableness Standard 类推不足以自保）。

## 五、赛点检查表（评审标准 → 可执行检查项）

- [ ] agent.yaml 位于 submission.zip 根目录，ADK 规范编译通过（本地用公开 sample_submission 结构对照）
- [ ] 全部 agent/subagent 的 base model = gemma-4-31b-it-qat-w4a16-ct
- [ ] LoRA adapter 目录名与 agent.yaml 引用逐一对应（adapter_config.json + adapter_model.safetensors 齐全）
- [ ] skills/ 每个目录有带 YAML frontmatter（name:）的 SKILL.md，脚本无路径穿越
- [ ] 12h 预算静态估算：任务数 × 平均耗时 + 沙箱 setup 余量 ≤ 12h；可选 eval_config.yaml 按任务难度分配
- [ ] public 129 任务本地回归：自建 pytest 复跑 test_patch 的 pass 率作为提交前唯一 gate
- [ ] 提交前每日限额核算（1 次/日，合并队提交数 ≤ 日限 × 运行天数）
- [ ] 若用外部 LLM/蒸馏：留存许可与费用证据，满足 Reasonableness Standard（超奖金成本即红线）
- [ ] 获奖预案：训练/推理代码 + 复现文档（Apache 2.0 兼容性检查）

## 六、对本框架的启示（喂给 K-02 / 验收报告）

- **提交格式即模板**：ADK agent config（agent.yaml + prompts + sub_agents + skills + LoRA 路由）是 Google 官方背书的 agent 编排范式，可直接映射到本框架 workspace 快速攻防的 agent 工程栈。
- **代码图工具三件套**（get_code_neighbors / search_similar_code / get_code_subgraph）是"结构化检索增强编码"的官方实例，与 KB-2 代码理解技术卡互补。
- **预算约束 agent 评测**（12h 全局 + per-task 分配）是本框架验收（acceptance.checklist）可借鉴的工程化评估维度。
- paper 赛道四主题（尤其"代码图/嵌入"与"图推理"）指明官方后续投入方向，可作为技术卡选题风向标。
