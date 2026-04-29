# FOR_AGENT.md — Agent 操作指南

> 本文件供 AI Agent（CodeBuddy）每次执行任务时读取，描述任务目标、操作步骤和输出规范。

---

## 任务目标

每次执行（定时或手动触发）完成以下工作：
1. 搜索最新论文或高质量技术帖子（来源：arXiv、Semantic Scholar、LessWrong、AI Safety Forum 等）
2. 按评分体系从候选中筛选出最佳一篇
3. 判断本次执行属于哪个研究方向（定时任务轮流推进；手动触发时由 prompt 指定方向）
4. 生成中文分析报告（HTML 格式），**所有引用内容必须注明出处和完整 URL**
5. 更新对应方向的 `<方向目录>/index.html` 归档列表
6. 更新根 `index.html` 最近报告列表（顶部插入新条目）
7. git push 到 GitHub 仓库，自动发布到 GitHub Pages

---

## 仓库目录结构

```
Daily-Paper-Anqi-Test/
├── index.html                    ← 总入口导航（三方向卡片 + 最近报告汇总）
├── FOR_AGENT.md                  ← 本文件
├── README.md
├── harness/                      ← 方向一：Harness Engineering
│   ├── index.html                ← 方向归档列表
│   ├── YYYY-MM-DD-1.html         ← 当日第1篇
│   ├── YYYY-MM-DD-2.html         ← 当日第2篇（手动追加，不覆盖）
│   └── ...
├── agent-safety/                 ← 方向二：Agent Skills Safety
│   ├── index.html
│   └── YYYY-MM-DD-N.html
└── benchmark/                    ← 方向三：Safety Benchmark
    ├── index.html
    └── YYYY-MM-DD-N.html
```

**绝对本地路径**：`/Users/yangjiahu/Desktop/workspace/temp_USTC/Daily-Paper-Anqi-Test`

---

## 研究方向关键词

**方向一：Harness Engineering（目录名：`harness`）**
- 核心关键词：`prompt harness`, `LLM harness`, `evaluation harness`, `harness engineering`, `LLM evaluation framework`, `benchmark harness`
- 代表工具：EleutherAI lm-evaluation-harness, OpenAI evals, BIG-Bench
- 重点关注：如何设计可复现、可扩展的评估框架；harness 的工程实现方式

**方向二：Agent Skills Safety（目录名：`agent-safety`）**
- 核心关键词：`agent safety`, `LLM agent skills`, `tool use safety`, `agentic AI safety`, `skill learning safety`, `autonomous agent alignment`
- 重点关注：Agent 在调用工具/技能时的安全边界；技能泛化带来的风险；对齐问题

**方向三：Safety Benchmark（目录名：`benchmark`）**
- 核心关键词：`safety benchmark`, `agent benchmark`, `LLM safety evaluation`, `red teaming benchmark`, `alignment benchmark`, `RLHF benchmark`
- 代表 Benchmark：AgentBench, SafetyBench, HarmBench, TrustLLM, AIR-Bench
- 重点关注：如何科学衡量 Agent 的安全性和能力边界

**来源渠道（按优先级）**：
1. arXiv cs.AI / cs.LG / cs.CL（最新预印本）
2. Semantic Scholar（高引用趋势）
3. ACL Anthology / NeurIPS / ICML / ICLR Proceedings
4. LessWrong（`https://www.lesswrong.com/`）— AI Safety 顶级技术帖子
5. AI Alignment Forum（`https://www.alignmentforum.org/`）
6. GitHub Trending（harness 工具类）

**排除**：纯硬件加速论文、与 AI Agent 无关的 Safety 研究（如自动驾驶安全）

---

## 操作步骤（每次执行）

### Step 0：确定本次方向和文件序号

**确定方向**：
- 定时任务：按 harness → agent-safety → benchmark 轮流，根据三个目录中最新文件日期判断哪个方向最久未更新，选该方向
- 手动触发：从 prompt 中读取指定方向（如 "为 harness 方向生成一篇新报告"）

**确定文件序号（防覆盖核心逻辑）**：
```bash
# 以 harness 方向为例，当天日期为 YYYY-MM-DD
ls /Users/yangjiahu/Desktop/workspace/temp_USTC/Daily-Paper-Anqi-Test/harness/YYYY-MM-DD-*.html 2>/dev/null | wc -l
# 若输出为 0，则本次序号为 1；若输出为 N，则本次序号为 N+1
```
最终文件名格式：`<方向目录>/YYYY-MM-DD-<N>.html`
例如：`harness/2026-04-29-1.html`、`harness/2026-04-29-2.html`（同日第二次触发）

### Step 1：搜索候选内容

**arXiv API 搜索（每个方向各搜一次）**：
```
http://export.arxiv.org/api/query?search_query=ti:"harness engineering" OR ti:"evaluation harness"&sortBy=submittedDate&sortOrder=descending&max_results=10
http://export.arxiv.org/api/query?search_query=ti:"agent safety" OR abs:"agent skills safety"&sortBy=submittedDate&sortOrder=descending&max_results=10
http://export.arxiv.org/api/query?search_query=ti:"safety benchmark" OR ti:"agent benchmark" OR ti:"alignment benchmark"&sortBy=submittedDate&sortOrder=descending&max_results=10
```

**Semantic Scholar API**：
```
https://api.semanticscholar.org/graph/v1/paper/search?query=LLM+agent+safety+benchmark&fields=title,authors,year,venue,citationCount,externalIds,abstract&limit=10
```

**LessWrong / Alignment Forum**：使用 WebFetch 抓取最新高赞帖子（热度 > 100 karma）：
```
https://www.lesswrong.com/tag/ai-safety
https://www.alignmentforum.org/
```

目标：收集 **5～10 篇候选论文或帖子**。

### Step 2：评分筛选

对每篇候选内容按以下维度打分（0～10 分），加权求和：

| 维度 | 权重 | 评分依据 |
|------|------|---------|
| 相关度 | 30% | 内容与本次方向关键词的语义匹配程度 |
| 来源质量 | 25% | 顶会/顶刊(10) > arXiv 知名作者(8) > LessWrong 高 karma(7) > 普通预印本(5) |
| 近期影响力 | 20% | 近 3 个月引用数/下载量/帖子互动量 |
| 新颖性 | 15% | 是否提出新方法、新框架或深刻洞见 |
| 开源/可复现 | 10% | 有代码/数据集/可操作的工具链 |

选取**综合得分最高**且**未在此前报告中出现过**的一篇作为本次推送内容。

### Step 3：生成 HTML 报告

**文件路径**：`<方向目录>/YYYY-MM-DD-<N>.html`（N 由 Step 0 确定）

报告必须包含以下部分，**每处引用均须附完整 URL**：

```
1. 内容基本信息
   - 标题（英文原文 + 中文翻译）
   - 作者/发布者、机构/平台
   - 发表期刊/会议/论坛
   - 原文链接（完整 URL，可点击）
   - arXiv 链接 / DOI（如有）
   - 综合评分及各维度得分

2. 一句话核心贡献（中文，30 字以内）

3. 摘要/内容概述翻译（中文，忠实原文）

4. 核心内容解读（中文，400～600 字）
   - 解决了什么问题（背景与动机）
   - 核心方法/观点/框架
   - 与现有工作的主要区别或突破点

5. 关键引用与出处（该论文/帖子本身引用的重要文献）
   - 每条引用须附：标题 + 作者 + 链接

6. 实验结果/核心数据亮点（列举 2～3 个关键数据点或核心论点）

7. 对研究方向的启发
   - 分别说明对 Harness Engineering / Agent Safety / Benchmark 方向的启发

8. 相关延伸阅读（2～3 篇相关论文/帖子，附链接）

9. 开源资源
   - GitHub 链接（如有）
   - 数据集链接（如有）
   - 在线 Demo / 工具链接（如有）
```

报告样式要求：
- 使用 `harness/2026-04-28-1.html` 作为样式参考模板（含候选对比表格、评分 chip、方向启发三栏等完整结构）
- 面包屑导航：`← 总导航 / <方向名>` → 链接指向 `../../index.html` 和 `../index.html`
- 页脚返回链接：指向 `../index.html`（方向归档页）
- 所有外部链接在新标签页打开（`target="_blank" rel="noopener"`）

### Step 4：更新方向归档页

读取 `<方向目录>/index.html`，在 `<ul class="paper-list">` 内**顶部新增一个 `<li>` 条目**：
- 日期徽章（月份 + 日期，颜色与方向一致）
- `#N` 序号徽章
- 论文/帖子标题（中文）
- 来源平台 + 第一作者
- 评分 Pill

同时将方向卡片中的 `count-badge` 数字 +1（读取当前数字再更新）。

### Step 5：更新根 index.html

读取根 `index.html`，在 `<ul class="paper-list">` 内**顶部新增一个 `<li>` 条目**：
- 日期徽章
- 方向标签（`tag-harness` / `tag-safety` / `tag-bench`，颜色区分）
- 论文标题 + 序号（`#N`）
- 评分 Pill

链接指向 `<方向目录>/YYYY-MM-DD-<N>.html`。

### Step 6：提交推送

```bash
REPO=/Users/yangjiahu/Desktop/workspace/temp_USTC/Daily-Paper-Anqi-Test
cd $REPO
git add <方向目录>/YYYY-MM-DD-<N>.html <方向目录>/index.html index.html
git commit -m "daily: YYYY-MM-DD <方向名> #<N> — <内容标题简短描述>"
git push origin main
```

---

## 输出规范

- HTML 文件编码：UTF-8
- 日期格式：`YYYY-MM-DD`（如 `2026-04-29`）
- 序号格式：整数，从 1 开始，同日同方向追加（如 `-1`、`-2`）
- commit message 格式：`daily: YYYY-MM-DD <方向名> #<N> — <标题关键词>`
- **所有引用内容必须注明来源和完整可访问 URL**
- 不得修改 `FOR_AGENT.md` 和 `README.md`（除非用户明确要求）
- 不得删除或覆盖已有的报告文件

---

## 错误处理

- 若当天没有高度相关的新论文（相关度得分 < 5），改搜近 7 天内容，或转为搜索 LessWrong/Alignment Forum 高质量帖子
- 若 arXiv 接口无响应，改用 Semantic Scholar
- 若 WebFetch 无法访问某 URL，记录失败原因并尝试备用来源
- 若 git push 失败，将报告文件保存后记录错误，下次执行时一并推送
- 若同日同方向已有 3 篇以上，提示用户是否继续（避免重复内容）
