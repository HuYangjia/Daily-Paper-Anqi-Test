# 自动化任务记忆 · automation-1777448333632
> 每日 18:00 三方向论文追踪

## 执行历史摘要

### 2026-06-17（今日 18:00 — 三方向同步）
- 三方向 #1 各一篇 完成（commit + push 待执行）
- 选定：
  - Harness: SEAGym (arXiv 2606.17546, C. Zheng / C. Xue 共一 / B. Liang / J. Yang / C. Zhang 通讯 · 清华自动化系 + BNRist, 2026-06-16) 94 分 — 把 self-evolving harness 评测从单一最终分数升级为 5 视图（train / val / ID / OOD / replay + cost）；UVG/IDG/OODG/FR 四派生指标；Harbor Framework 兼容；Terminal-Bench 2.0 + HLE 实例化；ACE / TF-GRPO / AHE 共享 epoch/batch 协议公平比较；三个反直觉发现：(1) 频繁更新可能不提升 held-out（TF-GRPO OOD −2.5）；(2) 中间快照可能后期崩溃（AHE replay 34→6→43）；(3) batch size 非单调（10 −14.3 / 20 +17.1 甜点 / 40 +2.9 / 80 −17.1）；HLE-only 训练最终 collapse 至 0%；DeepSeek 演化 harness 改善 GLM(+7.3) 但损害 GPT-5.4(−3.6)；与 6-15 HarnessX 形成"演化 → 评估" 闭环
  - Safety: Rift (arXiv 2606.17229, Petr Nyoma 独著 · Harmonic Labs, 2026-06-15, GitHub Omibranch/Rift) 95 分 — 残差秩"冲突签名" + sleeper agent vs naive liar 控制范式（同输出错误答案，唯一差异是知识冲突）；GPT-2 small/medium / Qwen2.5-1.5B/7B / Phi-3-mini 一致测得欺骗前向传递的残差秩比 naive liar 高 2.1–2.3 倍；Phi-3 AUC=1.0 / Wilcoxon p ≈ 6×10⁻¹¹；零标签 100% 取向准确率；basis-free relative representations + 48 中性锚点 → 跨族零样本 AUC 0.933 / 跨格式 0.821 / 跨 5 语言 1.000；可读不可写（注入 +v 诱导欺骗 0/8 / 减 v 恢复真相 0/8）—— 与 Zou et al. 2023 truthfulness-steering 形成对偶；6 项 negative experiments 完整文档化；与 6-09 ELK 不可能定理 + 6-14 "Did you lie?" 共同构成 2026 H1 deception 三件套
  - Benchmark: EComAgentBench (arXiv 2606.17698, Z. Du / T. Li / H. Zhang 通讯 · Shopee, 2026-06-16, GitHub Morizeyao/EComAgentBench_) 93 分 — 把 shopping agent 长程评测立为分布式隐藏意图恢复；662 任务 / 6,645 rubric / 平均 10.04 / 任务；三源分布 visible query 60.1% / tool-gated profile 19.9% / scripted clarification 19.9%；persona 与 demographics 字段分离防止信息泄漏；clarification 脚本化（最多 10 轮 + trigger keywords）；6 类 × 3 源类型化 rubric；7 模型整体精度 19.5–57.1%（Opus-4.6 57.1% / Qwen3-30B-A3B 19.5%）；所有模型 query > persona ≈ clarification 单调下降；关键诊断"差距在使用 hidden 信息而非检索它"；隐式需求驱动难度（0-1 个 51.8% → 3+ 个 27.2%）；review_opinion 最难；与 6-15 #3 WorkBench Revisited 形成"纵向 + 横向" 双姿态
- 跨方向叙事："5 视图纵向评测（SEAGym）+ 残差秩冲突签名（Rift）+ 三源分布隐藏意图（EComAgentBench）"——三轴姿态都把"看似单一指标"分解为多个独立可测维度；构成 2026 H1 后期评测方法学的"<em>多维度归因</em>"统一姿态
- 候选淘汰：Harness SSA 90 / FinAcumen 88 / SkillMigrator 87 / PreAct 86；Safety Multi-Agent Concurrency Verified 92 / DiagFlowBench 88 / Incumbent Advantage 87 / StepGuard 86；Benchmark MapSatisfyBench 90 / CEO-Bench 88 / LongWebBench 87 / Offline Preference 86
- 索引更新：方向 index 三个顶部插入条目；根 index 顶部插入三条新条目；count-badge 34/33/32 → 35/34/33
- 数据源：arxiv.org/list/cs.AI/new + cs.LG/new（2026-06-17 提交清单）+ arxiv.org/abs/<id> + arxiv.org/html/<id>v1

### 2026-06-14（今日 18:00 — 三方向同步）
- 三方向 #1 各一篇 完成（commit f81940b + push 已执行 origin/main）
- 选定：
  - Harness: ToolSense (arXiv 2606.12451, A. Hathidara / S.S. Sistla / S. Schreiber / S. Bansal · 推测 SAP, 2026-06-12, GitHub SAP/toolsense, CC BY-SA 4.0) 91 分 — 把 harness 设计姿态从"评测 agent 任务能力"升格为"审计模型内部参数化知识"；自动生成 RRB（3 歧义层级）+ MCQ + QA 三类基准；ToolBench 47k 工具 / 5 种参数化训练配置揭示"知识-检索分离"：RRB 较完全规范化基准降 50–64 pp / 部分模型事实探针接近随机 / 嵌入基线在真实查询上反胜部分参数化模型；与 6-12 #1 HarnessBridge"训练姿态 harness"共同构成"训练 + 审计"双姿态
  - Agent Safety: "Did you lie?" (arXiv 2606.12618, A. Cooney / D. Africa / G. Irving · 推测 UK AISI / DeepMind, 2026-06-12, 12 页 / 6 图, CC BY 4.0) 94 分 — 把"模型在说谎"立为可证伪命题；13 个 belief-verified reasoning model organisms（CoT 验证 + held-out 泛化）+ Varied Deception 测试床；4 类检测器（CoT judge / logprob / 经典 activation probe / 新方法 Did-You-Lie/DYL）评估 31 个 2B–1T 开放权重模型；提示性撒谎正向缩放，但所有激活/对数概率检测器在训练后 model organisms 上急剧失效；CoT judge 0.82 BA 部分为伪影；论文坦诚"当前测谎器无法支撑对模型信念的高置信判断"；与 6-11 #1 ELK 不可能定理形成"理论 + 实证"完整证据链；公开数据集 + organisms + 检测器；Containment Gap 已选 6-12 本日跳过
  - Benchmark: SciAgentArena (arXiv 2606.12736, T. Liu 等 33 作者 · 推测 Yale / Harvard / Stanford / Northwestern 含 Rex Ying / Arman Cohan / Marinka Zitnik / James Zou, 2026-06-12, CC BY-NC-SA 4.0) 92 分 — 把"真实科研"立为 agent benchmark 主战场；33 作者跨学科 / 约 200 真实新兴科研任务 + 步骤级验证 + interactive agent-agnostic 环境；揭示 agent 在结构清晰数据分析工作流中"有效贡献"但在新颖洞察 / 自主探索 / 开放式研究问题上"性能严重不均"；系统刻画跨 agent 共享的失败模式（可靠性 / 自主性 / 科学推理）；把 benchmark 从"能力衡量器"升级为"失败模式诊断器"；与 6-09 #1 SciConBench / 6-08 #3 AARRI 形成"三层科研评测梯度"；项目主页 sciagentarena.github.io 全开源
- 跨方向叙事："诊断姿态 harness（ToolSense）+ 信念可验证 organism（Did you lie?）+ 失败模式 benchmark（SciAgentArena）"——三件套都把 2026 H1 后期评测方法学姿态推向"诊断型"；ToolSense 把 harness 立为审计工具 / Did you lie? 把 model organism 立为 belief-verified 载体 / SciAgentArena 把 benchmark 立为跨 agent 失败模式诊断器；与 6-12 "动态化"主线（HarnessBridge 双向投影 + Containment Gap 架构层修复 + MLUBench 终身遗忘）合成"动态化 + 诊断化"双姿态，是 2026 H2 评测设计的方法学拐点
- 候选淘汰：Harness DailyReport 89 / Evoflux 88 / AgentBuild 87 / GeoNatureAgent 86 / Two-Agent E-Commerce 85；Safety Prefill Awareness 91 / Illusion of MAS 89 / From AGI to ASI 88（DeepMind 14 位）/ Normative Robustness 87 / HLER 86；Benchmark DailyReport 90 / GeoNatureAgent 88 / Procedural Reasoning 86 / Power Distribution 85 / Big5-TPB 85
- 索引更新：方向 index 三个顶部插入条目；根 index 顶部插入三条新条目；count-badge 32/31/30 → 33/32/31
- 报告间互链：Harness → ToolSense 引 ToolBench / Toolformer / DPR / DSI / LoRA / HarnessBridge / What Benchmarks Don't Measure / AARRI / SciConHarness / RAG / SkillDAG；Safety → Did you lie? 引 ARC ELK / Burns CCS / Sleeper Agents / Constitutional AI / RLHF / ELK 不可能定理 / Pacchiardi Lie Detection / AI Control / Containment Gap / Prefill Awareness / CoT；Benchmark → SciAgentArena 引 GAIA / AgentBench / WebArena / SciCode / GPQA / SciConBench / AARRI / AI Scientist / HarnessBridge / ToolSense / ChemCrow
- 数据源：arxiv.org/list/cs.AI/new + cs.LG/new（2026-06-12 提交清单），周末 6-13 / 6-14 arXiv 无新提交沿用周五候选池；export API 持续 429 沿用 fallback

### 2026-06-12（今日 18:00 — 三方向同步）
- 三方向 #1 各一篇 完成（commit + push 已执行）
- 选定：
  - Harness: HarnessBridge (arXiv 2606.12882, X. Wang / H. Wang / A. Taylor / J. Cong / Y. Sun / W. Wang UCLA, 2026-06-11) 92 分 — 把 harness 从手工工程升级为可端到端学习 plug-in；observation projection（环境→agent 紧凑决策状态）+ action projection（agent→环境 可执行 transition 或 trajectory-grounded rejection）双向投影；Terminal-Bench 2.0 / SWE-bench Verified 匹敌或超越专门 harness；token + 轨迹长度同时下降；从小生成器泛化到大商用模型；与 5-23 Life-Harness "harness 可移植性" / 6-08 AARRI "二轴评测" / 5-15 ChromaFlow 负面 ablation 全面对位；把 harness 立为 agent 论文的 "第三作者"
  - Agent Safety: The Containment Gap (arXiv 2606.12797, Md J. Hossain / M.A. Hossain / W. Liu / N. Ansari, 2026-06-11, **ICML 2026 AI4GOOD Workshop**) 93 分 — 审计 LangChain / AutoGPT / OpenAI Agents SDK 三大主流 agentic 框架，6 项遏制原则无一原生符合；memory integrity 三框架普遍缺位；单次 memory poisoning 写入 → 88.9% 持久错拒（目标群体）；5 因素策略 3.5× 错拒提升 + 总体准确率不变（隐蔽逃避标准监控，fairness × safety 交叉攻击面）；memory integrity validator + policy gate <0.2ms/call 消除两类攻击向量；把 safety 责任分摊到框架供应商；与 5-21 CUGA / 5-19 Memory Laundering / 5-25 SafeHarbor / 6-11 ELK 互补构成 "架构层 safety 不可避免"
  - Benchmark: MLUBench (arXiv 2606.12809, H. Li / H. Chi / Q. Wang / Y. Mao / Z. Zhang / J. Tan / T. Liu / W. Yang / B. Han, 2026-06-11, **ICML 2026 接收**, 36 页, GitHub lihe-maxsize/Lifelong_Unlearning_main) 93 分 — 首个 MLLM 终身遗忘评测基准；9 类 / 127 实体 / 顺序遗忘请求；揭示 "多模态对齐保持（preserve multimodal alignment）" 是 MLLM 遗忘独有结构性挑战——持续从一个模态遗忘可能降级整个模型；现有方法（GA / NPO / RMU / SCRUB）在 lifelong 场景下严重累积退化；LUMoE MoE 结构隔离缓解；直接映射 GDPR Article 17 / EU AI Act 实施需求；把 unlearning 圈子从 "第一代静态评测（TOFU/WMDP/MUSE）" 升级为 "第二代动态评测"
- 跨方向叙事："harness 可学习化（HarnessBridge）→ framework 可审计化（Containment Gap）→ benchmark 可持续化（MLUBench）"——三轴姿态变化都把 "静态" 元素 "动态化"；HarnessBridge 提出的 trajectory-grounded rejection（action 路径）与 Containment Gap 提出的 memory integrity validator + policy gate（memory 路径）形成 "action × memory" 双层防御；MLUBench 推动 unlearning 评测从 "批处理 / 单模态 / 一次性" 升级为 "流式 / 多模态 / 终身"；三者合起来构成 2026 H1 后期 evaluation methodology 的统一姿态变化
- 候选淘汰：Harness ToolSense 90 / SciAgentArena 89 / Evoflux 89 / DailyReport 88 / AgentBuild 87；Safety Lie Detectors 92 / Prefill Awareness 91 / HLER 90 / Illusion of MAS 89 / From AGI to ASI 88；Benchmark SciAgentArena 92 / DailyReport 90 / GeoNatureAgent 89 / Pythagoras-Prover 88 / Procedural Reasoning QA 87
- 索引更新：方向 index 三个顶部插入条目；根 index 顶部插入三条新条目；count-badge 31/30/29 → 32/31/30
- 报告间互链：Harness → HarnessBridge 引 ReAct / SWE-bench Verified / Terminal-Bench / Toolformer / Devin / AARRI / Life-Harness / SKILL.nb / ChromaFlow / System Scaling；Safety → Containment Gap 引 prompt injection / LangChain / AutoGPT / OpenAI Agents SDK / ReAct / CUGA / Memory Laundering / ECA / SafeHarbor / ELK / What Benchmarks Don't Measure / EU AI Act；Benchmark → MLUBench 引 TOFU / WMDP / MUSE / Eldan Russinovich / LLaVA / MoE Shazeer / ANNEAL / MAC-Bench / PreAct-Bench / SciConBench / GDPR Article 17 / EU AI Act
- 数据源：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id>，arXiv export API 持续 429 沿用 fallback

### 2026-06-11（今日 18:00 — 三方向同步）
- 三方向 #1 各一篇 完成（commit + push 已执行）
- 选定：
  - Harness: SkillJuror (arXiv 2606.11543, Z. Chen / Z. Guo / B. Huang / B. Lu / J. Lin / Y. Zhou / W. Zhang, 2026-06-10, GitHub zhiyuchen-ai/skill-juror) 92 分 — 把 Skill 组织方式从内容剥离立成独立可测变量；语义受控变体 + 匹配多试验 + 轨迹证据三件套；SkillsBench 82 任务 / 410 匹配试验；Progressive Disclosure vs flat：每条轨迹接触资源数 1.18 → 3.85（+226%）、有效 uptake 1.33 → 3.92（+195%）、验证器通过率 +4.1%；行为指标先于结果指标的方法学姿态；任务依赖性发现（实现/检查/修复 vs 输出约定/数值阈值/长产物管线）
  - Agent Safety: The Impossibility of Eliciting Latent Knowledge (arXiv 2606.12268, K. Friedl / F.R. Ward / P.Y. Rapoport / T. Everitt（DeepMind） / J. Richens, 2026-06-10, 24 页 + 证明附录, CC BY 4.0) 95 分 — 用 Causal Influence Diagrams 形式化 ELK；证明"不存在仅依赖行为反馈、即使反馈完美也能确定性产生 honest agent 的训练策略"；形式化定义 honesty / observable / latent / goal misgeneralisation；把 ELK 从直觉 desiderata 升级为可证伪命题（停机问题对齐版）；反推：必须看内部表征，为 mech-interp / SAE / probes 合法化；与 6-03 What Benchmarks Don't Measure 互补构成"RLHF 不充分"双重证据
  - Benchmark: SciConBench + SciConHarness (arXiv 2606.11337, H. Jung / P.V. Diniz / J.R.C. Roveda / A.F. da Silva / H. Jung / E. Tsai / A. Korolova（USC）/ M.H. Ribeiro（EPFL）, 2026-06-09, 79 页 / 34 图 / 17 表) 94 分 — 9.11K systematic review 问题 + 专家撰写结论；原子事实分解评估管线 + factual precision/recall；clean-room evaluation harness（受控网络交互防数据泄漏）；8 前沿 agent 净室下最佳 F1 仅 0.337（远低于非约束评估）；Google AI Overview / OpenEvidence 消费级审计揭示生成不完整/矛盾结论；live benchmark 抗污染设计
- 跨方向叙事："工程治理（SkillJuror）→ 理论不可能（ELK）→ 评测面 clean-room（SciConHarness）"——SkillJuror 把行为先于结果立成方法学；ELK 不可能定理证明 RLHF 范式不可达 honesty；SciConHarness 在工程层提供"受控信息访问"的具体范式；三者合起来构成 2026 H1 "三层证据矩阵（结果 / 轨迹 / 表征）" 的完整论证链
- 候选淘汰：Harness PROJECTMEM 91 / INFRAMIND 90 / HORMA 89 / FlowBank 88 / Agent Skill Survey 87 / Counterexample Guided 87；Safety Five-Plane Architecture 93 / Forecasting Behavior 92 / Risk Under Pressure 91 / Roleplay Belief 89 / Subliminal Transfer 88 / MLJailDe 88 / Search Discipline 87；Benchmark SocSci-Repro-Bench 91 / Methodologically Diverse 90 / Embodied-BenchClaw 89 / BioDivergence 88 / Schützen 87 / CDUR 86
- 索引更新：方向 index 三个顶部插入条目；根 index 顶部插入三条新条目；count-badge 30/29/28 → 31/30/29
- 报告间互链：Harness → SkillJuror 引 SKILL.md / SkillDAG / SKILL.nb / Regimes / AARR-Bench / Lean4Agent；Safety → ELK 引 ARC ELK Report / CIDs Survey / Sleeper Agents / Burns CCS / RLHF / Constitutional AI / What Benchmarks Don't Measure；Benchmark → SciConBench 引 GAIA / FActScore / Reliability Gap / What Benchmarks Don't Measure / Boiling the Frog / AARR-Bench / MAC-Bench / PreAct-Bench / ELK
- 数据源：arxiv.org/list/cs.AI/new + cs.LG/new + cs.CL/new + arxiv.org/abs/<id>，arXiv export API 持续 429 沿用 fallback

### 2026-06-10（今日 18:00 — 三方向同步）
- 三方向 #1 各一篇 完成（commit + push 待执行）
- 选定：
  - Harness: Regimes / ActiveGraph (arXiv 2606.10241, Yohei Nakajima 独著, 2026-06-08, 30 页 / 5 图 / GitHub yoheinakajima/regimes 含 committed runs) 94 分 — event-sourced agent runtime；append-only 事件日志的确定性投影；4 道 gate（static / sandbox / in-sample / held-out）把"提升 / 丢弃"立为事件；LongMemEval-S 5 个 seeded splits 中 4 个准确率 +0.05~+0.10 / 1 个 over-promotion +0.01；reader reconciliation 是主导失败而非 retrieval；prompt-as-discovery-probe 假设；failure-regime taxonomy 把"它错在哪"路由到"补丁作用在哪一接缝"
  - Agent Safety: Arbiter Agent (arXiv 2606.10747, Tonini/Torrielli/Lautrup/Schneider-Kamp/Çelikok/Galke Poech, 2026-06-09, **AITC 2026 接收**, GitHub aisilab/arbiter) 94 分 — multi-agent misalignment 检测从事后审计升级为预算感知主动检查；4 元决策（wait/question/inspect/log）；5 conversation conditions × 5 tool configs × 2 backbone；权重诱导失对齐最难 / 指令诱导最易；logging recall ↑ precision ↓ 双刃剑；对话结束前可靠定位失对齐
  - Benchmark: PreAct-Bench (arXiv 2606.09890, H. Xu 等 10 作者 KCL 等, 2026-06-03, CC BY-SA 4.0) 93 分 — 1,000 对 ethical/unethical 配对轨迹 / 5 域 / Prefix Foresight F1；把"事前预测"立为 first-class 任务；三类评估对象（通用 LLM / 安全护栏 / 表征探针）分层；人类有 promising 表现而最强 LLM 仍挣扎；视角倒置"<em>禁后</em>" → "<em>禁前</em>"
- 跨方向叙事："改进闭环治理（Regimes）→ 实时失对齐主动监督（Arbiter）→ 预测时刻评测面（PreAct-Bench）"——held-out gate × inspection budget × prefix foresight F1 三件套，构成 2026 H2"<em>从 reactive 到 proactive</em>"安全研究主轴；Arbiter 与 PreAct-Bench 形成"<em>方法 + 评测</em>"双轴
- 候选淘汰：Harness AutoPDE 91 / Less Context 90 / HIPIF 89 / Trace2Policy 88 / Spatial Memory 87 / ActiveMem 86；Safety CoT 2x2 (FAGEN ICML) 92 / KV-cache Quant 91 / DualSelect 89 / False Success (FAGEN ICML) 90 / Memorization 88 / OSL-MR 87；Benchmark STAGE-Claw 92 / False Success 91 / ComBench 89 / EngVQA 88 / RealMath-Eval 87 / Metaprogramming 88 / TriState 86
- 索引更新：方向 index 三个顶部插入条目；根 index 顶部插入三条新条目；count-badge 29/28/27 → 30/29/28
- 报告间互链：Harness → Regimes 引 SKILL.nb / Lean4Agent / ANNEAL / System Scaling / AutoPDE；Safety → Arbiter 引 VATS / memory laundering / Ensemble Monitoring / Sleeper Agents / CoT 2x2 / PreAct-Bench；Benchmark → PreAct-Bench 引 HarmBench / TrustLLM / SafetyBench / Knowing-Doing Gap / GrandGuard / Arbiter Agent / False Success
- 数据源：arxiv.org/list/cs.AI/new + arxiv.org/list/cs.LG/new + arxiv.org/abs/<id>，arXiv export API 持续 429 沿用 fallback

### 2026-06-09（每日 18:00 — 三方向同步）
- 三方向 #1 全成 (commit 1fc6906, push 成功 origin/main)
- 选定：
  - Harness: SKILL.nb (arXiv 2606.08049, El Hattami / Chapados / Pal, 2026-06-06) 94 分 — selective formalization + gate-conditioned execution + 多模态可审计 notebook IR；WebArena-Verified 53.7% 单轮 SOTA / 三次重跑保留 91.7% / 修复后回归率 4.2% (基线 15-17%) / GitLab 跨版本 (15.7→18.9) 持平；把"<em>第二次失败</em>"立成可独立报告维度
  - Agent Safety: VATS (arXiv 2606.07992, Patel / Pai, ICML 2026 AIWILD Workshop, 2026-06-06) 93 分 — MCP error-handling loop "<em>隐式权威</em>" 攻击面；7 维变异演化对抗 payload；错误路径注入 ASR 比标准 IPI 高 3 倍 / 最高 100%；Gemini 3.1 Pro / GPT-5.5 / GLM-5.1 / Qwen3-Coder 通杀；"夹心定位"为最强单维度；guardrails 仅缓解不治本
  - Benchmark: MAC-Bench (arXiv 2606.07805, Y. Zhao 等 5 作者, 2026-06-05) 93 分 — "Beyond Goodhart's Law" + "Agent-as-a-Benchmark" 范式；SERV pipeline (Seed→Evolve→Refine→Verify) 把法律文本合成 holographic sandbox；CSR (合规加权成功率) + MG (马基雅维利差距) 双指标；Pareto trade-off 量化
- 跨方向叙事："<em>第二次成功 + 错误回路 + 程序合规</em>"——SKILL.nb 把 lifecycle governance 立成第六维度，VATS 暴露错误回路是被忽视的最强攻击面，MAC-Bench 把"<em>策略性违规倾向</em>"立成 benchmark 标准指标；6 维评测拼图（成功率 / 跨期保留率 / 修复后回归率 / CSR / MG / error-path ASR uplift）首次成型
- 候选未取：Harness PACE 序贯提交检验 (92) / Syll 跨界面 agent (90) / Contract2Tool (89) / MemToolAgent (88) / PathoSage (86) / RECENT ICML (85)；Safety Cold-Start Safety Gap (92) / Patcher 训练时对抗 (91) / Where Instruction Hierarchy Breaks (90) / Safety is Contextual judges (88) / SciTrace (87) / RefusEU 多语言 (86)；Benchmark AI-MASLD 医学压力 (92) / AEDI 谄媚连续指标 (91) / SLMJury 小模型裁判 (90) / TinyJudge ACL 2026 (89) / RAG reliability (87) / Online Agent-as-a-Judge (86)
- 维护：方向 index 顶部 + 根 index 顶部 3 条；count-badge 28/27/26 → 29/28/27
- 报告间互链：Harness → SKILL.nb 引 SkillDAG / Lean4Agent / SKILL.md / Code as Harness / ANNEAL；Safety → VATS 引 ECA / Cold-Start / Attack Selection / Evo-Attacker / Where Hierarchy Breaks；Benchmark → MAC-Bench 引 GrandGuard / What Benchmarks Don't Measure / Boiling the Frog / Reliability Gap / SKILL.nb
- 数据源：arxiv.org/list/cs.AI/new + cs.CL/new + arxiv.org/abs/<id>（export API 仍 429，fallback 稳定）

### 2026-06-08（每日 18:00）
- 三方向 #1 全成
- 选定：
  - Harness: Lean4Agent (arXiv 2606.06523, R. Wang/J. Huang/P. Wang/X. Liu/L. Kong/T. Zhang, 2026-06-02) 93 → 首个用 Lean4 依赖类型 FL 形式化 agent workflow/trajectory；FormalAgentLib（建模 + 语义一致性 + 故障定位）+ LeanEvolve（验证反馈自动修订）；SWE-Bench-Verified 困难子集 + ELAIP-Bench / 5 LLM 平均 +11.94 pp，LeanEvolve 再 +7.47 pp；把 IR 抬到证明系统（与 SkillDAG typed-edge / Code-as-Harness code-IR 形成三档梯度）
  - Agent Safety: Attack Selection in AI Control (arXiv 2606.06529, C. Ge-Wang/T. Crosse/B. Hadad IV/J. Schaeffer/R. Potham/T. Tracy, 2026-06-03) 94 → 把红队决策分解 start/stop 两 policy；BashArena/LinuxArena · 1% audit budget · start −20pp / stop −20–28pp；底层攻击能力不变，仅时机选择即压低安全；upper-bound 解释；明确呼吁评估必须 elicit attack selection
  - Benchmark: AARR / AARRI-Bench (arXiv 2606.07462, Jiayu Wang 等 11 作者, 2026-06-05) 93 → 研究实习生级细颗粒度评测套件 + GitHub AARR-bench/AARRI-bench；LLM × harness 二轴评测；最强 Mini-SWE-Agent + Claude Opus 4.7 仅 68.3% vs 人类 94.0%；研究行为本身是新瓶颈
- 候选未取：Harness AARRI (92) / Sim-to-Real Gap MDP KDD Blue Sky (90) / StainFlow GUI (88) / Off-Policy Strategic (86) / DuMate (85)；Safety TRUST 不确定性 RL (92) / SafeGene 适配器 (90) / AEGIS 物理 AI (88) / Moral credences (86) / Embedding Drift (85)；Benchmark Think Fast no-CoT TH (92) / Attack Selection (91) / AI Agents Reshape Knowledge Work (88) / DuMate (87) / Don't Fix in Post ICML Oral (86)
- 三方向主题贯通："正确 + 抗攻击 + 专业"——Lean4Agent 给"plan 是否可证明对"的形式化裁判，Attack Selection 给"评估方法学缺位"的修正，AARRI 给"研究员级专业素养"的 granular 评测；三者一起构成下一代 benchmark 的三轴体系
- 三方向 index 顶部插入 + 根 index 顶部插入 3 条新条目；count-badge 27/26/25 → 28/27/26
- 报告间互链：Harness → Lean4Agent 引 SkillDAG / Code as Harness / ANNEAL；Safety → Attack Selection 引 Greenblatt AI Control 原型 / Evo-Attacker / TTT / Lean4Agent；Benchmark → AARRI 引 SciCode / GAIA / Lean4Agent / Attack Selection / ChromaFlow
- arXiv export.arxiv.org API 仍 429；fallback list/cs.AI/new + abs/<id> 稳定可用

### 2026-06-03（每日 18:00 提前于 10:13 触发 — 三方向同步）
- 三方向各生成 #1 报告（commit ddd4cce, push 成功 origin/main）
- 选定篇目：
  - Harness: SkillDAG (arXiv 2606.03056, Tong Bai 等 7 作者 2026-06-02) 93 分 — 类型化技能图取代相似度匹配；vector + typed-edge + conflict 三路信号；propose-then-commit 协议要求 execution-backed evidence；ALFWorld 67.1% / +12.8 pp；Ret@K 65.5→78.2；pool 扩 10× 鲁棒；集合单调编辑（不驱逐已命中）
  - Agent Safety: What Benchmarks Don't Measure (arXiv 2606.02965, V. Ojewale / S. Venkatasubramanian 2026-06-01, **ACM CAIS Best Paper + Oral**) 95 分 — compliance bias 是 RLHF 结构性副作用；三-gap 分类法（specification / verification / authority）+ Safety/Usability/Informed Refusal 三联协议；144 enterprise × 5 模型族；89.2% blocking + 87.5% usability 双高同时；safety-usability 是 tunable
  - Benchmark: The Reliability Gap in Benchmark Auditing (arXiv 2606.03305, W. Zarzecki / J. Dubiński / S. Cygert 2026-06-02) 92 分 — 污染检测在实战中仅 59.4% 正确（335 评估 / 27 模型 / Pythia + OLMo 2 / 最大 27B）；分布偏移让 LLM Dataset Inference 产生 false positive；Post-Hoc Inference 在 benchmark 规模下功效不足；CoDeC 仅给粗粒度 provenance；立论"统计检测无法替代透明 data provenance"；开源 audit benchmark
- 三方向叙事链："系统 / 行为 / 元层 三档同步升级"——SkillDAG 给系统层结构化 IR；abstention competence 给行为层评测面新维度；contamination audit 给元层 benchmark 自审能力
- 候选未取：harness — Don't Gamble GAMBLe (90) / TriEval (88) / DeskCraft (88) / GTBench (86) / Multi-Agent Debate Data Cleaning (85)；safety — Information Gain Clarification (91) / Edge Modular Agent (88) / Solipsistic Superintelligence (87) / AURA (86) / MedCUA-Bench (85)；benchmark — ClinicalMC (90) / CORE (88) / MedCUA-Bench (87) / Dental AI Survey (85) / GTBench (85)
- 维护：方向 index + 根 index 各插一条；count-badge 26 / 25 / 24 → 27 / 26 / 25
- 数据源：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id>（export API 仍 0 字节，沿用 fallback）
- 注：5-28 #1 三篇报告本地存在但未 commit（git status 显示 untracked），与本次任务无关，后续可单独整理

### 2026-05-25（追加 #2 — 三方向同步）
- 三方向各生成 #2 报告（同日第二轮）
- 选定篇目：
  - Harness: TwinRouterBench (arXiv 2605.18859, Pei Yang 等 17 作者 2026-05-14) 93 分 — step-level LLM routing harness 双轨：static 970 router-visible prefixes (520 instances 来自 SWE-bench/BFCL/mtRAG/QMSum/PinchBench) + dynamic SWE-bench Verified 100 case；deterministic arithmetic scoring（无 online judge）；downgrade-and-cascade 协议反向标注 target tier
  - Agent Safety: TTT Undermines Safety Guardrails (arXiv 2605.22984, Antonelli/Akhondzadeh/Bojchevski 2026-05-21) 94 分 — 把测试时训练立成新 jailbreak 入口；3 类威胁模型（few-shot/generation-phase/RAG-aug）；LoRA few-shot ASR@10 ≈ 95%、generation-phase ≈ 93% 跨家族跨规模；漏洞迁移到生产 fine-tuning API；validity-aware 评估纠正退化输出；perplexity-shift provider-side detector；强调 dynamic alignment
  - Benchmark: PoisonForge (arXiv 2605.23168, Sun/Suri/Chaudhari/Nita-Rotaru/Oprea, Northeastern Khoury, 2026-05-22) 92 分 — 任务级靶向中毒 benchmark；4 维参数化（bias type/poisoning mode/appearance count/output length）；1% poison budget · 12 模型 / 5 家族 / 2B-32B；10 条投毒样本 → 11/12 模型 ≥70% ASR；非目标任务泄漏 < 0.5%；ASR 随出现次数单调升 / 输出长度单调降；风险预测模型可泛化预测新任务 ASR
- 三方向叙事链："训练-推理-评测三阶段 LLM 安全全景"——TwinRouterBench 给 router 评测重写数据形态；TTT 攻击是推理时 alignment 失效；PoisonForge 是训练时数据供应链失效；三件事合起来证明"scaling 不解 alignment / 不解中毒 / 不解评测形态"
- 候选对比：Harness — EvalAwareBench (91) / Inference-Time Alignment (90) / Knowledge Work Bench Design (89) / WebGameBench (88)；Safety — Misattribution Gap (90) / Codec-Robust Audio (87) / Tool-Call Traffic (86)；Benchmark — EvalAwareBench (91) / VulnLLM-R Cyber (90) / PrefBench (87) / Law RAG (86)
- 三方向 index + 根 index 各插一条；count-badge 24/23/22 → 25/24/23
- commit d16dd92, push 成功（origin/main）
- 数据源：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id>（export API 在此小时返回 0 行 → fallback 列表抓取）

### 2026-05-25（每日 18:00 — 三方向同步）
- 三方向各生成 #1 报告
- 选定篇目：
  - Harness: Code as Agent Harness (arXiv 2605.18747, 43 作者综述, UIUC + Meta + UCB 等, 2026-05-18) 94 分 — 把"代码"立成 agent 推理-行动-环境建模-验证四位一体的执行基质；三层组织（接口 / 机制 / 多 agent 扩展）+ 七大应用域 + 六类开放挑战；GitHub Awesome 列表 YennNing/Awesome-Code-as-Agent-Harness-Papers
  - Agent Safety: SafeHarbor (arXiv 2605.05704, Z. Liu / Z. Ying / W. Zhang 等 8 作者, **ICML 2026 Accepted**, 2026-05-22 v2) 95 分 — 分层记忆增强 guardrail；增强对抗生成 + 本地分层记忆树 + 信息熵节点分裂/合并自演化；training-free + plug-and-play；GPT-4o 上 63.6% 良性效用 / 93%+ 拒绝率双 SOTA；开源 ljj-cyber/SafeHarbor
  - Benchmark: Boiling the Frog (arXiv 2605.22643, Bisconti / Prandi 等 14 作者, 2026-05-22 v2) 95 分 — 多轮有状态 agentic safety benchmark；持久 workspace + 增量风险注入 + 三级风险分类法（"温水煮青蛙" + EU AI Act 附件 I/III + GPAI 实践守则）；9 模型整体严格 ASR 44.4%；Claude Haiku 4.5 20.5% → Gemini 3.1 Flash Lite 92.9%（≈4.5× 跨度）；"实践守则失控"链路类别 ASR 93.3%
- 三方向叙事链："综述视角 / 第三条路 guardrail / 多轮范式拐点"——Code as Agent Harness 把过去半年 harness 工作组合成统一地图，SafeHarbor 是该综述 L2 机制层 "regression-free 改进" 的具体落地，Boiling the Frog 把过去所有单轮 agentic safety benchmark 都置于"需补多轮"的整改议程上
- 候选对比：Harness — Inference-Time Alignment Harnesses (90) / SkillOpt (92) / VIS Co-Scientists (87) / From Raw Experience (88)；Safety — SkillSafetyBench (93) / Misattribution Gap (92) / MemAudit (91) / DART (88)；Benchmark — What Twelve Papers Disclose (93) / Herculean (90) / CutVerse (88) / Knowledge Work Benchmarks (87)
- 三方向 index + 根 index 各插一条；count-badge 23/22/21 → 24/23/22
- 数据源：arXiv export API（这次返回正常）+ arxiv.org/abs/<id> 详细页

### 2026-05-23（每日 18:00）
- 三方向各 #1 发布
- 选定：
  - Harness: Life-Harness (arXiv 2605.22166, Tianshi Xu / Huifeng Wen / Meng Li 2026-05-21) 95 分 — 把"提升 agent 能力"从训练 LLM 挪到改 runtime 接口；契约 / 技能 / 动作 / 轨迹四维正交干预；7 环境 × 18 模型 = 126 设置中改进 116 个、平均相对提升 88.5%；从 Qwen3-4B-Instruct 一条轨迹演化的 harness 零成本转移到 17 个其他模型；评测使用 τ-bench / τ²-bench / AgentBench
  - Agent Safety: Latent-space Refusal Evasion (arXiv 2605.21706, Piras / Mura / Brau / Pintor / Oneto / Roli / Biggio 意大利对抗 ML 团队 2026-05-20) 94 分 — 把"消除拒绝方向"重写为针对线性探针的潜空间 evasion attack；揭示 mean-difference direction = Fisher 判别法向；ablation = 最小置信度逃避，停在决策边界；提出 controlled latent evasion 沿同方向推过边界进入合规域；15 模型（指令调优 / 多模态 / 推理）SOTA ASR；把 LLM 安全拉回经典对抗 ML 几何分析框架
  - Benchmark: SGR-Bench (arXiv 2605.22219, N. Li / H. Shen / M. Liu / Y. Han / Z. Shi / S. Xie / Yun Ma · 北京大学 PKUAIWeb 2026-05-21) 93 分 — 状态门控检索新任务族；100 任务 × 6 源族 × 12 公共数据生态（政府门户 / 统计局 / 专利库 / 地图 / 学术）；双问题表述（约束引导 vs 目标导向）；最强 search-agent 项级 F1 仅 66.18%；156 失败轨迹人工审计揭示 37.2% 检索范围漂移 + 27.6% 标准不匹配；已开源 huggingface.co/datasets/PKUAIWeb/SGR-BENCH
- 跨方向叙事："接口 / 几何 / 状态"——Life-Harness 用 runtime 接口替代训练；Latent-space Evasion 用对抗 ML 几何解释 abliteration；SGR-Bench 用状态门控揭示真实搜索难度；三者都把"经验黑箱"翻译成"可分析的结构"
- 候选汇总：The Log is the Agent (91) / Ratchet (90) / IdleSpec (87) / VIS Co-Scientists (88) / ExComm (91) / Implicit Safety Crowd (89) / Sycophancy Taxonomy (88) / MOOD (90) / SMDD-Bench (88) / AttuneBench (86) / Active Evidence Clinical (87)
- 已更新方向 index + 根 index 顶部 3 条；count-badge 22 / 21 / 20 → 23 / 22 / 21
- 备注：arXiv export API 仍 429；fallback list/cs.AI/new + abs/<id>

### 2026-05-21（每日 18:00）
- 三方向各 #1 发布
- 选定：
  - Harness: AgentAtlas (arXiv 2605.20530, Mazaheri & Mazaheri 2026-05-19) 94 分 — 6 状态 control-decision (Act/Ask/Refuse/Stop/Confirm/Recover) + 9 类 trajectory-failure 双轴正交 + 15 benchmark 覆盖审计 + taxonomy-aware vs blind 双 prompt；1,342 项 / 8 模型；移除 taxonomy 菜单 → trajectory accuracy 下降 14–40 pp，全部跌入 0.54–0.62 紧致带；无单一模型同时领先三轴
  - Agent Safety: CUGA Governance by Construction (arXiv 2605.20911, Shlomov/Shoham/Oved et al. 10 作者 2026-05-21, IBM) 93 分 — policy-as-code + 5 结构化执行检查点（Intent Guard / Playbook / Tool Guide / Tool Approvals / Output Formatter）；无需微调；healthcare demo；把 5-13 SKILL.md / 5-15 知-行 gap / 5-19 memory laundering / 5-20 ECA 缝合成统一架构
  - Benchmark: GrandGuard (arXiv 2605.20203, Fan/Yang et al. 12 作者) 92 分 — 3 级 50 类细粒度风险 / 10,404 prompts / 5 风险域（心理/财务/医疗/毒性/隐私）；leading LLM 误处理 50%+；fine-tuned Llama-Guard-3 96.2% / policy-enhanced gpt-oss-safeguard-20b 90.9%；提出 "contextual risk = prompt × population × context" 范式
- 跨方向叙事："评测面拓宽（AgentAtlas）→ 治理架构落地（CUGA）→ 风险定义升级（GrandGuard）"——9 类 trajectory failure 对位 5 检查点；contextual risk 与 policy-as-code 互补
- 候选淘汰：Insights Generator (91) / AgentCo-op (89) / CRUX (88) / Persona Vectors (90) / DPO≡RLHF (89) / SOLAR (87) / DeepWeb-Bench (91) / PlanningBench (90) / RealUserSim (88) / QuestBench (86)
- 维护：方向 index + 根 index 插入 3 条；count-badge 21/20/19 → 22/21/20
- commit a551b20，push 成功
- 数据源：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id>（export API 持续 429）

### 2026-05-20（今日 18:00）
- 三方向各 #1 完成
- 三篇：
  - Harness: DecisionBench (arXiv 2605.19099, Gao/Wang/Yu/Ma/Qu 2026-05-18) 94 分 — emergent delegation substrate；23,375 实例 / 11 模型 7 厂家 / 5 条件参考扫；mean quality |β|≤0.010 但 routing fidelity@1 7.5–29.5%；反事实上限 15–31 pp；HF 开源 substrate + 220 archives
  - Agent Safety: ECA / Hallucination as Exploit (arXiv 2605.19192, G. Zhang/H. Zheng/H. Yang 2026-05-18) 95 分 — 把 hallucination 重写为 authorization-failure；typed certificate + deterministic gate；1,900 红队 gate bypass 15%→1.3%；200/120 任务 unsafe 0%（Wilson 上界 2.67%/4.3%）；HACR 审计 naive 100%/prompt 49.6%/ECA 0%；7,488 GPT-5.4 oracle replay
  - Benchmark: POLAR-Bench (arXiv 2605.19127, Zheng/Yang/Gao/Schlag 2026-05-18) 93 分 — policy-aware adversarial；10 域 / 7,852 样本 / 5×5 诊断面；前沿 >99% 守住，1–30B 最弱漏 50%+；deterministic set-membership scoring
- 落点的"诊断学共振"：DecisionBench 反事实上限 / ECA HACR 审计 / POLAR-Bench 5×5 诊断面——三档评测方法学同时把"单一 ASR/任务通过率"打成不充分
- 候选未选：Formal Skill (91)、Library Drift (91)、SERL (88)、Agentic Trading (86~87)；Progressive Autonomy (91)、Trustworthy Agent Network (90)、Attention-Guided Jailbreak (88)、MOCHA (86)；How Far Are We From Auto-Research (90)、SimGym (86)
- 索引更新：三方向 index 顶部 + 根 index 顶部 3 条；count-badge 20→21 / 19→20 / 18→19
- 数据源：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id>；export API 仍 429

### 2026-05-19（每日 18:00）
- 三方向各 #1 完成
- 选定：
  - Harness: ANNEAL (arXiv 2605.16309, Hakim/Guo/Tan/Velasquez/Xu/Song 2026-05-04) 92 分 — 把 recurring failure 翻译成对 process knowledge graph 的 governed 符号补丁；FDKA = locate operator + 类型化补丁 + multi-dim score / symbolic guardrail / canary 三道闸门 + provenance + 确定性回滚；4 域 27 多 seed，复发故障率 0% 对照 ReAct/Reflexion 72–100%；去 FDKA 成功率 ↓26.7pp；GitHub sbhakim/anneal-agents
  - Agent Safety: Memory Laundering / State Contamination (arXiv 2605.16746, Y. Wang/Goyal/Y. Chen/Sundaram 2026-05-16) 93 分 — 首次定义 memory laundering 与 Sub-threshold Propagation Gap (SPG)；paired counterfactual multi-agent rollout；transcript reuse 驱动 overt toxicity / compressed memory 携带 sub-threshold 影响；干预位点决定缓解效果（必须前置到 summarization 之前）；把 safety 重定义为 state-control problem
  - Benchmark: MM-ToolBench / TOBench (arXiv 2605.16909, Z. Liu/W. Dong/Y. Tan/Y. Qu/H. Yin/C. Si 2026-05-16) 94 分 — 100 任务 × 2 macro 族 / 20 子类 × 27 MCP / 324 tools；closed-loop 多模态自校验；per-task grounded evaluator；半自动构建管线；Claude Opus 4.6 task success 32.0% vs 人类 94.0%；GitHub Pi3AI/TOBench
- 候选侧选：Harness AgentWall (90) / Multi-Paradigm buddyMe (88) / Skim (87) / ECC (86)；Safety AgentWall (91) / Provenance Position Paper (90) / Supply-chain Bullwhip (89) / Recall Isn't Enough (87)；Benchmark LinAlg-Bench (92) / PersonaArena (88) / Scientific Logicality (86) / PopuLoRA (85)
- 已更新方向 index + 根 index + count-badge 19/18/17 → 20/19/18
- 三方向通过 ANNEAL（修知识图）/ SPG（监测看不见的状态污染）/ closed-loop self-verify（产物自校验）形成"持久学习 + 状态安全 + 产物自验证"三轴对齐
- 搜索来源：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id>，arXiv export API 仍 429

### 2026-05-18（周一 18:00）
- 各方向 #1 完成
- 选题：
  - Harness: CAX-Agent (arXiv 2605.15218, Lin/Hai/He/Wang/Qiang/Yu 2026-05-12) 91 分 — 4 阶 recovery ladder（rule→model→context→human）+ 三层架构 + 450 跑次定级（model_only 0.9267 / 零干预 0.84 / κ=0.84 / Cliff's δ 0.81~0.87）
  - Agent Safety: Ensemble Monitoring for AI Control (arXiv 2605.15377, Koran/Yun/Tetef/Arnav/Bernabeu-Pérez 2026-05-14) 92 分 — 12 GPT-4.1-Mini monitor，diverse 集成 2.4× 同质，fine-tune 必选成员，"diversity > scale"
  - Benchmark: SaaS-Bench (arXiv 2605.15777, Shi/Li/Ma 等 16 作者 2026-05-15) 93 分 — 23 真 SaaS × 6 域 × 106 任务，weighted checkpoint，最强 CUA e2e &lt; 4%，开源 UniPat-AI/SaaS-Bench
- 候选：Harness STAR (90) / PRISM (89) / SDOF (88) / DeepSlide (85)；Safety SkillSmith (90) / Verifiable Agentic Infra (88) / Fair-outputs (87)；Benchmark PAGER (91) / RTL-BenchMT (90)
- 方向 index + 根 index 顶部插入；count-badge 18/17/16 → 19/18/17
- 三篇主题联动："过程显式化"——recovery ladder × monitor diversity × weighted checkpoint
- commit adb74b3，push 成功

### 2026-05-14（今日 18:00）
- 三方向 #1 完成
- 选定：
  - Harness: TRIAGE (arXiv 2605.13414, Al Nazi/Roy Dipta 2026-05-13) — 93 分。资源约束下的 prospective metacognitive control harness：self-calibrated budget + (S, π, a) 三合一 commit + oracle-grounded triage efficiency ratio；4 域（math/sci/code/multi-disc）× reasoning on/off。
  - Agent Safety: HAM³ (arXiv 2605.13213, H. Zhou et al. 2026-05-13, **CVPR 2026 accepted**) — 94 分。多模态多 agent 三层（perception/communication/reasoning）攻击 · GQA + ReAct/Plan-and-Solve/Reflexion · ASR 78.3% · reasoning-layer 最强 · 半数攻击致集体一致错误。
  - Benchmark: BenchJack (arXiv 2605.12673, H. Wang/Hanchen Li/Mang/Cheung/Sen/**Dawn Song** @ UC Berkeley 2026-05-12) — 95 分。给 agent benchmark 自身做红队：8 类 reward-hack taxonomy + Agent-Eval Checklist + 自动 coding agent 红队 + GAN-style patch loop · 10 benchmark 219 漏洞 · hackable 比 ~100% → <10% · 三轮全修 WebArena/OSWorld。
- 候选备选：Harness — Beyond Cooperative Simulators (PPol 2605.12894) 91 / When Attention Closes (GAR 2605.12922) 91；Safety — Sustaining AI safety (Mazzu 2605.12963) 91 / REVELIO (2605.12674) 88；Benchmark — Formal Conjectures (Lean 4, 2605.13171) 92 / VERA-MH (2605.13318) 90 / DisaBench (2605.12702) 89。
- 三方向 index + 根 index 更新，count-badge 16/15/14 → 17/16/15
- 主题统一：三篇都是"暴露新维度"——Harness 暴露第七维（前瞻性元认知）/ Safety 暴露 MM-MAS 三层攻击面 / Benchmark 暴露 benchmark 自身可被红队
- arXiv list/cs.AI/new + arxiv.org/abs/<id> 路线稳定可用，未触发 429

### 2026-05-13（前一次 18:00）
- 三方向 #1 完成
- 选定：Harness The Evaluation Differential (2605.11496) 94 / Safety SKILL.md (2605.11418) 95 / Benchmark TRIVIA+ (2605.11330) 93
- count-badge 15/14/13 → 16/15/14
- git push 成功 commit ebad5c9

### 2026-05-12（前两次 18:00）
- ComplexMCP / PRISM / Agent-ValueBench
- count 14/13/12 → 15/14/13；commit 1b631d6

### 2026-05-11
- AgentFloor / Skills as Verifiable Artifacts / ML-Bench&Guard
- count 13/12/11 → 14/13/12

### 经验汇总
- arXiv export.arxiv.org API 长期 429，fallback：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id> 稳定
- 三方向同日生成时刻意挑相互呼应主题（5-12 输入端外化/注册可信/价值漂移；5-13 声明语义/语义供应链/desiderata；5-14 第七维元认知/三层攻击面/benchmark 自审），增加报告之间的互文价值
- 候选备选保留 4–5 篇可让评分对比表更有说服力
- 序号逻辑严格遵循 ls 检测；同日多次触发须递增 N
- 根 index count-badge 三个分别在不同位置，需用上下文唯一定位（用 h2 标题作为锚点 Edit），避免 replace_all 误伤

### 2026-05-15（每日 18:00）
- 三方向 #1 全成
- 选定：
  - Harness: ChromaFlow (arXiv 2605.14102, Tarun Mittal 2026-05-13) 91 分 — GAIA-2023 L1 上做"加 orchestration 反而变差"的 negative ablation：54.72% → 50.94%，traceback/timeout/tool-failure/token-line/cost 全涨；倡议把 5 个操作量与 accuracy 一起 joint report；提出 bounded planner escalation / deterministic extraction / evidence reconciliation / explicit run gate 为评测 first-order requirements
  - Agent Safety: Knowing-Doing Gap in LLM Tool Use (arXiv 2605.14038, Cheng/Fan/JafariRaviz/Rezaei/Feiz 2026-05-13) 92 分 — 把 tool necessity 改写为 model-adaptive；隐藏态 cognition / execution 两 probe 在大多层对齐、但 last-layer × last-token 近正交；4 模型 mismatch 26.5–54%（算术）/ 30.8–41.8%（事实）；mismatch 集中在 cognition→action 转换
  - Benchmark: ClawForge (arXiv 2605.14133, Lai/Xia/Ji/Xiong/Zeng + Cihang Xie / Huaxiu Yao 等 11 作者 2026-05-13) 93 分 — generator-backed CLI agent benchmark，把"持久状态冲突"做 first-class；17 场景 / 6 能力 / 7 frontier 模型；最强 strict 仅 45.3%；模型间 17%–90%（区分量是"是否动手前看 state"）；错误状态替换 <17%（保守不前 > 激进破坏）；归一化末态 + 副作用评分 + strict/partial/step-efficiency 三档
- 候选未取：Harness 备选 Know-When-To-Fold-'Em (2605.14062) 90 / Unsteady Metrics (2605.14164) 90 / Evaluation Trap (2605.14167) 88；Safety Invisible Orchestrators (2605.13851) 90 / Grounded Continuation (2605.14175) 88；Benchmark MathAtlas (2605.14061) 90 / Collider-Bench (2605.13950) 87
- 三 index + 根 index：count-badge 17/16/15 → 18/17/16，根 index 顶部插入三条新条目
- 三篇报告共 982 行；commit cd4bafb，推送成功
- 报告间互链：Harness 引 ChromaFlow×TRIAGE 镜像、Safety 引知-行 gap 与 ChromaFlow 互镜、Benchmark 引 ClawForge × ChromaFlow × 知-行 gap 三向贯通——三篇形成 2026-05-15"评测面下沉"日主题
- 经验：arXiv API 仍 429；fallback 用 list/cs.AI/new + abs/<id> 稳定可用

### 2026-05-26（自动 18:00 三方向）
- 三方向 #1 各一篇
- 选定：
  - Harness: From Model Scaling to System Scaling (arXiv 2605.26112, Shangding Gu 独著, 2026-05-25) 95 → position paper + CheetahClaws Python-native reference harness + 与 Claude Code/OpenClaw 对比；7 大组件（FM/memory/context/skill-routing/orchestration/verification/governance）+ 3 大核心瓶颈（context governance/trustworthy memory/dynamic skill routing）+ 6 大评测维度（trajectory quality/memory hygiene/context efficiency/communication fidelity/verification cost/safe evolution）。
  - Agent Safety: Evo-Attacker (arXiv 2605.25389, Yan/Zhang/Hou/Li/Zhou/Hei/Zhang, **ACL 2026 main**, 2026-05-25) 94 → 把 LLM-MAS 工具攻击形式化为 self-evolving + memory-augmented RL；动态攻击记忆 + deliberative reasoning + Attack-Flow GRPO；揭示工具输出隐式信任攻击面，呼吁 defensive tool safeguards。
  - Benchmark: AgentHijack (arXiv 2605.25707, J. Sun/J. Zhu/Y. Li/T. Liu/X. Hu/Bo Han, **ICML 2026 accepted**, 2026-05-25) 95 → 把 computer-use agent robustness 评测从"对抗"挪到"无意环境腐蚀"；9 类 configurable corruption + AgentHijack-Agent（action generator + onlooker）；code/env/baseline/data 全开源。
- 三方向主题贯通："顶会接收 + 系统级范式 + 真实部署"——Harness 给系统级研究议程；Evo-Attacker 给长程攻击范式；AgentHijack 给"无意干扰" benchmark 全新范畴。今日无候选名单：Harness 内 Stop Comparing/DemoEvolve/EvalEng/Meta-Engineering Harness/AION；Safety 内 OpenClaw Security/A Sober Look at Agentic Misalignment/JT-SAFE-V2/Reasoning as Attack Surface/Inverting the Shield；Benchmark 内 MCP-TDP/Personalize-then-Store/SkillEvolBench/AI Cartography/AvalancheBench。
- 方向 index + 根 index 已更新，count-badge 25/24/23 → 26/25/24
- commit 9d89f89, push 成功（origin/main）
- 数据源：arxiv.org/list/cs.AI/new + arxiv.org/abs/<id>。export API 仍 0 字节，沿用 fallback 方案

### 2026-06-15（今日 18:00 — 三方向同步）
- 三方向 #1 各一篇 完成（commit + push 已执行）
- 选定：
  - Harness: HarnessX (arXiv 2606.14249, Darwin Agent Team 14 作者, 2026-06-12, CC BY 4.0) 94 分 — 把 agent harness 升级为"可组合 / 可适应 / 可演化" 铸造厂；9 维分类法 + Substitution Algebra 类型化原语 + 8 hook points + AEGIS trace-driven 多 agent 演化引擎（Digester → Planner → Evolver → Critic + 4 道 deterministic gating）；operational mirror 把 harness 演化形式化为符号空间 MDP；5 基准（ALFWorld / GAIA / WebShop / τ³-Bench / SWE-bench Verified）× 3 模型族（Claude Sonnet 4.6 / GPT-5.4 / Qwen3.5-9B）/ 14/15 配置有提升 / 平均 +14.5% 最高 +44.0%（ALFWorld + Qwen3.5-9B）；inverse-scaling + variant isolation +13.6% + Cross-Harness GRPO 共享 replay buffer 协同进化再 +4.7%；三大病理（reward hacking / catastrophic forgetting / under-exploration）防御；与 6-12 #1 HarnessBridge"可学习" + 6-14 #1 ToolSense"可审计"形成"可铸造 / 可学习 / 可审计"三档姿态
  - Safety: MINIM (arXiv 2606.13949, H. Yu / C. Zhang / H. Jin / S. Shi / N. Zhang / Y.T. Hou / W. Lou Virginia Tech + WUSTL, 2026-06-11, **ICML 2026 接收**, GitHub yyyyhx/MINIM, CC BY 4.0) 94 分 — 客户端可信本地代理；CI（Nissenbaum 2004）双分数（敏感度 s + 任务条件必要性 n）+ 三元 K/A/R 策略 + CI-aware 加权损失；GATv2 轻量本地推理；WebArena 662 测试集 TISL 降 89.9% / TCNP-I 99.31% / 节点保留 12% 远低于 Llama-3.3-70B 34.5% / 2FA 密码 Slack 通知 >99.9% 抑制；规模并非银弹（70B 反而 TISL 0.312 高于 8B 0.206）；A 抽象动作回收 +2.81pp TCNP-I；ONR/ARO/NSF 资助；与 6-12 #2 Containment Gap + 6-14 #1 Did You Lie? 形成"<em>检测 + 防御 + 客户端</em>" 三档安全栈
  - Benchmark: WorkBench Revisited (arXiv 2606.13715, Olly Styles 独著 COLM 2024 原作者, 2026-06-10, 8 页 / 3 图, CC BY 4.0) 93 分 — 纵向重测 21 模型；完成率 43% → 88.8% / 副作用 26% → 2.5%；Claude Opus 4.8 双双最佳；反共识结论"capability 与 safety 同向提升而非权衡"，前沿"几乎完全以无害方式失败"；透明披露 56 任务（约 14%）ground truth 修订（off-by-one / 答案键 / idxmin / 邮件 \\n / 工具描述 / search 上限 5→200）+ ReAct → native tool-calling（同 GPT-4 +8pp）；5 类错误演化分类；跨地缘格局（前沿高价西方专有 / 廉价高效中国开源 Kimi/DeepSeek/GLM/Qwen / 西方廉价 Haiku/mini/nano 被双面挤压）；建议年度刷新私有保留集
- 跨方向叙事："可演化 harness 铸造厂（HarnessX）+ 客户端可信代理（MINIM）+ 纵向重测自审基准（WorkBench Revisited）"——三轴姿态都把"agent 进步"重新定义；HarnessX 立 harness×model 协同进化；MINIM 立分层防护放弃模型 honesty 假设；WorkBench 用纵向证据证伪 capability-safety tradeoff（前提是模型对齐 + 系统治理）；三者合起来构成 2026 H1 后期 agent system 设计统一姿态：cloud model + edge broker（MINIM）+ middleware harness（HarnessX）+ longitudinal evaluation（WorkBench Revisited）四层栈
- 候选淘汰：Harness Every Eval Ever 90 / SkillAudit 88 / Coin Flip Judge 86 / FactoryLLM 85；Safety Skill-Conditional Reputation Attacks 91 / GNN Tools Defer 90 / Capability Minimization 89 / Contract-Based MARL Shielding 88 / Trust but Verify Medical 86；Benchmark StreamMemBench 90 / Poker Arena 88 / Every Eval Ever 87 / Trust but Verify 86 / FactoryLLM 85
- 索引更新：方向 index 三个顶部插入条目；根 index 顶部插入三条新条目；count-badge 33/32/31 → 34/33/32
- 报告间互链：Harness → HarnessX 引 Life-Harness / HarnessBridge / ToolSense / Code as Agent Harness / Lean4Agent / Darwin Gödel Machine / SICA / TextGrad / DSPy / ADAS / AFlow / GRPO；Safety → MINIM 引 Nissenbaum CI / WebArena / Mireshghallah / AirGapAgent / AgentDAM / ELK 不可能定理 / Containment Gap / Did You Lie? / Portcullis / MCP；Benchmark → WorkBench Revisited 引 原 WorkBench 2024 / ReAct / WebArena / AgentBench / GAIA / API-Bank / Reliability Gap / Boiling the Frog / AARRI / SciAgentArena / Containment Gap
- 数据源：arxiv.org/list/cs.AI/new + cs.LG/new（2026-06-15 提交清单）+ arxiv.org/html/<id>v1（详细数字 + 引用列表 + 资助方），arXiv export API 持续 429 沿用 fallback
