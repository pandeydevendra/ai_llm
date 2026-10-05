# Agentic AI

[← Back to main README](../README.md)

**Goal:** learn to build an agent you can talk to by **chat and voice**. Every topic below is a step toward the [capstone project](../projects/conversational_agent_design.md).

**Before you start:** be comfortable with LLM APIs, embeddings, vector DBs and RAG ([`3_gen_ai/`](../3_gen_ai/README.md) topics 2–9).

## 📖 Book Index — Part 4: Agentic AI

**Chapters:** [1. The agent loop](#chapter-1-the-agent-loop) · [2. Tool use / function calling](#chapter-2-tool-use--function-calling) · [3. Memory & state](#chapter-3-memory--state) · [4. Planning & reasoning patterns](#chapter-4-planning--reasoning-patterns) · [5. Agentic RAG](#chapter-5-agentic-rag) · [6. Model Context Protocol (MCP)](#chapter-6-model-context-protocol-mcp) · [7. LangGraph](#chapter-7-langgraph) · [8. Other agent frameworks](#chapter-8-other-agent-frameworks) · [9. Multi-agent systems](#chapter-9-multi-agent-systems) · [10. Guardrails, safety & evaluation](#chapter-10-guardrails-safety--evaluation) · [11. Deployment & observability](#chapter-11-deployment--observability) · [12. Voice AI: STT, TTS & voice agents](#chapter-12-voice-ai-stt-tts--voice-agents) · [13. Capstone: Chat & Voice Agent](#chapter-13-capstone-chat--voice-agent)

### Chapter 1: The agent loop

🟢 Core · [📄 Read the notes](01_agent_loop/README.md)

- **1.1** LLM call vs. workflow vs. agent
- **1.2** The think → act → observe loop
- **1.3** When to use an agent
- **1.4** Step limits & stopping

**🔑 Key terms:** agent, workflow, autonomy, loop, step limit  
**🎯 You'll learn:** What makes something an 'agent' and how the core loop works  
**🛠️ You can build:** A minimal agent from scratch in ~10 lines of Python

### Chapter 2: Tool use / function calling

🟢 Core · [📄 Read the notes](02_tool_use/README.md)

- **2.1** How tool calling works
- **2.2** Describing tools with JSON schema
- **2.3** Designing good tools
- **2.4** Returning errors
- **2.5** Confirming risky actions

**🔑 Key terms:** tool, function calling, JSON schema, tool_use, tool_result  
**🎯 You'll learn:** Let an LLM act on the world through your code  
**🛠️ You can build:** An assistant with calculator, web-search and database tools

### Chapter 3: Memory & state

🟢 Core · [📄 Read the notes](03_memory/README.md)

- **3.1** LLMs are stateless
- **3.2** Short-term (conversation) memory
- **3.3** Working state
- **3.4** Long-term & episodic memory
- **3.5** Sliding window, summaries, retrieval

**🔑 Key terms:** context window, message history, summary memory, semantic memory, episodic memory  
**🎯 You'll learn:** Make an agent remember within and across conversations  
**🛠️ You can build:** A chatbot that remembers your preferences next session

### Chapter 4: Planning & reasoning patterns

🟢 Core · [📄 Read the notes](04_reasoning_patterns/README.md)

- **4.1** Chain-of-thought
- **4.2** ReAct
- **4.3** Plan-and-execute
- **4.4** Reflection
- **4.5** Routing

**🔑 Key terms:** thought, action, observation, planner, executor, critique, router  
**🎯 You'll learn:** Patterns that help agents solve multi-step tasks  
**🛠️ You can build:** A hand-written ReAct agent and a request router

### Chapter 5: Agentic RAG

🟢 Core · [📄 Read the notes](05_agentic_rag/README.md)

- **5.1** Plain RAG vs. agentic RAG
- **5.2** What the agent decides
- **5.3** Patterns: Self-RAG, Corrective RAG, Adaptive RAG
- **5.4** Trade-offs

**🔑 Key terms:** routing, query rewriting, multi-hop, self-grading, Self-RAG, CRAG  
**🎯 You'll learn:** Let the agent decide when, where and how to retrieve  
**🛠️ You can build:** A Corrective RAG agent that retries when results are poor

### Chapter 6: Model Context Protocol (MCP)

⚪ Later · [📄 Read the notes](06_mcp/README.md)

- **6.1** Host, client & server
- **6.2** Tools, resources & prompts
- **6.3** Transports: stdio & HTTP
- **6.4** MCP vs. plain function calling

**🔑 Key terms:** MCP, host, client, server, resource, transport  
**🎯 You'll learn:** A standard way to plug tools and data into any agent  
**🛠️ You can build:** Your own MCP server, used from Claude and from your agent

### Chapter 7: LangGraph

🟢 Core · [📄 Read the notes](07_langgraph/README.md)

- **7.1** State, nodes & edges
- **7.2** Conditional edges (routing & loops)
- **7.3** Checkpointers (memory)
- **7.4** Interrupts (human-in-the-loop)
- **7.5** Streaming
- **7.6** Common patterns

**🔑 Key terms:** state, node, edge, conditional edge, checkpointer, thread, interrupt  
**🎯 You'll learn:** Build agents as graphs you can control and debug  
**🛠️ You can build:** A router agent with memory and human approval

### Chapter 8: Other agent frameworks

⚪ Later · [📄 Read the notes](08_agent_frameworks/README.md)

- **8.1** Claude Agent SDK
- **8.2** CrewAI
- **8.3** AutoGen
- **8.4** OpenAI Agents SDK
- **8.5** Choosing a framework

**🔑 Key terms:** agent harness, crew, role, handoff  
**🎯 You'll learn:** How different frameworks package the same ideas  
**🛠️ You can build:** The same agent built in two frameworks

### Chapter 9: Multi-agent systems

⚪ Later · [📄 Read the notes](09_multi_agent/README.md)

- **9.1** Supervisor / orchestrator–worker
- **9.2** Handoffs
- **9.3** Debate & review
- **9.4** When one agent is enough

**🔑 Key terms:** orchestrator, worker, supervisor, handoff  
**🎯 You'll learn:** Split work across specialised agents  
**🛠️ You can build:** A research team: supervisor + researcher + writer

### Chapter 10: Guardrails, safety & evaluation

⚪ Later · [📄 Read the notes](10_guardrails_evals/README.md)

- **10.1** Input & output guardrails
- **10.2** Prompt injection
- **10.3** Tool approval
- **10.4** Tracing
- **10.5** Evals & LLM-as-judge

**🔑 Key terms:** guardrail, prompt injection, trace, span, eval set, LLM-as-judge  
**🎯 You'll learn:** Know your agent works, and keep it safe  
**🛠️ You can build:** An eval suite and injection tests for your agent

### Chapter 11: Deployment & observability

⚪ Later · [📄 Read the notes](11_deployment/README.md)

- **11.1** Serving with FastAPI
- **11.2** Streaming responses
- **11.3** Docker
- **11.4** Logging latency & cost

**🔑 Key terms:** endpoint, streaming (SSE), container, environment variable, latency  
**🎯 You'll learn:** Put an agent behind an API that a UI can use  
**🛠️ You can build:** An agent API with a chat UI, running in Docker

### Chapter 12: Voice AI: STT, TTS & voice agents

🟢 Core · [📄 Read the notes](12_voice_ai/README.md)

- **12.1** The voice pipeline
- **12.2** VAD & turn detection
- **12.3** Speech-to-text (STT)
- **12.4** Text-to-speech (TTS)
- **12.5** Barge-in & latency
- **12.6** Writing for the ear

**🔑 Key terms:** VAD, STT / ASR, TTS, WebRTC, endpointing, barge-in, latency  
**🎯 You'll learn:** Turn a text agent into one you can talk to  
**🛠️ You can build:** A real-time voice agent connected to your chat agent

### Chapter 13: Capstone: Chat & Voice Agent

🟢 Core · [📄 Read the notes](../projects/conversational_agent_design.md)

- **13.1** Text chatbot
- **13.2** Knowledge (RAG)
- **13.3** Tools & memory
- **13.4** LangGraph orchestration
- **13.5** Voice

**🎯 You'll learn:** Put every chapter together, phase by phase  
**🛠️ You can build:** An assistant you can chat with and talk to

Legend: 🟢 Core = study now · ⚪ Later = after the core ([Core Path](../README.md#core-path))

## Learning Path

```
Core:   1 Agent loop → 2 Tools → 3 Memory → 4 Reasoning → 5 Agentic RAG → 7 LangGraph → 12 Voice → 🎯 Capstone
Later:  6 MCP · 8 Frameworks · 9 Multi-agent · 10 Guardrails & evals · 11 Deployment
```

## How to Study Each Topic

1. **Read** the topic's README: concept first, then diagrams and examples.
2. **Practice** its Hands-On exercises in the same folder (`1.1_basic_loop.ipynb`, …). Start without a framework when you can.
3. **Write notes** in `notes.md` in the topic folder: what clicked, what didn't, questions.
4. **Tick** the topic in the [Progress Tracker](../README.md#progress-tracker).

```
4_agentic_ai/
├── README.md               # book index (this file)
├── 01_agent_loop/
│   ├── README.md           # concept notes + exercises
│   ├── notes.md            # your notes
│   └── 1.1_basic_loop.ipynb
├── 02_tool_use/
└── ...
```
