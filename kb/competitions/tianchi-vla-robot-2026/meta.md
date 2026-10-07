---
id: tianchi-vla-robot-2026
name: "蚂蚁灵波具身大模型挑战赛（2026 首届·天池 532514）"
tier: 编程/黑客松
directions:
  - 黑客松与数据竞赛
status: active
organizer: "发起：蚂蚁灵波科技（Robbyant）× 魔搭社区（ModelScope）× 阿里云天池；算力战略合作：AMD（Radeon Cloud + ROCm）；决赛真机平台：松灵 AgileX Cobot Magic 移动双臂（页面硬件说明）"
award_levels:
  - name: "一等奖"
    count_or_ratio: "1 名 × ¥80,000（税前）+ 证书 + 魔搭 5000 魔粒值/500h Notebook GPU"
  - name: "二等奖"
    count_or_ratio: "2 名 × ¥50,000（税前）+ 证书 + 3000 魔粒值/300h GPU"
  - name: "三等奖"
    count_or_ratio: "3 名 × ¥20,000（税前）+ 证书 + 2000 魔粒值/200h GPU"
  - name: "优秀奖"
    count_or_ratio: "若干名 × ¥5,000（税前）+ 证书 + 1000 魔粒值/100h GPU（名额未公布；按 ¥280K 总盘倒推约 8 名——推断，未证实）"
key_dates:
  launch:
    date: 2026-09-14
    verified: false
    note: "外滩大会见解论坛启动（量子位 2026-09-14 报道，媒体级）；官方页仅写'即日起'；任务包线索'09-11 启动'未获证实"
  registration_close:
    date: 2026-10-26
    verified: true
    note: "'即日起 - 10 月 26 日：选手报名 & 线上初赛'（官方赛程表原文）；与提交截止同日；侧栏倒计时 20d04h（2026-10-07 抓取）与该口径吻合——三处互证"
  preliminary_submit_close:
    date: 2026-10-26
    verified: true
    note: "10 月 26 日 24:00 初赛作品提交截止（官方赛程表原文）；此后锁定队成员"
  preliminary_review:
    date: 2026-10-27
    verified: true
    note: "初赛评审 10-27 ~ 11-05（官方赛程表原文；date 为区间起点）"
  finalists_announced:
    date: 2026-11-06
    verified: true
    note: "公示入围决赛名单（官方赛程表原文；名额数未载）"
  final:
    date: 2026-11-13
    verified: true
    note: "上海线下决赛·真机黑客马拉松 11-13 ~ 11-15 三天（官方页 + 量子位双源一致）；详细安排'另行通知'；主办方为入围队提供交通与住宿支持"
deliverables:
  - "线上初赛：基于 LingBot-VLA 2.0 在 RoboTwin 2.0 仿真任务上训练调优的模型与评测结果提交（提交格式/评测协议在官方钉钉交流群发布，公开页未载）"
  - "可选：真机创新 Demo（小红书创意征集，周边礼品非现金）"
  - "决赛（入围队）：线下真机黑客马拉松——基于主办方提供的真实机器人平台、数据集和算力，现场完成模型调优与真机部署"
ai_policy:
  summary: "未发现 AI 工具使用限制条款（本赛本身即开源 VLA 模型微调赛；核对维度：赛程/合规/IP，2026-10-07）。合规红线（原文）：严禁伪造评测结果（人工遥控/剪辑伪造/硬编码演示等）、刷分、破坏平台；训练数据仅限官方指定 RoboTwin 2.0 clean 数据集，禁用 randomized 数据训练；初赛结果仅用于筛选入围、不与决赛成绩累加。IP：参赛作品著作权归参赛团队，授予主办方免费非独占许可（期限活动期间+3 年，地域境内，用途限赛事公示/成果展示/科普/行业非商业传播）。平台层惯例（见前例 tianchi-cross-embodied-cognition-2026 核验）：赛事期间禁公开分享赛事数据/代码。"
  url: https://tianchi.aliyun.com/competition/entrance/532514/introduction
  checked: 2026-10-07
credibility: 交叉验证
last_verified: 2026-10-07
sources:
  - url: https://tianchi.aliyun.com/competition/entrance/532514/introduction
    title: "官方详情页 introduction 标签页（简介/赛程/参赛详情/奖金/评审/IP/资源链接全文；webReader 渲染 no_cache，last-modified 2026-10-06；快照 kb/raw/tianchi-vla-robot-2026/introduction-532514-20261007.md）"
    accessed: 2026-10-07
  - url: https://tianchi.aliyun.com/competition/entrance/532514/summary
    title: "官方详情页 summary 标签页（侧栏动态字段：Bonus ¥280,000 / Team 1360 / 报名倒计时 20d04h；curl 直抓为 34KB SPA 空壳已存档，正文靠渲染通道）"
    accessed: 2026-10-07
  - url: https://www.qbitai.com/2026/09/489105.html
    title: "量子位《首届蚂蚁灵波具身大模型挑战赛正式启动》（科技媒体报道级独立佐证：09-14 外滩大会启动/报名初赛至 10-26/决赛 11-13~15 上海/三方主办/决赛真机平台由主办方提供；快照 kb/raw/tianchi-vla-robot-2026/qbitai-489105-20261007-extract.md）"
    accessed: 2026-10-07
  - url: https://huggingface.co/robbyant/lingbot-vla-v2-6b
    title: "LingBot-VLA 2.0 权重页（公开非 gated，Apache-2.0，6.4B 参数/F32/25.5GB 分片，免登录可下载——框架兼容性核验）"
    accessed: 2026-10-07
  - url: https://github.com/Robbyant/lingbot-vla-v2
    title: "LingBot-VLA 2.0 代码仓库（公开，Apache-2.0，含 RoboTwin 2.0 post-training/仿真评估/真机部署全链路；官方基线 Clean 93.52%/Randomized 92.80%——框架兼容性核验）"
    accessed: 2026-10-07
---

# 蚂蚁灵波具身大模型挑战赛（天池 532514）— meta

## 概况（全部为 2026-10-07 实抓）

- 首届"蚂蚁灵波具身大模型挑战赛"，蚂蚁灵波科技 × 魔搭社区 × 阿里云天池联合发起（官方页原文；量子位报道互证），2026-09-14 于外滩大会见解论坛启动（媒体级）。
- 命题：以开源 **LingBot-VLA 2.0** 为统一技术基座，在 **RoboTwin 2.0** 仿真任务上做后训练与调优（线上初赛，纯仿真提交）→ 入围队赴上海参加三天**线下真机黑客马拉松**（2026-11-13 ~ 11-15，基于主办方提供的真实机器人平台/数据/算力现场调优与真机部署）。
- 赛制两段：线上初赛（即日起 ~ 10-26 24:00 提交，评审至 11-05）→ 11-06 公示入围名单 → 线下决赛。**初赛结果仅用于筛选、不与决赛成绩累加；决赛奖项以线下真机评测 + 官方评审为准**（原文）。
- 规模与门槛（抓取时点）：报名队伍 **1360 队**（侧栏 Team，2026-10-07）；每队最多 5 人（1 队长）、每人限 1 队；面向全球企业/高校/个人开发者，无学历职业限制；赛题方员工可排名不参与奖金。
- 奖金：总盘 **¥280,000**（侧栏 Bonus，两标签页一致）= 一等 1×80K + 二等 2×50K + 三等 3×20K + 优秀奖若干×5K（现金固定部分 240K，优秀奖倒推约 8 名）；另有 AMD 特别奖（RX 9000 系显卡）与小红书创意征集奖（周边），是否占现金盘页面未说明。附带魔搭魔粒值与 Notebook GPU 时长权益。

## 线索纠错（对任务包线索，2026-10-07 核）

- "系列入口 532514 已被此赛占用"：**成立**——532514 现解析为蚂蚁灵波具身大模型挑战赛（直抓证实）。注意与本库既有条目 `tianchi-cross-embodied-cognition-2026`（532508，专题"2026具身世界realworld挑战赛"，中国中检主办）为**不同赛事**：主办方、奖金、赛程均独立，勿混条。
- "¥280,000"：**成立**——侧栏 Bonus ¥280,000（summary/introduction 两页一致）；拆分见 award_levels。
- "9-11~11-15"：终点 **11-15 成立**（决赛 11-13~15）；起点 09-11 **未获证实**——官方仅"即日起"，媒体佐证 09-14 外滩大会启动（09-11 与 09-14 差 3 天，疑为线索误记或预热口径，记待核验）。
- "线下真机决赛"：**成立且细化**——11-13~15 上海真机黑客马拉松；**真机平台由主办方提供**（量子位原文"基于主办方提供的真实机器人平台、数据集和算力"），官方页另载"主办方将为入围团队提供交通与住宿支持"——参赛队无需自带机械臂。

## 框架兼容性备注（LingBot-VLA 2.0 开源可本地跑核验，2026-10-07）

- **权重开源可下载**：HuggingFace `robbyant/lingbot-vla-v2-6b` 公开、非 gated、免登录直下（Apache-2.0；6.4B 参数，F32 分片 25.5GB）；ModelScope 同步镜像（官方页资源节 + WebFetch 实核）。
- **代码开源**：GitHub `Robbyant/lingbot-vla-v2`（Apache-2.0，999 stars/28 commits，实核）——post-training 代码（RoboTwin 2.0 50 任务训练配置，Muon/Distributed Muon/AdamW）、RoboTwin 仿真评估一键脚本、真机部署接口（`deploy.lingbot_vla_v2_policy`；RTX 4090D 单次推理约 130ms/10 步去噪）。
- **仿真环境开源**：RoboTwin 2.0（robotwin-platform.github.io）；初赛指定训练数据 = HF `TianxingChen/RoboTwin2.0` 的 clean 子集（**禁用 randomized 数据训练**，原文红线）。
- **官方基线**：发布权重 RoboTwin Clean 93.52% / Randomized 92.80%（仓库 README）。
- **结论：无真机可完整参赛（仿真参赛成立）**——线上初赛为纯仿真评测，无机械臂要求；本地复现/微调的实际门槛是 **GPU 算力**（推理 4090 级单卡可跑；6.4B VLA 后训练需多卡或云算力）。免费通道：AMD Radeon Cloud 专项算力（约 200 张 GPU，2026-09-15 14:00 ~ 10-26 20:00，按队先到先得自愿申请，ROCm 栈绑定）。

## 物理约束判断（build-or-skip 关键字段，2026-10-07 判）

- **线上初赛：无机械臂硬件要求**——RoboTwin 2.0 仿真环境与数据全开源可本地部署；本队无机械臂**不构成参与障碍**（与任务包"真机赛通常限入围队或需硬件"的保守假设相反，此处须如实修正）。
- **线下决赛：硬件壁垒不存在**——真机平台由主办方现场提供（双源：官方页交通住宿支持条款 + 量子位"主办方提供的真实机器人平台"原文）；约束为**入围队人工到场上海 11-13~15 三天**。
- 实际门槛排序：GPU 算力（微调 6.4B）> 现场出席决赛 > 机器人硬件（不构成门槛）。是否参赛由 decide 阶段裁决；本条仅记录约束事实与证据。

## 数据缺口（2026-10-07）

- 初赛提交格式/评测协议/官方数据下载地址——在官方钉钉交流群发布，公开页未载（未入群，无法核）。
- 优秀奖名额数（"若干"）；入围决赛名额数；报名确切开放日——页面未载。
- AMD 算力申请审核标准与配额细则——页面仅载先到先得口径。

## 待核验清单

- [ ] 报名开放日口径（官方"即日起" vs 媒体 09-14 启动 vs 任务包线索 09-11）。
- [ ] 优秀奖名额数与 ¥280K 全额发放口径（AMD 特别奖/小红书征集奖是否占现金盘未说明）。
- [ ] 入围决赛名额数（11-06 公示时回填）。
- [ ] 初赛提交格式与评测协议（下钻官方交流群公告或后续页面更新）。
- [ ] 决赛详细安排公布后更新 final 节点（官方"另行通知"）。

## 重验记录

- **2026-10-07 首建**：no_cache 渲染双标签页（summary + introduction）侧栏字段一致无串页（Bonus ¥280,000 / Team 1360 / 倒计时 20d04h，页面 last-modified 2026-10-06 20:02:19）；量子位报道 + HF/GitHub 仓库三向佐证。倒计时 20d04h 与"10-26 24:00 截止"口径吻合（±数小时，时区/抓取时刻解释范围内）。
