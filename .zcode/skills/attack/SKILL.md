---
name: attack
description: 战役咨询与开战役入口壳（/attack）：咨询态只对话回复不落盘；显式确认开战役后建档并产三节方案书落战役 docs/briefs/。当用户要参赛参考、赛事推荐、开新战役时使用。
---

# attack：命令入口壳（注册适配）

本技能是 `.zcode/commands/attack.md` 命令的**同名斜杠入口壳**（客户端 `/` 菜单只认技能名——2026-10-10 评审补口）。薄壳不复制流程：

按 `.zcode/commands/attack.md` 流程执行（两态一闸门：咨询态零落盘 → 显式确认是否开始战役 → 建档并落战役 docs/briefs/）；编排细节调用 strategy-gen 技能（K-02）。

## 产物说明（收尾必做，用户审阅口径）

咨询态——**无产物（对话交付）**；落盘态——① `<战役根>/docs/briefs/<日期>-<赛事slug>-<方案slug>.md`；② `<战役根>/docs/briefs/<同slug>-grill-notes.md`；③ 禁用节护栏（doc_lint --project）检查结果声明。
