# 3. Memory & state

[← 2. Tool use / function calling](../02_tool_use/README.md) · [↑ Agentic AI contents](../README.md) · [4. Planning & reasoning patterns →](../04_reasoning_patterns/README.md)

LLMs are **stateless**: they remember nothing between calls. All "memory" is information your code stores and puts back into the prompt.

**Prerequisites:** the agent loop (1), embeddings & vector databases (`3_gen_ai/` 2, 6).

**In this section:** [Types of memory](#types-of-memory) · [Handling long conversations](#handling-long-conversations) · [Hands-On: Memory](#hands-on-memory)

## Types of memory

| Type | What it holds | How it works | Example |
|---|---|---|---|
| **Short-term (conversation)** | The current chat | Send the message history with every call | "As I said earlier…" |
| **Working state** | Data for the current task | Variables / graph state | The order ID being processed |
| **Long-term (semantic)** | Facts about the user | Save facts, retrieve relevant ones (vector DB) | "Prefers replies in Hindi" |
| **Episodic** | Past conversations | Store summaries, search them later | "Last week you asked about refunds" |

```
New message → load: recent history + relevant long-term facts → LLM → reply
                                                              └─► save new facts
```

## Handling long conversations

The context window is limited and long prompts cost more, so you can't keep everything forever:

- **Sliding window:** keep only the last N messages.
- **Summarize:** replace older messages with a short summary.
- **Retrieve:** store everything, and pull back only what's relevant to the current message.

## Hands-On: Memory

| # | Exercise | Tools |
|---|---|---|
| 3.1 | Chatbot with no memory, then add message history | LLM API |
| 3.2 | Sliding window + running summary | LLM API |
| 3.3 | Save user facts and recall them in a new session | Chroma / Mem0 |
| 3.4 | Memory with a LangGraph checkpointer | LangGraph |

---

[← 2. Tool use / function calling](../02_tool_use/README.md) · [↑ Agentic AI contents](../README.md) · [4. Planning & reasoning patterns →](../04_reasoning_patterns/README.md)
