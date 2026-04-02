# 12 周每日学习计划

> 说明：每天学习时间约 2-3 小时。周六适当加量，周日用于复盘和补漏。
> 最低完成标准：只要完成"今日输出物"，当天即算完成。

---

# 第一阶段：工程基础（Week 1-4）

---

## Week 1：Python 工程化 + 异步编程

**本周主题**：从"能写 Python 脚本"升级到"能写工程化的异步 Python 代码"

---

### Day 1（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | Python 与 JavaScript 的对应关系快速上手 |
| **学什么** | Python 的模块系统、类型注解、f-string、列表推导式 |
| **为什么学** | 前端工程师最大的障碍是 Python 语法陌生，1 天集中扫清 |
| **具体做什么** | 读《Python for JavaScript Developers》全文；把现有 `llm.py` 加上完整类型注解 |
| **学习资料** | Python for JavaScript Developers: https://www.valentinog.com/blog/python-for-js/ |
| **今日输出物** | `llm.py` 加上完整的 type hints，所有函数有 docstring |
| **最低完成标准** | `llm.py` 里每个函数都有 `def func(arg: type) -> return_type:` 格式 |
| **有余力可以做** | 把 `db.py` 也加上类型注解 |

---

### Day 2（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | Python 异步编程基础（asyncio） |
| **学什么** | `async/await`、`asyncio.run()`、`asyncio.gather()`、event loop |
| **为什么学** | 当前 `llm.py` 是同步 requests，调一次 LLM 要阻塞 10-30 秒，多个 agent 并发时无法使用 |
| **具体做什么** | 读 Real Python asyncio 教程前半部分（Coroutines 到 gather 部分） |
| **学习资料** | Real Python asyncio: https://realpython.com/async-io-python/ |
| **今日输出物** | 写一个测试脚本 `test_async.py`，用 `asyncio.gather` 并发执行 3 个 sleep 任务，验证理解 |
| **最低完成标准** | `test_async.py` 能跑通，3 个任务总时间 < 最长单个任务时间 |
| **有余力可以做** | 读 httpx 文档的 async 部分 |

---

### Day 3（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | 用 httpx 重写 llm.py 为异步版本 |
| **学什么** | httpx 异步客户端、async context manager |
| **为什么学** | 把现有系统的 LLM 调用改成异步，这是最直接有价值的实践 |
| **具体做什么** | 安装 httpx；把 `shared/llm.py` 的 `chat()` 函数改成 `async def chat_async()`，保留同步版本做兼容 |
| **学习资料** | httpx async 文档: https://www.python-httpx.org/async/ |
| **今日输出物** | `shared/llm_async.py`，有 `async def chat_async(...)` 实现，有测试脚本验证可用 |
| **最低完成标准** | 在服务器上跑 `python3 test_llm_async.py`，成功调用 LLM 并返回结果 |
| **有余力可以做** | 用 `asyncio.gather` 同时发 3 个 LLM 请求，对比耗时 |

---

### Day 4（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | Python 项目结构 + 依赖管理 |
| **学什么** | `pyproject.toml`、`uv` 工具、`__init__.py` 规范、相对导入 vs 绝对导入 |
| **为什么学** | 当前 `/opt/avengers` 项目没有依赖管理文件，别人无法复现，不能放 GitHub |
| **具体做什么** | 在本地 `openclaw-ai` 仓库里为 avengers 项目写 `pyproject.toml`；列出所有依赖 |
| **学习资料** | uv 文档: https://docs.astral.sh/uv/ |
| **今日输出物** | `pyproject.toml` 文件，包含所有依赖，加入 `.gitignore` |
| **最低完成标准** | 在新环境里 `uv sync` 能装好所有依赖 |
| **有余力可以做** | 给项目加 `Makefile`，用 `make run` 启动 friday bot |

---

### Day 5（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 写单元测试 |
| **学什么** | `pytest` 基础、mock（`unittest.mock`）、测试 LLM 调用（mock 掉 API） |
| **为什么学** | 有测试才能放心改代码，当前 avengers 项目 0 测试覆盖 |
| **具体做什么** | 为 `shared/db.py` 写 3 个测试：create_task / get_pending_tasks / update_task |
| **学习资料** | pytest 官方文档: https://docs.pytest.org/en/stable/getting-started.html |
| **今日输出物** | `tests/test_db.py`，3 个测试全部通过 |
| **最低完成标准** | `pytest tests/test_db.py` 全绿 |
| **有余力可以做** | 给 `llm_async.py` 写 mock 测试（不真实调用 API） |

---

### Day 6（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 把 avengers 项目初始化到 GitHub |
| **学什么** | git 基础（你应该会）、`.gitignore`（避免提交 API key）、GitHub README 结构 |
| **为什么学** | 项目要能放到 GitHub 才有展示价值，环境变量管理是基础工程能力 |
| **具体做什么** | 在 GitHub 新建 `avengers-ai-team` 仓库；把 `/opt/avengers` 代码整理到本地，写 `README.md`（中文）；用环境变量替换硬编码的 API key |
| **学习资料** | GitHub README 模板: https://github.com/matiassingers/awesome-readme |
| **今日输出物** | GitHub 仓库有 README、有 `.env.example`、代码已推上去 |
| **最低完成标准** | 仓库里没有硬编码的 API key 或密码 |
| **有余力可以做** | 加 GitHub Actions 自动运行 pytest |

---

### Day 7（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 1 复盘 |
| **具体做什么** | 填写 `plan/weekly-check-template.md`；回顾这周学了什么；把卡住的点记录下来 |
| **今日输出物** | `plan/logs/week-01-check.md` |
| **最低完成标准** | 复盘文件填完，写清楚"本周最大收获"和"最大卡点" |

---

## Week 2：Prompt Engineering 系统化

**本周主题**：用结构化方法重新设计复仇者团队的 system prompt

---

### Day 8（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | Prompt Engineering 核心原则 |
| **学什么** | 角色设定、任务描述、输出格式、限制条件的结构化写法 |
| **为什么学** | 现有 agent 的 system prompt 都很简单，导致输出质量不稳定 |
| **具体做什么** | 读 Anthropic Prompt Engineering 官方指南全部内容（约 2 小时） |
| **学习资料** | https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview |
| **今日输出物** | 整理一份"Prompt 设计模板"笔记，包含：角色/能力/输出格式/限制/示例 5 个要素 |
| **最低完成标准** | 笔记写完，能用自己的话解释为什么每个要素重要 |

---

### Day 9（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | Few-shot Prompting + Chain-of-Thought |
| **学什么** | 什么时候用 few-shot、如何写 chain-of-thought 引导词 |
| **为什么学** | 复杂任务（如奇异博士的战略分析）需要引导模型一步步思考 |
| **具体做什么** | 读 Prompt Engineering Guide 的 few-shot 和 CoT 章节；给奇异博士写一个含 CoT 的 system prompt |
| **学习资料** | https://www.promptingguide.ai/zh/techniques/fewshot |
| **今日输出物** | `prompts/doctor_strange.md`，包含完整的 system prompt + 使用说明 |
| **最低完成标准** | 在 OpenClaw 控制面板里测试新 prompt，效果明显优于原版（主观判断） |

---

### Day 10（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | 重写 Friday 总控 system prompt |
| **学什么** | 如何写路由型 agent 的 prompt（决策/分发/汇总） |
| **为什么学** | Friday 是整个团队的入口，prompt 写好了整个团队的表现都会提升 |
| **具体做什么** | 分析 Friday 现有的 `SIMPLE_PROMPT`（只有一行）；重写成包含：身份/能力/路由规则/输出格式/安全限制 的完整版本 |
| **学习资料** | Anthropic - Be Clear and Direct: https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/be-clear-and-direct |
| **今日输出物** | `prompts/friday.md`，至少 30 行的完整 system prompt |
| **最低完成标准** | 把新 prompt 部署到服务器上的 Friday，发 10 条测试消息，结果明显更专业 |

---

### Day 11（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 重写其他 4 个 agent 的 system prompt |
| **学什么** | 不同角色（情报收集 vs 技术分析）的 prompt 差异 |
| **为什么学** | 每个 agent 有专门职责，prompt 要体现专业性 |
| **具体做什么** | 为 captain / black_widow / iron_man / vision 分别写专属 system prompt，每个至少 20 行 |
| **今日输出物** | `prompts/` 目录下 4 个文件 |
| **最低完成标准** | 4 个文件都写完，每个有明确的角色/能力/输出格式 |

---

### Day 12（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | Prompt 版本管理 + A/B 测试思维 |
| **学什么** | 如何用 git 管理 prompt 版本；如何系统比较两个 prompt 的效果 |
| **为什么学** | Prompt 改了之后怎么知道好还是不好，需要系统的方法 |
| **具体做什么** | 给 `prompts/` 目录建立版本命名规范（`friday_v1.md`、`friday_v2.md`）；写一个小脚本，对同一个问题分别用两版 prompt 调用，对比输出 |
| **今日输出物** | `scripts/prompt_compare.py`，能对比两个 prompt 的输出 |
| **最低完成标准** | 脚本能跑，能看到两个版本的输出并排显示 |

---

### Day 13（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 长上下文管理 |
| **学什么** | 如何在长对话中保持 agent 聚焦；如何压缩历史消息 |
| **为什么学** | 现有 friday.py 对话没有 context 管理，长对话容易跑偏或超 token 限制 |
| **具体做什么** | 读 Anthropic Long Context 文档；给 friday.py 的对话历史加上滚动窗口（只保留最近 20 条消息） |
| **学习资料** | https://docs.anthropic.com/en/docs/build-with-claude/long-context-tips |
| **今日输出物** | 修改后的 `friday.py`，对话历史有滚动窗口机制 |
| **最低完成标准** | 发送 30 条消息后，历史窗口不超过设定上限 |

---

### Day 14（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 2 复盘 |
| **具体做什么** | 填写 weekly check；把这周写的所有 prompt 提交到 GitHub；写一篇短笔记"我对 Prompt Engineering 的理解" |
| **今日输出物** | week-02-check.md + GitHub 上有 prompts/ 目录 |

---

## Week 3：Tool Use / Function Calling

**本周主题**：理解 function calling 机制，给 agent 添加第一个真实工具

---

### Day 15（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | Function Calling 基础原理 |
| **学什么** | tools 参数格式（JSON Schema）、模型如何决定调用哪个工具、工具结果如何回传 |
| **为什么学** | Tool Use 是 agent 能"干活"的核心，不懂原理就无法调试问题 |
| **具体做什么** | 读 Anthropic Tool Use 官方文档全部；手写一个最小的 tool use 示例（不用框架，直接调 API） |
| **学习资料** | https://docs.anthropic.com/en/docs/build-with-claude/tool-use/overview |
| **今日输出物** | `examples/tool_use_basic.py`，实现一个 `get_weather(city)` dummy 工具，LLM 能调用它 |
| **最低完成标准** | 问"北京今天天气"，模型返回 tool_use，你的代码处理后返回结果 |

---

### Day 16（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 实现 web_search 工具 |
| **学什么** | Serper API 或 Tavily API 的用法；如何把搜索结果整合进对话 |
| **为什么学** | 搜索是 agent 最有用的工具，现有黑寡妇 agent 没有联网能力 |
| **具体做什么** | 注册 Serper API（免费 2500 次/月）；写 `tools/web_search.py`；让 agent 调用它 |
| **学习资料** | Serper API: https://serper.dev ; Tavily: https://tavily.com |
| **今日输出物** | `tools/web_search.py`，能搜索并返回前 5 个结果的摘要 |
| **最低完成标准** | 调用 `web_search("AI agent 2026")` 返回真实搜索结果 |

---

### Day 17（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | 把 web_search 接入 black_widow agent |
| **学什么** | 如何在 agent 的 system prompt 里描述工具；multi-turn tool use |
| **为什么学** | 有了工具，黑寡妇才能真正"收集情报" |
| **具体做什么** | 修改 `agents/black_widow.py`，加入 web_search 工具；测试"请搜索最新的 AI Agent 新闻" |
| **今日输出物** | 修改后的 `black_widow.py`，能调用 web_search 并汇报结果 |
| **最低完成标准** | Telegram 里发给 Friday "让黑寡妇搜索 XXX"，能得到真实搜索结果 |

---

### Day 18（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 工具链（Tool Chain）和错误处理 |
| **学什么** | 工具调用失败如何处理；如何让模型在工具失败后有备用方案 |
| **为什么学** | 生产环境工具会失败（API 限速、网络错误），需要优雅降级 |
| **具体做什么** | 给 `web_search.py` 加入重试逻辑（最多 3 次）；加入超时（10 秒）；写错误处理测试 |
| **今日输出物** | 更健壮的 `web_search.py`，有重试和超时；测试脚本模拟各种失败场景 |
| **最低完成标准** | 故意让搜索失败，agent 能给出"搜索失败，尝试从已有知识回答"的降级响应 |

---

### Day 19（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 实现 note_writer 工具 |
| **学什么** | 文件系统操作、append vs overwrite、Markdown 格式 |
| **为什么学** | 让 agent 能写笔记，是"agent 能产出持久化内容"的第一步 |
| **具体做什么** | 写 `tools/note_writer.py`：接收标题和内容，写入 `~/notes/YYYY-MM-DD-title.md` |
| **今日输出物** | `tools/note_writer.py`，能创建和追加 markdown 笔记 |
| **最低完成标准** | 调用 `note_writer(title="AI学习笔记", content="今天学了tool use")` 能在磁盘上创建文件 |

---

### Day 20（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 实现 OpenClaw skill：web_search |
| **学什么** | OpenClaw skill 的文件结构和接口规范 |
| **为什么学** | OpenClaw skill 可以让整个平台的所有 agent 共用工具，比单个 Python 脚本更强大 |
| **具体做什么** | 阅读 OpenClaw skill 开发文档（官网或服务器 `/opt/occ` 源码）；把 web_search 封装成 skill |
| **学习资料** | OpenClaw 官网文档 + 服务器 /opt/occ 源码 |
| **今日输出物** | 一个可以在 OpenClaw 控制面板安装的 web_search skill 包 |
| **最低完成标准** | 在 OpenClaw 控制面板里能看到并安装这个 skill |

---

### Day 21（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 3 复盘 |
| **具体做什么** | 填写 weekly check；把 tools/ 目录推到 GitHub；整理本周的技术发现 |
| **今日输出物** | week-03-check.md |

---

## Week 4：RAG 原理 + 向量数据库入门

**本周主题**：理解 RAG 全链路，搭起第一个可用的向量知识库

---

### Day 22（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | RAG 整体概念 |
| **学什么** | Retrieval、Augmentation、Generation 三个环节分别是什么；向量化的基本原理 |
| **为什么学** | RAG 是整个第二阶段的核心，Week 4 先把概念搞清楚 |
| **具体做什么** | 读 Pinecone 的 What is RAG 全文（30 分钟）；读 LangChain RAG 概念文档 |
| **学习资料** | https://www.pinecone.io/learn/retrieval-augmented-generation/ |
| **今日输出物** | 一份"RAG 架构笔记"，用 mermaid 画出数据流图 |
| **最低完成标准** | 能解释 chunking / embedding / similarity search / context injection 各是什么 |

---

### Day 23（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | ChromaDB 基础操作 |
| **学什么** | collection 创建、add / query 接口、持久化存储 |
| **为什么学** | ChromaDB 是最轻量的向量库，适合在现有服务器直接用 |
| **具体做什么** | 安装 ChromaDB；写 `rag/chroma_demo.py`：创建 collection、加入 10 条测试文本、查询最相似的 3 条 |
| **学习资料** | https://docs.trychroma.com/getting-started |
| **今日输出物** | `rag/chroma_demo.py`，能跑通 add + query |
| **最低完成标准** | 查询"人工智能"能返回内容相关的段落 |

---

### Day 24（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | Embedding 模型选择 + 中文优化 |
| **学什么** | 不同 embedding 模型的区别；中文 embedding 为什么要用专门的模型 |
| **为什么学** | 你的数据主要是中文，用通用 embedding 效果差，需要选对模型 |
| **具体做什么** | 测试 3 个 embedding 模型：`text-embedding-3-small`（火山方舟）、`BAAI/bge-m3`（本地）、`text-embedding-v3`；用相同的中文查询对比结果 |
| **学习资料** | MTEB 中文排行: https://huggingface.co/spaces/mteb/leaderboard |
| **今日输出物** | 对比测试结果文档 `docs/embedding-comparison.md`，选定你的 embedding 方案 |
| **最低完成标准** | 测试完 3 个模型，有明确结论 |

---

### Day 25（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | Chunking 策略 |
| **学什么** | 固定大小 chunking vs 语义 chunking；chunk overlap 的作用；中文分块特殊性 |
| **为什么学** | chunking 策略直接影响 RAG 检索质量，是 RAG 最重要的工程决策之一 |
| **具体做什么** | 写 3 个 chunking 策略的实现：固定 500 字符、按段落、按标题；用同样的文档测试检索效果 |
| **今日输出物** | `rag/chunking.py`，3 种 chunking 方法，有测试 |
| **最低完成标准** | 3 种方法都能跑，有检索效果对比 |

---

### Day 26（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 搭起 personal-rag MVP 第一步：数据 ingestion |
| **学什么** | 如何从 Telegram 导出历史消息；如何批量向量化并存入 ChromaDB |
| **为什么学** | 这是项目 A 的第一个里程碑，Week 5 的基础 |
| **具体做什么** | 写 `ingest/telegram_ingest.py`：读取 collector bot 的 SQLite 数据库，提取文本，向量化，存入 ChromaDB |
| **今日输出物** | `ingest/telegram_ingest.py`，能把 tasks.db 里的数据导入向量库 |
| **最低完成标准** | 向量库里有 50 条以上的记录 |

---

### Day 27（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 向量检索 + 手动测试 |
| **学什么** | 语义相似度 vs 关键词搜索；如何评估检索质量（手动对比） |
| **为什么学** | 建了库但没有验证质量，等于没建 |
| **具体做什么** | 写 `rag/search.py`：接收查询，返回 top-5 最相关段落；手动测试 10 个查询，评估相关性 |
| **今日输出物** | `rag/search.py` + 手动测试记录 `docs/rag-test-results.md` |
| **最低完成标准** | 10 个查询中至少 7 个返回了相关内容 |

---

### Day 28（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 4 复盘 + 第一阶段总结 |
| **具体做什么** | 填写 weekly check；回顾第一阶段（4 周）；写下进入第二阶段前的状态 |
| **今日输出物** | week-04-check.md + `docs/phase1-summary.md` |

---

# 第二阶段：Agent 实战（Week 5-8）

---

## Week 5：RAG 完整项目

**本周主题**：完成个人知识库 RAG 系统，接入 Friday bot

---

### Day 29（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | RAG 生成环节（Retrieval + Generation） |
| **学什么** | 如何把检索到的段落注入 prompt；context injection 模板 |
| **为什么学** | Week 4 只做了检索，这周要加上生成 |
| **具体做什么** | 写 `rag/rag_chain.py`：接收用户问题 → 检索相关段落 → 构建 augmented prompt → 调用 LLM → 返回答案 |
| **今日输出物** | `rag/rag_chain.py`，端到端 RAG 能跑通 |
| **最低完成标准** | 问一个知识库里有内容的问题，返回有来源引用的回答 |

---

### Day 30（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 来源引用 + 置信度 |
| **学什么** | 如何在回答里显示"来源：第 X 段"；如何让模型说"不确定"而不是胡说 |
| **为什么学** | 没有来源引用的 RAG 系统很难被信任 |
| **具体做什么** | 修改 `rag_chain.py`，在回答末尾加入来源列表；在 prompt 里加"如果检索结果与问题无关，直接说不知道"的指令 |
| **今日输出物** | 回答格式包含来源信息的 RAG 系统 |
| **最低完成标准** | 每次回答末尾都有"来源：[...]"；对不相关问题能回答"我的知识库里没有这方面内容" |

---

### Day 31（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | 接入 Friday Telegram Bot |
| **学什么** | 如何把 RAG 模块集成进现有 bot；路由逻辑（什么时候用 RAG，什么时候不用） |
| **为什么学** | RAG 只有用起来才有价值 |
| **具体做什么** | 修改 `agents/friday.py`，加入"搜索笔记：XXX"命令路由到 RAG；在 Telegram 里测试 |
| **今日输出物** | 修改后的 `friday.py`，能响应"搜索笔记：AI Agent"这类命令 |
| **最低完成标准** | 在 Telegram 里成功查询个人知识库并得到回答 |

---

### Day 32（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 增量更新知识库 |
| **学什么** | 如何只更新新增的文档而不是全量重建 |
| **为什么学** | 每次全量重建太慢，知识库要能动态更新 |
| **具体做什么** | 给 `ingest/telegram_ingest.py` 加入增量更新逻辑：记录最后更新时间，只处理新消息 |
| **今日输出物** | 增量更新版 ingest 脚本 + cron 设置（每天自动更新） |
| **最低完成标准** | 第二次运行只处理新增消息，不重复处理 |

---

### Day 33（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | RAG 项目 README 和文档 |
| **学什么** | 如何写清楚技术项目的 README（架构图/安装/使用/效果展示） |
| **为什么学** | GitHub 展示价值在于 README 质量 |
| **具体做什么** | 写 `personal-rag` 仓库的完整 README：包含 mermaid 架构图、安装步骤、使用截图 |
| **今日输出物** | 完整的 README.md（中文），有架构图和使用截图 |
| **最低完成标准** | 一个没用过这个项目的人看完 README 能理解它是什么、怎么用 |

---

### Day 34（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | LangChain RAG 链学习（对比理解） |
| **学什么** | LangChain LCEL（LangChain Expression Language）；用 LangChain 重写你的 RAG chain |
| **为什么学** | 求职时面试官会问 LangChain；用 LangChain 重写是最好的学习方式 |
| **具体做什么** | 读 LangChain RAG Tutorial；用 LCEL 写一个等价的 RAG chain |
| **学习资料** | https://python.langchain.com/docs/tutorials/rag/ |
| **今日输出物** | `rag/langchain_rag.py`，LangChain 版本的 RAG chain |
| **最低完成标准** | LangChain 版本跑通，能对比两种实现的代码差异 |

---

### Day 35（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 5 复盘 |
| **具体做什么** | 填写 weekly check；把 personal-rag 推到 GitHub；记录 RAG 实践中遇到的真实问题 |
| **今日输出物** | week-05-check.md |

---

## Week 6：单 Agent 工作流（LangGraph）

**本周主题**：用 LangGraph 重构日报生成流程，建立有状态的 agent 工作流

---

### Day 36（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | LangGraph 基础概念 |
| **学什么** | State、Node、Edge、Graph 四个核心概念；有向图工作流 vs 线性脚本的区别 |
| **为什么学** | LangGraph 是做复杂 agent 工作流最主流的框架 |
| **具体做什么** | 读 LangGraph Quickstart；跑通官方示例 |
| **学习资料** | https://langchain-ai.github.io/langgraph/ |
| **今日输出物** | 跑通 LangGraph 官方示例，写 100 字理解笔记 |
| **最低完成标准** | 官方示例能在本地/服务器跑通 |

---

### Day 37（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 设计日报工作流的状态图 |
| **学什么** | 如何把业务流程映射成状态图；每个节点的输入输出如何定义 |
| **为什么学** | 先设计再写代码，避免写到一半发现架构有问题 |
| **具体做什么** | 在纸上/Mermaid 里画出日报工作流：collect_news → filter → summarize → format → send → done；定义 StateSchema |
| **今日输出物** | `daily-digest-agent/docs/workflow-design.md`，包含状态图和每个节点的输入输出定义 |
| **最低完成标准** | 画出完整状态图，每个节点有明确的职责 |

---

### Day 38（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | 实现 collect + filter 两个节点 |
| **学什么** | LangGraph node 的编写方式；条件边（conditional edge）的用法 |
| **为什么学** | filter 节点需要条件判断（内容是否相关），需要用到条件边 |
| **具体做什么** | 实现 `collect_node`（从 SQLite 获取今日收集）和 `filter_node`（用 LLM 过滤无关内容） |
| **今日输出物** | 两个节点实现完成，单独测试通过 |
| **最低完成标准** | collect_node 能返回今日消息；filter_node 能过滤掉广告类无关内容 |

---

### Day 39（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 实现 summarize + format + send 节点 |
| **学什么** | 如何设计摘要节点的 prompt；结构化输出（JSON mode） |
| **为什么学** | 摘要质量决定日报价值 |
| **具体做什么** | 实现剩余 3 个节点；把所有节点串成完整图；端到端测试 |
| **今日输出物** | 完整的 LangGraph 工作流，能端到端跑通 |
| **最低完成标准** | 工作流能跑完，Telegram 收到一条格式正确的测试日报 |

---

### Day 40（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 错误恢复 + 状态持久化 |
| **学什么** | LangGraph 的 checkpointing（状态保存）；如何从中途失败的节点恢复 |
| **为什么学** | 生产环境工作流会失败，必须能从失败点继续 |
| **具体做什么** | 给工作流加入 SQLite checkpointer；测试：在 summarize 节点前强制失败，然后从 checkpoint 恢复 |
| **学习资料** | LangGraph checkpointing: https://langchain-ai.github.io/langgraph/concepts/persistence/ |
| **今日输出物** | 有 checkpointing 的工作流，失败后能从断点继续 |
| **最低完成标准** | 模拟中途失败后，能从上次成功的节点继续 |

---

### Day 41（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 修复 OpenClaw Cron 错误 + 接入 LangGraph 工作流 |
| **学什么** | OpenClaw cron 的 delivery.channel 配置 |
| **为什么学** | cron 一直在报错（consecutiveErrors: 2），修了之后每天自动触发工作流 |
| **具体做什么** | 读 OpenClaw cron 配置文档；修复 delivery.channel 设置；把 LangGraph 工作流设为 cron 触发目标 |
| **今日输出物** | OpenClaw cron 不再报错，每天 22:00 自动触发日报生成 |
| **最低完成标准** | cron lastRunStatus 变为 "success" |

---

### Day 42（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 6 复盘 |
| **具体做什么** | 填写 weekly check；把 daily-digest-agent 推到 GitHub |
| **今日输出物** | week-06-check.md |

---

## Week 7：OpenClaw Skills 开发

**本周主题**：开发 2 个生产可用的 OpenClaw Skills

---

### Day 43（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | OpenClaw Skill 开发规范深入研究 |
| **学什么** | skill 的 manifest 格式、tool schema、执行环境 |
| **为什么学** | 需要搞清楚 skill 的接口规范才能写 |
| **具体做什么** | 在服务器上找已有 skill 示例（如果有）；读 OpenClaw 官方 skill 文档；如果文档不足，读 /opt/occ 源码 |
| **今日输出物** | 笔记：OpenClaw skill 开发规范总结 |
| **最低完成标准** | 能说清楚一个 skill 需要有哪些文件，每个文件的作用 |

---

### Day 44（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 开发 web_search skill |
| **学什么** | Skill 的具体实现；工具输入验证 |
| **为什么学** | web_search 是最有用的 skill，优先开发 |
| **具体做什么** | 基于 Week 3 的 `tools/web_search.py`，封装成 OpenClaw skill 格式 |
| **今日输出物** | 可安装的 `web-search` skill |
| **最低完成标准** | 在 OpenClaw 控制面板安装后，黑寡妇能调用它搜索 |

---

### Day 45（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | 测试和调试 web_search skill |
| **学什么** | 如何调试 skill（日志、错误信息）；OpenClaw 的工具调用日志在哪里 |
| **具体做什么** | 发 10 条需要搜索的消息给黑寡妇，记录成功/失败情况；修复发现的 bug |
| **今日输出物** | 测试报告：10 次调用结果 |
| **最低完成标准** | 10 次中 8 次成功返回搜索结果 |

---

### Day 46（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 开发 note_writer skill |
| **学什么** | 文件系统 skill 的权限设计；如何避免路径穿越漏洞 |
| **为什么学** | 让 agent 能写笔记是"agent 能产出有价值内容"的关键 |
| **具体做什么** | 封装 `tools/note_writer.py` 为 OpenClaw skill；加入路径安全检查（只允许写入指定目录） |
| **今日输出物** | 可安装的 `note-writer` skill |
| **最低完成标准** | friday 能通过这个 skill 把重要信息写入笔记文件 |

---

### Day 47（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 开发 rag_search skill |
| **学什么** | 如何让 skill 调用本地服务（RAG 系统） |
| **为什么学** | 把 Week 5 的 RAG 系统接入 OpenClaw，让所有 agent 都能查知识库 |
| **具体做什么** | 把 RAG 系统封装成一个简单的 HTTP API（用 FastAPI 或 Flask）；写 skill 调用这个 API |
| **今日输出物** | RAG HTTP API + rag_search skill |
| **最低完成标准** | OpenClaw 里任何 agent 都能调用 `rag_search("查询内容")` |

---

### Day 48（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | Skills 整合测试 + 文档 |
| **学什么** | 如何写 skill 的 README（给其他 OpenClaw 用户用） |
| **具体做什么** | 为每个 skill 写使用文档；做一个综合演示（Friday 协调 3 个 agent 同时使用不同 skill） |
| **今日输出物** | `avengers-skills` GitHub 仓库有完整文档和演示截图 |
| **最低完成标准** | 3 个 skill 都有 README，都有使用截图 |

---

### Day 49（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 7 复盘 |
| **今日输出物** | week-07-check.md |

---

## Week 8：Memory / Session / State

**本周主题**：给 agent 加记忆，让对话跨会话保持上下文

---

### Day 50（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | Agent 记忆的类型 |
| **学什么** | in-context memory、external memory、long-term memory 的区别和适用场景 |
| **为什么学** | 现有 Friday 对话没有跨 session 的记忆，每次启动都是全新对话 |
| **具体做什么** | 读 Anthropic Memory and Storage 文档；读 LangGraph Memory 文档；做笔记 |
| **学习资料** | https://docs.anthropic.com/en/docs/build-with-claude/memory-and-storage |
| **今日输出物** | 笔记：3 种记忆类型的对比表格 |
| **最低完成标准** | 能解释什么时候用哪种记忆方式 |

---

### Day 51（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 实现 User Profile 记忆 |
| **学什么** | 如何从对话中提取重要信息并持久化存储 |
| **为什么学** | 让 Friday 记住"我喜欢什么、我在做什么项目"这类长期信息 |
| **具体做什么** | 写 `memory/user_profile.py`：用 LLM 从对话里提取关键事实，存入 JSON 文件；Friday 每次对话开始都加载这个 profile |
| **今日输出物** | `memory/user_profile.py` + Friday 集成 |
| **最低完成标准** | 告诉 Friday "我在学 LangGraph"，下次对话时它能记住这个事实 |

---

### Day 52（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | mem0 集成（可选的高级方案） |
| **学什么** | mem0 库的 API；自动记忆提取 vs 手动记忆管理 |
| **为什么学** | mem0 是专门做 agent 记忆的库，可以比自己写的更完善 |
| **具体做什么** | 安装 mem0；用它替换手写的 user_profile.py；对比两种方案的优劣 |
| **学习资料** | https://github.com/mem0ai/mem0 |
| **今日输出物** | mem0 版本的 memory 实现；对比分析笔记 |
| **最低完成标准** | 两种方案都跑通，写清楚选哪个及原因 |

---

### Day 53（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | Session 管理深入理解 |
| **学什么** | OpenClaw 的 session 概念（per-channel-peer）；如何控制 session 范围 |
| **为什么学** | 理解 OpenClaw 的 session 机制，才能更好地控制多 agent 协作的上下文 |
| **具体做什么** | 读 OpenClaw session 相关文档；测试不同 session 配置对 agent 行为的影响 |
| **今日输出物** | 笔记：OpenClaw session 机制理解 |
| **最低完成标准** | 能解释 `dmScope: per-channel-peer` 的含义和影响 |

---

### Day 54（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 给 daily-digest-agent 加历史对比功能 |
| **学什么** | 如何存储历史状态；如何比较今天 vs 昨天的内容 |
| **为什么学** | 有历史对比的日报更有价值（"今天新出现了 X 话题"） |
| **具体做什么** | 给工作流加入"历史日报存储"节点；在格式化节点加入与昨日的对比 |
| **今日输出物** | 升级版日报，包含"今日新增话题"部分 |
| **最低完成标准** | 日报里有"今日新增"一节 |

---

### Day 55（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 第二阶段项目整合 + 测试 |
| **学什么** | 系统集成测试；如何发现项目之间的冲突 |
| **具体做什么** | 测试 3 个项目（RAG + 日报 + Skills）在服务器上同时运行是否稳定；修复发现的问题 |
| **今日输出物** | 测试报告；修复了的 bug 列表 |
| **最低完成标准** | 3 个项目在服务器上稳定运行 24 小时 |

---

### Day 56（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 8 复盘 + 第二阶段总结 |
| **今日输出物** | week-08-check.md + `docs/phase2-summary.md` |

---

# 第三阶段：平台化 + 工程化（Week 9-12）

---

## Week 9：多 Agent 协作进阶

**本周主题**：把复仇者团队升级为真正的协作系统

---

### Day 57（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | 多 Agent 协作模式研究 |
| **学什么** | Orchestrator-Worker 模式、Peer-to-Peer 模式、Pipeline 模式的区别 |
| **为什么学** | 现有复仇者团队是 Friday 单向调度，更复杂的任务需要更灵活的协作模式 |
| **具体做什么** | 读 Anthropic Building Effective Agents 全文（重点看 Multi-agent 部分）；对照现有系统分析当前是哪种模式 |
| **学习资料** | https://www.anthropic.com/engineering/building-effective-agents |
| **今日输出物** | 笔记：现有复仇者团队的协作模式分析 + 升级方向 |

---

### Day 58（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 设计任务分解协议 |
| **学什么** | 如何让 Friday 自动把复杂任务分解成子任务，分发给合适的 agent |
| **具体做什么** | 给 Friday 设计"任务分解 prompt"；让它能把"分析 X 领域的市场机会"拆成情报收集/技术分析/战略规划 3 个子任务 |
| **今日输出物** | 升级版 Friday 能把大任务自动拆分成子任务并分发 |
| **最低完成标准** | 发一个复杂问题，Friday 能自动分配给 2 个以上 agent |

---

### Day 59（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | Agent 结果汇总机制 |
| **学什么** | 如何收集各 agent 的子任务结果；如何让 Friday 综合多个结果给出统一回答 |
| **具体做什么** | 修改 `shared/db.py` 的任务状态查询；让 Friday 等待所有子任务完成后再汇总 |
| **今日输出物** | Friday 能等待多个子任务，汇总结果后回复 |
| **最低完成标准** | 发一个复杂任务，收到包含多个 agent 贡献的综合回复 |

---

### Day 60（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 并发任务执行 |
| **学什么** | asyncio 任务并发；子任务并行 vs 串行的选择 |
| **为什么学** | 当前子 agent 是串行执行，可以改成并发大幅提速 |
| **具体做什么** | 把 Friday 的子任务分发改成并发执行（`asyncio.gather`）；测试性能提升 |
| **今日输出物** | 并发版子任务执行；性能对比数据 |
| **最低完成标准** | 3 个子任务并发执行时间 < 串行执行时间的一半 |

---

### Day 61（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 给每个 agent 添加专属工具 |
| **学什么** | 不同角色的 agent 应该有哪些专属工具 |
| **具体做什么** | 黑寡妇加 web_search；钢铁侠加 code_runner；Friday 加 rag_search；验证每个 agent 能用对工具 |
| **今日输出物** | 3 个 agent 都有专属 skill，能在对话中自动调用 |

---

### Day 62（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 多 Agent 协作演示案例 |
| **具体做什么** | 做一个完整演示："帮我研究一下最近 AI 编程工具的竞争格局" → 黑寡妇搜索 → 钢铁侠技术分析 → 奇异博士战略总结 → Friday 汇报 |
| **今日输出物** | 演示录屏 + 流程文档 |
| **最低完成标准** | 整个流程端到端跑通，得到有实质内容的回答 |

---

### Day 63（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 9 复盘 |
| **今日输出物** | week-09-check.md |

---

## Week 10：Eval + 监控 + 成本追踪

**本周主题**：给系统加上"眼睛"——知道系统跑得怎么样

---

### Day 64（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | Agent Eval 基础 |
| **学什么** | 什么是 faithfulness / answer relevancy / context precision；如何用 RAGAS 评估 RAG |
| **为什么学** | 没有 eval 就不知道 RAG 质量好不好 |
| **具体做什么** | 安装 RAGAS；创建 20 个测试问答对；运行评估，得到分数 |
| **学习资料** | https://docs.ragas.io/en/latest/ |
| **今日输出物** | RAG 系统的 RAGAS 评估报告 |
| **最低完成标准** | 得到 faithfulness 和 answer_relevancy 两个指标的具体数值 |

---

### Day 65（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | Token 成本追踪 |
| **学什么** | 如何统计每次调用的 token 消耗；如何估算月成本 |
| **为什么学** | 生产系统必须知道成本，避免不知不觉超支 |
| **具体做什么** | 修改 `shared/llm_async.py`，记录每次调用的 input/output token 数量到数据库；写统计脚本 |
| **今日输出物** | `monitoring/token_tracker.py`；能查询总 token 使用量和估算成本 |
| **最低完成标准** | 能查到"今日总 token 消耗"和"今日预估费用" |

---

### Day 66（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | Agent Success Rate 统计 |
| **学什么** | 如何定义 agent 任务的"成功"；如何从日志里提取成功率 |
| **具体做什么** | 给 `shared/db.py` 的任务状态加上 "success" / "partial" / "failed" 分类；写统计脚本 |
| **今日输出物** | `monitoring/success_rate.py`；能统计每个 agent 的任务成功率 |
| **最低完成标准** | 能看到每个 agent 的 7 日成功率 |

---

### Day 67（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | LangSmith 接入（可选） |
| **学什么** | LangSmith 的 trace 功能；如何可视化 agent 的调用链 |
| **为什么学** | LangSmith 是海外最主流的 LLM 观测平台，了解它对求职有帮助 |
| **具体做什么** | 注册 LangSmith；给 LangChain RAG chain 加上追踪；查看一次完整调用的 trace |
| **学习资料** | https://docs.smith.langchain.com/ |
| **今日输出物** | LangSmith 里有至少一条完整的 RAG 调用 trace |

---

### Day 68（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 每日监控报告 |
| **学什么** | 如何把监控数据格式化成易读的报告；如何通过 Telegram 发送 |
| **具体做什么** | 写 `monitoring/daily_report.py`：汇总今日 token 成本、任务成功率、RAG 查询次数；每天 23:00 通过 Telegram 发给自己 |
| **今日输出物** | 自动发送的每日监控报告 |
| **最低完成标准** | 收到一条包含成本和成功率数据的监控消息 |

---

### Day 69（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 用 eval 数据优化 RAG |
| **学什么** | 基于评估结果改进 RAG：哪个环节分数低就改哪里 |
| **具体做什么** | 分析 Day 64 的 RAGAS 报告，找出最低分的维度；有针对性地优化（可能是 chunk size、可能是 prompt） |
| **今日输出物** | 优化后的 RAG 系统，RAGAS 分数至少提升 10% |

---

### Day 70（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 10 复盘 |
| **今日输出物** | week-10-check.md |

---

## Week 11：部署工程化

**本周主题**：让项目可以被别人复现和部署

---

### Day 71（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | Docker 化 Python 应用 |
| **学什么** | Dockerfile 编写、多阶段构建、环境变量管理 |
| **为什么学** | 容器化是让项目可复现的标准方式，也是部署到任何环境的基础 |
| **具体做什么** | 为 avengers-ai-team 写 `Dockerfile` 和 `docker-compose.yml` |
| **学习资料** | https://docs.docker.com/get-started/ |
| **今日输出物** | 能用 `docker-compose up` 启动整个 avengers 系统 |
| **最低完成标准** | Friday bot 能在 Docker 里正常运行 |

---

### Day 72（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 环境变量管理 + 部署文档 |
| **学什么** | `.env` 文件规范；`.env.example` 最佳实践；secrets 管理 |
| **为什么学** | 现在代码里还有硬编码的 API key，这是安全问题 |
| **具体做什么** | 全面检查所有代码，把硬编码的 key 改成环境变量；写部署文档 |
| **今日输出物** | 0 个硬编码 secret；完整的 `docs/deploy.md` |
| **最低完成标准** | grep -r 'api_key' 找不到任何硬编码值 |

---

### Day 73（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | GitHub Actions CI/CD |
| **学什么** | GitHub Actions 基础；自动运行测试；lint 检查 |
| **为什么学** | 有 CI 才能保证代码质量，这是工程化的标志 |
| **具体做什么** | 写 `.github/workflows/test.yml`：PR 时自动运行 pytest |
| **今日输出物** | GitHub Actions 绿色，pytest 自动运行 |

---

### Day 74（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 为 3 个项目写双语 README |
| **学什么** | 英文技术写作规范；如何描述技术项目 |
| **为什么学** | 海外求职需要英文 README |
| **具体做什么** | 给 personal-rag / daily-digest-agent / avengers-skills 都加上英文 README（可以先用中文写，再翻译） |
| **今日输出物** | 3 个仓库都有中英双语 README |

---

### Day 75（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 项目架构图 |
| **学什么** | Mermaid 图表语法；架构图的内容和层次 |
| **为什么学** | 架构图让别人快速理解系统设计，是展示系统思维的关键 |
| **具体做什么** | 为 3 个项目各画一张架构图（用 Mermaid，嵌入 README） |
| **今日输出物** | 3 个架构图，都嵌入 README |

---

### Day 76（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 录制 Demo 视频 |
| **学什么** | 如何录制有效的技术演示（屏幕录制 + 说明字幕） |
| **为什么学** | Demo 视频比截图更有说服力 |
| **具体做什么** | 录制 2-3 分钟演示视频：RAG 查询演示 + 日报自动生成演示 |
| **今日输出物** | 演示视频（可上传到 Bilibili 或 YouTube） |

---

### Day 77（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | Week 11 复盘 |
| **今日输出物** | week-11-check.md |

---

## Week 12：作品集 + 简历 + 面试准备

**本周主题**：把 3 个月的成果转化为求职竞争力

---

### Day 78（周一）

| 项目 | 内容 |
|------|------|
| **今日主题** | 更新 GitHub Profile README |
| **学什么** | GitHub Profile README 的设计原则；如何展示项目 |
| **具体做什么** | 创建 GitHub Profile 仓库（用户名/用户名）；写个人介绍：AI Agent 工程师方向，附项目链接 |
| **今日输出物** | GitHub Profile 有完整的自我介绍和项目展示 |

---

### Day 79（周二）

| 项目 | 内容 |
|------|------|
| **今日主题** | 更新简历 |
| **学什么** | AI 工程师简历的写法；如何描述项目经验 |
| **具体做什么** | 用 project-suggestions.md 里的"简历怎么写"作为参考，更新简历的项目经验部分 |
| **今日输出物** | 更新后的简历（AI Agent 工程师方向） |

---

### Day 80（周三）

| 项目 | 内容 |
|------|------|
| **今日主题** | 写技术文章 1：RAG 实践总结 |
| **学什么** | 技术文章的结构（背景/方案/实现/效果/经验总结） |
| **具体做什么** | 写一篇关于搭建个人 RAG 知识库的文章，发到掘金 |
| **今日输出物** | 掘金发布的技术文章链接 |
| **最低完成标准** | 文章字数 > 1500 字，有代码示例 |

---

### Day 81（周四）

| 项目 | 内容 |
|------|------|
| **今日主题** | 写技术文章 2：OpenClaw 多 Agent 实践 |
| **具体做什么** | 写一篇关于复仇者团队的文章：如何用 OpenClaw 搭建多 agent 系统 |
| **今日输出物** | 掘金/知乎发布的技术文章链接 |

---

### Day 82（周五）

| 项目 | 内容 |
|------|------|
| **今日主题** | 面试问题准备 |
| **学什么** | AI 工程师面试常见问题（RAG / Agent / Prompt / Eval） |
| **具体做什么** | 整理 20 个高频面试题，用自己的语言写出回答（结合自己的项目） |
| **今日输出物** | `docs/interview-prep.md`，20 个问题 + 自己的回答 |

---

### Day 83（周六）

| 项目 | 内容 |
|------|------|
| **今日主题** | 整理 portfolio/ 目录 |
| **具体做什么** | 按照 `portfolio/github-showcase-plan.md` 的规划，确保所有展示材料就位；更新 `openclaw-ai` 仓库的主 README |
| **今日输出物** | 完整的作品集目录，所有项目都有截图/视频/README |

---

### Day 84（周日）

| 项目 | 内容 |
|------|------|
| **今日主题** | 3 个月总复盘 |
| **具体做什么** | 填写 monthly-review-template（第 3 个月）；回顾整个 3 个月；给下一阶段（月 4+）设定目标 |
| **今日输出物** | `plan/logs/month-03-review.md` + `docs/next-phase-plan.md` |

---

## 附录：每月模板文件位置

- 每日日志：`plan/logs/YYYY-MM-DD.md`
- 每周复盘：`plan/logs/week-XX-check.md`
- 每月复盘：`plan/logs/month-XX-review.md`
