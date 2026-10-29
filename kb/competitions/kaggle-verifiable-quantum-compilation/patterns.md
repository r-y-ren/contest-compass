---
competition_id: kaggle-verifiable-quantum-compilation
last_verified: 2026-10-29
coverage: []
confidence: 低
sources:
  - "官方页快照 kb/raw/kaggle-verifiable-quantum-compilation/pages-api-20261029.md（2026-10-29，内容接口通道）"
---

# Google Quantum AI - Verifiable Quantum Circuit Compilation 模式库（patterns）

> 首届赛事（2026-10-22 开赛），无历届获奖作品可解构——本文件仅基于官方评审文件起步，方法论分布/往届差异化/反面观察三节在首届终榜（2027-01-20）后回填。

## 一、评审偏好（从章程/评委讲评/获奖名单可观察到的取向）

- 评分即官方唯一取向：三任务相对基线改进的**几何均值**（∏(cost_ref/cost)^(1/3)）——三任务均衡推进优于单任务极端优化（几何均值对短板敏感）；单任务奖另设，鼓励专精路线并行。（来源：Evaluation 页直抓，信源等级：官网）
- 附加奖取向偏公开与持久：Milestone/Longest Leader 均要求 notebook 公开且持续公开，"早公开、长期霸榜"被制度化奖励。（来源：Prizes 页直抓，信源等级：官网）

## 二、方法论分布（获奖作品的方法/方案套路）

- 无数据（首届未终榜；覆盖=[]，本节待 2027-01 后回填）。

## 三、往届差异化点（什么样的作品拿到了最高奖）

- 无数据（首届）。

## 四、反面观察（常见失分模式，若有依据）

- 官方规则可证的硬失分点：dfthcsos angle 线路 >128 量子比特**直接拒收**；哈密顿量偏差 >20 mHa、LCU 归一化 Λ≤49.0 或 E_gap≤3.914898 Ha 不合格；verifier 按提交哈希+密盐播种测试，改线路即换测试——投机硬编码不可行。（来源：Evaluation/data-description 页直抓，信源等级：官网）

## 五、赛点检查表（评审标准 → 可执行检查项）

- [ ] 三任务 zip 齐全且格式合规（.kmb/.kmx、dfthcsos 编号无缺口、npz 键名精确匹配）。
- [ ] dfthcsos 每条 angle 线路宽度 ≤128 量子比特（提交前静态检查）。
- [ ] 几何均值策略自检：三任务 cost 比值是否均衡，最弱任务是否拖垮总分。
- [ ] 若冲附加奖：notebook 与数据集公开时间戳是否早于对应截止（11-20 / 01-04）并保持公开至终交。

## 六、对本框架的启示

- 可验证闭环类赛题（verifier 公开+密盐播种）与 fn-ladder 实测区机制同构：本地 verifier 全通过 ≈ 线上复现，适合直接接入现有验证流水线；无量子背景门槛声明降低了启动成本。
