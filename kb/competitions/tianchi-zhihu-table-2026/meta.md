---
id: tianchi-zhihu-table-2026
name: "知乎知学堂大模型挑战赛：大模型复杂表格识别与内容理解（天池 532510，长期赛·季度赛季制）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "知乎知学堂（联系邮箱 shaoyihui@zhihu.com；知乎知学堂《AI大模型应用开发实战营》课程为配套学习资源）；阿里云天池平台提供技术支持（页面声明'赛事由第三方主办，本平台仅提供技术支持'）"
award_levels:
  - name: 一等奖
    count_or_ratio: "每季度 1 名 × ¥6,000"
    note: "奖金于每季度比赛结束后次月发放（详情页奖项表原文）"
  - name: 二等奖
    count_or_ratio: "每季度 2 名 × ¥4,000"
  - name: 三等奖
    count_or_ratio: "每季度 3 名 × ¥2,000"
    note: "季度奖金池合计 ¥20,000，与列表卡'奖金 ¥20000'口径一致"
key_dates:
  competition_start:
    date: "2026-08-07"
    verified: true
    note: "官方列表卡'比赛时间 2026.08.07~2026.12.31'（kb/raw/tianchi-list/snapshot-20261010.md，官网快照）；详情页未单列开始日期，单一官方信源"
  season_cadence:
    date: "每季度为一个赛季"
    verified: true
    note: "详情页 intro 正文：'本次赛事为长期赛……每季度为一个赛季，设置赛季排行榜'；赛季具体起止日（Q3/Q4 边界）官方未公布"
  registration_close:
    date: "约 2026-12-31"
    verified: true
    note: "双源互证（2026-10-13）：详情页报名倒计时 Sign up remaining: 80 days 05 hours（no_cache 口径，80 天后≈2027-01-01，时区余量）+ 官方列表卡比赛时间终点 2026.12.31。注：同日缓存态抓取显示 18 days（Team 568），与 10-10 列表卡 Team 1285 不单调，判定为陈旧缓存残留，不采信"
  competition_end:
    date: "2026-12-31"
    verified: true
    note: "官方列表卡'比赛时间 2026.08.07~2026.12.31'；详情页倒计时 80 天口径互证"
deliverables:
  - "submission.xlsx：id + answer 两列，每题一行；structure 题 answer 为 JSON 字符串（row_count/col_count/cells，cells 含 row/col/row_span/col_span/text）；extract 题 answer 为与原文完全一致的文本；thinking 题 answer 为计算结果字符串；无法回答置空字符串（information 页直抓）"
ai_policy:
  summary: "AI/大模型是赛题前提而非违规项：强制仅使用阿里云通义千问（Qwen）系列模型（百炼 API / PAI 等阿里云云产品），严禁非阿里云来源模型、第三方闭源 API、本地私有化部署开源模型；允许叠加 OCR/版面分析/表格检测/规则后处理/数值校验模块但均须阿里云来源；提交答案必须程序自动生成，禁止人工检查隐藏测试集后手填答案、禁止利用文件名/页码样式/来源网站线索猜答案（intro 与 information 页原文）。未发现'限制 AI 生成参赛文本'类条款（本赛即大模型应用赛）。"
  url: "https://tianchi.aliyun.com/competition/entrance/532510/introduction"
  checked: "2026-10-13"
credibility: 官网
last_verified: "2026-10-13"
sources:
  - url: https://tianchi.aliyun.com/competition/entrance/532510/introduction
    title: "报名页详情（webReader 渲染，缓存态+no_cache 各一次；赛制：长期赛/季度赛季/个人赛不可组队、Qwen 强制约束、参赛对象、季度奖项表、知学堂课程前置、联系邮箱）。快照 kb/raw/tianchi-zhihu-table-2026/detail-intro-20261013.md"
    accessed: "2026-10-13"
  - url: https://tianchi.aliyun.com/competition/entrance/532510/information
    title: "赛题与数据页（webReader 渲染 no_cache；三类题型 structure/extract/thinking 定义、数据字段 tests.xlsx、submission.xlsx 提交规范、得分=正确数/总数×100、模型与算力约束、待定事项清单）。快照 kb/raw/tianchi-zhihu-table-2026/detail-information-20261013.md"
    accessed: "2026-10-13"
  - url: https://tianchi.aliyun.com/competition/
    title: "天池竞赛列表快照（browser-use 预抓，kb/raw/tianchi-list/snapshot-20261010.md）：532510 卡片'知乎知学堂大模型挑战赛：大模型复杂表格识别与内容理解'、奖金 ¥20000、团队数 1285、比赛时间 2026.08.07~2026.12.31、#自然语言处理 #大语言模型（列表卡口径）"
    accessed: "2026-10-10"
---

# 知乎知学堂大模型挑战赛：大模型复杂表格识别与内容理解（天池 532510） — meta

## 概况（2026-10-13 详情页实抓）

- **赛事形态**：AI大模型赛；**长期赛 + 季度赛季制**——报名成功后即可下载题目和测试集参赛，每季度为一个赛季，设赛季排行榜，季度奖金于赛季结束后次月发放。[intro]
- **奖金**：¥20,000/季度（一等奖 1×¥6,000、二等奖 2×¥4,000、三等奖 3×¥2,000）。[intro 奖项表]
- **个人赛**：**不允许多人组队**（intro 原文口径），面向全社会开放；阿里云员工与主办方员工可参赛可排名但**不参与评奖**。
- **体量**：详情页 Team 1317（2026-10-13 no_cache）；官方列表卡团队数 1285（2026-10-10 口径）。
- **主办方**：知乎知学堂（联系邮箱 shaoyihui@zhihu.com）；配套学习资源为知乎知学堂《AI大模型应用开发实战营》课程，页面口径"选手需观看完课程后再行参赛"。[intro]

## 赛题与数据（本赛核心事实）

- **任务**：识别图片/PDF 中的复杂表格并转结构化数据。三类题型：① **structure** 表格结构恢复（输出 JSON：row_count/col_count/cells，含 row/col/row_span/col_span/text）；② **extract** 内容提取（按自然语言问题提取单元格/区域，答案须与原文完全一致）；③ **thinking** 内容推理（加总/求差/比例/筛选/排序/格式归一）。[information]
- **表格复杂性设定**：跨页表格、合并单元格、多级表头、弱边框线、页眉页脚干扰、脚注混入、旋转扫描、单位变化、字段继承；来源覆盖财务报表/销售报告/采购对账单/质检报告/物流结算单/统计公报。[information]
- **数据**：文件目录（图片/PDF）+ `tests.xlsx`（id/file_name/question_type/question/table_hint/answer_format）；数据包 16MB（报名前脱敏显示 `m****n.zip`）。[information]
- **评分**：自动评分，最终得分 = 正确题数/总题数 × 100（一位小数），structure 按 JSON 结构比对、extract/thinking 按文本完全匹配。[information]

## 模型与算力约束（参赛前提）

- **仅限阿里云通义千问（Qwen）系列模型**：模型调用须来自阿里云百炼 API 或 PAI 等阿里云云产品；**严禁**非阿里云来源模型、第三方闭源 API、本地私有化部署的开源模型。[intro/information 双页一致]
- 允许叠加 OCR、版面分析、表格检测、规则后处理、数值校验模块，但所用模型与算力均须阿里云来源。[intro]
- 答案必须**程序自动生成**；严禁人工检查隐藏测试集后手动填答案、严禁利用文件名/页码样式/来源网站线索猜答案；提交须严格遵循 Excel 规范否则无法评分。[intro]
- 福利：在校大学生通过大学生认证可领 300 元阿里云代金券；可参与"百度百炼淘客宝"活动获额外资源（页面活动口径）。[information]

## 待定事项（官方明示"待定"，未发布）

- 单份文件处理时长上限、单道题推理成本上限、提交文件大小限制、**每日提交次数**、测评失败是否扣次数——官方口径"以官方后续说明为准"。[information]

## 与既有条目的关系

- 与 `tianchi-ant-lingbot-vla-2026`（具身 VLA）、`tianchi-cross-embodied-cognition-2026`（跨本体具身）无关联，本赛为文档智能/多模态表格理解方向。
- 表格识别方向与 `kb/tech/` 既有 MinerU 相关卡（如 heywhale-mineru-mdic2026 条目所在的文档解析线条）存在方法论重叠：本赛限 Qwen+阿里云算力，MinerU 类自部署管线不可直接用（模型/工具均须阿里云来源），可作为版面分析思路参考但实现须替换为阿里云来源组件。

## 数据缺口与待核验

- [ ] **winners/ 未建**：长期赛进行中（本轮赛程至 2026-12-31，季度放榜节奏官方未公布），无任何获奖名单可抓。按 `award_levels` 前两级（一等奖 1 名、二等奖 2 名）待首个赛季榜单公示后补建。**核对的维度**：天池该赛排行榜页、官方 forum 公告——2026-10-13 均未见季度榜单公告入口。
- [ ] 赛季（Q3/Q4）具体起止日与各赛季独立榜单口径未公布（官方仅"每季度为一个赛季"）。
- [ ] "选手需观看完课程后再行参赛"（知学堂课程）是否为硬性报名门槛待核——页面为课程推广口径，未见报名系统层面的课程完成校验说明。
- [ ] 官方 forum/答疑帖未消费（详情页交流入口在登录墙内）。
- [ ] 评分对 structure 题的 JSON 比对细则（row_span/col_span 容差、文本归一化规则）页面未给出，待官方补充说明或 forum 口径。

## 重验记录

- **2026-10-29（滚动重验·官方列表卡）**：团队数 1285（10-10 快照口径）→ **1656**（+371/19 日）；窗口 2026.08.07~12.31、奖金 ¥20000、"立即报名"态均与既有口径一致，无漂移。列表层核验。（来源：kb/raw/tianchi-list/snapshot-20261029.md ；抓取日期：2026-10-29）
