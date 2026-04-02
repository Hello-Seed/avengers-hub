# 学习资料清单

> 原则：权威来源优先，有链接，说清楚为什么推荐、看什么部分

---

## 一、LLM 基础

### 1.1 大模型工作原理（够用即可，不深究）

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Andrej Karpathy - Intro to LLMs | 视频 | 1 小时讲清 LLM 本质，前端工程师能懂 | 全看，重点看 tokenization 和 context 部分 | https://www.youtube.com/watch?v=zjkBMFhNj_g |
| The Illustrated Transformer | 博客 | 图文并茂，transformer 结构最清晰的入门 | attention 机制那一节 | https://jalammar.github.io/illustrated-transformer/ |
| OpenAI Tokenizer | 工具 | 直观感受 token 是什么 | 随便输入中英文感受 | https://platform.openai.com/tokenizer |

---

## 二、Prompt Engineering / Context Engineering

### 2.1 核心资料

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Anthropic Prompt Engineering 官方指南 | 官方文档 | Anthropic 官方出品，最权威，质量高 | 全部章节，尤其 system prompt 设计 | https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview |
| OpenAI Prompt Engineering 指南 | 官方文档 | 覆盖面广，有实际例子 | few-shot、chain-of-thought、format output | https://platform.openai.com/docs/guides/prompt-engineering |
| Prompt Engineering Guide（DAIR.AI） | 仓库/网站 | 社区整理，覆盖全面，中文版可用 | CoT、Self-Consistency、ReAct 部分 | https://www.promptingguide.ai/zh |
| Anthropic - Be Clear and Direct | 官方文档 | 具体讲如何写好 system prompt | 全部，这是实操指南 | https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/be-clear-and-direct |

### 2.2 Context Engineering（进阶）

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Anthropic - Long context tips | 官方文档 | 讲如何在长上下文窗口里高效使用 token | 文档放置位置、引导模型关注特定内容 | https://docs.anthropic.com/en/docs/build-with-claude/long-context-tips |
| Simon Willison - Context is Everything | 博客 | 讲清楚 context engineering 的本质 | 全文 | https://simonwillison.net/2025/Jun/27/context-engineering/ |

---

## 三、RAG（检索增强生成）

### 3.1 概念入门

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| LangChain - RAG Tutorial | 官方文档 | 官方出品，从索引到检索到生成完整流程 | Conceptual guide + Tutorials | https://python.langchain.com/docs/tutorials/rag/ |
| LlamaIndex - RAG Basics | 官方文档 | 另一个主流框架，思路稍有不同 | Starter Tutorial，SimpleVectorStoreIndex | https://docs.llamaindex.ai/en/stable/getting_started/starter_example/ |
| Pinecone - What is RAG | 博客 | 图文并茂，讲清楚 retrieval 的本质 | 全文，重点是 chunking 策略 | https://www.pinecone.io/learn/retrieval-augmented-generation/ |

### 3.2 向量数据库

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| ChromaDB 官方文档 | 官方文档 | 本地可用、开源、适合入门和中小项目 | Getting Started + Collections | https://docs.trychroma.com/getting-started |
| FAISS（Meta）文档 | 官方文档 | CPU 可跑、无需网络、最轻量选择 | Getting Started | https://faiss.ai/index.html |
| Qdrant 快速入门 | 官方文档 | 功能更强，适合后期用 | Quickstart | https://qdrant.tech/documentation/quickstart/ |

### 3.3 Embedding 模型

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| OpenAI Embeddings 指南 | 官方文档 | 讲清楚 embedding 的用法和最佳实践 | Use cases + FAQ | https://platform.openai.com/docs/guides/embeddings |
| MTEB Leaderboard | 排行榜 | 选 embedding 模型的参考，选中文模型看这里 | Chinese retrieval 榜单 | https://huggingface.co/spaces/mteb/leaderboard |

---

## 四、Agent 基础

### 4.1 核心概念

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Anthropic - Build Effective Agents | 官方文档 | Anthropic 官方最佳实践，2024年底发布，质量极高 | 全部，尤其 Agent design patterns | https://www.anthropic.com/engineering/building-effective-agents |
| LangChain - Agent Concepts | 官方文档 | 最流行框架的 agent 设计解释 | Tools, Agents, Toolkits | https://python.langchain.com/docs/concepts/agents/ |
| ReAct: Synergizing Reasoning and Acting | 论文/博客 | ReAct 是现代 agent 的基础架构，必须理解 | 读 blog 版即可，不必读原论文 | https://react-lm.github.io/ |

### 4.2 Tool Use / Function Calling

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Anthropic - Tool Use 官方文档 | 官方文档 | Claude 的工具调用最权威文档 | How to implement tool use + Force tool use | https://docs.anthropic.com/en/docs/build-with-claude/tool-use/overview |
| OpenAI Function Calling | 官方文档 | 接口标准，火山方舟兼容此格式 | How to call functions with chat models | https://platform.openai.com/docs/guides/function-calling |

---

## 五、单 Agent 工作流

### 5.1 LangGraph（推荐学习）

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| LangGraph 官方文档 | 官方文档 | 做有状态 agent 工作流最推荐的框架 | Quickstart + How-to guides | https://langchain-ai.github.io/langgraph/ |
| LangGraph - Introduction to Agentic Concepts | 教程 | 官方教程，从无到有做一个 agent | 全部 | https://langchain-ai.github.io/langgraph/concepts/agentic_concepts/ |

---

## 六、Code Agent

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| OpenHands（前 OpenDevin） | 仓库 | 最成熟的开源 code agent，读它的架构 | README + 架构文档 | https://github.com/All-Hands-AI/OpenHands |
| Claude Code 官方文档 | 官方文档 | 你正在用的 Claude Code，理解它的设计 | How Claude works + Tool use | https://docs.anthropic.com/en/docs/claude-code/overview |
| SWE-bench | 基准测试 | Code agent 行业标准评估，了解现有水平 | 看 leaderboard 即可 | https://www.swebench.com/ |

---

## 七、OpenClaw / Platform Agent

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| OpenClaw 官网 | 官方 | 官方文档和社区 | Skills 开发指南、Agent 配置、Cron 说明 | https://openclaw.ai |
| OpenClaw 控制面板 | 你的实例 | 直接用自己的实例，边用边学 | Sessions、Agents、Skills 面板 | https://openclaw.healsee.me |
| /opt/occ 源码（服务器） | 源码 | 遇到文档不清楚的问题，直接看源码 | src/index.ts 和 skills 相关模块 | 服务器本地 |

---

## 八、Eval / 质量评估

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Anthropic - Evaluate LLM performance | 官方文档 | Anthropic 出的评估指南，权威 | Evaluation methods 部分 | https://docs.anthropic.com/en/docs/build-with-claude/develop-tests |
| LangSmith（LangChain） | 工具 | 最流行的 agent trace + eval 工具 | Quickstart + Evaluation | https://docs.smith.langchain.com/ |
| RAGAS | 仓库 | RAG 专用评估框架，检验你的 RAG 质量 | Metrics 部分：faithfulness, answer relevancy | https://docs.ragas.io/en/latest/ |
| Braintrust | 工具 | 更轻量的 LLM eval 平台 | Quickstart | https://www.braintrust.dev/docs |

---

## 九、Tool Use / Memory / State / Routing / Session

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| LangGraph - Memory 文档 | 官方文档 | 讲 short-term 和 long-term memory 怎么做 | How to add memory | https://langchain-ai.github.io/langgraph/concepts/memory/ |
| Anthropic - Memory and Storage | 官方文档 | Claude agent 的记忆设计原则 | Storage types 部分 | https://docs.anthropic.com/en/docs/build-with-claude/memory-and-storage |
| mem0（MemoryOS） | 仓库 | 专注 agent 记忆的开源库，可集成进现有系统 | Quickstart + Integration | https://github.com/mem0ai/mem0 |

---

## 十、工程化与部署

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Docker 官方教程 | 官方文档 | Python 应用容器化必学 | Getting started + Compose | https://docs.docker.com/get-started/ |
| Python httpx 文档 | 官方文档 | 替代 requests，支持异步，适合 LLM 调用 | Async API | https://www.python-httpx.org/async/ |
| Python asyncio 官方文档 | 官方文档 | 异步编程核心 | Coroutines and Tasks | https://docs.python.org/3/library/asyncio-task.html |
| PM2 文档 | 官方文档 | 你现在用的进程管理，需要掌握 | Ecosystem file + Logs | https://pm2.keymetrics.io/docs/usage/quick-start/ |

---

## 十一、Python 快速入门（专为前端工程师）

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| Python for JavaScript Developers | 博客 | 专门对比 JS vs Python，上手快 | 类型系统、异步、模块系统对比 | https://www.valentinog.com/blog/python-for-js/ |
| Real Python - asyncio | 教程 | 最清晰的 Python asyncio 入门，有实例 | async/await、event loop 部分 | https://realpython.com/async-io-python/ |
| pyproject.toml + uv/poetry | 工具文档 | Python 依赖管理（对应 package.json） | 基础用法即可 | https://docs.astral.sh/uv/ |

---

## 十二、技术英语补充资料

| 资料 | 类型 | 为什么推荐 | 重点看什么 | 链接 |
|------|------|-----------|-----------|------|
| AI Engineer 常用词汇表 | 自整理 | 把你日常遇到的技术词汇整理成词表 | 遇到不懂的词就加进去 | 自建 |
| GitHub README 模板集合 | 仓库 | 学如何写规范的英文 README | awesome-readme | https://github.com/matiassingers/awesome-readme |
| Anthropic Blog | 博客 | 读权威机构的英文技术文章，培养技术英语阅读习惯 | 每周选一篇读完 | https://www.anthropic.com/blog |
| Simon Willison's Blog | 博客 | LLM 实践领域最值得关注的英文博主 | 每周 1-2 篇 | https://simonwillison.net |
