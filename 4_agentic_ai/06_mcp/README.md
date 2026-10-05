# 6. Model Context Protocol (MCP)

[← 5. Agentic RAG](../05_agentic_rag/README.md) · [↑ Agentic AI contents](../README.md) · [7. LangGraph →](../07_langgraph/README.md)

An open standard for connecting LLM apps to tools and data. Instead of writing custom tool code for every app, you build an **MCP server** once (for example for your calendar or database), and any MCP-capable client (Claude Desktop, Claude Code, your own agent) can use it.

**Prerequisites:** tool use (2).

## What you'll learn

- MCP's parts: **host / client / server**, and what a server exposes: **tools**, **resources** and **prompts**
- Transports: local (stdio) and remote (HTTP)
- How MCP compares with plain function calling

## Hands-On: MCP

| # | Exercise | Tools |
|---|---|---|
| 6.1 | Use an existing MCP server (filesystem or fetch) from Claude Desktop / Claude Code | MCP |
| 6.2 | Build a small MCP server with one tool, e.g. notes or weather | MCP Python SDK |
| 6.3 | Call your MCP server from your own agent | MCP Python SDK, LLM API |

---

[← 5. Agentic RAG](../05_agentic_rag/README.md) · [↑ Agentic AI contents](../README.md) · [7. LangGraph →](../07_langgraph/README.md)
