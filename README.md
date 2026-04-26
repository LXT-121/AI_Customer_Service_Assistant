# 智答客服助手 🤖📚

基于 FastAPI、Vue 3 与 LangGraph 构建的 RAG 智能客服与知识问答助手，支持多轮对话、知识检索、联网搜索、文件上传索引与工作流式问答，适合用作个人学习复现后的工程化整理项目。

## ✨ 功能特点

- 💬 **多轮智能对话**: 支持基础聊天、推理问答与会话上下文管理
- 🔎 **检索增强问答**: 集成文档上传、知识索引与 RAG 问答能力
- 🌐 **联网搜索增强**: 支持搜索型问答场景，结合外部信息辅助生成回复
- 🧠 **LangGraph 工作流**: 提供基于 LangGraph 的工作流式查询能力
- 🖼️ **多模态扩展入口**: 支持图片上传与视觉理解相关接口扩展
- 🧩 **前后端分离架构**: 前端提供聊天与演示页面，后端提供统一 API 服务

## 🏗️ 技术栈

### 后端

- **Web 框架**: FastAPI
- **工作流编排**: LangGraph
- **知识增强**: GraphRAG
- **数据库**: MySQL + SQLAlchemy Async
- **缓存 / 状态**: Redis
- **模型接入**: DeepSeek、Ollama、OpenAI 兼容接口

### 前端

- **框架**: Vue 3 + TypeScript
- **构建工具**: Vite
- **路由管理**: Vue Router
- **状态管理**: Pinia
- **请求库**: Axios
- **内容渲染**: Markdown-It / Marked / DOMPurify

## 📁 项目结构

```text
Knowledge-Desk/
├── backend/                       # 后端工程
│   ├── llm_backend/              # FastAPI 主应用
│   │   ├── app/
│   │   │   ├── api/              # 认证等 API 路由
│   │   │   ├── core/             # 配置、日志、中间件、数据库
│   │   │   ├── services/         # 聊天、搜索、索引等服务
│   │   │   ├── models/           # 数据模型
│   │   │   ├── lg_agent/         # LangGraph 工作流相关逻辑
│   │   │   ├── graphrag/         # GraphRAG 接入与必要配置
│   │   │   └── tools/            # 工具能力封装
│   │   ├── run.py                # 后端启动入口
│   │   ├── main.py               # FastAPI 应用入口
│   │   └── static/               # 可选前端静态资源托管目录
│   ├── requirements.txt
│   ├── .env.example
│   └── README.md
├── frontend/                      # 前端工程
│   ├── src/
│   │   ├── views/                # 登录页、聊天页、服务演示页
│   │   ├── router/               # 路由配置
│   │   ├── stores/               # 状态管理
│   │   ├── services/             # API 调用封装
│   │   └── assets/               # 静态资源
│   ├── package.json
│   └── readme.md
├── THIRD_PARTY.md                 # 第三方组件归属说明
└── README.md
```

## 🚀 快速开始

### 前提条件

- Python 3.10+
- Node.js 16+
- MySQL、Redis
- 可用的模型服务配置（如 DeepSeek / Ollama / OpenAI 兼容接口）

### 后端启动

1. 进入后端目录

```bash
cd backend
```

2. 创建虚拟环境并安装依赖

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

3. 配置环境变量

```bash
copy .env.example llm_backend\.env
```

4. 启动后端服务

```bash
cd llm_backend
python run.py
```

5. 打开接口文档

- Swagger 文档: `http://localhost:8000/docs`
- 健康检查: `http://localhost:8000/health`

### 前端启动

1. 进入前端目录

```bash
cd frontend
```

2. 安装依赖

```bash
npm install
```

3. 启动开发环境

```bash
npm run dev
```

4. 打开浏览器访问 `http://localhost:5173`

### 前端构建

```bash
cd frontend
npm run build
```

如需由后端统一托管前端静态资源，可将构建产物复制到 `backend/llm_backend/static/dist`。

## 📝 使用说明

1. 注册并登录系统，进入主聊天页面
2. 在聊天窗口中发起普通问答、推理问答或搜索型问答
3. 如需知识库问答，可上传文档并触发索引流程
4. 在支持的场景下，可调用 LangGraph 工作流能力完成更复杂的问答任务
5. 通过服务演示页查看项目的前端交互形态与接口联动效果

## 🔧 核心能力

### 对话与会话管理

- 支持用户登录、注册与历史会话管理
- 支持多轮上下文对话与消息持久化

### 检索增强与文件索引

- 支持上传文档并建立索引
- 支持基于知识内容的问答增强
- 集成第三方 GraphRAG 组件用于图谱型索引和查询能力扩展

### LangGraph 工作流问答

- 提供 LangGraph 驱动的工作流式查询接口
- 支持更复杂的任务拆分、状态续跑与流式输出

## 📄 API 文档

启动后端后，可通过 `http://localhost:8000/docs` 查看接口文档。

常用接口包括：

- `GET /health` - 服务健康检查
- `POST /api/chat` - 普通聊天
- `POST /api/reason` - 推理问答
- `POST /api/search` - 搜索增强问答
- `POST /api/upload` - 文件上传与索引
- `POST /api/langgraph/query` - LangGraph 工作流查询
- `POST /api/langgraph/resume` - LangGraph 流程续跑

## ⚠️ 使用说明

- GraphRAG 与 LangGraph 相关能力依赖额外模型和运行环境，若依赖未就绪，相关接口会返回降级提示。
- `.env`、日志目录、上传目录、缓存目录与构建产物不应提交到公开仓库。
- 第三方能力归属说明见 [THIRD_PARTY.md](./THIRD_PARTY.md)。

## 🙏 致谢

- [FastAPI](https://fastapi.tiangolo.com/) - 现代化 Python Web 框架
- [LangGraph](https://github.com/langchain-ai/langgraph) - 工作流与多智能体编排框架
- [GraphRAG](https://github.com/microsoft/graphrag) - 图谱检索增强能力
- [Vue.js](https://vuejs.org/) - 前端框架
- [Vite](https://vitejs.dev/) - 前端构建工具


