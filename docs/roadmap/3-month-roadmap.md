# 3 个月转型路线图：前端工程师 → AI Agent 工程师

> 起点：多年前端经验 + 已有 OpenClaw 多 agent 系统  
> 终点：能独立设计、开发、部署 AI Agent 应用的工程师

---

## 总目标

3 个月后，能够：
1. 独立设计并实现一个有 RAG 能力的 AI Agent 系统
2. 用 OpenClaw 平台开发自定义 Skills，让 agent 真正有工具能力
3. 能评估 agent 质量（Eval），知道系统好不好、哪里需要改
4. 拥有 3 个 GitHub 上可展示的真实项目
5. 能用中英文描述自己做了什么，去面试或接单

---

## 为什么这条路线适合我

| 我的特点 | 路线的对应设计 |
|---------|--------------|
| 前端背景，JS/TS 熟练 | 用 Python 快速入门，复用 TS 思维，后期做 TS 版 agent |
| 已有 OpenClaw 生产系统 | 每周学完立刻用在现有系统，不是空转 |
| 不想走算法路线 | 全程工程化优先，只学必要的数学 |
| 目标中国 + 海外 | 工具覆盖两端（OpenClaw+火山方舟 vs LangChain+Anthropic） |
| 时间有限 | 每天学习时间 2-3 小时，周末可稍多 |
| 英语一般 | 读英文文档为主，写英文 README，不要求口语 |

---

## 三阶段总览

```
┌─────────────────────────────────────────────────────────────────┐
│  第一阶段（Week 1-4）：工程基础 + LLM 核心能力                      │
│  ✓ Python 工程化    ✓ LLM API 深度使用    ✓ Prompt Engineering  │
│  ✓ Tool Use（工具调用）  ✓ 基础 RAG 概念                          │
├─────────────────────────────────────────────────────────────────┤
│  第二阶段（Week 5-8）：Agent 实战 + RAG 实现                       │
│  ✓ RAG 完整实现    ✓ 单 Agent 工作流    ✓ OpenClaw Skills         │
│  ✓ Memory & State   ✓ 现有系统升级                                │
├─────────────────────────────────────────────────────────────────┤
│  第三阶段（Week 9-12）：平台化 + 工程化 + 展示                      │
│  ✓ 多 Agent 协作深化   ✓ Eval 体系   ✓ 部署工程化                 │
│  ✓ 作品集打磨   ✓ 简历/面试准备                                   │
└─────────────────────────────────────────────────────────────────┘
```

---

## 第一阶段：工程基础（Week 1-4）

### 月度目标
从"能用 Python 调 LLM API"升级到"能系统设计 prompt、理解 tool use、知道 RAG 是什么"

### 每周重点

| 周 | 主题 | 核心输出 |
|----|------|---------|
| Week 1 | Python 工程化 + 异步编程 | 把现有 llm.py 改成异步版，写单元测试 |
| Week 2 | Prompt Engineering 系统化 | 重写 6 个 agent 的 system prompt |
| Week 3 | Tool Use / Function Calling | 给 friday agent 添加第一个真实 tool |
| Week 4 | RAG 原理 + 向量数据库入门 | 搭起第一个 chroma 向量库，能查询 |

### 本阶段结束后，我能做什么
- 不再用 `requests` 同步调 API，改用 `httpx` 或 `openai` SDK 的异步接口
- 写出有结构的 system prompt（角色/能力/限制/输出格式）
- 让 agent 能调用一个真实工具（如 search_web）
- 搭起一个小型向量知识库并查询

### 本阶段需要补的能力
- Python asyncio 基础
- Python 类型注解、模块组织
- OpenAI SDK 使用（用于兼容接口，即使不用 OpenAI 也要会）
- 向量化（embedding）基本原理
- ChromaDB 或 FAISS 基础操作

---

## 第二阶段：Agent 实战（Week 5-8）

### 月度目标
完成 RAG 系统，做出能跑起来的单 agent 工作流，开始给 OpenClaw 写 Skills

### 每周重点

| 周 | 主题 | 核心输出 |
|----|------|---------|
| Week 5 | RAG 完整项目 MVP | 个人知识库 RAG，Friday 能查询它 |
| Week 6 | 单 Agent 工作流（LangGraph 入门） | 信息日报 agent 工作流，有状态转移 |
| Week 7 | OpenClaw Skills 开发 | 写 2 个 skill：web_search + note_writer |
| Week 8 | Memory / Session / State | 给 agent 加记忆，跨对话知道上下文 |

### 本阶段结束后，我能做什么
- 从零搭一个 RAG 系统（文档 ingestion → 向量化 → 检索 → 生成）
- 用 LangGraph 或 OpenClaw 的 workflow 写有条件分支的 agent 流
- 开发并发布一个 OpenClaw skill
- 让 agent 在对话间记住关键信息

### 本阶段需要补的能力
- LangChain / LlamaIndex 核心概念
- LangGraph 状态机基础
- 向量数据库进阶（索引策略、检索排序）
- OpenClaw skill 开发文档
- SQLite + JSON 持久化模式

---

## 第三阶段：平台化 + 工程化（Week 9-12）

### 月度目标
把前两阶段的成果系统化，补 Eval，部署上线，打磨作品集

### 每周重点

| 周 | 主题 | 核心输出 |
|----|------|---------|
| Week 9 | 多 Agent 协作进阶 | 升级复仇者团队，实现真正的任务分发 |
| Week 10 | Eval + 监控 + 成本追踪 | 给每个 agent 加 success rate 统计 |
| Week 11 | 部署工程化 | Docker 化、环境变量管理、日志集中 |
| Week 12 | 作品集 + 简历 + 面试准备 | README 双语、GitHub profile、面试稿 |

### 本阶段结束后，我能做什么
- 设计可以被别人用的多 agent 系统
- 知道如何评估 agent 质量，有量化数据
- 将项目 Docker 化并部署
- 用英文和中文讲清楚自己做了什么

---

## 学习顺序说明

**为什么先 Python 工程化，再 Prompt，再 RAG？**

不少人一上来就学 LangChain，但工程基础不扎实，写出来的代码一塌糊涂。  
Python asyncio → 异步 LLM API → Prompt 设计 → Tool Use → RAG  
这个顺序是从"我能用"到"我用好"再到"我能做复杂的"的自然递进。

**为什么把 OpenClaw Skills 放 Week 7，不是更早？**

Skills 需要先对 tool use 概念理解到位（Week 3），  
也需要有实际要解决的问题（Week 5-6 的项目告诉你需要什么工具）。  
Week 7 做 Skills 是水到渠成。

**为什么把 Eval 放第三阶段？**

Eval 需要你有一个 agent 系统在跑，没有系统就没有东西可以评估。  
Week 10 去做 Eval 是刚好有 2 个月积累的系统可以评估了。

---

## 风险提醒

| 风险 | 可能性 | 应对方案 |
|------|-------|---------|
| 只看资料不动手 | 高 | 每天必须有代码或文档输出，无输出等于没学 |
| OpenClaw 文档不完整，卡住 | 中 | 直接读 `/opt/occ` 源码，或切换到标准框架实现 |
| Python 基础拖后腿 | 中 | Week 1 集中补，不要拖到 Week 2 再说 |
| 时间不够，跑偏到有趣但不重要的方向 | 高 | 每周日做检查，用 weekly-check-template 对照路线 |
| 选的模型没有 function calling 支持 | 低 | 火山方舟主流模型都支持，但要测试确认 |

---

## 如何兼顾中国求职和海外远程

### 中国求职策略
- 重点展示：OpenClaw 深度使用、火山方舟模型接入、完整 Python 后端
- 平台：掘金、知乎发技术文章，GitHub 加中文 README
- 岗位关键词：AI Agent 工程师、LLM 应用工程师、智能体工程师

### 海外远程策略
- 重点展示：LangChain/LangGraph 使用、英文 README、Anthropic/OpenAI API
- 平台：LinkedIn、GitHub（英文）
- 岗位关键词：AI Engineer、LLM Application Engineer、Agent Engineer
- 语言策略：英文写作（文档/README）优先，不强求英文口语

### 两条线并行的关键
- 每个项目写双语 README（中文主，英文副）
- 技术栈选择时优先考虑"国内外都认可"的工具（LangChain、Python、SQLite）
- 在中国求职时重点讲 OpenClaw 经验；海外求职时重点讲框架和工程实践
