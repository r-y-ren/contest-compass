---
id: gh-SakanaAI_AutoIllustrate
name: "AutoIllustrate：从方法段落到可编辑 draw.io 出版级插图的 LLM agent 流水线"
field: [LLM agents, 科研自动化, 图表生成]
directions: [创新创业大赛]
published: "2026-10-14"
maturity: demo
venue_tier: arXiv
reproducibility_level: high
signal:
  venue: GitHub
  stars: 29
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "申报书/商业计划书/路演 PPT 的技术路线图与系统架构图自动化：把『方法段落→可编辑矢量 draw.io 图』流水线化，六阶段（Plan→Render→Inspect→Compose→Enhance→Verify）带视觉审计-修复闭环；对比直接让模型生图的不可编辑位图（文字乱码、改一处全部重生成），本工具交付可编辑 XML、后期人工微调不动骨架，正合申报材料多轮改稿工作流；npm 一条命令接入，SakanaAI 官方出品（README 称其姊妹论文 The Agentic Scientist 的图示即由本工具生成）"
    reuse_cost: "低"
    open_source: "https://github.com/SakanaAI/AutoIllustrate（Apache-2.0，npm install -g autoillustrate）"
  - track: "黑客松-数据与算法"
    edge: "决赛演示环节的架构图/系统图快速产出：时间盒紧张的黑客松 final presentation 里省下画图时间写 demo；图文从同一份方法描述生成，天然一致，降低『图不符码』的答辩风险；light 模式约 10 分钟出图，--interactive 边改边看"
    reuse_cost: "低"
    open_source: "https://github.com/SakanaAI/AutoIllustrate（Apache-2.0）"
sources:
  - url: https://github.com/SakanaAI/AutoIllustrate
    title: "SakanaAI/AutoIllustrate: Generate publication-ready, editable draw.io figures for research papers"
    accessed: "2026-10-16"
  - url: https://arxiv.org/abs/2610.18933
    title: "The Agentic Scientist: Orchestrating Coding Agents for Automated Scientific (Co-)Discovery（2026-10-13 v1，88 页）"
    accessed: "2026-10-16"
---

# AutoIllustrate：让 LLM agent 画"可编辑"的论文插图，而不是生成一张位图

## 是什么

SakanaAI 2026-10-14 开源的 CLI 工具（Apache-2.0，TypeScript，`npm install -g autoillustrate`；2026-10-16 实抓 GitHub 页，仓库创建 2 天、1 commit）。输入论文方法章节/系统描述/草图，输出三层交付物：可编辑 `.drawio` 矢量图（XML，主交付物）、确定性导出的 `full_figure.png`（不经模型）、图像模型重绘的 `full_figure_enhanced.png` 风格化版。六阶段流水线 Plan → Render panels → Inspect → Compose → Enhance → Verify，第 3/6 阶段是审计-修复闭环（默认关，`--mode full` 开启；light 约 10 分钟 / medium 约 15 分钟 / full 约 30 分钟）。设计原则（README 原文）："LM sub-agents decide content, deterministic Python owns geometry, and the generative image model only restyles"——编码 agent 后端默认 Claude Code（经 `@roberttlange/headless`，可换其他），视觉审计用 gpt-6-astra，风格化用 gpt-image-2.5-sunburst（Gemini 系 nanobanana/gemini-3.1-pro 可选），需 OPENAI_API_KEY 或 GEMINI_API_KEY。依赖 Node ≥ 22、Python ≥ 3.10（自动建 venv）、draw.io desktop CLI 在 PATH；`autoillustrate doctor` 自检环境；支持 `--interactive`、`--resume-from`、目录批量输入，示例直接喂 `examples/ai_scientist_method.tex`。README 安全明示：工具会启动可执行任意命令的 agent 并继承环境密钥，建议容器/VM 内运行。配套论文 arXiv 2610.18933（The Agentic Scientist，2026-10-13 v1，88 页，Lange/Grillotti/Yamada/Charakorn/Ha）——"论文图示由本工具生成"为 README 单方说法，论文摘要页未提及本工具。

## 解决什么问题

论文、申报书、技术文档的示意图是纯手工耗时活：直接让 LLM 生图得到不可编辑位图（文字易乱码、改一处需整图重生成），手画 draw.io/Visio 动辄数小时且与文本脱节。AutoIllustrate 把"方法段落 → 可编辑矢量图"流水线化：内容/几何/风格三层分离保证图的**正确性**（确定性 Python 管几何）与**可维护性**（交付 XML，人工后期微调不推倒重来），审计-修复闭环自查文字溢出与元素重叠。

## 相比前方法优势

- **对比 LLM 直接生图**：产物是可编辑 XML 而非位图；几何由确定性代码而非生成模型决定，文字、连线、对齐可控；
- **对比模板库/手工绘制**：从自然语言方法描述直出成图，`--interactive` 边改边看，改稿迭代成本低一个量级；
- **对比一次性脚本拼 XML**：有 inspect/verify 的审计-修复回路（`--mode full`）与 doctor 环境自检，可中断续跑；
- **出品方背书**：SakanaAI 官方仓库，README 称 Agentic Scientist 论文（88 页，含 AI Scientist Nature 论文示例）的图示即由其生成——工具在真实科研产出里用过。

## 局限（如实标注）

- **极年轻**：2026-10-14 创建、1 commit、29 stars，无社区验证，CLI/配置随时可能破坏性变更；
- **强依赖闭源商业 API**（OpenAI/Gemini/Claude Code 后端），离线赛场不可用、有 API 费用；
- README 自警示：agent 可执行任意命令并继承宿主密钥，安全敏感环境必须容器隔离；
- "出版级"为工具自述、无第三方基准；擅长流程/架构/管线类示意图，**统计图表仍应走 matplotlib 等数据驱动工具**（本工具不是画数据图的）；
- draw.io desktop CLI 需预先安装，赛场/CI 环境要提前准备；生成质量高度依赖输入方法描述的清晰度。

## 如何用于比赛

1. **双创-文书与申报（主用）**：申报书/计划书/路演 PPT 的技术路线图、系统架构图批量生成与迭代——评审前多轮改稿只改 `.drawio` 不重画；团队工作流 npm 一条命令接入。reuse_cost 低：Node ≥ 22 + draw.io CLI + API key，离线答辩场需预生成图片。
2. **黑客松决赛演示**：final presentation 的架构图 10 分钟级产出，省下的时间写 demo；图与代码同源（都来自方法描述）规避"图不符码"追问。
3. **数模论文辅助（轻用）**：模型流程图/算法框图可用 light 模式起草再人工修；但注意其定位是示意图而非数据图，论文里的结果图仍走常规绘图栈。
