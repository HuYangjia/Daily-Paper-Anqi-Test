# Automation 1777448333632 — 每日论文追踪

## 历史执行汇总

### 2026-06-23（今日 18:00 — 三方向同步）
- 三方向 #1 各一篇完成（commit + push 已执行）
- Harness: AOHP / Android Open Harness Project (arXiv 2606.23449) 95 — 首次把 harness 抽象**从 application 进程下沉到操作系统内核**；基于 AOSP 构建 OS 级 agent harness；三大系统机制（personalized service composition / efficient agent interfaces / secure information flow）；OS 一等 actor；任务完成 +21.12% / token cost −51.55% / 安全合规三角增益；清华 IIIS + 上海期智院 + HKU 17 作者；17 页/3 图；cs.AI + cs.OS（首次 OS 主类 harness）
- Agent Safety: AgentLens (arXiv 2606.22673) 96 — 多轮 coding agent 白盒 mechanistic subspace 干预；单层 10 维子空间 + step-level 探针；MAS benchmark 194 任务/10 类 MITRE ATT&CK；ASR 平均 85.99→13.36（−72.63 pp），Qwen 4.35%；lookahead 94.54%；反向干预 100% ASR 因果验证；OSU + Rutgers + 威斯康星 + Toronto + UGA；GitHub EddyLuo1232/AgentLens；把 Arditi 2024 单方向推到 multi-turn agent
- Benchmark: Evaluation Awareness Is Not One Capability (arXiv 2606.23583) 95 — 命名 "Benchmark Illusion"；评估意识 4 轴拆解（detection / behavior / representation / controllability）；37 模型 × 7 家族 × 8 实验；最强检测 AUROC 0.714（人类 0.819）；行为框架 21/140 显著最大 +30 pp；探针在行为崩溃后 ≥0.98；4 轴 15 对相关仅 1 对显著（ρ=−0.79）；Microsoft + 多机构；重新定义"可靠 benchmark 报告"标准
- 跨方向叙事："系统层降维（OS）+ 表征层下沉（10 维子空间）+ 评测层升维（4 轴矩阵）" — 2026 H1 方法学三联拍；AOHP 给出"架构改良无法被 gaming 替代"的工程证据，与今日 #3 评测幻象诊断形成正反两面互证
- 候选淘汰：Harness Survey 20704 (93) / Harness-MU 21856 (92) / Fara-1.5 20785 (91) / Harnessing Agent Skills 20631 (90)；Safety Relinking 21732 (92) / Self-Report 23671 (91) / SkillHarness 20614 (90) / Confidence Laundering 20662 (88)；Benchmark LIBERO-Safety 23686 (93) / Self-Awareness KAPRO 20661 (93) / Skill Coverage 20659 (92) / DEMM-Bench 20634 (91)
- 索引：三方向 index 顶部新增；根 index 顶部 3 条新增；count-badge 36/35/34 → 37/36/35
- 数据源：arxiv.org/list/cs.AI/new + arXiv export API（ti:harness 搜索 + agent safety / safety benchmark abs 搜索成功，未 429）+ arxiv.org/html/<id>v1（22673 / 23583 成功，23449 无 HTML 源）
- ⚠️ git push 失败：本地 commit af020ba 已生成，但 GitHub SSH 22/443 端口均被网络阻断（Connection closed by 100.12.0.10）；按 FOR_AGENT.md 规范，下次执行时一并 push

### 近期执行简史
- 06-15：HarnessX (94) / MINIM (94) / WorkBench Revisited (93) — count 33/32/31 → 34/33/32
- 06-17：SEAGym (94) / Rift (95) / EComAgentBench (93) — count 34/33/32 → 35/34/33
- 06-18：Xcientist (95) / SRP (95) / SciRisk-Bench (94) — count 35/34/33 → 36/35/34
- 06-23：AOHP (95) / AgentLens (96) / Eval-Awareness-Multivariate (95) — count 36/35/34 → 37/36/35

### 历史趋势 / 经验
- 三方向 #1 平均评分稳定 92–96；候选筛选规模 5 篇 + 评分对比表
- 报告间互文：每天注意挑能与方向内/方向间形成镜像或对偶的论文（今日 #1 AOHP 降维 / #2 AgentLens 表征下沉 / #3 Benchmark Illusion 评测升维 形成方法学三联拍）
- arXiv export API 此次未 429（与 06-18 持续 429 不同），可继续优先尝试 export API；fallback 用 list/cs.AI/new + abs/<id> 仍稳定
- 每日 commit + push 流程稳定
- 经验：当某论文 arxiv.org/html/<id>v1 返回 "No HTML for ..."，说明源未配置 LaTeX 渲染，应直接用 abs 页摘要 + 同期对照论文构造解读，无需再尝试 PDF

