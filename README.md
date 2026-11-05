# OpenSafely-RAG

[![Stars](https://img.shields.io/github/stars/zwelshman/OpenSafely-RAG?style=flat-square&logo=github&color=blue)](https://github.com/zwelshman/OpenSafely-RAG/stargazers)
[![Forks](https://img.shields.io/github/forks/zwelshman/OpenSafely-RAG?style=flat-square&logo=git&color=orange)](https://github.com/zwelshman/OpenSafely-RAG/network/members)
[![Issues](https://img.shields.io/github/issues/zwelshman/OpenSafely-RAG?style=flat-square&logo=issues&color=critical)](https://github.com/zwelshman/OpenSafely-RAG/issues)
[![Repo Size](https://img.shields.io/github/repo-size/zwelshman/OpenSafely-RAG?style=flat-square&logo=codeforces&color=success)](https://github.com/zwelshman/OpenSafely-RAG)

⚠️ **Disclaimer:** This project is independent and *not affiliated* with the official OpenSafely project.

An open-source **Langflow workflow** that exposes a hosted Model Context Protocol (MCP) server. It allows you to seamlessly integrate OpenSafely's `ehrql` documentation into your AI assistant of choice (such as Cursor, VS Code, or Claude Desktop).

---

## 🛠️ Tech Stack

* **Workflow Orchestration:** Langflow
* **Data Ingestion:** GitExtractor
* **LLM Gateway:** OpenRouter
* **Vector Database:** AstraDB
* **Hosting Platform:** Render

---

## 📊 Data Pipeline

1. **Source:** Documentation pulled directly from the [OpenSafely ehrql Repository](https://github.com/opensafely-core/ehrql).
2. **Processing:** The documentation is chunked, embedded, and stored in an AstraDB vector database for highly relevant Retrieval-Augmented Generation (RAG).

---

## 🚀 Deployment & Integration

* **Hosted MCP Server (SSE):** `https://opensafely-rag-1.onrender.com/mcp/sse`

### VS Code / Cursor Configuration

Add the following snippet to your MCP settings file (e.g., `mcpServers.json`) to connect your assistant:

```json
{
  "mcpServers": {
    "opensafely-rag": {
      "type": "http",
      "url": "https://opensafely-rag-1.onrender.com/mcp/sse"
    }
  }
}
```
*(Note: Depending on your client implementation, you can restrict or expand tool access as needed).*
