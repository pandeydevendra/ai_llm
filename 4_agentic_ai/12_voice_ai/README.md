# 12. Voice AI: STT, TTS & Voice Agents

[← 11. Deployment & observability](../11_deployment/README.md) · [↑ Agentic AI contents](../README.md) · [Capstone project →](../../projects/conversational_agent_design.md)

Turning a text agent into one you can **talk to**: listen (speech-to-text), think (the same agent as chat), speak (text-to-speech) — fast enough to feel like a real conversation.

**Prerequisites:** an agent with tools & memory (4.1–4.3), LangGraph (4.7), streaming (`3_gen_ai/` 5).

**In this section:** [Voice pipeline](#voice-pipeline) · [Building blocks](#voice-building-blocks) · [Making voice feel natural](#making-voice-feel-natural) · [Hands-On: Voice AI](#hands-on-voice-ai)

## Voice pipeline

```
Mic → VAD → streaming STT → Agent (same as chat) → sentence splitter → streaming TTS → Speaker
        ▲                                                                     │
        └──────────── user speaks again → stop audio (barge-in) ◄─────────────┘
```

Two approaches, compared in the [design doc](../../projects/conversational_agent_design.md#3-voice-pipeline-options): **cascaded** (STT → LLM → TTS) and **speech-to-speech** realtime models.

## Voice building blocks

| Block | Job | Tools |
|---|---|---|
| **VAD** | Detect speech vs. silence | Silero VAD, WebRTC VAD |
| **STT (ASR)** | Speech → text, streaming | Deepgram, AssemblyAI, Whisper / faster-whisper |
| **Turn detection** | Decide when the user has finished speaking | LiveKit turn detector, silence thresholds |
| **TTS** | Text → natural speech, streaming | Cartesia, ElevenLabs, OpenAI TTS, Piper (local) |
| **Transport** | Real-time audio to and from the browser or phone | WebRTC (LiveKit), WebSocket, Twilio |
| **Voice framework** | Wires everything together | LiveKit Agents, Pipecat |

## Making voice feel natural

- **Latency:** first audio within about 1 s of the user stopping. Stream every step.
- **Barge-in:** stop speaking immediately when the user interrupts.
- **Write for the ear:** short sentences, no markdown or lists, spell out numbers and dates.
- **Fillers:** "Let me check that…" while a tool runs.
- **Confirm key details:** read back names, dates and amounts.

## Hands-On: Voice AI

| # | Exercise | Tools |
|---|---|---|
| 12.1 | Transcribe audio files, then live mic audio | faster-whisper, Deepgram |
| 12.2 | Generate speech and compare voices and latency | Piper, Cartesia / ElevenLabs |
| 12.3 | Push-to-talk voice bot: record → STT → LLM → TTS | Python, LLM API |
| 12.4 | Real-time voice agent in the browser | LiveKit Agents or Pipecat |
| 12.5 | Add barge-in and turn detection | LiveKit / Pipecat |
| 12.6 | Connect the voice pipeline to your LangGraph chat agent | LangGraph |
| 12.7 | Measure time to first audio and tune it | Tracing, timers |

---

[← 11. Deployment & observability](../11_deployment/README.md) · [↑ Agentic AI contents](../README.md) · [Capstone project →](../../projects/conversational_agent_design.md)
