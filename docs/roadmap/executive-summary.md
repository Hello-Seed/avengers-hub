# 执行摘要：3 个月 AI Agent 工程师转型路线

> 写给自己：用 5 分钟看懂全局

---

## 我现在在哪里

- 多年前端工程师，JavaScript/TypeScript 熟练
- 已在腾讯云部署了 OpenClaw + 6 个 AI agent（复仇者团队）
- 已接通 Telegram、火山方舟 LLM API、SQLite 任务系统
- **核心缺口**：没有 RAG、没有 Eval、没有系统化的 prompt 工程、没有自定义 skills

---

## 未来 3 个月主线

```
月 1：Python 扎基础 + LLM 工程 + 工具调用
    ↓
月 2：RAG 实战 + 单 Agent 工作流 + OpenClaw Skills 开发
    ↓
月 3：多 Agent 协作深化 + Eval + 部署工程化 + 作品集打磨
```

---

## 为什么这条路适合我

1. **不绕弯路**：直接从我已有的 OpenClaw 项目出发，每天学习都能立刻用在现有系统上
2. **工程优先**：不学算法、不看论文，学完就做项目，项目直接进 GitHub
3. **前端优势复用**：TypeScript / Node.js 在 agent 工程里价值很高，不浪费积累
4. **真实部署环境**：很多人学 agent 只有本地环境，我有云服务器 + 生产系统，差异明显
5. **兼顾中国 + 海外**：国内用 OpenClaw + 火山方舟，海外用 LangChain + Anthropic/OpenAI

---

## 最关键的 3 个学习重点

### 1. RAG（检索增强生成）
- **为什么是第一**：Agent 没有知识库等于没有记忆，RAG 是让 agent 能用的核心能力
- **我要达到什么程度**：能独立搭建向量索引、写检索逻辑、集成进现有 agent

### 2. Context Engineering（上下文工程）
- **为什么重要**：同样的模型，prompt 好与差，输出质量差 3-5 倍
- **我要达到什么程度**：能系统设计 system prompt，知道如何用 few-shot、chain-of-thought

### 3. OpenClaw Skills 开发
- **为什么重要**：Skills 是让 agent 真正有"手"的关键，目前我的 agent 什么工具都没有
- **我要达到什么程度**：能自己写 skill，让 agent 能搜索、写文件、调 API、执行代码

---

## 最关键的 3 个项目

### 项目 A：个人知识库 RAG 系统
- 把我的笔记、文章、收藏整理成向量数据库
- Friday agent 能查询这个知识库来回答我的问题
- **GitHub 价值**：展示 RAG 工程实现，面试必讲

### 项目 B：AI 信息日报 Agent 工作流
- 基于现有 collector bot，设计完整的"收集→分析→生成日报→推送"工作流
- 用 LangGraph 或 OpenClaw 实现有状态的工作流
- **GitHub 价值**：展示单 agent 完整工程，有真实用户（自己）

### 项目 C：OpenClaw 自定义 Skills 套件
- 为复仇者团队开发 5 个实用 skill：网页搜索、代码执行、日历管理、笔记写入、GitHub 操作
- **GitHub 价值**：展示对 OpenClaw 平台的深度理解，国内 OpenClaw 社区价值高

---

## 最重要的输出目标

3 个月后，我应该拥有：

| 输出 | 具体形式 |
|------|---------|
| GitHub 仓库 | 3 个有完整 README 的项目仓库 |
| 可演示 Demo | RAG 查询 + 日报自动生成 + agent 工具调用 |
| 技术文章 | 至少 3 篇写实践经验的中文技术文章（掘金/知乎） |
| 简历更新 | "AI Agent 工程师"方向的新版简历 |
| 英文 README | 核心项目有双语 README，为海外求职准备 |

---

## 风险提醒

- **最大风险**：只看资料不动手。解法：每天必须有代码产出
- **第二风险**：跑偏去学算法/训练模型。解法：只要不是工程实现就跳过
- **第三风险**：OpenClaw 生态小，遇到问题没人问。解法：遇到问题就 hack，读源码，记录在博客里
