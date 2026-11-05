# OpenSafely-RAG

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
