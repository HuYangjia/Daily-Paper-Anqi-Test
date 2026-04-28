# FOR_AGENT.md — Agent 操作指南

> 本文件供 AI Agent（CodeBuddy）每次执行任务时读取，描述任务目标、操作步骤和输出规范。

---

## 任务目标

每天自动完成以下工作：
1. 搜索今日最新论文（来源：arXiv、Semantic Scholar）
2. 按评分体系筛选出最佳一篇
3. 生成中文分析报告（HTML 格式）
4. 更新主页归档列表（index.html）
5. git push 到 GitHub 仓库，自动发布到 GitHub Pages

---

## 研究方向关键词

> ⚠️ 待用户填写。格式示例如下：

```
方向：扩散模型 / Diffusion Model
关键词：diffusion model, score matching, denoising, generative model
排除：video generation（与方向不相关的子领域）
```

---

## 操作步骤（每次执行）

### Step 1：搜索论文

使用以下接口搜索最近 3 天发布或更新的论文：

- **arXiv API**：`http://export.arxiv.org/api/query?search_query=<关键词>&sortBy=submittedDate&sortOrder=descending&max_results=20`
- **Semantic Scholar**：按关键词搜索，筛选近期高引用

目标：收集 5～10 篇候选论文。

### Step 2：评分筛选

对每篇候选论文按以下维度打分（0～10 分），加权求和：

| 维度 | 权重 | 评分依据 |
|------|------|---------|
| 相关度 | 30% | 标题/摘要与关键词的语义匹配度 |
| 期刊/会议质量 | 25% | 顶刊/顶会（NeurIPS、ICML、ICLR、Nature 等）得高分 |
| 近期引用趋势 | 20% | 近 6 个月引用增速；新论文可用下载量估算 |
| 新颖性 | 15% | 是否提出新方法/新框架，而非增量改进 |
| 开源复现度 | 10% | 有 GitHub 代码库 +3 分，有数据集 +2 分 |

选取**综合得分最高**的一篇作为当日论文。

### Step 3：生成 HTML 报告

文件路径：`papers/YYYY-MM-DD.html`（用当天日期命名）

报告必须包含以下部分：

```
1. 论文基本信息
   - 标题（英文原文 + 中文翻译）
   - 作者、机构
   - 发表期刊/会议
   - arXiv 链接 / DOI
   - 综合评分及各维度得分

2. 一句话核心贡献（中文，30 字以内）

3. 摘要翻译（中文，忠实原文）

4. 方法解读（中文，300～500 字）
   - 解决了什么问题
   - 用了什么方法/框架
   - 与以往方法的主要区别

5. 核心图表说明（如有，描述论文中关键图的含义）

6. 实验结果亮点（中文，列举 2～3 个关键数据点）

7. 对我的研究启发（结合用户研究方向，100 字以内）

8. 开源资源
   - GitHub 链接（如有）
   - 数据集链接（如有）
```

报告样式要求：
- 使用 `papers/2026-04-28.html` 作为样式模板
- 保持响应式布局，手机和电脑均可正常显示
- 配色简洁，学术风格

### Step 4：更新主页

更新 `index.html`，在归档列表顶部**新增一行**当日报告的链接。格式参考现有条目。

### Step 5：提交推送

```bash
cd /path/to/Daily-Paper-Anqi-Test
git add papers/YYYY-MM-DD.html index.html
git commit -m "daily: YYYY-MM-DD 论文报告 — <论文标题简短描述>"
git push origin main
```

---

## 输出规范

- HTML 文件编码：UTF-8
- 日期格式：`YYYY-MM-DD`（如 `2026-04-28`）
- commit message 格式：`daily: YYYY-MM-DD 论文报告 — <标题关键词>`
- 不得修改 `FOR_AGENT.md` 和 `README.md`（除非用户明确要求）

---

## 错误处理

- 若当天没有高度相关的新论文（相关度得分 < 5），放宽搜索范围（扩大关键词）并记录原因
- 若 arXiv 接口无响应，改用 Semantic Scholar
- 若 git push 失败，在报告文件末尾追加错误记录，下次执行时一并推送
