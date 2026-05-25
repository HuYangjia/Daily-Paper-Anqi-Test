# 自动化任务记忆 · automation-1777448333632
> 每日 18:00 三方向论文追踪

## 执行历史摘要

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
