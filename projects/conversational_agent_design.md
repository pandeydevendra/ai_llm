# Conversational Agentic System — Chat & Voice

[← Back to Agentic AI](../4_agentic_ai/README.md) · [← Back to main README](../README.md)

**Goal:** one agentic assistant that users can talk to by **text chat** or **voice**, with the same brain, tools, memory and knowledge behind both.

> **Learning capstone.** This is the target to build toward while learning, not a spec to build all at once. Follow the [Build Phases](#14-build-phases) one at a time. Sections 9–12 (latency budget, guardrails, evaluation, full tech stack) describe production concerns and are ⚪ Later material: read them, but don't let them block the core build.

## Table of Contents

1. [Requirements](#1-requirements)
2. [High-Level Architecture](#2-high-level-architecture)
3. [Voice Pipeline Options](#3-voice-pipeline-options)
4. [Request Flow (One Turn)](#4-request-flow-one-turn)
5. [Agent Orchestration](#5-agent-orchestration)
6. [Memory Design](#6-memory-design)
7. [Knowledge & Tools](#7-knowledge--tools)
8. [Voice-Specific Concerns](#8-voice-specific-concerns)
9. [Latency Budget](#9-latency-budget)
10. [Guardrails & Safety](#10-guardrails--safety)
11. [Evaluation & Observability](#11-evaluation--observability)
12. [Tech Stack](#12-tech-stack)
13. [Project Structure](#13-project-structure)
14. [Build Phases](#14-build-phases)

---

## 1. Requirements

### Functional

| # | Requirement |
|---|---|
| F1 | Text chat with streaming responses (web UI) |
| F2 | Real-time voice conversation (browser mic, optionally phone) |
| F3 | Switch between chat and voice in the same session without losing context |
| F4 | Answer from a private knowledge base (Agentic RAG) |
| F5 | Take actions through tools (search, calendar, tickets, APIs) |
| F6 | Remember the user across sessions (preferences, past issues) |
| F7 | Hand off to a human when stuck or when the user asks |

### Non-functional

| # | Requirement | Target |
|---|---|---|
| N1 | Voice response latency (user stops speaking → first audio) | < 1 s |
| N2 | Chat time to first token | < 1 s |
| N3 | Barge-in: the user can interrupt the agent mid-sentence | Agent stops within ~200 ms |
| N4 | Safety: no harmful output, no leaking private data | Guardrails on input and output |
| N5 | Observability: every turn traced end to end | 100% of turns |
| N6 | Cost per conversation is tracked | Per-turn token & audio cost |

---

## 2. High-Level Architecture

```
 ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
 │  Web Chat UI │   │ Browser Voice│   │ Phone (SIP)  │
 └──────┬───────┘   └──────┬───────┘   └──────┬───────┘
        │ WebSocket        │ WebRTC           │ Twilio / SIP
 ┌──────▼──────────────────▼──────────────────▼───────┐
 │                 Gateway / Session Manager           │
 │  auth · session id · channel (chat | voice) · rate  │
 └──────┬──────────────────────────────────┬───────────┘
        │ text                             │ audio
        │                     ┌────────────▼─────────────┐
        │                     │      Voice Pipeline      │
        │                     │ VAD → STT ──┐   ┌── TTS  │
        │                     └─────────────┼───┼────────┘
        │                          text in  │   ▲ text out
 ┌──────▼───────────────────────────────────▼───┴──────┐
 │              Agent Orchestrator (LangGraph)          │
 │  input guardrail → router → specialist agent →       │
 │  output guardrail → channel formatter (chat | voice) │
 └───┬──────────────┬──────────────┬───────────────┬────┘
     │              │              │               │
 ┌───▼────┐   ┌─────▼─────┐  ┌─────▼──────┐  ┌─────▼──────┐
 │ Memory │   │ Knowledge │  │ Tools (MCP)│  │ Human      │
 │ Redis  │   │ Vector DB │  │ APIs, DBs  │  │ handoff    │
 │ Mem0 / │   │ (RAG)     │  │ search ... │  │ queue      │
 │ Postgres   └───────────┘  └────────────┘  └────────────┘
 └────────┘
        └──────── Tracing · Evals · Cost (Langfuse / OTel) ────────┘
```

**Key idea:** chat and voice are just two **channels**. Both turn into text and enter the same orchestrator. Only the edges differ: voice adds STT before and TTS after, and its replies are formatted for speech.

---

## 3. Voice Pipeline Options

| | **Cascaded** (STT → LLM → TTS) | **Speech-to-speech** (realtime model) |
|---|---|---|
| How it works | Three separate models, streamed together | One model hears audio and speaks audio |
| Latency | ~0.8–1.5 s, with careful streaming | ~0.3–0.8 s |
| Control | Full: any LLM, any voice, inspect every transcript | Less: tied to one provider's model and voices |
| Tools, RAG, guardrails | Easy: the same text agent as chat | Possible, but harder to share with chat |
| Emotion & tone | Lost in transcription | Preserved |
| Cost | Usually lower, components can be swapped | Usually higher |
| Debugging | Easy: every step produces text | Harder |

**Recommendation:** start **cascaded**. It reuses the chat agent unchanged, which is the whole point of one brain for both channels. Try a speech-to-speech model later as an experiment and compare them.

---

## 4. Request Flow (One Turn)

### Chat turn

```
User types → Gateway → load session + memory → input guardrail
  → router → specialist agent (may call RAG / tools in a loop)
  → output guardrail → stream tokens to UI → save turn to memory
```

### Voice turn (cascaded)

```
Mic audio (streaming)
  → VAD detects speech start / end
  → streaming STT produces partial, then final transcript
  → same orchestrator as chat (channel = voice)
  → LLM streams text → split into sentences
  → each sentence → streaming TTS → audio plays immediately
  → if user starts talking: stop TTS, cancel LLM, listen (barge-in)
```

Streaming at every step is what keeps voice fast: TTS starts speaking the first sentence while the LLM is still writing the second.

---

## 5. Agent Orchestration

A LangGraph state graph with a small, fast **router** in front of specialist agents.

```
            ┌──────────────────┐
  input ──► │ Input guardrail  │──blocked──► safe refusal
            └────────┬─────────┘
                     ▼
            ┌──────────────────┐
            │ Router (fast LLM)│
            └─┬──────┬──────┬──┘
     smalltalk│  knowledge  │ action        ┌───────────────┐
              ▼      ▼      ▼               │ Escalate to   │
         ┌──────┐┌──────┐┌────────┐ stuck ─►│ human         │
         │ Chat ││ RAG  ││ Task   │────────►└───────────────┘
         │ agent││ agent││ agent  │
         └──┬───┘└──┬───┘└───┬────┘
            └───────┼────────┘
                    ▼
            ┌──────────────────┐
            │ Output guardrail │
            └────────┬─────────┘
                    ▼
            ┌──────────────────┐
            │ Channel formatter│  chat: markdown · voice: short spoken sentences
            └──────────────────┘
```

| Agent | Job | Uses |
|---|---|---|
| **Router** | Classifies intent in one quick call | Small fast model (e.g. Claude Haiku) |
| **Chat agent** | Small talk, clarifying questions | Main model, conversation memory |
| **RAG agent** | Answers from the knowledge base | Agentic RAG: rewrite → retrieve → grade → answer |
| **Task agent** | Does things: book, look up, create ticket | Tools over MCP, confirms before acting |
| **Escalation** | Hands off with a summary of the conversation | Ticket / live-agent queue |

**State shared across the graph:** `session_id`, `user_id`, `channel`, `messages`, `user_profile`, `retrieved_docs`, `tool_results`, `turn_count`, `escalate`.

---

## 6. Memory Design

| Layer | What it holds | Storage | Lifetime |
|---|---|---|---|
| **Working memory** | Current conversation turns | LangGraph state + Redis | Session |
| **Summary memory** | Rolling summary once the conversation gets long | Redis | Session |
| **Long-term memory** | Facts & preferences ("prefers Hindi", "has order #123") | Mem0 / vector DB | Across sessions |
| **User profile** | Name, account, language, channel preference | Postgres | Permanent |

**Rules:**
- Load the profile and relevant long-term memories at session start.
- Summarize older turns instead of sending the full history every time.
- Save new facts asynchronously after the turn, so memory never slows down the reply.

---

## 7. Knowledge & Tools

### Knowledge (Agentic RAG)

- **Ingestion:** documents → chunk → embed → vector DB, with metadata (source, date, access level).
- **Retrieval:** hybrid search (vector + keyword) → rerank → the agent grades relevance and retries if needed.
- **Grounding:** answers cite their sources in chat. In voice they say "according to the refund policy…".

### Tools (via MCP)

| Tool | Example |
|---|---|
| Web search | Current information |
| Calendar | Check availability, book a slot |
| CRM / orders | Look up an order or account |
| Ticketing | Create or update a support ticket |
| Human handoff | Transfer with a summary |

**Rule:** any tool that changes something (booking, payment, cancellation) asks the user to confirm first. In voice: "Should I book Tuesday at 3 pm?"

---

## 8. Voice-Specific Concerns

| Concern | What to do |
|---|---|
| **Voice activity detection (VAD)** | Detect speech vs. silence (Silero VAD) |
| **Endpointing / turn-taking** | Decide when the user has *finished*: silence timeout plus a turn-detection model, so the agent doesn't cut people off mid-thought |
| **Barge-in** | When the user speaks, stop audio immediately and cancel the in-flight LLM and TTS |
| **Write for the ear** | Short sentences, no markdown, lists, URLs or tables; spell out numbers, dates and units |
| **Filler & acknowledgements** | "Let me check that…" while a slow tool runs |
| **Confirmation** | Read back key details: names, dates, amounts |
| **Noise & accents** | Noise suppression, STT with good accent and language support |
| **Multilingual** | Detect language in STT, reply in the same language, pick a matching TTS voice |
| **Echo** | Echo cancellation so the agent doesn't hear itself |

---

## 9. Latency Budget

Target for voice: **user stops speaking → first audio in < 1 s**.

| Step | Budget |
|---|---|
| Endpointing (deciding the user is done) | 200–300 ms |
| Final STT transcript | 100–200 ms |
| Router + LLM time to first token | 300–500 ms |
| TTS time to first audio | 100–200 ms |
| Network | 50–100 ms |
| **Total** | **~0.75–1.3 s** |

**Ways to cut latency:**
- Stream everything: STT partials, LLM tokens, TTS by sentence.
- Use a small fast model for routing. Skip the router for obvious small talk.
- Keep connections to STT, LLM and TTS warm, and host them in the same region.
- Use prompt caching for the long system prompt.
- Say a filler line before slow tools or retrieval.

---

## 10. Guardrails & Safety

| Layer | Checks |
|---|---|
| **Input** | Prompt injection, abuse, off-topic, PII detection |
| **Tool calls** | Allow-list of tools per agent, argument validation, confirm before changes |
| **Retrieval** | Only documents the user is allowed to see |
| **Output** | Harmful content, leaked PII or secrets, answers not grounded in sources |
| **Voice** | Never read out sensitive data (full card numbers, passwords) |
| **Escalation** | Hand off to a human after repeated failures, or when the user is upset or asks for one |

---

## 11. Evaluation & Observability

### Metrics

| Area | Metric |
|---|---|
| Quality | Task success rate, answer correctness, groundedness (RAGAS) |
| Conversation | Turns to resolution, escalation rate, user rating |
| Voice | STT word error rate (WER), time to first audio, interruption handling |
| Performance | Time to first token, p50/p95 latency per step |
| Cost | Tokens, STT minutes and TTS characters per conversation |

### How

- **Tracing:** every turn as one trace (STT → router → agent → tools → TTS) in Langfuse or LangSmith, with OpenTelemetry.
- **Offline evals:** a fixed test set of chat and voice conversations, re-run on every change.
- **LLM-as-judge:** score helpfulness, tone and groundedness.
- **Simulated users:** an LLM plays the customer, to test multi-turn flows.

---

## 12. Tech Stack

| Layer | Options (recommended first) |
|---|---|
| Chat UI | Next.js / React, or Streamlit / Gradio to prototype |
| Transport | WebSocket (chat), WebRTC via LiveKit (voice), Twilio (phone) |
| Voice framework | LiveKit Agents, Pipecat |
| VAD / turn detection | Silero VAD, LiveKit turn detector |
| STT | Deepgram, AssemblyAI, faster-whisper (local) |
| LLM | Claude Sonnet (main), Claude Haiku (router); Ollama for local experiments |
| TTS | Cartesia, ElevenLabs, OpenAI TTS, Piper (local) |
| Orchestration | LangGraph |
| Tools | MCP servers |
| Memory | Redis, Mem0, Postgres |
| Knowledge | pgvector / Qdrant + reranker |
| Guardrails | Guardrails AI, custom classifiers |
| Observability | Langfuse, OpenTelemetry |
| Backend & deploy | FastAPI, Docker, Docker Compose → cloud |

---

## 13. Project Structure

```
conversational_agent/
├── app/
│   ├── gateway/          # FastAPI: WebSocket chat, session management, auth
│   ├── voice/            # LiveKit / Pipecat pipeline: VAD, STT, TTS, barge-in
│   ├── agent/
│   │   ├── graph.py      # LangGraph orchestrator
│   │   ├── router.py
│   │   ├── agents/       # chat, rag, task, escalation
│   │   ├── prompts/      # system prompts, chat vs voice style
│   │   └── formatter.py  # channel-specific output
│   ├── memory/           # Redis session, Mem0 long-term, profile
│   ├── knowledge/        # ingestion, retrieval, reranking
│   ├── tools/            # MCP servers & clients
│   └── guardrails/
├── ui/                   # chat + voice web client
├── evals/                # test conversations, judges, voice WER tests
├── docker-compose.yml
└── README.md
```

---

## 14. Build Phases

Each phase works on its own and builds on the last.

| Phase | Build | Uses topics |
|---|---|---|
| **1. Text chatbot** | Streaming chat with an LLM API and a system prompt | `3_gen_ai` 4–5 |
| **2. Knowledge** | Embeddings + vector DB + RAG (LangChain or LlamaIndex), then upgrade to agentic RAG | `3_gen_ai` 2, 6–9 · `4_agentic_ai` 5 |
| **3. Tools** | Tool calling, then move tools to MCP servers | `4_agentic_ai` 2, 6 |
| **4. Memory** | Session memory, summaries, long-term memory | `4_agentic_ai` 3 |
| **5. Orchestration** | LangGraph router + specialist agents + human handoff | `4_agentic_ai` 4, 7, 9 |
| **6. Voice** | Cascaded voice pipeline that reuses the same agent | `4_agentic_ai` 12 |
| **7. Voice polish** | Barge-in, turn detection, filler lines, latency tuning | `4_agentic_ai` 12 |
| **8. Safety & evals** | Guardrails, tracing, eval suite, simulated users | `4_agentic_ai` 10 |
| **9. Deploy** | Docker Compose, cloud deploy, dashboards | `4_agentic_ai` 11 |
| **10. Stretch** | Phone calls (Twilio), multilingual, speech-to-speech comparison | — |
