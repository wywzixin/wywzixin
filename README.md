# 王亚伟

**Agent 开发工程师 | AI Agent · RAG · 大模型微调**

[技术博客](https://wywzixin.github.io/) · [精选项目](#精选项目) · [微调实战](#技术写作)

## 关于我

我是王亚伟，拥有 **9 年研发经验**，专注于 **AI Agent、RAG 与大模型应用开发**。曾在亚信科技参与企业行研多智能体、运营商智能客服和 ChatBI 系统建设，工作覆盖架构设计、工作流编排、工具集成、模型微调与效果评估。

我的工程背景来自 WebGIS 与三维可视化，曾在泰瑞数创、商汤科技、中科星图从事前端与三维平台研发，熟悉 Cesium、Three.js 和 WebGL。这些经历让我能够同时考虑模型能力、后端执行和用户交互，把 Agent 从原型做成可以持续使用的应用。

近期主要投入 **Agent 运行时、上下文管理、长期记忆、多 Agent 协作，以及面向工具调用的微调数据构造**。我会把项目实现与实验过程整理成开源代码和技术文章。

📍 北京 · 🎓 吉首大学，地理信息系统本科

## 技术栈

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=for-the-badge&logo=langgraph&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)

| 方向 | 技术与实践 |
| --- | --- |
| **Agent 工程** | ReAct、Function Calling、LangChain / LangGraph、MCP、Skills、多 Agent 协作、上下文与记忆管理 |
| **RAG 检索** | 文档解析与分块、Embedding、Milvus、BM25、RRF 融合、Rerank、检索与回答质量评估 |
| **模型微调** | Qwen3、Transformers、PEFT、LoRA SFT、训练数据构造、assistant 标签掩码、Badcase 迭代 |
| **应用开发** | Python / asyncio / FastAPI、Java / Spring Boot、TypeScript / Vue 3 / Vite、SSE 流式交互 |
| **三维可视化** | Cesium、Three.js、WebGL、WebGIS 与空间分析 |

## 精选项目

### [TravelNova](https://github.com/wywzixin/TravelNova) · 面向工具调用微调的旅行 Agent

**从场景构造、工具执行轨迹到 LoRA 微调与本地推理，完成旅行助手的训练与应用链路。**

`Python` · `Qwen3-0.6B` · `Transformers / PEFT` · `LoRA` · `Milvus` · `Langfuse`

- **数据构造**：围绕旅行规划、路线、住宿、闲聊与拒答生成 **1,010 条场景**；采集工具调用、工具结果和最终回答，将 **808 条训练对话**通过前缀扩展与末轮重采样整理为 **2,207 条训练序列**。
- **微调与部署**：处理 Qwen Chat Template、assistant 监督区间与标签掩码，完成 Qwen3-0.6B 的 LoRA SFT 和权重合并，再将训练产物接回本地 Function Calling 链路。
- **检索与观测**：基于 **361 份城市攻略**建立 Milvus 检索库，结合向量、关键词与 RRF 融合，接入攻略、天气、路线等工具，并通过 Langfuse 记录调用轨迹。

[查看源码与复现步骤](https://github.com/wywzixin/TravelNova#运行与复现) · [阅读微调实战](https://wywzixin.github.io/agent/travel-assistant-finetuning/)

### [NexCode](https://github.com/wywzixin/NexCode) · 支持长任务与多 Agent 协作的 AI 编程助手

**让模型在真实代码仓库中读取上下文、执行工具、观察结果，并持续推进编程任务。**

`Python` · `asyncio` · `Textual` · `MCP` · `Skills` · `Git worktree`

- **异步运行时**：统一 Anthropic、OpenAI 等模型服务的流式事件；完整工具调用到达后即可调度执行，让工具运行与模型输出交叠，并持续反馈任务进度。
- **上下文与记忆**：结合工具结果预算、历史摘要、近期原文和恢复附件控制上下文增长；通过 JSONL 会话记录与 Markdown 长期记忆支持任务续接和跨会话复用。
- **协作与扩展**：实现子 Agent 分工、团队消息和共享任务状态，通过 Git worktree 隔离工作目录；支持 MCP 工具 Schema 按需加载、Skills 扩展及执行前权限检查。

[查看源码](https://github.com/wywzixin/NexCode) · [记忆机制](https://github.com/wywzixin/NexCode/blob/main/docs/memory.md) · [多 Agent 协作](https://github.com/wywzixin/NexCode/blob/main/docs/agent-teams.md)

## 技术写作

在 [个人博客](https://wywzixin.github.io/) 记录 Agent 工程实践、模型训练和源码拆解。TravelNova 的微调流程整理成了三篇连续文章：

1. [旅行助手的微调数据是怎么来的：从场景生成到工具调用轨迹](https://wywzixin.github.io/agent/travel-assistant-sft-data/)
2. [LoRA 是怎么接进旅行助手的：Qwen3-0.6B 微调脚本拆解](https://wywzixin.github.io/agent/qwen3-lora-training/)
3. [旅行助手中的大模型微调：从 Qwen3-0.6B 到可调用工具的本地 Agent](https://wywzixin.github.io/agent/travel-assistant-finetuning/)

## 联系与交流

- **博客**：[wywzixin.github.io](https://wywzixin.github.io/)
- **GitHub**：[github.com/wywzixin](https://github.com/wywzixin)

欢迎交流 Agent 架构、RAG、模型微调和 AI 开发工具，也欢迎通过项目 Issue 讨论实现细节。
