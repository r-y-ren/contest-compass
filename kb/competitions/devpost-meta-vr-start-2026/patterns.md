---
competition_id: devpost-meta-vr-start-2026
last_verified: 2026-10-11
coverage: []
confidence: 中
sources:
  - url: https://start-developer-competition-26.devpost.com/rules
    title: "Complete Official Rules（webReader 直抓 2026-10-11）：评审标准/奖金表/设计原则/资格——快照 kb/raw/devpost-meta-vr-start-2026/2026-10-11-devpost-rules.md"
    accessed: "2026-10-11"
---

# Meta VR Start Developer Competition 2026 模式库（patterns）

> 本文件是 KB-1 条目的解构总结层。当届未放榜（2026-12-11 前后公布），本版基于**官方评审文件与 2025 届官方回顾口径**建库，无获奖样本——方法论分布节留空。

## 一、评审偏好（从章程可观察到的取向）

- **等权四维、无营销加分**（rules §7 直抓）：Innovation & Creativity / Experience Design / Technical Implementation / Polish & Presentation 各 25%——与传统黑客松"创意独大"不同，体验设计与完成度合计占 50%。
- **VR 原生性是硬审美**（rules §5 design principles 直抓）：airplane seat test（狭小空间可玩）、one bus stop test（短会话友好）、take it away test（"If you removed the headset, would your project still make sense? If so, you might be missing an opportunity"）——评审明确排斥"平屏移植品"。
- ** hands-first 强制**（rules §5）：全程手部交互是提交硬要求，控制器为主的体验在合规层就不过关。
- **AI 为核心的体验被官方单列奖励**：Best Agentic Interaction（$25,000）文案"AI isn't just a feature—it's a core part of how the world feels and responds"；同时 Polish & Presentation 明示"不要靠 AI 生成视频撑 pitch，展示真实 gameplay"。
- **社交/留存/无障碍/开场五分钟**各设 $25k 专项——产品留存导向（long-term engagement loop、onboarding）而非纯演示导向。
- 2025 届规模信号（首页官方回顾）：2,900+ 开发者 / 650+ 提交——提交率约 22%，参与热度高但产出门槛实际存在。
- 信源等级：官网。

## 二、方法论分布（获奖作品的方法/方案套路）

| 模式 | 出现频次/占比 | 代表年份与条目 | 可迁移性 |
|---|---|---|---|
| （当届未放榜，2025 届名单未抓取；无获奖样本，留待 winners 深构后回填） | — | — | — |

## 三、往届差异化点（什么样的作品拿到了最高奖）

- 2025 届获奖名单未实抓（首页仅官方回顾口径）。待补抓后回填本节。

## 四、反面观察（规则原文可证的失分点与合规红线）

- 资格红线（rules §3）：巴西、魁北克居民不可参赛；非 VR Start Program 成员提交即无效；未满 18 岁不可参赛。
- 原创性红线（rules §9）：曾获 Meta 直接资助的项目不可参赛；只用公开/Start 会员工具；作品不原创即取消资格。
- 提交红线（rules §4/§5）：每人/每组织仅一次提交；APK 未放 "Competition" release channel 或缺 Invite URL 形式上不完整；demo video ≥3 分钟或未公开可看即缺件；材料非英文（无字幕）有被筛掉风险。
- 体验红线（rules §5）：非 hands-first、违反 Meta 平台政策、薄包装（YouTube/ChatGPT port 无附加价值）在 Stage One pass/fail 即出局。
- pitch 红线（rules §7 评分准则）：AI 生成宣传视频撑门面会被 Polish & Presentation 维度反噬（官方明文不鼓励）。

## 五、赛点检查表（评审标准 → 可执行检查项）

- [ ] 参赛者 18+、非巴西/魁北克居民；提交时 VR Start Program 会员资格有效
- [ ] 项目原创、未获 Meta 直接资助、仅用公开/Start 会员工具（工具清单留痕备查）
- [ ] APK 部署到 Developer Dashboard "Competition" release channel + Invite URL 可访问（或 WebXR 链接）
- [ ] demo video <3 分钟、YouTube/Vimeo 公开、含真实 gameplay（非 AI 生成宣传片）
- [ ] 提交表单全项：tagline ≤140 字符 / description ≤500 词 / track / division / 手部交互描述 / 团队信息；全英文
- [ ] hands-first 全程可玩（无控制器依赖路径）
- [ ] airplane seat test：坐姿狭小空间 15 分钟无眩晕/无出界操作
- [ ] one bus stop test：5 分钟内完成一个完整会话环（含保存/恢复）
- [ ] take it away test：摘掉头显体验不成立（纯平屏功能占比较低）
- [ ] 四维自评：创新 25%（新颖机制）/ 体验设计 25%（交互流）/ 技术 25%（性能稳定性）/ 打磨 25%（视觉音效 UX 一致性）——每维有可演示证据

## 六、对本框架的启示（喂给 K-02 / 验收报告）

- **评审结构可直接套用**：等权四维 + Stage One pass/fail 是黑客松类作品 self-acceptance 清单的现成骨架（本条 patterns §五已派生）。
- **AI 奖项信号**：Meta 官方给"agentic/AI 原生体验"单列 $25k——与 KB-2 agent 技术卡方向契合：agent 编排能力可向"体验内 AI 角色"迁移，但须以 MR 交互形态落地（非聊天窗口式包装）。
- **三条 test 类验收原则**（airplane seat / bus stop / take it away）是"体验类作品"验收 checklist 的通用化模板，可复用到任意 XR/交互类战役的 acceptance.checklist。
- **窗口现实**：截止 2026-11-18，从零组建 VR Start 会员资格 + Horizon OS 开发栈的时间成本高，若参与需立即决策（约 5 周）；Adapted Division 允许重大更新现有作品，是降低冷启动成本的合法路径。
