# GitHub 展示规划

> 3 个月后，GitHub 应该能清晰讲述一个故事：  
> "我是一个从前端转型 AI Agent 工程师的工程师，我做了真实系统，不只是跟教程。"

---

## 一、整体 GitHub 结构规划

### 核心仓库（3 个项目仓库 + 1 个主仓库）

| 仓库名 | 定位 | 优先级 |
|--------|------|-------|
| `avengers-ai-team` | 生产级多 Agent 系统，OpenClaw 驱动 | ⭐⭐⭐ 最重要 |
| `personal-rag` | 个人知识库 RAG 系统 | ⭐⭐⭐ 最重要 |
| `daily-digest-agent` | LangGraph 自动日报工作流 | ⭐⭐⭐ 重要 |
| `avengers-skills` | OpenClaw 自定义 Skills 套件 | ⭐⭐ 加分项 |
| `openclaw-ai`（本仓库） | 转型文档和路线图（这个仓库） | ⭐ 背景故事 |

### GitHub Profile README

你的 GitHub Profile（github.com/你的用户名）应该有一个特别的 README，展示：

```markdown
# Hi, I'm [名字] 👋

I'm an AI Agent Engineer specializing in building production agent systems.

## What I Build
- 🤖 Multi-agent systems with OpenClaw
- 🔍 RAG-powered knowledge bases
- 🔄 Automated workflows with LangGraph

## Current Projects
- [Avengers AI Team](链接) - 6-agent collaborative system
- [Personal RAG](链接) - Knowledge base with semantic search
- [Daily Digest Agent](链接) - Automated information workflow

## Tech Stack
Python · TypeScript · LangChain · LangGraph · ChromaDB · OpenClaw
```

---

## 二、每个仓库的 README 组织方式

### 通用结构（每个仓库都应该有）

```markdown
# 项目名

一句话说清这个项目是什么、解决什么问题。

## 效果展示
[最重要的部分，放在最前面]
- 截图或 GIF
- 或者在 Telegram 里的实际使用截图

## 架构
[Mermaid 图]

## 技术栈
| 组件 | 技术选型 | 选择原因 |
|------|---------|---------|

## 快速开始
[能让别人 10 分钟内跑起来]

## 功能特性

## 项目背景（为什么做这个）

## 经验总结 / Lessons Learned
[这是加分项，展示你不只是写代码，还在思考]
```

### 中英双语策略

- README.md = 中文（主要面向国内求职）
- README_EN.md = 英文（面向海外求职，可以是机器翻译初稿 + 自己修改）
- 代码注释：英文（国际惯例）
- commit message：英文（国际惯例）

---

## 三、哪些项目值得单独展示

### 必须独立仓库展示
1. **avengers-ai-team**：你的核心项目，展示生产级 agent 系统能力
2. **personal-rag**：展示 RAG 工程能力，面试必讲
3. **daily-digest-agent**：展示 LangGraph 工作流能力

### 可以合并在同一仓库
- avengers-skills 里的各个 skill，放在同一个仓库
- 学习笔记和路线图（openclaw-ai，即本仓库）

---

## 四、哪些内容适合公开

### 可以公开
- ✅ 项目架构和代码（去掉 API key）
- ✅ 学习笔记和路线图（这个仓库）
- ✅ 技术文章链接
- ✅ Telegram bot 的截图（展示效果）
- ✅ 系统设计文档

### 不能公开
- ❌ API keys、密码、token（用 .env 管理）
- ❌ 服务器 IP 和 SSH 凭据
- ❌ 包含个人信息的日志

### 建议私有或谨慎处理
- ⚠️ Telegram 消息记录（涉及个人隐私）
- ⚠️ 个人知识库的具体内容

---

## 五、哪些内容适合整理成 Case Study

### Case Study 1：从 Python 脚本到 Agent 工作流

**故事线**：
- 起点：`daily_summary.py` 是一个 300 行脚本
- 问题：失败了没有恢复，不知道哪一步出错，无法扩展
- 解法：用 LangGraph 重构成有状态工作流
- 结果：节点级错误恢复，可观测，可扩展

**适合发布平台**：掘金、知乎、个人博客

---

### Case Study 2：为什么 RAG 比 Fine-tuning 更适合个人知识库

**故事线**：
- 问题：Friday 不记得我告诉过它的事情
- 方案对比：Fine-tuning vs RAG（成本、时效、工程复杂度）
- 实施：ChromaDB + Telegram 消息索引
- 效果：查询"我之前研究过什么"有实际结果对比

**适合发布平台**：掘金、微信公众号

---

### Case Study 3：OpenClaw 多 Agent 系统实战：6 个 AI 角色如何协作

**故事线**：
- 背景：复仇者团队的设计思路
- 挑战：任务分解、结果汇总、工具调用
- 实现：OpenClaw + 自定义 Skills
- 效果：复杂任务的协作完成率

**适合发布平台**：掘金（有 OpenClaw 用户群体）

---

## 六、如何为后续简历和求职做准备

### 简历更新节奏

| 时间 | 操作 |
|------|------|
| Month 1 结束 | 在简历里加一行"项目：个人知识库 RAG 系统（开发中）" |
| Month 2 结束 | 更新为完整的项目描述 + GitHub 链接 |
| Month 3 结束 | 完整的 AI Agent 工程师方向简历，附 GitHub profile |

### 投递前的 Checklist

- [ ] GitHub Profile 有完整介绍
- [ ] 3 个核心仓库 README 完整，有截图
- [ ] 每个仓库有 `.env.example` 说明（而不是 `.env`）
- [ ] 代码能在新环境跑起来（别人能复现）
- [ ] 至少 1 篇技术文章（掘金/知乎）
- [ ] 简历里的 GitHub 链接能打开且内容匹配描述

### 国内投递重点展示

1. **OpenClaw 经验**（OpenClaw 社区认知度高）
2. **中文注释和文档**（展示沟通能力）
3. **具体的业务场景**（每天用的日报、知识库）

### 海外投递重点展示

1. **英文 README**（必须）
2. **LangChain/LangGraph 经验**（海外主流框架）
3. **技术深度**（架构决策原因、Eval 数据、性能对比）
4. **贡献记录**（commit 历史清晰）

---

## 七、长期展示规划（3 个月后）

3 个月后，这个 GitHub 应该展示：

```
github.com/[你]
├── 📌 avengers-ai-team     ⭐ Multi-agent production system
├── 📌 personal-rag          ⭐ Knowledge base with RAG
├── 📌 daily-digest-agent    ⭐ Automated agent workflow
├── 📌 avengers-skills       OpenClaw custom skills
└── 📌 openclaw-ai           AI Agent learning journey (this repo)
```

**3 个月后能对面试官说的话**：

> "我有一套运行在生产服务器上的 6 个 AI Agent 协作系统，我为它开发了 RAG 知识库和自动日报工作流，每天在用。代码都在 GitHub 上，有架构图和 Demo。"

这句话的每一个词都有对应的 GitHub 证据。
