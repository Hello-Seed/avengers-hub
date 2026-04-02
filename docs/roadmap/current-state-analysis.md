# 当前项目现状分析

> 分析时间：2026-04-02  
> 分析对象：openclaw-ai 本地仓库 + 腾讯云服务器（43.157.56.164）

---

## 一、本地仓库现状

本地仓库 `openclaw-ai` 目前是一个**规划与文档仓库**，并非 OpenClaw 主源码仓库。

```
openclaw-ai/
├── .claude/settings.local.json   # Claude Code 权限配置
├── AIAgent-prompt.md             # 转型规划 meta prompt
└── 服务器资料.md                  # 服务器与账号信息
```

**结论：本地仓库目前没有实际业务代码，是转型学习的起始基地。**

---

## 二、服务器部署现状

### 2.1 基础设施

| 项目 | 详情 |
|------|------|
| 云服务商 | 腾讯云 |
| OS | Ubuntu 6.8.0，运行 8 天+ |
| 内存 | 3.6GB 总计，已用 1.4GB |
| 磁盘 | 59GB，已用 7.5GB（14%） |
| 负载 | 1.97/2.41/2.50（稍高，agent 持续运行中） |

### 2.2 OpenClaw 部署

- **版本**：OpenClaw `2026.3.23-2`（最新版，安装于 `/usr/bin/openclaw`）
- **控制面板**：`https://openclaw.healsee.me`（已对外可访问）
- **网关**：本地端口 `18789`，token 鉴权模式
- **进程管理**：PM2 管理 `pandas-control-center`（OpenClaw 控制中心，路径 `/opt/occ`）
- **模型后端**：火山方舟（Volcengine），主模型 `ark-code-latest`（volcengine-plan）

### 2.3 AI Agent 团队（复仇者联盟）

6 个已配置的 OpenClaw Agent + 1 个独立 Python 机器人框架：

| Agent | 身份 | 定位 |
|-------|------|------|
| friday | 🎯 Friday 总控 | Telegram 入口，任务路由，调用其他 agent |
| captain | 🛡️ 美国队长 | 任务调度、协调 |
| black_widow | 🕷️ 黑寡妇 | 情报收集、信息整理 |
| doctor_strange | 🔮 奇异博士 | 战略规划、方案设计 |
| iron_man | ⚙️ 钢铁侠 | 技术分析、代码支持 |
| vision | 🤖 幻视 | 产品设计、用户体验 |

### 2.4 Python 后端（/opt/avengers/）

除 OpenClaw 配置外，还有一套独立的 Python 业务层：

```
/opt/avengers/
├── agents/         # 各 agent 的 Python 脚本（friday.py 等）
├── collector/      # Telegram 收集机器人 + 每日日报脚本
├── shared/
│   ├── llm.py      # 火山方舟 DeepSeek API 封装（同步 requests）
│   ├── db.py       # SQLite 任务数据库（tasks + messages 表）
│   └── github_tool.py  # GitHub 工具集成
├── data/tasks.db   # 任务持久化数据库
└── logs/           # 各 agent 独立日志文件
```

**架构流程**：

```
用户 Telegram 消息
    → Friday Bot (Python/Telegram)
        → 简单问题：直接调用 LLM API 回答
        → 复杂任务：subprocess 调用 openclaw agent
            → OpenClaw 多 agent 协作（captain/black_widow/...）
            → 结果回传 Telegram
```

### 2.5 模型配置

已接入多个模型（通过火山方舟）：

| 模型 | 用途 |
|------|------|
| ark-code-latest | 所有 agent 默认主模型（coding 特化） |
| deepseek-v3-2-251201 | DeepSeek V3.2（128k context） |
| doubao-seed-code-preview | Doubao 代码预览版（256k context） |
| kimi-k2-5-260127 | Kimi K2.5（256k context） |
| glm-4-7-251222 | GLM 4.7（200k context） |

### 2.6 Cron 任务现状

- 已配置 1 个 cron：每天 22:00（上海时区）触发 Friday 创建每日任务
- **当前状态：报错**（`consecutiveErrors: 2`）
  - 原因：没有配置 `delivery.channel`，没有找到可发送消息的频道

### 2.7 已完成的真实使用案例

从 subagent runs 记录来看，已成功执行过：
- AI Agent 就业市场分析（Friday 调度 → 子 agent 协作 → 生成完整报告）

---

## 三、能力边界评估

### 3.1 已具备的能力

| 能力 | 程度 | 说明 |
|------|------|------|
| OpenClaw 平台使用 | 中级 | 已部署、已配置多 agent、已接通 Telegram |
| 多 agent 配置 | 中级 | 6 个 agent 均已配置身份和模型 |
| LLM API 调用 | 中级 | Python 直接调用火山方舟，同步 requests |
| 任务持久化 | 初级 | SQLite 实现任务队列，结构完整但未深度使用 |
| 多模型接入 | 中级 | 同时接入 5 种模型，具备切换能力 |
| Telegram Bot | 中级 | 收发消息、路由逻辑、分段发送 |
| 定时任务 | 初级 | Cron 已配置但有错误，需修复 |
| 日志系统 | 初级 | 各 agent 独立 log 文件，无集中监控 |

### 3.2 尚缺失的关键能力

| 缺失能力 | 影响程度 | 说明 |
|---------|---------|------|
| RAG 实现 | 高 | 无任何向量检索、知识库能力 |
| 异步 LLM 调用 | 中 | 当前是同步 subprocess，任务超时5分钟 |
| Agent 评估（Eval） | 高 | 无任何 success rate / 质量评估机制 |
| Context Engineering | 中 | System prompt 简单，未系统设计 |
| Token Cost 追踪 | 中 | 无成本统计 |
| 向量数据库 | 高 | 未引入 |
| Skill 开发 | 中 | OpenClaw skills 目录为空，未开发自定义工具 |
| 流式输出 | 低 | 当前批量返回，无流式体验 |
| 单元测试 / CI | 中 | 无测试覆盖 |
| 多模态输入 | 低 | 仅文本 |

---

## 四、已有优势（转型起点优势分析）

1. **真实运行中的 Agent 系统**：不是教程项目，是真正在生产环境跑的系统
2. **多 Agent 实践经验**：已经亲手配置、调试过 6 个协作 agent
3. **OpenClaw 平台第一手经验**：了解其 agent 结构、cron、subagent、session 概念
4. **云服务器 + 公网可访问**：具备真实部署条件，不需要额外申请资源
5. **前端工程背景**：JS/TS 能力直接复用，Node.js 生态熟悉
6. **已有 LLM API 调用经验**：Python + requests 调用，理解 messages 结构
7. **多模型接入经验**：了解不同模型的能力差异

---

## 五、从工程视角：最适合先补什么

基于上述分析，按优先级排序：

### P0（最优先，能立刻提升现有系统价值）
1. **RAG**：现有团队没有知识库能力，加入 RAG 后每个 agent 都能"查资料"
2. **Agent Eval 基础**：知道 agent 在干什么、成功率多少，现在是黑盒

### P1（中期，系统化提升）
3. **Context Engineering**：优化现有 6 个 agent 的 system prompt，提升输出质量
4. **OpenClaw Skills 开发**：给 agent 添加真正的工具能力（搜索/写文件/执行代码）
5. **异步架构**：把 subprocess 调用改为真正的异步任务，解决超时问题

### P2（后期，求职/展示价值）
6. **Python 异步编程**（asyncio）：提升代码工程质量
7. **LangChain / LlamaIndex 框架**：求职必须了解的行业标准工具
8. **TypeScript Agent 实现**：前端背景优势，做 Node.js/TS 版本的 agent

---

## 六、与求职的关联

| 岗位方向 | 当前匹配度 | 主要缺口 |
|---------|---------|---------|
| AI Agent 工程师（国内） | 60% | RAG、Eval、框架（LangChain）经验 |
| AI Application Engineer（海外） | 40% | 英语、Anthropic/OpenAI API 使用经验、测试规范 |
| Platform Agent Engineer | 70% | OpenClaw 深度理解是优势，需补工程化能力 |
| LLM Ops | 30% | 需要补监控、评估、数据飞轮 |
