---
id: gh-SakanaAI_AutoIllustrate
name: "AutoIllustrate：LLM agent 流水线把方法章节变成可编辑 draw.io 论文级插图（AI Scientist-v3 正式采用）"
field: [LLM agents, scientific figure generation, document automation]
directions: [创新创业大赛]
published: "2026-10-14"
maturity: product
venue_tier: industry
reproducibility_level: high
signal:
  venue: "GitHub SakanaAI/AutoIllustrate（API 实查 2026-10-16：27 stars/2 forks，Apache-2.0，TypeScript，2026-10-14 创建，次日仍在推送；npm 全局分发）"
  stars: 27
  runnable: true
competition_fit:
  - track: "双创-文书与申报"
    edge: "申报书/答辩 PPT/结题材料的系统架构图产线：把方法描述文本喂进去直接得到**可继续编辑的矢量 .drawio**（生成模型只碰最后的重绘风格层，版式与内容仍是确定性 XML）——图能改是申报材料迭代的刚需，纯文生图工具给不了；已用于 AI Scientist-v3（Nature 刊文团队）论文插图的背书可写入技术选型依据"
    reuse_cost: 低
    open_source: "github.com/SakanaAI/AutoIllustrate（Apache-2.0；npm install -g autoillustrate，自带 doctor 环境自检）"
  - track: "黑客松-数据与算法"
    edge: "路演/demo 环节的架构图快速产出：light 档约 10 分钟出草稿图，单面板/最多三面板自动布局；产物含确定性导出 PNG + 增强风格 PNG 双版本，评审材料与现场展示两用"
    reuse_cost: 低
    open_source: "同上；依赖 draw.io desktop CLI + Node>=22 + coding agent（默认 Claude Code）+ OPENAI_API_KEY"
sources:
  - url: https://github.com/SakanaAI/AutoIllustrate
    title: "官方仓库 README 与 GitHub API 元数据（2026-10-16 实抓：27 stars/Apache-2.0/TypeScript；两步法、三种模式时长、产物三文件、依赖与安全注意事项均出自本次抓取）"
    accessed: "2026-10-16"
---

# AutoIllustrate：论文级插图的可编辑产线，不是又一张文生图

> 来源：https://github.com/SakanaAI/AutoIllustrate （README + GitHub API，2026-10-16 实抓）。本卡内容全部出自本次抓取的 README，未读源码全文。

## 是什么

SakanaAI 出的命令行工具：输入一段**方法简述**（论文章节、系统描述或口头草图），产出一幅论文级学术插图。两步走——先由 agent 流水线生成**可编辑的矢量 .drawio 文件**（本质是 XML），再用图像生成模型（默认 gpt-image-2.5-sunburst）做最终视觉增强出 .png。已实际用于 AI Scientist-v3（SakanaAI）的论文插图生成。

## 解决什么问题

学术/申报场景的示意图痛点：文生图模型输出不可编辑、文字常错、改版式要重抽；手画 draw.io 又太耗时。本工具把"内容编排"交给编码 agent（生成可改的 XML 源），把"好不好看"留给风格化模型——**可编辑性与美观解耦**，产物随时回 draw.io 手工调整。

## 相比前方法优势

- **产物是工程资产而非一次成图**：每次运行落 `runs/<时间戳>/figures/` 三个文件——full_figure.drawio（可编辑源）、full_figure.png（确定性导出，无模型参与）、full_figure_enhanced.png（风格增强版）；
- **三档时长可控**：light 约 10 分钟草稿 / medium 约 15 分钟（默认）/ full 约 30 分钟全审计环，适配从黑客松到 camera-ready 的不同时间预算；
- **质量审计内建**：视觉审计（VLM 审查）与重绘风格层分离，增强模型可换（nanobanana/nanobanana-pro 等 Gemini 后端）；
- **工程化成色**：npm 全局分发、`autoillustrate doctor` 环境自检、首跑自建缓存 venv、无头 Linux 与多 coding agent 后端有专门文档。

## 局限（如实标注）

- **安全注意（官方明示）**：工具会启动可执行任意命令、继承环境变量（含 API key）的 coding agent，输入文档会引导 agent 行为——只对可信文档使用，建议容器/VM 内运行，runs 目录日志可能回显文档内容；
- 依赖较重：draw.io desktop CLI、Node>=22、默认需 Claude Code 在 PATH，且默认要 OPENAI_API_KEY（审计与风格化）；单机非交互环境下依赖链失败点不少；
- 仓库创建仅 2 天（27 stars），多面板并行等能力的稳定性尚无社区验证；
- 单图耗时 10-30 分钟，不适合批量成百张图的场景。

## 如何用于比赛（比赛映射展开）

- **双创-文书与申报**（reuse_cost 低）：项目申报书、答辩 PPT 的技术路线图/系统架构图产线——把自家方法描述喂入即可得可编辑底稿，迭代版本时改 .drawio 而非重抽；"生成模型只碰风格层"保证图的内容与文字可控可校，这是它区别于文生图的核心申报价值。
- **黑客松-数据与算法**（reuse_cost 低）：路演前用 light 档 10 分钟出架构图草稿；确定性 PNG 导出可作为备份展示物（不依赖生成模型成功与否）。

**族内定位**：库内暂无"图表/文书自动生成"位卡；本卡与 agent 安全类卡（如 AgentSafeEvo）构成对照——一个管 agent 产出物可信，一个管 agent 产出物可用。其官方明示的 agent 执行安全注意恰好是安全类卡的现实注脚。
