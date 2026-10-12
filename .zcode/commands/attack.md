---
description: 战役开始前的咨询入口：咨询态只对话回复不落盘；显式确认开战役后建档并产三节方案书落战役 docs/briefs/
---

# /attack —— 战役咨询与开战役入口（两态一闸门）

用法：`/attack <赛事ID或方向描述> [--campaign <cid>]`（省略参数 = 询问建议）。

执行流程（编排细节见 `.zcode/skills/strategy-gen/SKILL.md`）：

1. 先触发一次慢循环增量（K-01 流程）确保参考基于最新 KB
2. 读 `kb/INDEX.md` + `config/profile.yaml`（画像未填先提示用户）
2.5. **grilling 前置步**：以 KB 为语境做完整 grilling（意图与优先级 / 时间窗与人力 / 范围边界 /
   技术栈偏好 / 一鱼多吃期望）
3. **咨询态（默认，零落盘）**：对比矩阵 + 一鱼多吃路线 + 三节方案概要（赛事/方案/技术栈）——
   **只在对话里回复，不生成任何文件**（含 grill 纪要）
4. **硬闸门：显式询问"是否开始战役？"**——不可跳过、不可默认、不可替用户决定：
   - **否** → 结束。产物说明：无产物（对话交付）
   - **是** → 继续第 5 步
5. **建档（新战役收口）**：`python scripts/guard/init_state.py --campaign <cid> --phase deliver`
   登记 + `python scripts/maint/repo_split.py --remote-base https://github.com/r-y-ren bootstrap
   --path workspace/<cid> --push` 建项目库入清单；**已有战役上下文**（`--campaign` 显式、或恰一个
   登记战役自动选中、多战役并存必填）时跳过建档，直接产到该战役
6. **落盘态**：三节方案书 + grill 纪要 → `<战役根>/docs/briefs/`（自动建目录）；随后**项目仓库
   commit + 立即 push**（铁律 6，随项目版本管理，fn-ladder 侧直接可见）
7. **收尾**：`python scripts/maint/doc_lint.py --project <战役根>` 跑禁用节护栏并在产物说明声明结果

铁律：方案书**禁止**包含 milestones / acceptance / 接口契约 / fn-ladder 需求种子——不得影响或
指挥后续推进；推荐结论须引用具体 KB 条目 ID，禁止凭印象；数据不足的维度如实降权告知，禁止硬推。
方案书是**单源**：只有战役侧一份落盘副本（咨询态零副本）。

**收尾产物说明**：咨询态——无产物（对话交付）；落盘态——① `<战役根>/docs/briefs/<日期>-<赛事slug>-<方案slug>.md`
② `<战役根>/docs/briefs/<同slug>-grill-notes.md` ③ 护栏检查结果声明；无产物时明说。
