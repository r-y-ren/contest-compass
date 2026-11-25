---
competition_id: devpost-aws-msp-ai-2026
last_verified: 2026-11-25
coverage: []
confidence: 低
sources:
  - "AWS MSP AI Hackathon 详情页直抓 https://aws-agentic-msp.devpost.com/（2026-11-25，WebFetch）"
  - "devpost 官方渲染列表快照 kb/raw/devpost-list/snapshot-20261125.md（2026-11-25）"
---

# AWS MSP AI Hackathon 模式库（patterns）

> 赛事进行中（2026-12-11 截止），无获奖作品可解构；本文件为模板起步态，评审标准为详情页四维原文（未经往届获奖数据验证）。

## 一、评审偏好（从章程/评委讲评/获奖名单可观察到的取向）

- 详情页评审四维原文：Technological Implementation / Design / Potential Impact / Innovation。（来源：官方详情页，信源等级：官网，2026-11-25 直抓）
- 可观察取向：AWS AI 服务族绑定（Bedrock/AgentCore/Strands/Quick/Kiro/Frontier Agents 至少一项且为核心组件）+ production-ready（部署 URL + 架构图/HLD 证明）——"能跑的企业级"而非"能演示的原型"。
- 特别奖按产品线分设：选型深度直接对应额外奖金入口。

## 二、方法论分布（获奖作品的方法/方案套路）

- 无数据（赛中，无历史届次可引；勿凭记忆补写往届）。

## 三、往届差异化点（什么样的作品拿到了最高奖）

- 无数据（首次届次信息未核实）。

## 四、反面观察（常见失分模式，若有依据）

- 无数据（无获奖记录可引）。风险预告维度（机制推断，非实测）：①AWS AI 服务仅表面集成（官方明文排除 "surface-level add-on"）；②未公开部署或无 HLD 证明 production-ready；③参赛组织无 MSP/APN 资质被取消资格——资格门槛是本赛最硬的失分点。

## 五、赛点检查表（评审标准 → 可执行检查项）

- [ ] 资格：参赛组织为 AWS MSP partner 或 APN 成员（个人达法定成年）——参战第一检查项。
- [ ] 窗口硬点：2026-12-11 12:00pm PST 前完成提交（距 2026-11-25 快照日 17 天）。
- [ ] 提交清单完整：赛道声明 + AWS 服务声明 + 可度量成效说明 + 部署 URL + 私有仓库（共享 testing@devpost.com / aws-msp@amazon.com）+ ~3 分钟 YouTube 演示 + 架构图 + HLD。
- [ ] 存量方案参赛时在提交期内做显著更新并留痕。

## 六、对本框架的启示

- 本库 devpost 线首个 toB 云生态绑定象限：Bedrock AgentCore / Strands Agents / AWS Frontier Agents 特别奖设置是 AWS 官方 agent 技术栈的权威风向标，可作库内 agent 基础设施作品线的选型参考（即使不参赛）。
- 若库内无 APN 资质渠道，本赛降级为模式库观察样本，不建议作为参战目标。
