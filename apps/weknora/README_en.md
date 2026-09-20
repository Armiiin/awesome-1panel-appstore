WeKnora is Tencent's open-source LLM knowledge platform built around three core capabilities: **RAG-based quick Q&A**, a **ReAct agent** that autonomously orchestrates retrieval and tools, and a **Wiki mode** that distills raw documents into a self-maintaining Markdown knowledge base.

## Key Features

- **Document understanding**: 10+ formats (PDF, Word, Excel, images, XMind) via the bundled docreader service with OCR and layout analysis.
- **RAG Q&A**: chunking, embeddings, hybrid retrieval and reranking with citations.
- **Agents**: a ReAct agent that can orchestrate retrieval, MCP tools, sandboxes and web search for multi-step tasks.
- **Wiki & knowledge graph**: auto-generated interlinked wiki pages with revision history and rollback.
- **Data sources**: Feishu, Notion, Yuque, GitLab, RSS and more.
- **Models & observability**: 20+ LLM providers (OpenAI-compatible, DeepSeek, Qwen, Zhipu, Ollama, etc.) plus optional Langfuse tracing.
- **Private deployment & collaboration**: multi-workspace RBAC, audit logs, full data sovereignty.

## Deployment Notes

This package deploys WeKnora with Docker Compose and includes the following services:

| Service | Description | Default port |
| --- | --- | --- |
| frontend | Web UI (Nginx with API proxy) | configured at install (default 80) |
| app | Backend API / agent | configured at install (default 8080) |
| docreader | Document parsing gRPC (internal only) | not exposed |
| postgres | ParadeDB (PostgreSQL + full-text/vector search) | not exposed |
| redis | Task queue and streams | not exposed |
| minio | Object storage, **default storage backend** | S3 9000 / console 9001 |
| searxng | Bundled metasearch for web retrieval | configured at install (default 8888) |

After startup, open the **Web UI port** to initialize.

### Important: configure an LLM first

WeKnora ships no built-in model. After deployment you must configure at least a chat model and an embedding model (remote API or local Ollama) before you can query documents. For local Ollama the default address is `http://host.docker.internal:11434`, and it can be changed at install time.

### Object storage

The bundled MinIO is used as the default file storage, and the bucket is created automatically on first initialization. Be sure to change the default access and secret keys.

### SearXNG (web search)

The bundled SearXNG is not enabled automatically. Add a SearXNG provider under Settings → Web Search with instance URL `http://searxng:8080`.

WeKnora also supports connecting to an **external SearXNG instance**: simply enter its URL in the provider. The external instance must enable JSON output (`search.formats: [json]`); for private/LAN addresses the host must also be added to the `SSRF_WHITELIST` environment variable.

### Secrets

- `SYSTEM_AES_KEY`: encrypts sensitive fields such as API keys in the database. It **must be exactly 32 characters** and kept safe — losing it makes encrypted data unrecoverable.
- `JWT_SECRET`: auto-generated at install time; replace it with a strong random value.
- Change the default database, Redis and MinIO passwords as well as the SearXNG secret during installation.

## Requirements

- Recommended: 4 CPU cores, 8 GB RAM, 20 GB free disk.
- The docreader image is large (~1.5 GB), so the first pull and startup take a while.

## Official Resources

- Website: [https://weknora.weixin.qq.com](https://weknora.weixin.qq.com)
- GitHub: [https://github.com/Tencent/WeKnora](https://github.com/Tencent/WeKnora)
- Documentation: [https://github.com/Tencent/WeKnora](https://github.com/Tencent/WeKnora)
