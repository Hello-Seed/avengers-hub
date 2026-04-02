# 3 个月项目规划

> 3 个项目，从简单到复杂，每个都有真实用户（你自己），都能上 GitHub

---

## 项目 A：个人知识库 RAG 系统

### 项目名称
`personal-rag` — 基于 OpenClaw / Friday 的个人知识库问答系统

### 项目目标
把你的笔记、文章、收藏、Telegram 收集的信息，构建成向量知识库。  
Friday agent 能查询这个知识库，回答"我之前有没有研究过 X"、"我关于 Y 有什么笔记"这类问题。

### 为什么适合我
- 直接用于现有 Friday bot，上线即可用
- RAG 是 AI Agent 最重要的能力之一，面试必问
- 数据来源就是你自己的信息流，不需要找数据集
- 可以从小做起（100 条文档就能跑），不需要大规模基础设施

### MVP 范围

**Phase 1（Week 4-5，2 周完成）**：
- 从 Telegram 收集 bot 的历史消息中提取文本
- 用 ChromaDB 建立向量索引
- 写一个 Python 查询接口：`search(query) → list[Document]`
- Friday bot 接入：用户问 "搜索我的笔记：XXX" → 返回相关段落

**Phase 2（Week 6，1 周完成）**：
- 加入"生成"环节（RAG 的 G）：检索到内容后，让 LLM 综合回答
- 加入来源引用（回答时显示"来源：第 X 条消息"）
- 支持文件上传（上传 markdown 文件进知识库）

**Phase 3（可选，展示加分项）**：
- Web UI（用 Streamlit 或 Gradio，半天搭起来）
- 增量更新（新消息自动进知识库）

### 推荐技术栈
- **向量库**：ChromaDB（本地可用，免费，有 Python SDK）
- **Embedding**：`text-embedding-3-small`（OpenAI 兼容接口）或 `BAAI/bge-m3`（中文效果好）
- **框架**：直接用 LangChain 的 RAG chain（学习成本低）
- **存储**：现有 SQLite + ChromaDB 双存储
- **语言**：Python

### 项目里程碑

| 里程碑 | 时间 | 完成标准 |
|--------|------|---------|
| M1：能索引 100 条消息 | Week 4 末 | 能跑 ingest.py，向量库有数据 |
| M2：能查询返回相关段落 | Week 5 中 | 查询"AI agent"能返回相关内容 |
| M3：Friday 能用这个知识库 | Week 5 末 | Telegram 里问 Friday 它能搜索笔记 |
| M4：加入 RAG 生成环节 | Week 6 末 | 返回综合回答而非原始片段 |

### GitHub 如何展示
```
personal-rag/
├── README.md          # 讲清楚：为什么做/怎么用/架构图
├── docs/
│   └── architecture.md  # RAG 架构图（用 mermaid）
├── ingest/            # 文档入库脚本
├── retrieval/         # 检索逻辑
├── api/               # Friday 集成接口
└── demo/              # 截图/录屏
```
README 里放效果截图（Telegram 截图），这是最有说服力的展示。

### 简历怎么写
> 设计并实现基于 RAG 的个人知识库系统，使用 ChromaDB 向量数据库对个人 Telegram 消息和笔记进行向量索引，通过 LangChain RAG chain 实现语义检索 + LLM 生成回答，集成至 Telegram Bot 供日常使用。

### 面试怎么讲
1. "我为什么做这个"：因为我的 Friday agent 没有知识库，回答问题全靠模型自身知识，加了 RAG 之后它能查我的笔记
2. "技术难点"：chunking 策略（怎么切文档不破坏语义）、embedding 模型选择（中文特化模型 vs 通用模型）、检索排序（相关度 vs 时间）
3. "效果对比"：加 RAG 前后各问同样的问题，截图对比

### 对国内求职的价值
RAG 是 2024-2026 年国内 AI 岗位面试最高频考点之一，有实际项目直接加分

### 对海外远程的价值
RAG engineer 是海外 AI 公司最需要的工程师类型，有 LangChain 实践直接对应岗位需求

---

## 项目 B：AI 信息日报 Agent 工作流

### 项目名称
`daily-digest-agent` — 自动化信息收集 → 分析 → 日报生成工作流

### 项目目标
把现有的 `daily_summary.py` 升级成完整的 Agent 工作流：  
定时触发 → 从多个来源收集信息 → 分类/过滤/总结 → 生成格式化日报 → 推送到 Telegram

### 为什么适合我
- 现有 `/opt/avengers/collector/daily_summary.py` 已经是雏形
- 这是一个真实有价值的应用，你自己每天都会用
- 可以展示"有状态的 agent 工作流"，是面试最受欢迎的项目类型
- 代码复杂度适中，不会做不完

### MVP 范围

**当前状态**：`daily_summary.py` 是一个简单脚本，没有 agent 工作流，没有状态管理

**Phase 1（Week 6，1 周）**：
- 用 LangGraph 改写成有状态的工作流
- 状态节点：`collect → filter → summarize → format → send`
- 每个节点有明确输入输出，失败可以从断点重试

**Phase 2（Week 7，0.5 周）**：
- 加入 OpenClaw black_widow skill（让黑寡妇 agent 执行信息收集任务）
- 加入质量检查节点（doctor_strange 审核日报质量）

**Phase 3（Week 9，升级）**：
- 支持个性化（根据你今天关注的主题调整日报内容）
- 加入历史对比（今天 vs 昨天，哪些话题新出现）

### 推荐技术栈
- **工作流框架**：LangGraph（状态机，适合多节点流程）
- **数据存储**：现有 SQLite
- **推送**：现有 Telegram bot
- **语言**：Python

### 项目里程碑

| 里程碑 | 时间 | 完成标准 |
|--------|------|---------|
| M1：LangGraph 工作流基础搭通 | Week 6 中 | collect→summarize→send 跑通 |
| M2：有状态恢复能力 | Week 6 末 | 中途失败后能从上次节点继续 |
| M3：接入 OpenClaw agent | Week 7 | black_widow 能被工作流调用 |
| M4：每日自动触发 | Week 8 | 修复 cron 错误，稳定运行 |

### GitHub 如何展示
```
daily-digest-agent/
├── README.md              # 架构图 + 效果截图
├── workflow/
│   ├── graph.py           # LangGraph 工作流定义
│   ├── nodes/             # 各节点实现
│   └── state.py           # 状态定义
├── collectors/            # 数据来源收集器
└── examples/              # 示例日报截图
```
在 README 里放一张日报的截图，展示效果。

### 简历怎么写
> 使用 LangGraph 构建自动化信息日报 Agent 工作流，实现多源信息收集→智能过滤→LLM 摘要生成→格式化输出的完整 pipeline，支持节点级错误恢复和状态持久化，每日自动推送至 Telegram。

### 面试怎么讲
1. "工作流设计"：画出状态图，每个节点做什么
2. "技术选型"：为什么用 LangGraph 而不是直接写脚本（可维护性、可观测性、可扩展性）
3. "实际使用"：我自己每天在用，展示真实日报

### 对国内求职的价值
展示"从想法到实际落地"的工程能力，国内公司很看重这个

### 对海外远程的价值
LangGraph 是海外 agent 工程最主流框架，有实际项目直接证明能力

---

## 项目 C：OpenClaw 自定义 Skills 套件

### 项目名称
`avengers-skills` — 复仇者团队专属工具箱

### 项目目标
为 OpenClaw 复仇者团队开发一套自定义 Skills，让每个 agent 真正拥有"动手"能力，而不只是生成文字。

### 为什么适合我
- 直接升级现有复仇者团队，立竿见影
- OpenClaw Skills 开发是独特技能，国内 OpenClaw 用户很少做到这一步
- 可以展示"把现有系统变成平台"的工程思维
- 前端背景在 Node.js skill 开发上有优势

### 5 个核心 Skills

| Skill | 功能 | 对应 Agent | 技术难点 |
|-------|------|-----------|---------|
| `web_search` | 联网搜索 | 黑寡妇（情报收集） | API 接入（Serper/Tavily） |
| `note_writer` | 写入本地文件 | 所有 agent | 文件系统操作 + 格式规范 |
| `code_runner` | 在沙箱执行代码 | 钢铁侠（技术分析） | 安全沙箱（Docker exec） |
| `calendar_reader` | 读取今日日程 | Friday（总控） | 文件读取 + 日期处理 |
| `rag_search` | 查询个人知识库 | 所有 agent | 接入项目 A 的知识库接口 |

### MVP 范围

**Phase 1（Week 7，1 周）**：
- 开发 `web_search` skill（最有用）
- 开发 `note_writer` skill（最简单）
- 在 OpenClaw 控制面板验证 skill 工作

**Phase 2（Week 8-9，2 周）**：
- 开发 `rag_search` skill（接入项目 A）
- 开发 `code_runner` skill
- 写一套测试脚本

**Phase 3（Week 11，展示完善）**：
- 整理成可供其他人安装的 skill 包
- 写详细的 README 和使用文档

### 推荐技术栈
- **语言**：TypeScript（Node.js，符合 OpenClaw 生态）或 Python（视 OpenClaw skill 规范而定）
- **search API**：Serper API（每月 2500 次免费）或 Tavily（agent 专用搜索）
- **代码沙箱**：Docker exec（用现有 Docker 环境）

### 项目里程碑

| 里程碑 | 时间 | 完成标准 |
|--------|------|---------|
| M1：第一个 skill 在 OpenClaw 里生效 | Week 7 中 | 黑寡妇能用 web_search |
| M2：5 个 skill 全部可用 | Week 9 | 每个 skill 有测试 |
| M3：文档完整，可供他人使用 | Week 11 | README + 安装步骤完整 |

### GitHub 如何展示
```
avengers-skills/
├── README.md              # 展示 5 个 skill，有演示截图
├── skills/
│   ├── web_search/
│   ├── note_writer/
│   ├── code_runner/
│   ├── calendar_reader/
│   └── rag_search/
├── tests/                 # 每个 skill 的测试
└── docs/
    └── install.md         # 安装指南
```
在 README 里展示每个 skill 的使用截图（从 Telegram 发指令 → agent 调用 skill → 返回结果）。

### 简历怎么写
> 为 OpenClaw 平台开发 5 个自定义 Skills（web_search/code_runner/rag_search 等），实现 AI Agent 的工具调用能力扩展，包含沙箱代码执行、语义知识库检索等功能，供复仇者 AI 团队日常使用。

### 面试怎么讲
1. "为什么做 skill"：agent 能生成文字但不能执行操作，skill 给了 agent 真正的手
2. "技术设计"：skill 的接口设计（输入/输出格式），如何保证安全性（代码沙箱）
3. "实际效果"：展示前后对比，加了 skill 后 agent 能做到哪些之前做不到的事

### 对国内求职的价值
OpenClaw 是国内 AI 工具链方向的代表，能深度开发 skill 说明有平台工程能力

### 对海外远程的价值
Skills = Tool Use，这是 agent 工程核心能力，任何 agent 岗位都需要
