# 1. What is an agent? The agent loop

[↑ Agentic AI contents](../README.md) · [2. Tool use / function calling →](../02_tool_use/README.md)

A plain LLM call is one question → one answer. An **agent** is an LLM running in a **loop**: it decides what to do, does it (usually by calling a tool), looks at the result, and repeats until the task is done.

**Prerequisites:** working with LLM APIs (`3_gen_ai/` 5).

**In this section:** [LLM call vs. workflow vs. agent](#llm-call-vs-workflow-vs-agent) · [The agent loop](#the-agent-loop) · [When to use an agent](#when-to-use-an-agent) · [Hands-On: Agent Loop](#hands-on-agent-loop)

## LLM call vs. workflow vs. agent

| | What decides the steps? | Example |
|---|---|---|
| **Single LLM call** | Nothing, it's one step | "Summarize this email" |
| **Workflow** | **Your code** decides the fixed steps | Classify → retrieve → answer, the same path every time |
| **Agent** | **The LLM** decides the next step, in a loop | "Find a free slot next week and book a meeting" |

## The agent loop

```
          ┌─────────────────────────────────────┐
          ▼                                     │
User goal → LLM thinks → wants a tool? ──yes──► run tool → add result to messages
                              │
                              no
                              ▼
                        final answer
```

In code, the whole idea fits in a few lines:

```python
messages = [{"role": "user", "content": goal}]
while True:
    reply = llm(messages, tools=tools)
    if not reply.tool_calls:
        break                      # done: reply holds the final answer
    for call in reply.tool_calls:
        result = run_tool(call)    # your code runs the tool, not the LLM
        messages.append(tool_result(call, result))
```

Every agent framework (LangGraph, Claude Agent SDK, CrewAI) is a more capable version of this loop.

## When to use an agent

- **Use one when:** the steps can't be known in advance, or the task needs several tool calls that depend on each other.
- **Don't use one when:** a fixed workflow works. Agents are slower, cost more and are harder to test.
- **Always add:** a maximum number of steps, so a confused agent can't loop forever.

## Hands-On: Agent Loop

| # | Exercise | Tools |
|---|---|---|
| 1.1 | Write the loop above with one fake tool (`get_weather`) | Python, LLM API |
| 1.2 | Print every step: thought, tool call, result | Python |
| 1.3 | Add a step limit and see what happens when it's hit | Python |
| 1.4 | Solve the same task as a fixed workflow and compare | Python |

---

[↑ Agentic AI contents](../README.md) · [2. Tool use / function calling →](../02_tool_use/README.md)
