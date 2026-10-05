# 7. LangGraph

[← 6. Model Context Protocol (MCP)](../06_mcp/README.md) · [↑ Agentic AI contents](../README.md) · [8. Other agent frameworks →](../08_agent_frameworks/README.md)

A framework from the LangChain team for building **stateful agents as graphs**. Nodes do the work, edges decide what runs next, and a shared state object carries data between them. Loops, branches, memory and human approval are all first-class.

**Prerequisites:** tool use (4.2), reasoning patterns (4.4), LangChain basics (`3_gen_ai/` 7).

**In this section:** [Core concepts](#langgraph-core-concepts) · [A minimal agent graph](#a-minimal-agent-graph) · [Key features](#key-langgraph-features) · [Common patterns](#common-langgraph-patterns) · [Hands-On: LangGraph](#hands-on-langgraph)

## LangGraph core concepts

| Concept | What it is |
|---|---|
| **State** | A typed object (TypedDict / Pydantic) shared by all nodes, such as `messages` and `user_id` |
| **Node** | A Python function that reads the state and returns updates (an LLM call, a tool, a check) |
| **Edge** | A fixed next step |
| **Conditional edge** | Picks the next node from the state, which is how routing and loops work |
| **Checkpointer** | Saves the state after each step, giving memory, resume and time travel |
| **Interrupt** | Pauses the graph to wait for human input or approval |

## A minimal agent graph

```
START → [agent (LLM)] ──tool call?──yes──► [tools] ──┐
              ▲                                       │
              └───────────────────────────────────────┘
              │
              no
              ▼
             END
```

```python
graph = StateGraph(State)
graph.add_node("agent", call_model)
graph.add_node("tools", ToolNode(tools))
graph.add_edge(START, "agent")
graph.add_conditional_edges("agent", tools_condition)
graph.add_edge("tools", "agent")
app = graph.compile(checkpointer=MemorySaver())
```

## Key LangGraph features

- **Persistence:** conversation memory per `thread_id` (in memory, SQLite, Postgres or Redis).
- **Streaming:** stream tokens, node updates or events, which is needed for chat and voice.
- **Human-in-the-loop:** pause before risky tool calls and resume after approval.
- **Subgraphs:** nest one agent graph inside another.
- **Deployment:** LangGraph Platform / server, or your own FastAPI app.

## Common LangGraph patterns

| Pattern | Shape |
|---|---|
| **ReAct agent** | agent ⇄ tools loop |
| **Router** | classify → branch to specialist nodes |
| **Corrective RAG** | retrieve → grade → (rewrite → retrieve) → generate |
| **Plan-and-execute** | planner → executor loop → replanner |
| **Supervisor (multi-agent)** | a supervisor node delegates to worker agents |
| **Reflection** | generate → critique → revise |

## Hands-On: LangGraph

| # | Exercise | Tools |
|---|---|---|
| 7.1 | ReAct agent with 2–3 tools | LangGraph |
| 7.2 | Add memory with a checkpointer | LangGraph, SQLite / Postgres |
| 7.3 | Router graph → chat, RAG and task nodes | LangGraph |
| 7.4 | Human approval before a tool runs | LangGraph interrupts |
| 7.5 | Supervisor with two worker agents | LangGraph |
| 7.6 | Stream tokens to a web UI, then trace them | LangGraph, FastAPI, LangSmith |

---

[← 6. Model Context Protocol (MCP)](../06_mcp/README.md) · [↑ Agentic AI contents](../README.md) · [8. Other agent frameworks →](../08_agent_frameworks/README.md)
