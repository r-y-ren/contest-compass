# Google - The Gemma 4 Developer Agent Competition — 分析正文（competition.md）

> 全部事实基于 2026-09-24 kaggle CLI 2.2.4 OAuth 全站实抓（原件：`kb/inbox/gemma-4-dev-agent/gemma4-competition-pages.md`，抓取通道说明见同目录 .meta.yaml），滚动列表卡口径另注日期。引用不另标则为该实抓合集对应小节直抓。

## 一、赛题与官方动机

- 现状痛点（Description 原文）："Today's most capable coding agents rely on internet-connected models that require powerful commercial infrastructure"——高级 SWE 能力被锁在云 API 侧；小模型在多轮软件工程（大代码库导航、可靠修 bug/加 feature）上仍挣扎。
- 任务定义：**post-train Gemma 4**（微调 + 强化学习探索）构建自主 SWE agent，"independently navigate repositories and draft solutions"，把人类工程师解放到架构/逻辑/评审层。
- 定位：**SWE-bench 式的 agentic AI 风向标赛**，且是"开源小模型 agent 化"的官方信号事件（Gemma 4 31B QAT 量化版为指定基模）。

## 二、评测协议（Evaluation 页直抓）

1. 提交 `submission.zip`（Agent Config），根目录必须 `agent.yaml`；编译为 ADK agent 后评测。
2. 对每个 issue：agent 产出的 patch 应用到该 issue 的仓库快照，跑该 issue 的验证测试，PASS/FAIL。
3. **总得分 = 通过验证测试的仓库百分比**（补丁级二值，无部分分）。
4. 预算：**12 小时**跑全部任务（含沙箱 setup，不含 patch 验证）；可按任务设时限制（eval_config.yaml，可选）。
5. 测试集：约 120 任务、public/private 均分、私有仓库策展；public 榜基于 public split，private 定榜（Kaggle 常规）。

## 三、提交格式与 Harness 约束（Model Selection/Harness Rules 节直抓）

- **唯一基模**：`gemma-4-31b-it-qat-w4a16-ct`（W4A16 量化的 31B it 版），每个 agent/subagent 都必须用它；可配多个 PEFT LoRA adapter 按 agent 路由（如主 coder 用 main_lora、只读 analyzer 用 tool_lora）。
- Agent Config 结构：configs/sampling.yaml、prompts/*.md（!include 相对路径解析）、sub_agents/*.yaml（agent_tool 复合）、adapters/*、skills/*（SKILL.md 带 YAML frontmatter，脚本在持久 Docker 容器内执行、计入中央时间预算）。
- **9 个预定义工具**：run_command（/bin/bash -c @ /workspace）、submit_patch（git add -N . + git diff HEAD）、get_status、read_file（行号切片）、edit_file（old/new 串替换）、write_file、**get_code_neighbors**（符号调用/依赖图邻居）、**search_similar_code**（预计算嵌入 top-k 余弦检索）、get_code_subgraph（诱导子图）。
- 沙箱红线：禁止路径穿越（../、symlink）出 submission root；agent 只能用 harness 提供的工具或自定义 subagent。
- HARNESS_README.md（46KB）：swegemma / adk-submission / adk-eval-core 三库、双容器沙箱生命周期、上下文压缩、本地 CLI 评测命令——**需接受规则后下载**（实抓时未取得）。

## 四、数据资产（data-description 直抓）

- **129 个公开训练任务**：`tasks.jsonl`（instance_id 如 fastapi_11194；repo 为 fastapi/fastapi、Textualize/rich、psf/requests、encode/httpx；含 problem_statement/hints_text/patch/test_patch/base_commit/created_at）。
- snapshots/：129 个 tgz（base_commit 冻结、剪除后续提交，可在 /workspace 安全跑 git status/log/diff 不泄漏答案）。
- graphs/：NetworkX AST 调用/依赖图 JSON（multigraph、directed；node=全限定符号路径，含完整源码 text；edge=calls 等结构关系）——支撑图工具。
- embeddings/：每符号 256 维 float32 语义向量（npz）。
- wheels/：124 个离线 wheel（含历史依赖版本）；docker/：swebench-sandbox 镜像构建规格（Python 3.13 + imp/telnetlib 兼容 shim）；sandbox/setup.py 自动解析依赖、editable 安装、打 baseline commit。
- **数据管线（测试集同管线）**：Commit&PR Mining（同改 .py 与测试）→ Issue 关联提示抽取 → 去噪（排除机械重构/文档/LSC/无验收标准）→ 两阶段执行验证（Fail-to-Pass：无 fix 必须失败；Pass-to-Pass：有 fix 全绿）；测试集另要求 frontier model "接近通过或差一个 test case"的饱和筛选。

## 五、规则红线（rules/foundational-rules 直抓）

- 团队 ≤5；每日 1 次提交；2 个 final submissions；合并队伍的提交数上限 = 每日限额 × 已运行天数。
- Winner License：**Apache 2.0**（开源不限商用）；Competition Data：**Apache 2.0 商用可用**（"for any purpose, whether commercial or non-commercial"）。
- 外部数据/模型：默认允许，受 Reasonableness Standard（费用可及性）；AMLT 允许须持许可。
- 资格：18+，全球（Crimea/DNR/LNR/古巴/伊朗/朝鲜及美制裁对象除外）；单账号；获奖须交训练/推理代码与复现文档。
- 管辖：加州法（Santa Clara County 法院）。

## 六、榜单与社区观察（2026-09-24 实抓）

- 榜单：12 队上榜，最高 0.10（parthenos）、次 0.08（okacchi），多数 0.00-0.06——**开赛首日榜单近乎全零**，任务难度高、非 trivial 基线（sample submission）得分极低，头部提升空间大。
- 社区关键帖：
  - 742882（6 票）：swegemma harness 未随数据集放出，本地评测链路暂缺（无 host 回复）——对"先本地调通再提交"路线是实质障碍。
  - 742911（2 票）：数据问题——半数 embeddings 空文件 + 图缺 async 函数（影响 search_similar_code 与图工具有效性）。
  - 742815：官方入门帖 + Discord。
  - 742882-distill（14 票，0 回复）：外部 LLM 蒸馏（distillation）合规澄清请求——规则仅有 Reasonableness 条款可类推（大模型订阅可接受、超奖金成本数据集不合理），**蒸馏小模型是否在边界内官方未表态**。
- 热度滚动（列表卡口径，kb/raw/kaggle-list/）：10-05 1684 队 → 10-11 2422 队（+738/周）；paper 赛道 189 队。

## 七、参与价值分析（本框架视角，非官方信息）

- **方向契合**：autonomous coding agent 与 KB-2 技术卡的 agent 工程线（ADK config/多 agent/技能目录结构）高度同构——本赛提交格式（agent.yaml + prompts + sub_agents + skills + LoRA）就是一套可复用的 agent 编排模板。
- **可行性窗口**：终交 2026-12-02，报名 11-25 截止；无需本地 harness 也可基于公开 129 任务 + 代码图做离线提示工程；但 LoRA 后训练路线需要 GPU 预算，与免训练路线冲突——免训练路线的现实打法是**上下文工程 + 图工具编排 + 蒸馏合规未明的 prompt 级方案**。
- **方法论产出价值高**：pass@patch 二值指标 + 12h 预算约束下的 agent 预算分配（per-task time limit）、代码图检索增强、多 LoRA 路由都是可迁移到 workspace 快速攻防的工程模式（详见 patterns.md）。

## 八、与本库其他条目的关系

- 同为 Kaggle Google 系 agent 赛：kaggle-kaggriculture（仿真对抗、Bradley-Terry 定榜）与本赛（静态 benchmark、PASS/FAIL 定榜）构成两种 agentic 评测范式对照。
- paper 赛道与 kaggle-arc-prize-2026 的 Paper Track 同构（"文档化方法"的次赛道），但本赛 paper 有独立 $35k 奖池且要求原创未发表。
