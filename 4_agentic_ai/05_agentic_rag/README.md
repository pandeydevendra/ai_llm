# 5. Agentic RAG

[← 4. Planning & reasoning patterns](../04_reasoning_patterns/README.md) · [↑ Agentic AI contents](../README.md) · [6. Model Context Protocol (MCP) →](../06_mcp/README.md)

RAG where an LLM agent controls the retrieval, instead of a pipeline that always runs the same way.

**Prerequisites:** embeddings, vector databases & RAG (`3_gen_ai/` 2, 6, 9), tool use (4.2), reasoning patterns (4.4).

**In this section:** [Plain RAG vs. Agentic RAG](#plain-rag-vs-agentic-rag) · [What the agent decides](#what-the-agent-decides) · [Known patterns](#known-patterns) · [Trade-offs](#trade-offs) · [Hands-On: Agentic RAG](#hands-on-agentic-rag)

## Plain RAG vs. Agentic RAG

**Plain RAG** runs one fixed path. It retrieves once, from one source, and doesn't check the results:

```
Question → embed → retrieve top-k → stuff into prompt → answer
```

**Agentic RAG** runs a loop the agent controls:

```
Question → Agent thinks
             ├─ Do I need to retrieve at all?
             ├─ Which source? (vector DB, SQL, web search, API)
             ├─ Rewrite / split the query
             ├─ Retrieve → grade results: relevant enough?
             │     └─ no → refine query or try another source, loop
             └─ Enough context → generate → check answer is grounded
```

## What the agent decides

| Decision | Example |
|---|---|
| **Whether to retrieve** | "What's 2+2?" needs no retrieval |
| **Routing** | Policy questions go to the docs index, and sales numbers go to a SQL tool |
| **Query rewriting** | Turns a vague question into precise search queries |
| **Decomposition / multi-hop** | "Compare X's 2023 and 2024 revenue" becomes two retrievals, then a synthesis |
| **Self-grading** | Throws out irrelevant chunks and retrieves again if the context is weak |
| **Answer verification** | Checks that the answer is supported by the sources (catches made-up answers) |

## Known patterns

| Pattern | Idea |
|---|---|
| **Self-RAG** | The model decides when to retrieve and critiques its own output |
| **Corrective RAG (CRAG)** | Grades what it retrieved and falls back to web search when the results are poor |
| **Adaptive RAG** | Sends easy, medium and hard questions down different strategies |
| **Multi-agent RAG** | Separate agents handle retrieval, grading and writing |

## Trade-offs

- **Pros:** better answers on complex, ambiguous or multi-source questions.
- **Cons:** more LLM calls, so it's slower, costs more and is harder to debug. Use plain RAG when the questions are simple and the data is well indexed.

## Hands-On: Agentic RAG

| # | Exercise | Tools |
|---|---|---|
| 5.1 | Give an agent retrieval as a tool | Anthropic SDK / Claude Agent SDK, Chroma |
| 5.2 | Corrective RAG: retrieve → grade → rewrite → retrieve again | LangGraph |
| 5.3 | Router across a vector DB, a SQL database and web search | LangGraph, LlamaIndex |
| 5.4 | Compare plain RAG and agentic RAG on the same question set | RAGAS / DeepEval |

---

[← 4. Planning & reasoning patterns](../04_reasoning_patterns/README.md) · [↑ Agentic AI contents](../README.md) · [6. Model Context Protocol (MCP) →](../06_mcp/README.md)
