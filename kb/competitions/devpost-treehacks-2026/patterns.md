---
competition_id: devpost-treehacks-2026
last_verified: 2026-11-10
coverage:
  - 2026
confidence: 高
sources:
  - url: https://treehacks-2026.devpost.com/project-gallery
    title: "Devpost 项目画廊页（官方获奖名单唯一载体：24 个 CreativeWork JSON-LD 全量名单 + 24 条官方 tagline + 35 条赞助奖线全菜单——本文件主事实源；原件 kb/raw/devpost-treehacks-2026/gallery-20261107.html + winners-itemlist-20261107.json）"
    accessed: "2026-11-07"
  - url: https://devpost.com/software/raising-cane
    title: "Shepherd 项目页（大奖 1st，参赛队自述全文 + Built With 技术栈；原件 kb/raw/devpost-treehacks-2026/project-raising-cane-20261110.html）"
    accessed: "2026-11-10"
  - url: https://devpost.com/software/we-use-nix
    title: "Robosurge 项目页（大奖 2nd，参赛队自述全文；原件 kb/raw/devpost-treehacks-2026/project-we-use-nix-20261110.html）"
    accessed: "2026-11-10"
  - url: https://devpost.com/software/chromachord
    title: "ChromaChord 项目页（大奖 3rd，参赛队自述全文 + Built With 技术栈；原件 kb/raw/devpost-treehacks-2026/project-chromachord-20261110.html）"
    accessed: "2026-11-10"
  - url: https://treehacks-2026.devpost.com/
    title: "Devpost 赛站首页（评审三轴 / AI 署名条款 / 奖项结构——一手依据）"
    accessed: "2026-08-28"
  - url: https://ose.stanford.edu/news/treehacks-12-sam-altman-and-llamas
    title: "Stanford OSE 校方源（'audacious but feasible' 取向 / hack packs / 现场组队——赛事背景旁证）"
    accessed: "2026-08-28"
  - url: https://stanforddaily.com/2026/02/15/12th-annual-treehacks/
    title: "Stanford Daily 校媒（申请筛选规模——二手降级，仅存档）"
    accessed: "2026-08-28"
---

# TreeHacks 模式库（patterns）

> coverage 2026 一届；名单层已升级为**一手全量**（24 获奖项目 / 34 奖槽，官方 gallery JSON-LD，抓取 2026-11-07，数字口径与 winners/2026.md 一致）。方法论分布的依据：官方 tagline 24/24（gallery 页一手）+ 三大奖项目页深构 3/24（一手，2026-11-10）。旧版据二手校媒入库的 "HackOverflow 获 fetch.ai 奖 / ZoneZero 获 Ecopreneurship 奖" 经官方全量名单核对**不成立，已废弃**（见第四节废弃记录）。

## 一、评审偏好（从章程/评委讲评/获奖名单可观察到的取向）

- **一手（Devpost 赛站首页直抓，2026-08-28）**：评审三轴 Creativity / Technical Complexity / Social Impact；AI 工具使用须署名。
- **官方类目奖的实际授予（gallery 名单一手，2026-11-07）**：Most Creative=diffuji（扩散模型即时相机）、Most Impactful=Mira（AI 养老助手，兼 OpenAI 赛道）、Most Technically Complex=Freak in the Sheets（自研 LLVM 后端把代码编译到表格，兼 Human Capital fellowship）、Best Hardware=Sentinel（树莓派裸机 OS 从零 24h 写成）、Best Beginner=HeartStart（自主 CPR 机器人）。可观察取向：技术复杂度奖给了**编译器/系统层**而非 LLM wrapper；硬件奖给了**底层嵌入式自研**而非外设拼装。
- **大奖三档画像（项目页一手，2026-11-10）**：GP1 盲杖实时闭环（软硬结合）、GP2 手术机器人（软硬结合）、GP3 爵士和声助手（确定性理论核心 + AI 层）；三者全部挂公开 GitHub 仓库、全部是实时系统——主办方"可验证的完成度"文化。
- **校方源（OSE 直抓，2026-08-28）**：赛制鼓励 "audacious but feasible"；提供 "hack packs" 起步代码、现场配队——完成度文化的制度性保障。
- 机制差异（一手）：大奖是**硬件实物**（iPhone 17 Pro Max 等）而非现金；现金大顶在赞助商赛道（本届记录在案最大为 Human Capital $50k/人至多 $200k，Freak in the Sheets 兼得，gallery JSON-LD 2026-11-07）。

## 二、方法论分布（获奖作品的方法/方案套路）

**样本声明**：24/24 为官方获奖名单全量，但获奖者是全部参赛盘的筛选子集（校媒称 15,000+ 申请筛 1,000 入场，二手·降级），**频次为"获奖者内部占比"，不代表全体参赛盘**。分类依据为官方 tagline（gallery 页一手，2026-11-07），粗粒度、可多标签（同一项目可入多行）；技术栈实证仅 3/24（大奖项目页），其余 21 项未抓项目页、不作技术栈推断。各条目明细见 winners/2026.md。

| 模式 | 出现频次/占比（获奖者内） | 代表年份与条目 | 可迁移性 |
|---|---|---|---|
| 健康/照护/无障碍方向（Social Impact 轴主战场） | 7/24（29%），持有奖槽 11/34（32%） | 2026：Shepherd（GP1st）、Robosurge（GP2nd）、Mira（Most Impactful）、HeartStart（Best Beginner）、VisionOS、ShadowGuard、Bloom | 高：叙事天然占 Social Impact 轴；对口 OpenEvidence/Decagon 等健康赞助赛道 |
| 软硬结合/嵌入式/机器人 | 8/24（33%） | 2026：Shepherd、Robosurge、diffuji、Sentinel、HeartStart、Project Lend、GridVeda、aesthetica | 中-高：GP 前二皆此型；36h 需实体迭代，须配现场演示预案 |
| AI agent 自主执行/多智能体 | 4/24（17%） | 2026：Mobius（YC+Modal Sandbox）、ContainOS（OpenAI）、HireUp（YC）、Project Lend（Anthropic） | 高：纯软件 36h 可完成；但注意 6 条 agent 主题赞助奖线官方名单无获奖记录（见赛道分布注） |
| "垂直领域 × 知名产品"类比定位 | 3/24（13%），且 GP2/GP3 两者在内 | 2026：Robosurge "Cursor for surgery"、Tribune "GitHub for democracy"、Zeta "Grammarly for Math" | 高：一句话降评审理解成本，零技术成本 |
| 数据/工具链"卖铲子"基础设施 | 3/24（13%） | 2026：Mirage（合成 3D 世界模型训练数据，Modal）、ShotSpot（视频→训练数据，Modal+Bright Data）、Freak in the Sheets（LLVM→表格编译器，Most Technically Complex+Human Capital） | 中：差异化强、demo 门槛高 |
| 确定性核心 + AI 决策层（反纯 LLM wrapper） | 深构实证 1/3 大奖（ChromaChord）；类目奖旁证 2（Freak in the Sheets、Sentinel 均为非 LLM 系统层） | 2026：ChromaChord（GP3rd+Suno Best Musical Hack，项目页自陈回避低可解释性 LLM 做核心） | 高：评审疲劳于 wrapper 时的差异化模板，艺术/文科赛道同样适用 |
| 量化对比叙事（成本/规模一句话定价） | 3/24（13%） | 2026：Shepherd "~1/20 of existing devices"（tagline+项目页）、Project Lend "一个周末分发 50+ lbs 食物"（tagline）、Robosurge "10 人→1 人、OR 成本 $2,200/h"（项目页） | 高：零成本高杠杆叙事件 |
| 气候/工业/公共系统 | 3/24（13%） | 2026：GridVeda（电网边缘监测，Ecopreneurship）、Morro（气候工程 OS，Ecopreneurship）、ContainOS（野火多智能体，OpenAI） | 中：Ecopreneurship 类赛道对口 |

### 技术栈分布（实证仅 3/24——其余 21 项未抓项目页，禁止推断）

- Shepherd（来源：https://devpost.com/software/raising-cane ；抓取：2026-11-10；Built With）：Swift/SwiftUI + ARKit LiDAR 60fps + Vision/CoreML/DeepLabV3 + CoreBluetooth BLE + ESP32/FreeRTOS/C++——消费级传感器 + 嵌入式执行器。
- Robosurge（来源：https://devpost.com/software/we-use-nix ；抓取：2026-11-10）：自研逆运动学 + Intel RealSense/ArUco 12-DOF 标定 + SAM/YOLOv11 边缘部署 + GPT-5.2×Gemini Robotics-ER 双 LLM fusion + Quest 3 遥在 + TanStack/FastAPI/WebRTC + Nix 复现 + Lean 形式化验证。
- ChromaChord（来源：https://devpost.com/software/chromachord ；抓取：2026-11-10；Built With：claude/nextjs/perplexity/python/vercel）：24D chroma 向量 + 谐和图 + Perplexity Sonar 检索 + Claude（Agent SDK）生成。
- 三项共同 denominator（可迁移观察）：实时管线（3/3）、公开 GitHub 开源（3/3）、多模型 LLM 编排（2/3 有实证）、一句话类比定位（2/3）。

### 赛道分布（奖槽口径，与 winners/2026.md 一致）

- **总盘子**：24 项目 / 34 奖槽 = 大奖 3（1st/2nd/3rd 各 1）+ 主办方类目 5 + 赞助商赛道 26（来源：https://treehacks-2026.devpost.com/project-gallery ；抓取：2026-11-07）。
- **赞助商赛道 26 槽**：YC 5、OpenEvidence 3、OpenAI 3、Anthropic Human Flourishing 3、Modal Inference 3、Stanford Ecopreneurship 2、Decagon/Bright Data/Zoom x Render/Suno/Neo/Human Capital/Modal Sandbox 各 1。
- **赛道菜单 vs 获奖记录**：gallery 筛选菜单列出赞助奖线 35 条，官方名单仅记录其中 15 条有获奖者，**20 条无获奖记录**（Ecopreneurship"pain point"子线、Google Cloud AI、NVIDIA Edge AI、NVIDIA DGX Spark、Zoom Education、Anthropic Claude Agent SDK、Greylock、Visa、Fetch.ai、Runpod、Elastic、Cloudflare、HeyGen、Poke、Browserbase、Zingage、Graphite、Warp、Vercel、Perplexity）。**缺口约束**：官方名单是唯一载体（/winners 404），不能区分"无人得奖"与"名单未收录"（winners/2026.md 缺口声明），只能作"官方名单未记录"层级结论；若为前者，agent 基建类赞助线（Fetch.ai/Greylock/Elastic/Warp/Browserbase/Anthropic SDK 全部空缺）是低竞争度加选机会。

## 三、往届差异化点（什么样的作品拿到了最高奖）

- **GP1 Shepherd**：三轴各有一个硬证据点——Social Impact（视障出行 + 成本论 ~1/20）、Technical Complexity（亚 50ms 实时闭环横跨感知/CV/嵌入式/BLE 四域 + 双端 watchdog）、Creativity（电机本体触觉引导而非语音播报）（来源：https://devpost.com/software/raising-cane ；抓取：2026-11-10）。
- **GP2 Robosurge**：全场稀缺的 Lean 形式化验证（自陈 hackathon 规模罕见）+ 首触硬件的队伍 36h 完成软硬件全栈自研——复杂度轴的强差异（来源：https://devpost.com/software/we-use-nix ；抓取：2026-11-10）。
- **GP3 ChromaChord**：反同质化路线——确定性领域理论（24D chroma + 谐和图）当核心、LLM 只作决策增强层，附学术文献背书（来源：https://devpost.com/software/chromachord ；抓取：2026-11-10）。
- **共性（3/3）**：实时系统 + 公开开源仓库 + 三轴每轴一句可陈述证据；与 "audacious but feasible" 赛制文化咬合（OSE，2026-08-28）。
- 机制差异（一手）：大奖为硬件实物；现金大顶在赞助商赛道（Human Capital fellowship 本届记录在案最大）。

## 四、反面观察（常见失分模式，若有依据）

- **一手红线（Devpost Requirements 直抓，2026-08-28）**：hack 须 36 小时内完成（赛前成品搬运违规）；AI 工具使用必须署名；队 >5 人违规；须线下到场。资格红线：18+、在校/应届。
- **二手获奖信息废弃记录**：2026-08-28 轮据 Stanford Daily 二手入库的 "HackOverflow 获 fetch.ai 奖 / ZoneZero 获 Ecopreneurship 奖"，经官方 gallery 全量名单（抓取 2026-11-07）核对**不成立**——fetch.ai 奖线在官方名单中无获奖记录，Ecopreneurship 获奖者为 GridVeda/Morro。教训：二手获奖信息必须待官方名单核销后才可进入模式层。
- 二手观察（Daily，降级）：15,000+ 申请筛 1,000——入选门槛在申请材料叙事（申请评审标准原文未取得，标待核）。
- 官方名单 20/35 赞助奖线无获奖记录（缺口约束下不作"无人得奖"断言，见第二节赛道分布注）。

## 五、赛点检查表（评审标准 → 可执行检查项）

- [ ] 项目叙事同时覆盖三轴：创意点 / 技术复杂度点 / 社会影响点各一句话可陈述（GP1-3 共性）
- [ ] "垂直 × 已知产品"一句话类比定位打磨进 tagline（获奖盘 13% 显式使用，GP2/GP3 均有）
- [ ] 36 小时内可完成的最小可演示实时闭环（"audacious but feasible"）
- [ ] 公开 GitHub 仓库 + 复现路径（3/3 大奖项目均开源——评审可验证性）
- [ ] 量化对比叙事至少一条（成本 1/N、人力 10→1、分发 50 lbs 级别的硬数字）
- [ ] AI 工具使用清单与署名（合规硬条款）
- [ ] 硬件类项目：现场演示预案与故障兜底（录屏备份）
- [ ] 队伍 ≤5 人、全员到场；报名申请材料提早打磨（15k→1k 筛选，二手降级）
- [ ] 赞助商赛道加选（用其 API 可得额外奖项；优先官方名单未记录的空缺线作低竞争度加选——受名单缺口约束，作弱策略）

## 六、对本框架的启示（喂给 K-02 / 验收报告）

- 方向契合：AI 工具全放行（仅署名义务）+ 赞助奖线 35 条中 agent/edge/voice AI 密集——合规栈成本近零；36h 线下制对远程/自动化交付不友好，**须线下到场**，属"人工出席型"目标，快循环排期按 2027 届（约 2027-02）预留行程。
- 获奖模板（置信度已由"低"升"高"）：健康/照护/无障碍是本届最大获奖方向（29% 项目 / 32% 奖槽），软硬结合占 GP 前二；"确定性核心 + AI 决策层"与"形式化验证当评委钩子"是反同质化的高辨识度路线；hack packs 机制说明主办方重新手可及性——不必堆 SOTA。
- 方法论教训：对"奖金总额"必须区分现金/价值/宣传三口径再入库（见 meta）；对二手获奖名单必须等官方载体核销后才进模式层（本届 HackOverflow/ZoneZero 误判已废弃，见第四节）。
