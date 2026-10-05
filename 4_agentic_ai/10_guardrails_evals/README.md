# 10. Guardrails, safety & evaluation

[← 9. Multi-agent systems](../09_multi_agent/README.md) · [↑ Agentic AI contents](../README.md) · [11. Deployment & observability →](../11_deployment/README.md)

How to know your agent works, and keep it from doing harm.

**Prerequisites:** a working agent (1–5).

## What you'll learn

- **Guardrails:** input checks (prompt injection, abuse), output checks (harmful content, leaked data), confirming tool calls before they run
- **Tracing:** seeing every step of an agent run
- **Evaluation:** test sets, LLM-as-judge, task success rate

## Hands-On: Guardrails & Evals

| # | Exercise | Tools |
|---|---|---|
| 10.1 | Trace your agent's runs and inspect the steps | Langfuse / LangSmith |
| 10.2 | Try prompt-injection attacks on your own agent, then add an input check | LLM API |
| 10.3 | Build a 20-question test set and score it with an LLM judge | DeepEval / promptfoo |
| 10.4 | Require human approval before a risky tool call | LangGraph interrupts |

---

[← 9. Multi-agent systems](../09_multi_agent/README.md) · [↑ Agentic AI contents](../README.md) · [11. Deployment & observability →](../11_deployment/README.md)
