# Backend

后端基于 `FastAPI`，负责会话管理、聊天接口、联网检索、LangGraph 工作流问答、文件上传与索引处理。

## 启动

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
copy .env.example llm_backend\.env
cd llm_backend
python run.py
```

## 说明

- `llm_backend/` 是主应用目录。
- `.env.example` 仅提供字段模板，真实配置请保留在本地环境中。
- 图谱索引相关第三方集成说明见根目录 `THIRD_PARTY.md`。
