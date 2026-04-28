# FOR_AGENT.md — Agent 操作指南

> 本文件供 AI Agent（CodeBuddy）每次执行任务时读取，描述任务目标、操作步骤和输出规范。

---

## 任务目标

每天自动完成以下工作：
1. 搜索最新论文或高质量技术帖子（来源：arXiv、Semantic Scholar、LessWrong、AI Safety Forum 等）
2. 按评分体系筛选出最佳一篇/一篇帖子
3. 生成中文分析报告（HTML 格式），**所有引用内容必须注明出处和完整 URL**
4. 更新主页归档列表（index.html）
5. git push 到 GitHub 仓库，自动发布到 GitHub Pages

---

## 研究方向关键词

**方向一：Harness Engineering**
- 核心关键词：`prompt harness`, `LLM harness`, `evaluation harness`, `harness engineering`, `LLM evaluation framework`, `benchmark harness`
- 代表工具：EleutherAI lm-evaluation-harness, OpenAI evals, BIG-Bench
- 重点关注：如何设计可复现、可扩展的评估框架；harness 的工程实现方式

**方向二：Agent Skills Safety**
- 核心关键词：`agent safety`, `LLM agent skills`, `tool use safety`, `agentic AI safety`, `skill learning safety`, `autonomous agent alignment`
- 重点关注：Agent 在调用工具/技能时的安全边界；技能泛化带来的风险；对齐问题

**方向三：相关 Benchmark**
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
| 相关度 | 30% | 内容与三个研究方向的语义匹配程度 |
| 来源质量 | 25% | 顶会/顶刊(10) > arXiv 知名作者(8) > LessWrong 高 karma(7) > 普通预印本(5) |
| 近期影响力 | 20% | 近 3 个月引用数/下载量/帖子互动量 |
| 新颖性 | 15% | 是否提出新方法、新框架或深刻洞见 |
| 开源/可复现 | 10% | 有代码/数据集/可操作的工具链 |

选取**综合得分最高**的一篇作为当日推送内容。

### Step 3：生成 HTML 报告

文件路径：`papers/YYYY-MM-DD.html`（用当天日期命名）

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
- 使用 `papers/2026-04-28.html` 作为样式参考模板
- 保持响应式布局，手机和电脑均可正常显示
- 配色简洁，学术风格
- 所有外部链接在新标签页打开（`target="_blank" rel="noopener"`）
- 论文中所有引用的内容必须标注来源，格式：[作者, 年份] — [标题](URL)

### Step 4：更新主页

读取 `index.html` 当前内容，在 `<ul class="paper-list">` 内**顶部新增一个 `<li>` 条目**，格式完全参照现有条目：
- 日期徽章（月份 + 日期）
- 论文/帖子标题（中文）
- 来源平台 + 第一作者 + 方向标签
- 评分 Pill

### Step 5：提交推送

```bash
cd /Users/yangjiahu/Desktop/workspace/temp_USTC/Daily-Paper-Anqi-Test
git add papers/YYYY-MM-DD.html index.html
git commit -m "daily: YYYY-MM-DD 报告 — <内容标题简短描述>"
git push origin main
```

---

## 输出规范

- HTML 文件编码：UTF-8
- 日期格式：`YYYY-MM-DD`（如 `2026-04-28`）
- commit message 格式：`daily: YYYY-MM-DD 报告 — <标题关键词>`
- **所有引用内容必须注明来源和完整可访问 URL**
- 不得修改 `FOR_AGENT.md` 和 `README.md`（除非用户明确要求）

---

## 错误处理

- 若当天没有高度相关的新论文（相关度得分 < 5），改搜近 7 天内容，或转为搜索 LessWrong/Alignment Forum 高质量帖子
- 若 arXiv 接口无响应，改用 Semantic Scholar
- 若 WebFetch 无法访问某 URL，记录失败原因并尝试备用来源
- 若 git push 失败，将报告文件保存后记录错误，下次执行时一并推送
