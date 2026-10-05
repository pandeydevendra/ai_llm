# 9. Multi-agent systems

[← 8. Other agent frameworks](../08_agent_frameworks/README.md) · [↑ Agentic AI contents](../README.md) · [10. Guardrails, safety & evaluation →](../10_guardrails_evals/README.md)

Several specialised agents work together instead of one agent doing everything, for example a **supervisor** that delegates to a researcher and a writer.

**Prerequisites:** LangGraph (7).

## What you'll learn

| Pattern | Idea |
|---|---|
| **Supervisor / orchestrator–worker** | One agent plans and delegates to workers |
| **Handoff** | An agent passes the conversation to a better-suited agent |
| **Debate / review** | One agent drafts, another critiques |

**Rule of thumb:** start with one agent. Add more only when one agent's prompt or toolset gets too big.

## Hands-On: Multi-Agent

| # | Exercise | Tools |
|---|---|---|
| 9.1 | Supervisor with researcher + writer agents | LangGraph |
| 9.2 | Handoff from a general agent to a billing specialist | LangGraph |
| 9.3 | Compare cost and quality with a single-agent version | Tracing |

---

[← 8. Other agent frameworks](../08_agent_frameworks/README.md) · [↑ Agentic AI contents](../README.md) · [10. Guardrails, safety & evaluation →](../10_guardrails_evals/README.md)
