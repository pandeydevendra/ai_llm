# 11. Deployment & observability

[← 10. Guardrails, safety & evaluation](../10_guardrails_evals/README.md) · [↑ Agentic AI contents](../README.md) · [12. Voice AI: STT, TTS & voice agents →](../12_voice_ai/README.md)

Putting your agent behind an API so a UI (or other people) can use it.

**Prerequisites:** a working agent (1–5, 7).

## What you'll learn

- Serving an agent with **FastAPI**, including **streaming** responses
- Packaging with **Docker**, and keeping secrets in environment variables
- Basic monitoring: logs, latency, token cost

## Hands-On: Deployment

| # | Exercise | Tools |
|---|---|---|
| 11.1 | Wrap your agent in a FastAPI endpoint with streaming | FastAPI |
| 11.2 | Add a simple chat UI | Streamlit / Gradio |
| 11.3 | Containerise it | Docker, Docker Compose |
| 11.4 | Log latency and token cost per request | Python logging / Langfuse |

---

[← 10. Guardrails, safety & evaluation](../10_guardrails_evals/README.md) · [↑ Agentic AI contents](../README.md) · [12. Voice AI: STT, TTS & voice agents →](../12_voice_ai/README.md)
