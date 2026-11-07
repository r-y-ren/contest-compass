---
competition_id: kaggle-enveda-casmi26
last_verified: "2026-11-07"
coverage: []            # 赛事进行中（终交 2026-12-14），2026 本届获奖名单未放榜，本届获奖作品可解构为零
confidence: 中          # 章程反推层（官方 overview/evaluation/rules）+ CASMI 2022 历届谱系实证（winners/2022.md 14 条一手方法书，2026-11-07 回填第二节）
sources:
  - url: https://www.kaggle.com/api/i/competitions.PageService/ListPages?competitionId=143318
    accessed: "2026-10-13"
  - url: https://fiehnlab.ucdavis.edu/casmi/casmi-2022-results
    title: "CASMI 2022 官方结果页（16 组×四类目成绩唯一权威源；历届谱系数值均引自此）——快照 kb/raw/kaggle-enveda-casmi26/casmi-history/fiehnlab-casmi-2022-results-20261016.html"
    accessed: "2026-10-16"
  - url: https://drive.google.com/embeddedfolderview?id=12cCAdUjV_mXZ7tavdz9A_r18B6rDk437#list
    title: "CASMI 2022 官方方法书 Google Drive 父夹 embeddedfolderview 清单（16 子夹 name→ID 配对；2022 届 14 组方法书原件经此通道逐夹实抓归档）——快照 kb/raw/kaggle-enveda-casmi26/casmi-history/gdrive-methods-listing-embeddedfolderview-20261107.html"
    accessed: "2026-11-07"
---

# Enveda CASMI 2026 模式库（patterns）

> 本文件为章程反推层（官方 overview/evaluation/rules 页）+ 历届谱系实证层（CASMI 2022 的 16 组中 14 组有一手方法书原件，见 winners/2022.md；2026 本届进行中无获奖实证）。
> 官方页结论追溯快照 kb/raw/kaggle-enveda-casmi26/；2022 实证结论追溯 winners/2022.md 各条目（原件在 kb/raw/kaggle-enveda-casmi26/casmi-history/）。信源等级：官网 + 一手参赛材料。

## 一、评审偏好（从评测规则可观察到的取向）

- **MRR@25 排序指标**：奖励"把正确答案排到最前"的能力，首位命中 1.0、第 25 位仅 0.04（evaluation 页原文）→ 偏好高置信度排序校准，而非盲目扩候选列表。
- **骨架级匹配宽容**：RDKit 互变异构规范化 + InChIKey14 比对，立体中心/互变形式错误不扣分（原文附葡萄糖双 SMILES 示例）→ 评测设计明显偏向"2D 骨架判定正确即可"，降低化学规范性门槛。
- **按分子聚合**：同分子多谱图（不同碰撞能/加合离子）须融合为一个排序 → 偏好多证据融合的稳健管线，单谱图过拟合无意义。
- **三档新颖性分级**是官方明示的难度轴（Class 1 谱库可解 → Class 3 必须 de novo），虽归属隐藏，但 MRR 均值意味着 Class 3 的少量突破即可显著拉动名次 → 官方在引导参赛者攻 de novo 而非只卷谱库检索。

## 二、方法论分布（获奖作品的方法/方案套路）

> **实证口径说明**：2026 本届未放榜，下表为 **CASMI 2022 历届实证**（16 组中 14 组一手方法书，winners/2022.md；CASMI 2022 与 2026 同评测基因——2D 按 InChIKey 首块计分即 2026 InChIKey14 前身），代表年份与条目均指 winners/2022.md 的条目名。放榜后按同口径回填 2026 行。

| 模式 | 出现频次/占比 | 代表年份与条目 | 可迁移性 |
|---|---|---|---|
| 谱库检索+规则工具链（MS-DIAL/MS-FINDER/Progenesis/mzCloud 等库匹配主力） | 2022 届 7/14 组主力或兜底（Tsugawa/Frigerio-msdial/Alcazar/Namini-Mosley/Wei/Rutz 行等） | Tsugawa：加合 89% / 2D 12% | 加合与公式层够用，**结构层不可当主力**（全场该路线 2D 5-12%） |
| SIRIUS 指纹预测族（公式先行→CSI:FingerID 检索→CANOPUS） | 3 提交行（Duhrkop/Rutz/Nothias 同方法族） | Boosting SIRIUS：四类目 93/94/69/26%（Bonus 2D 榜首 29%） | 唯一在结构层进 25%+ 的路线；2026 官方点名 SIRIUS——主力骨架直接平移 |
| 三工具加权投票集成（SIRIUS+MetFrag+MS-FINDER） | 1/14 组（三策略三提交自带消融） | Si Wei：公式 74%（全场第三）、2D 仅 5-7% | 公式层廉价增益配方；其"公式取自 top-1 SMILES"耦合须解耦 |
| 学习型结构路线（谱预测/de novo 生成/自研指纹 CNN） | 4/14 组（Young/Elser/Hong/Ressom，另有 Wang 的 CFM-ID 预测库） | Elser mass2smiles：域内验证 42% → 赛场 0/97；Hong Mol3DNet 预测库 216,704 化合物 → 2D 1% | **2022 全线失败**（2D ≤9%）：谱预测可作重排特征，作主排序键不行——2026 Class 3 押注前必须配分布对齐 |
| 高置信筛选 vs 全覆盖 | 2 端各 1-2 组 | Nikolic 38%@22% 覆盖 vs Wei/Xing 99% 覆盖@5-15% | MRR@25 把覆盖率-精度张力设计进指标：弃答改排序后置，不弃答 |
| 候选留档+赛后回查协议（fragScore 排序自评） | 1/14 组明示 | Frigerio/Talavera：patRoon fragScore→generic score，候选全量留档 | 排序校准的标准前置实验，零成本平移 |

官方 overview/resources 页点名的方法生态（非获奖实证，官方背书工具清单）：MIST-CF / SIRIUS（分子式先行约束搜索空间）、matchms（谱图清洗/相似性）、GeMS 与 DreaMS（MassIVE 规模谱图预训练嵌入）、MassIVE 语料（自监督预训练）、GNPS 传播标注（"suspect"注释，被明确排除出训练集因标签为推断）。2022 实证与官方背书的交点：SIRIUS/MIST-CF 的"公式先行"同时是 2022 综合最强族的第 1 步与官方建议起手式。

## 三、往届差异化点（什么样的作品拿到了最高奖）

- CASMI 2022（最近一届有公开结果的历届，2026-10-16 官网直抓确认）：无官方授衔，按八表数值的编辑判断=**Boosting SIRIUS 方法族综合最强**（四类目全覆盖头部），Nikolic 单项 2D 命中率 38% 第一但覆盖仅 22%——"排序校准能力"比"命中率峰值"更接近 MRR@25 的赢家画像（winners/2022.md 综合读法）。
- 谱系沿革锚点已核：Schymanski & Neumann 2013 Metabolites（CASMI 2012 创始，Europe PMC 24958137 题录入库）；2017 届是否实际举办仍未核（旧站侧栏有导航、无成绩页实抓——遗留待办）。

## 四、反面观察（常见失分模式，官方规则/评测口径可证）

- **提交格式拒收清单明确**：缺 molecule_id/smiles 列、空值、重复 molecule_id、单分子超 25 个候选 → 直接拒收（evaluation 页原文）。自动评测下这是零成本失分。
- **人工标注测试数据** → 基础规则一票否决（Foundational Rules §3.4.b）。
- **外部数据/模型成本失衡**：许可证费用超奖金级的私有数据被判"不合理"而禁用（§2.6.b Reasonableness 原文示例）。
- **获奖者无法交付可复现代码** → 失格风险（§2.8 获奖者义务 + §3.7.c Kaggle 可要求代码与文档验证合规）。
- **预训练模型许可证不兼容获奖开源义务**：§2.5 要求获奖方案开源，不兼容许可证的输入数据/模型可豁免但须申报——用商业限制许可的谱图模型打底是隐性雷。

## 五、赛点检查表（评审标准 → 可执行检查项）

- [ ] 提交文件用官方 metric notebook 本地预检：列名/行数/重复 id/候选数≤25/无空值
- [ ] 候选列表排序按置信度校准（MRR 对首位敏感：校准分/集成投票而非模型原始 logit 直接排序）
- [ ] 谱图→分子聚合层实现（同 molecule_id 多谱图证据融合），禁止按单谱图生成再截断
- [ ] 匹配预演：本地用 RDKit（钉 2026.03.3）做 tautomer canonicalization + InChIKey14 比对自评
- [ ] Class 2/3 路线显式设计（分子式约束 + de novo 生成/检索融合），不只做谱库相似检索
- [ ] 域适配：以 enveda-np-examples（250 天然产物同管线锚点）与 enveda-180（同仪器）做分布对齐
- [ ] 外部模型/数据台账：许可证记录 + 成本留痕（应对 Reasonableness 审查与获奖开源义务）
- [ ] 获奖预案：可复现代码仓 + 方法说明草稿在终交前备好（§2.8 两周文件期限内可交付）

## 六、对本框架的启示（喂给 K-02 / 验收报告）

- 方向契合：谱图→结构识别属 AI for Science 检索+生成混合任务；候选生成（检索/分子式约束/de novo 生成）与排序校准两层解耦是可迁移的工程骨架，可复用到其他"多证据→排序输出"赛题。
- 与数模/时序方向完全不重叠；与 ARC 类推理赛亦不同源——若我方投入需补化学基线知识，冷启动成本中等（官方 data 页提供零化学基础科普，官方工具链 MIST-CF/SIRIUS/matchms 降低门槛）。
- 合规栈：外部数据台账 + OSI 许可核查 + 获奖代码仓预案，均属快循环可模板化的检查项（见第五节，可直接派生 acceptance.checklist）。
- 体量参考：3169 队（2026-10-13），$50k 池前五名分配——头部争夺激烈度介于 NFL Big Data Bowl（205 队）与 ARC（2807+ 队）之间。
