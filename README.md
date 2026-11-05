# OpenSafely-RAG

[![Stars](https://img.shields.io/github/stars/zwelshman/OpenSafely-RAG?style=flat-square&logo=github&color=blue)](https://github.com/zwelshman/OpenSafely-RAG/stargazers)
[![Forks](https://img.shields.io/github/forks/zwelshman/OpenSafely-RAG?style=flat-square&logo=git&color=orange)](https://github.com/zwelshman/OpenSafely-RAG/network/members)
[![Issues](https://img.shields.io/github/issues/zwelshman/OpenSafely-RAG?style=flat-square&logo=issues&color=critical)](https://github.com/zwelshman/OpenSafely-RAG/issues)
[![Repo Size](https://img.shields.io/github/repo-size/zwelshman/OpenSafely-RAG?style=flat-square&logo=codeforces&color=success)](https://github.com/zwelshman/OpenSafely-RAG)

⚠️ **Disclaimer:** This project is independent and not affiliated with the official OpenSafely project.

An open-source Langflow workflow that exposes a hosted Model Context Protocol (MCP) server. It allows you to seamlessly integrate OpenSafely's `ehrql` documentation and workspace structure into your AI assistant of choice (such as Cursor, VS Code, or Claude Desktop).

## 🛠️ Tech Stack
*   **Workflow Orchestration:** Langflow
*   **Data Ingestion:** GitExtractor
*   **Vector Database:** AstraDB
*   **Hosting Platform:** Render

## 📊 Data Pipeline
*   **Source:** Documentation pulled directly from the OpenSafely `ehrql` Repository.
*   **Processing:** The documentation is AST-Python chunked, embedded via Nvidia EmbedQA, and stored in an AstraDB vector database for highly relevant Retrieval-Augmented Generation (RAG).

## 🚀 Supported MCP Tools

Your AI assistant will automatically discover and use the following structural and search capabilities:

*   `query_knowledge_base(question)` – Search and retrieve conceptual answers from the Astra DB Vector Store RAG knowledge base.
*   `search_file_names(query)` – Performs a rapid substring match over project paths to locate source files instantly.
*   `get_file_content(file_path, start_line, end_line)` – Fetches the full or partitioned contents of any workspace file to restore missing context from a RAG chunk.
*   `get_file_structure(file_path)` – Uses Python's Abstract Syntax Tree (AST) to map imports, classes, functions, and docstrings without raw code clutter.
*   `locate_test_file(source_file_path)` – Automatically finds corresponding unit test suites to provide immediate implementation examples.

## ⚙️ Deployment & Integration

*   **Hosted MCP Server (SSE Endpoint):** `https://opensafely-rag-1.onrender.com/mcp/sse`

### VS Code / Cursor Configuration
Add the following snippet to your MCP settings file (e.g., `mcpServers.json` or through your IDE settings panel) to connect your assistant:

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
*(Note: Depending on your client implementation, your AI assistant will intelligently choose between semantic RAG queries and live codebase exploration tools depending on what you ask).*
