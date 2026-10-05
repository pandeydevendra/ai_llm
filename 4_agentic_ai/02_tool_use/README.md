# 2. Tool use / function calling

[← 1. What is an agent? The agent loop](../01_agent_loop/README.md) · [↑ Agentic AI contents](../README.md) · [3. Memory & state →](../03_memory/README.md)

Tools let an LLM **do things** and **get fresh information**: search the web, query a database, call an API. The LLM never runs the tool itself. It asks for a tool by name with arguments, and **your code** runs it and sends the result back.

**Prerequisites:** the agent loop (1).

**In this section:** [How tool calling works](#how-tool-calling-works) · [Defining a good tool](#defining-a-good-tool) · [Hands-On: Tool Use](#hands-on-tool-use)

## How tool calling works

```
1. You send:     user message + list of tools (name, description, JSON schema of inputs)
2. LLM replies:  tool_use → get_weather(city="Pune")
3. Your code:    runs get_weather("Pune") → "31°C, sunny"
4. You send:     the tool result back
5. LLM replies:  "It's 31°C and sunny in Pune right now."
```

A tool definition:

```json
{
  "name": "get_weather",
  "description": "Get the current weather for a city. Use when the user asks about weather.",
  "input_schema": {
    "type": "object",
    "properties": { "city": { "type": "string", "description": "City name, e.g. Pune" } },
    "required": ["city"]
  }
}
```

## Defining a good tool

| Tip | Why |
|---|---|
| **Clear name & description** | The LLM picks tools from their descriptions, so say *when* to use the tool |
| **Few, simple parameters** | Fewer mistakes in the arguments |
| **Return short, useful results** | Long outputs waste context and confuse the model |
| **Return errors as text** | "City not found" lets the agent recover and try again |
| **Confirm risky actions** | Ask the user before deleting, paying or booking |

## Hands-On: Tool Use

| # | Exercise | Tools |
|---|---|---|
| 2.1 | One tool: a calculator | Anthropic SDK / OpenAI SDK |
| 2.2 | Three tools: calculator, web search, current time. Watch the model choose | LLM API, a search API |
| 2.3 | A tool that queries a small SQLite database | LLM API, SQLite |
| 2.4 | Return an error from a tool and watch the agent recover | LLM API |

---

[← 1. What is an agent? The agent loop](../01_agent_loop/README.md) · [↑ Agentic AI contents](../README.md) · [3. Memory & state →](../03_memory/README.md)
