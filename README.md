# MCP-powered Agentic RAG using Firecrawl and Qdrant

This project is an agentic Retrieval-Augmented Generation (RAG) system powered by FastMCP, Firecrawl, and Qdrant. It enables intelligent document and web search using LLM tools, with a local vector database for fast, semantic retrieval.

---

## Features:
- **Agentic RAG:** Combines local vector search (Qdrant) and web search (Firecrawl) for robust information retrieval.
- **FastMCP Tool Orchestration:** Exposes tools for LLMs and clients like Cursor IDE.
- **Modular & Extensible:** Easily add new tools or data sources.
- **Clean Repo:** No virtual environments, caches, or local database files tracked in git.

---

## Setup:

### Clone the repository:
```sh
git clone https://github.com/SudeekshaVandrangi/MCP_AgenticRAG_Firecrawl.git
cd MCP_AgenticRAG_Firecrawl
```

### Install Python dependencies:
Make sure you have Python 3.11+ installed.
```sh
pip install -r requirements.txt
```

### Get a Firecrawl API Key:
- Sign up at [Firecrawl](https://www.firecrawl.dev/i/api).
- Add your API key to a `.env` file in the project root:
```
FIRECRAWL_API_KEY=your_api_key_here
```

### Start Qdrant (Vector Database):
You can use Docker:
```sh
docker run -p 6333:6333 -p 6334:6334 \
  -v $(pwd)/qdrant_storage:/qdrant/storage:z \
  qdrant/qdrant
```

### Prepare the Vector Database:
- Run `notebook.ipynb` to create and populate your Qdrant collection.

---

## Running the MCP Server

Start the server:
```sh
python server.py
```

Or configure it as an MCP server in Cursor IDE with a config like:
```json
{
  "mcpServers": {
    "mcp-rag-app": {
      "command": "python",
      "args": ["/absolute/path/to/server.py"],
      "host": "127.0.0.1",
      "port": 8080,
      "timeout": 30000
    }
  }
}
```
![Mcp_Powered_Agentic_RAG_Workflow](https://github.com/user-attachments/assets/f50387bf-688e-4841-8f94-8eab63aa1c2a)


---

## Usage

- Interact with the server via Cursor IDE or any MCP-compatible client.
- Use the provided tools for:
  - **Machine Learning FAQ retrieval** (from Qdrant)
  - **Web search** (via Firecrawl)

---

## Best Practices

- **Recreate environments:** Use `requirements.txt` for dependencies.

---

## Project Structure

```
MCP_AgenticRAG_Firecrawl/
├── server.py           # MCP server with tool definitions
├── rag_code.py         # Retrieval and embedding logic
├── notebook.ipynb      # Setup and data population for Qdrant
├── requirements.txt    # Python dependencies
├── .gitignore          # Excludes venv, cache, and DB files
├── README.md           # This file
└── ...
```

---



---



