# Daily Paper Tracker — Anqi Test

> 每天自动追踪指定研究方向的最新论文，由 AI Agent 完成搜索、筛选、分析与中文讲解，并发布到 GitHub Pages。

## 网站地址

**[https://huyangjia.github.io/Daily-Paper-Anqi-Test/](https://huyangjia.github.io/Daily-Paper-Anqi-Test/)**

## 这个仓库是干什么的

本仓库是一个自动化 + 手动精选并存的科研论文追踪系统：

- **每天中午 12:00**，AI Agent 自动从 arXiv / Semantic Scholar 搜索指定方向的最新论文
- 按照多维评分体系筛选出当日最值得读的一篇
- 生成包含中文摘要、方法解读、核心贡献的 HTML 报告
- 支持新增你手动挑选的论文与分析，统一发布到同一网站
- 自动 `git push` 到本仓库，GitHub Pages 实时发布上线

## 目录结构

```
Daily-Paper-Anqi-Test/
├── index.html              # 主页：所有历史报告的归档列表
├── harness/                # 方向一：Harness Engineering
├── agent-safety/           # 方向二：Agent Skills Safety
├── benchmark/              # 方向三：Safety Benchmark
├── my-papers/              # 你的手动精选论文与分析
│   ├── index.html
│   └── YYYY-MM-DD-N.html
├── FOR_AGENT.md            # Agent 操作指南（AI 读取，人类也可看）
└── README.md               # 本文件
```

## 论文评分维度

| 维度 | 权重 | 说明 |
|------|------|------|
| 相关度 | 30% | 与研究方向关键词的匹配程度 |
| 期刊/会议质量 | 25% | NeurIPS / ICML / Nature 等顶刊优先 |
| 近期引用趋势 | 20% | 近 6 个月引用速度 |
| 新颖性 | 15% | 方法是否突破现有框架 |
| 开源复现度 | 10% | 是否有代码/数据集 |

## 如何运行

本系统通过 CodeBuddy Automation 自动运行，无需手动操作。
如需手动触发，可在 CodeBuddy 中执行 `FOR_AGENT.md` 中描述的任务。
