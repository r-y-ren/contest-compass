---
id: arxiv-2610.11482
name: "本地 LLM agent 数据工程实证：闭环工作台拉开工件级通过率 26.7-52 个百分点（量化 9B 模型 6.5GB 达 69.3%）"
field: [LLM agents, on-device inference, 数据工程评测]
directions: [创新创业大赛, 黑客松与数据竞赛]
published: "2026-10-08"
maturity: paper
venue_tier: arXiv
reproducibility_level: medium
signal:
  venue: "arXiv（26 页，under review 预印本，西班牙 Universitat d'Alacant 团队 5 人）+ Zenodo 数据集（DOI 10.5281/zenodo.21397610）"
  runnable: false
competition_fit:
  - track: "黑客松-数据与算法"
    edge: "本地/量化模型跑数据任务的可行性证据 + 工作台设计模板：闭环工作台（生成→确定性检查器→按暴露错误迭代）比 one-shot 通过率高 26.7-52.0 个百分点，15 个数据工作流任务与确定性检查器是现成的评测设计参照；量化 9B 模型 6.5GB 显存达 69.3% 通过率——『零 API 成本参赛』方案有了系统实证"
    reuse_cost: 中
    open_source: "基准数据集公开（Zenodo DOI 10.5281/zenodo.21397610）；工作台与检查器代码未释出，需按论文自建"
  - track: "双创-文书与申报"
    edge: "『数据不出域』章节的现成证据链：消费级 GPU 上 10 种本地配置的系统实证（规模/架构/量化/运行时/工具/失败模式，1500 次评分尝试），支撑隐私敏感数据工作（政务/医疗/企业内部）本地 agent 产品的可行性与成本论证"
    reuse_cost: 中
    open_source: "数据集公开（Zenodo），实证结论引用论文自报数字"
sources:
  - url: https://arxiv.org/abs/2610.11482
    title: "Evaluating Local Language Model Agents for Reproducible Data Engineering: An Empirical Software Engineering Study of Mobility Workflows（arXiv abs 页，v1 2026-10-08，Jorge García-Carrasco 等 5 人，Comments：Preprint under review，26 页，数据集链接指向 Zenodo）"
    accessed: "2026-10-13"
  - url: https://doi.org/10.5281/zenodo.21397610
    title: "基准数据集 DOI（abs 页 Comments 所附，2026-10-13 自 abs 页记录；未逐一验证数据集内容）"
    accessed: "2026-10-13"
---

# 本地 LLM agent 能否干好数据工程的活：一次 1500 次尝试的实证

> 来源：https://arxiv.org/abs/2610.11482 （v1 2026-10-08，Jorge García-Carrasco/Juan Trujillo 等 5 人，26 页 under review；abs 页 2026-10-13 实抓，Comments 附 Zenodo 数据集 DOI）。本卡内容出自摘要页，未读 PDF 全文。

## 是什么

实证软件工程研究：评估**本地部署的开源权重 LLM agent**能否产出正确且可复现的数据工程工件。自建基准含 **15 个移动性（mobility）工作流任务**，覆盖数据发现、连接器、运输数据流处理、语义增强、特征工程、校验、可视化、报表全链条；用**确定性检查器**评生成的脚本、表、结构化文件、图与报表（评的是完整工件而非文本回答）。10 种本地配置（模型规模/架构/量化/运行时/工具使用），one-shot 与闭环工作台两条件、每配置 5 次重复，共 **1500 次评分尝试**，全部在消费级 GPU 上完成。

## 解决什么问题

本地小模型 agent 的既有评测多停留在"文本回答质量"或孤立代码片段，没人系统回答：**不开 API、不用云模型，agent 能否把数据工程整条链的工件做对、做可复现？** 以及：闭环工作台（相对一次性生成）值多少分？

## 相比前方法优势

- **闭环收益量化到位**：>2B 参数的模型中，工作台条件把通过率拉高 **26.7-52.0 个百分点**——"让 agent 看见中间工件的错误再改"是最大单一杠杆；
- **工件级评测**：确定性检查器评真实产物（表/文件/图/报表），比"看起来对"的文本评测可信；
- **边缘可用性证据**：最强配置工件级成功率 **85.3%**；量化 9B 模型以约 **6.5GB 显存**达 69.3%——笔记本级硬件跑数据 agent 的下限有了具体数字；
- **失败模式成谱系**：规模/架构/量化/运行时/工具使用各维度的取舍有 1500 次尝试支撑。

## 局限（如实标注）

- **工作台与检查器代码未释出**：只有数据集公开（Zenodo），复现评测框架需按论文自建；
- under review 预印本无 venue，数字作者自报；
- 任务域绑定 mobility（交通/移动性数据），其他数据域需迁移任务集；
- "本地"上限明确：最强配置 85.3% 意味着约 15% 工件仍失败——关键业务不可无人值守；
- 摘要未列 10 种配置的具体模型名单与提示词/工具配置细节。

## 如何用于比赛（比赛映射展开）

- **黑客松-数据与算法**（reuse_cost 中）：预算全无的队伍按此方案搭"本地模型 + 闭环工作台"参赛管线：9B 量化模型 + 生成→检查→修循环，6.5GB 显存门槛意味着观众级笔记本可跑；其 15 任务基准可裁剪成队内训练集，提前磨 agent。
- **双创-文书与申报**（reuse_cost 中）：隐私敏感数据处理的申报项目引用其量化结论（69.3% @ 6.5GB、85.3% 上限）论证"本地化 agent 方案"的可行边界——有第三方实证背书而非自说自话。

**族内定位**：库内 agent 卡集中在云端 API agent；本卡占"本地/量化 agent × 数据工程"生态位，与 on-device inference field 对齐；数据集公开但代码缺失，maturity 如实标 paper。
