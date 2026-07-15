##我的学习资源(complot##
Hugging Face Course（实操）：https://huggingface.co/learn
Hugging Face Transformers 文档：https://huggingface.co/docs/transformers
LangChain 文档：https://langchain.readthedocs.io/
LlamaIndex（索引/检索）：https://llamaindex.ai/ 或 https://gpt-index.readthedocs.io/
SentenceTransformers：https://www.sbert.net/
FAISS（GitHub）：https://github.com/facebookresearch/faiss
OpenAI 文档（若用）：https://platform.openai.com/docs
The Illustrated Transformer（可视化讲解）：http://jalammar.github.io/illustrated-transformer/
FastAPI：https://fastapi.tiangolo.com/
Gradio：https://gradio.app/
tiktoken（OpenAI token 工具）：https://github.com/openai/tiktoken

##我的学习计划(ai生成的）##
Week 1 — LLM 与基础（第 1–7 天） Day 1 — Python / 环境（6h）

学：快速复习 Python（函数、类、虚拟环境）。资源：廖雪峰 Python 教程 https://www.liaoxuefeng.com/wiki/1016959663602400
做：创建 venv、requirements.txt、基本项目结构（src/, notebooks/, data/, README.md）。提交到 GitHub。
Day 2 — Git / Linux / Colab（6h）

学：git 常用命令、分支流程；Linux 常用终端命令。资源：Pro Git https://git-scm.com/book/zh/v2
做：在仓库中提交一个 Jupyter notebook（Hello PyTorch）。
Day 3 — Transformer 概念（6h）

学：看 The Illustrated Transformer（http://jalammar.github.io/illustrated-transformer/）和 Attention is All You Need（摘要）。
做：写一页笔记解释 self-attention、position embedding、multi-head。
Day 4 — Token & Tokenizer（6h）

学：token 概念、BPE / SentencePiece。资源：Hugging Face tokenizers https://github.com/huggingface/tokenizers 与 tiktoken https://github.com/openai/tiktoken
做：运行 tokenizer 示例（gpt2、sentence-transformers），统计不同文本 token 数，提交 tokenize_demo.py。
Day 5 — 解码策略与 prompt（6h）

学：greedy/beam/sampling、temperature/top_k/top_p；prompt engineering 基本形式（system/user/examples）。资源：Hugging Face Course https://huggingface.co/learn
做：用 OpenAI 或 HF Inference API 试验不同解码参数并记录结果。
Day 6 — 小规模 PyTorch 练习（6h）

学：PyTorch 基础训练流程（autograd、optimizer、DataLoader）。资源：PyTorch tutorials https://pytorch.org/tutorials/
做：训练一个非常小的文本分类/序列模型 Demo（或复现官方 tutorial）。
Day 7 — 周复盘 + 小项目开题（6h）

做：把 week1 的 notebook、token 实验整理成一个 folder，写 week1.md，总结问题与待改进项。
决定第一个小项目（RAG for 3–5 文档），准备数据集（抓取或写 3–5 篇短文章到 data/）。
Week 2 — Embeddings & RAG 实战（第 8–14 天） Day 8 — Embeddings 概念（6h）

学：什么是 embeddings、余弦相似度、常用 embedding 模型（sentence-transformers、OpenAI embeddings）。资源：https://www.sbert.net/
做：用 sentence-transformers 生成 embeddings（model: all-MiniLM-L6-v2）。
Day 9 — 文档切片（chunking）与策略（6h）

学：如何 chunk（token-based）、overlap 设计（避免断句丢信息）。
做：实现 split_documents 函数，生成 chunk 文件并记录每片 token 数。
Day 10 — FAISS 入门与索引建立（6h）

学：FAISS 基本索引类型（IndexFlat、IVF、HNSW）。资源：https://github.com/facebookresearch/faiss
做：把 chunks 的 embeddings 加入 FAISS index，执行 kNN 检索 notebook。
Day 11 — RAG 流程整合（6h）

学：如何把检索结果拼入 prompt、摘要/过滤策略。
做：实现一个 notebook：query -> retrieve top-k -> build prompt -> call LLM -> 返回答案（记录 token counts）。
Day 12 — Embedding/检索性能与评估（6h）

学：评估检索召回质量（准确度/精确率/人工评估）与 token 成本估算。
做：对 10 条 query 做人工评估与成本分析，记录在 report.md。
Day 13 — 尝试不同 embedding 方法（6h）

学：比较 sentence-transformers 与 OpenAI embeddings 的差别（表现/速度/成本）。
做：在你的数据集上做对比实验并记录结论。
Day 14 — 周复盘 + 小改进（6h）

做：整理 RAG_demo.ipynb，把重要函数模块化（embeddings.py, retriever.py）。写 week2.md，总结最佳 chunk size、k 值、prompt 模板。
Week 3 — Agent 框架与多工具（第 15–21 天） Day 15 — LangChain 基础（6h）

学：LangChain 的 Chains / Agents / Tools / Memory 概念。资源：https://langchain.readthedocs.io/
做：安装 langchain，用示例搭起简单 chain（LLM -> prompt template）。
Day 16 — 用 LangChain 做 RAG（6h）

做：把你第 2 周的 retriever 接入 LangChain（利用 FAISSRetriever 或自定义 retriever），实现 RAG chain。
Day 17 — Tools & Function Calling（6h）

学：如何把外部工具（计算器、web 搜索、文件读取）包装为 LangChain Tool；理解 function calling 概念（OpenAI）。
做：实现两个工具：calculator（Python 函数）与 web_search（简单 requests 封装），并在 agent 中调用它们。
Day 18 — Memory 与 对话管理（6h）

学：session memory（短期/长期）、如何保存对话历史并避免 token 爆炸。
做：在 agent 中实现对话记忆（简易的 sliding window 或 summary memory），并测试多轮对话。
Day 19 — 多步骤 agent 测试（6h）

做：设计 5 个复杂 user intent（例如：基于文档生成摘要并做数值计算），让 agent 分步完成并记录失败用例。
Day 20 — 安全与输入过滤（6h）

学：基本的输入审查/滥用防护与敏感信息过滤策略。资源：OpenAI 使用指南 https://platform.openai.com/docs
做：实现简单的输入预处理（长度检测、黑名单/白名单），并记录策略。
Day 21 — 周复盘 + agent_core.py（6h）

做：把 agent 代码整理为模块（agent_core.py、tools.py、memory.py）、写测试脚本 test_agent.py，提交到 GitHub。
Week 4 — 工程化、部署与前端（第 22–28 天） Day 22 — FastAPI 快速上手（6h）

学：FastAPI 基本路由、异步、依赖注入。资源：https://fastapi.tiangolo.com/
做：把 agent 封装成 /query REST endpoint（POST { "query": "..." } -> 返回 answer + provenance）。
Day 23 — Gradio 前端集成（6h）

学：Gradio 快速界面搭建。资源：https://gradio.app/
做：做一个简单页面：输入框、发送按钮、显示回答和检索来源，前端调用本地 FastAPI 或在同进程中直接调用 agent。
Day 24 — Dockerize（6h）

学：写 Dockerfile，把后端 + 前端打包。资源：https://docs.docker.com/
做：构建并在本地运行容器（docker build/run），确保环境变量（API keys）不写入代码。
Day 25 — 部署到 Hugging Face Spaces（Gradio）或 VPS（6h）

选项 A（快速）：HF Spaces（Gradio）部署，按官方说明 push repo。资源：https://huggingface.co/spaces
选项 B（生产化）：把容器部署到 VPS（Docker Compose），并设置简单的域名/端口转发。
做：任选一项完成部署并拿到可访问 URL。
Day 26 — 日志、监控与成本控制（6h）

学：记录请求 token、响应时间、简单 rate limiting。
做：在服务中加入日志（请求 id、token count），并写一个小脚本统计每天 token 使用量与估算费用。
Day 27 — 性能优化（6h）

学：批量 embedding、缓存策略、减少重复检索、使用 smaller models for embeddings。
做：实现 embedding cache，调整 k 值 及 chunk size 做对比，记录性能/质量 tradeoff。
Day 28 — 安全审查与隐私（6h）

学：敏感数据处理、API key 管理、依赖审计。
做：把所有 secrets 移到环境变量并写 .env.example；在 README 中写隐私与限制说明。
第 29–30 天 — 收尾、文档与作品集（第 29–30 天） Day 29 — 文档与博客（6h）

做：把 README 完成（项目简介、架构图、运行步骤、部署链接、限制），写一篇 800–1200 字的项目总结博客（放在仓库或个人博客）。
Day 30 — Demo 视频与复盘（6h）

做：录制 2 分钟演示视频（手机或电脑录屏），展示功能与局限；准备面试时的项目讲稿（3–5 分钟）。
