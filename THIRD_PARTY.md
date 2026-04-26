# Third-Party Components

本项目集成了以下第三方开源组件用于实现智能客服问答能力。

## Microsoft GraphRAG

| 属性 | 详情 |
|------|------|
| 项目地址 | https://github.com/microsoft/graphrag |
| 版本 | 2.1.0 |
| License | MIT License |
| 用途 | 文档索引、知识图谱构建和图谱检索能力接入 |
| 集成方式 | 作为 pip 依赖集成，通过 `graphrag` 包调用 |

> GraphRAG 是 Microsoft 开发的开源项目，用于从非结构化文本中提取知识图谱并支持检索增强生成。

## LangChain / LangGraph

| 属性 | 详情 |
|------|------|
| 项目地址 | https://github.com/langchain-ai/langchain, https://github.com/langchain-ai/langgraph |
| License | MIT License |
| 用途 | 工作流编排、LLM 接口封装、Agent 实现 |
| 代码来源 | 部分实现基于 LangChain/LangGraph 官方文档和教程 |

主要使用的子包：
- `langgraph` - 工作流编排框架
- `langchain-core` - 核心抽象
- `langchain-community` - 社区集成
- `langchain-deepseek` - DeepSeek 模型适配
- `langchain-ollama` - Ollama 本地模型适配
- `langgraph-checkpoint-sqlite` - 状态持久化

## Neo4j & langchain-neo4j

| 属性 | 详情 |
|------|------|
| 项目地址 | https://github.com/neo4j/, https://github.com/langchain-ai/langchain-neo4j |
| License | Apache 2.0 / GPL v3 |
| 用途 | 图数据库连接、Text2Cypher 实现 |
| 代码来源 | 部分代码参考自 langchain-neo4j 和 neo4j-graphrag-python 项目 |

主要使用的包：
- `neo4j` - Neo4j Python 驱动
- `langchain-neo4j` - LangChain Neo4j 集成
- `neo4j-graphrag` - Neo4j GraphRAG 检索器

## 其他开源组件

| 组件 | License | 用途 |
|------|---------|------|
| FastAPI | MIT | Web 框架 |
| SQLAlchemy | MIT | ORM |
| Pydantic | MIT | 数据验证 |
| sentence-transformers | Apache 2.0 | 文本嵌入 |
| tiktoken | MIT | Token 计数 |
| networkx | BSD-3-Clause | 图算法 |
| loguru | MIT | 日志系统 |

## 项目自定义代码说明

以下代码是本项目基于开源项目文档和教程的自定义实现：

1. **agentic_rag_agents** (`app/lg_agent/kg_sub_graph/agentic_rag_agents/`)
   - 基于 LangChain/LangGraph 官方文档的 Agent 工作流实现
   - 包含意图识别、任务规划、工具选择等核心逻辑

2. **Text2Cypher 组件**
   - 部分实现参考自 langchain-neo4j 项目
   - 用于将自然语言转换为 Cypher 查询

## 许可证说明

本项目整体采用 MIT License。本项目使用的所有开源组件均兼容 MIT License。

如需进一步了解各组件的许可证要求，请参考各自项目的 LICENSE 文件。

## 致谢

感谢以下开源项目为本项目提供技术支持：

- Microsoft GraphRAG
- LangChain / LangGraph
- Neo4j
- FastAPI
- 所有其他开源贡献者
