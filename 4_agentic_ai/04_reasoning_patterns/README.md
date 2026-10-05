# 4. Planning & reasoning patterns

[← 3. Memory & state](../03_memory/README.md) · [↑ Agentic AI contents](../README.md) · [5. Agentic RAG →](../05_agentic_rag/README.md)

Patterns that help an agent handle tasks needing several steps: **think before acting**, **plan ahead**, and **check its own work**.

**Prerequisites:** the agent loop (1), tool use (2).

**In this section:** [The main patterns](#the-main-patterns) · [ReAct step by step](#react-step-by-step) · [Hands-On: Reasoning Patterns](#hands-on-reasoning-patterns)

## The main patterns

| Pattern | Idea | Good for |
|---|---|---|
| **Chain-of-thought** | Think step by step before answering | Logic, maths, multi-step questions |
| **ReAct** | Alternate **Re**asoning and **Act**ing (tool calls) | Most tool-using agents |
| **Plan-and-execute** | Write a full plan first, then do each step | Long tasks with clear steps |
| **Reflection** | Draft → critique → improve | Writing, code, quality-sensitive answers |
| **Routing** | Classify the request, then send it to a specialist | Assistants that handle many kinds of requests |

## ReAct step by step

```
Question: Is it warmer in Pune or Delhi right now?

Thought:      I need the weather in both cities.
Action:       get_weather(city="Pune")
Observation:  31°C
Thought:      Now Delhi.
Action:       get_weather(city="Delhi")
Observation:  27°C
Thought:      31 > 27, so Pune is warmer.
Answer:       Pune is warmer: 31°C vs. 27°C.
```

## Hands-On: Reasoning Patterns

| # | Exercise | Tools |
|---|---|---|
| 4.1 | Compare answers with and without chain-of-thought | LLM API |
| 4.2 | Write a ReAct agent by hand, printing each Thought / Action / Observation | Python, LLM API |
| 4.3 | Plan-and-execute: a planner writes steps, an executor does them | Python / LangGraph |
| 4.4 | Reflection loop: write → critique → rewrite | LLM API |
| 4.5 | Router: send greetings, questions and tasks to different prompts | LLM API / LangGraph |

---

[← 3. Memory & state](../03_memory/README.md) · [↑ Agentic AI contents](../README.md) · [5. Agentic RAG →](../05_agentic_rag/README.md)
