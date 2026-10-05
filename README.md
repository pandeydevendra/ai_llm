# AI / LLM — Hands-On Learning

A personal repo for **learning and practice**: a hands-on path from classical Machine Learning to Deep Learning, Generative AI, and Agentic AI. Each track has concept notes, practice exercises and small projects.

## Goal

Build an **agentic conversational assistant you can talk to by chat and voice**: one agent with knowledge (RAG), tools, memory and guardrails, reachable through a text chat UI and a real-time voice interface.

➡️ **[System design: Chat & Voice Conversational Agent](projects/conversational_agent_design.md)**

## Table of Contents

- [Goal](#goal)
- [Repository Structure](#repository-structure)
- [Learning Roadmap](#learning-roadmap)
- [Core Path](#core-path)
- [How to Practice](#how-to-practice)
- [1. Machine Learning (`1_ml/`)](#1-machine-learning-1_ml)
- [2. Deep Learning (`2_dl/`)](#2-deep-learning-2_dl)
- [3. Generative AI (`3_gen_ai/`)](#3-generative-ai-3_gen_ai)
- [4. Agentic AI (`4_agentic_ai/`)](#4-agentic-ai-4_agentic_ai)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Progress Tracker](#progress-tracker)
- [Resources](#resources)

---

## Repository Structure

```
ai_llm/
├── 1_ml/           # Classical machine learning
├── 2_dl/           # Deep learning & neural networks
├── 3_gen_ai/       # LLMs, embeddings, vector DBs, LangChain, LlamaIndex, RAG
├── 4_agentic_ai/   # Agentic AI, LangGraph, voice agents, deployment
│   ├── 01_agent_loop/ … 12_voice_ai/   # one folder per chapter: notes + exercises
├── projects/      # Practice projects that combine the tracks
│   └── conversational_agent_design.md   # Capstone: chat & voice agent
└── README.md
```

## Learning Roadmap

```
ML fundamentals ──► Deep Learning ──► Generative AI ──► Agentic AI ──► Chat & Voice Agent
```

## Core Path

Study the 🟢 **Core** topics first: they are the minimum needed to build the chat & voice agent. Come back to the ⚪ **Later** topics once the core works.

| Track | Core topics |
|---|---|
| **1. ML** | 1.1 Python for ML · 1.2 Preprocessing · 1.3 Linear & Logistic Regression · 1.4 Trees & Random Forests · 1.8 Evaluation |
| **2. DL** | 2.1 Neural networks & backprop · 2.2 PyTorch / TensorFlow · 2.3 Optimization · 2.4 CNNs · 2.7 RNNs · 2.8 Transformers |
| **3. Gen AI** | 3.1 Tokenization · 3.2 Embeddings · 3.3 LLMs · 3.4 Prompting · 3.5 LLM APIs · 3.6 Vector DBs · 3.7 LangChain · 3.9 RAG · 3.11 Evaluation · 3.13 Project |
| **4. Agentic AI** | 4.1 Agent loop · 4.2 Tool use · 4.3 Memory · 4.4 Reasoning patterns · 4.5 Agentic RAG · 4.7 LangGraph · 4.12 Voice AI · 4.13 Capstone |

Legend: 🟢 Core = study now · ⚪ Later = advanced or optional, after the core

## How to Practice

For each topic:

1. **Learn:** read the concept notes in the track's README (what it is, why it matters).
2. **Practice:** do the topic's **Hands-On** exercises in a notebook or script, starting from scratch before reaching for a library.
3. **Note:** write down what you learned and what confused you, in the topic's folder.
4. **Tick:** update the [Progress Tracker](#progress-tracker).

Suggested layout inside each track:

```
4_agentic_ai/
├── README.md              # concept notes + exercise list
├── 01_agent_loop/
│   ├── notes.md           # your own notes
│   └── 1.1_basic_loop.ipynb
├── 02_tool_use/
└── ...
```

---

## 1. Machine Learning (`1_ml/`)

[Go to 1_ml/](1_ml/)

| # | Level | Topic | Hands-On | Tools |
|---|-------|-------|----------|-------|
| 1.1 | 🟢 Core | Python for ML: NumPy, Pandas, Matplotlib | Exploratory data analysis (EDA) on a real dataset | NumPy, Pandas, Matplotlib, Seaborn |
| 1.2 | 🟢 Core | Data preprocessing & feature engineering | Cleaning, encoding, scaling pipeline | Pandas, scikit-learn |
| 1.3 | 🟢 Core | Linear & Logistic Regression | Implement from scratch + scikit-learn | NumPy, scikit-learn |
| 1.4 | 🟢 Core | Decision Trees, Random Forests | Classification on tabular data | scikit-learn |
| 1.5 | ⚪ Later | Gradient Boosting (XGBoost, LightGBM) | Kaggle-style competition | XGBoost, LightGBM, CatBoost |
| 1.6 | ⚪ Later | SVM, KNN, Naive Bayes | Model comparison notebook | scikit-learn |
| 1.7 | ⚪ Later | Unsupervised: K-Means, DBSCAN, PCA | Customer segmentation | scikit-learn |
| 1.8 | 🟢 Core | Model evaluation & cross-validation | Metrics, bias/variance, tuning | scikit-learn, Optuna |
| 1.9 | ⚪ Later | **Project** | End-to-end ML pipeline | scikit-learn, MLflow, FastAPI |

## 2. Deep Learning (`2_dl/`)

[Go to 2_dl/](2_dl/)

| # | Level | Topic | Hands-On | Tools |
|---|-------|-------|----------|-------|
| 2.1 | 🟢 Core | Neural network basics, backpropagation | MLP from scratch in NumPy | NumPy |
| 2.2 | 🟢 Core | Framework fundamentals | Tensors, autograd, training loop | PyTorch, TensorFlow / Keras |
| 2.3 | 🟢 Core | Optimization & regularization | SGD/Adam, dropout, batch norm | PyTorch, TensorFlow / Keras |
| 2.4 | 🟢 Core | [CNNs](2_dl/README.md#4-cnns-convolutional-neural-networks) | Image classification (CIFAR-10) | PyTorch, torchvision, Keras |
| 2.5 | ⚪ Later | Transfer learning | Fine-tune ResNet / ViT | torchvision, timm, Keras Applications |
| 2.6 | ⚪ Later | [Computer Vision](2_dl/README.md#6-computer-vision) | Object detection, segmentation, OCR | OpenCV, Ultralytics YOLO, SAM, CLIP |
| 2.7 | 🟢 Core | [RNNs, LSTMs, GRUs](2_dl/README.md#7-rnns-lstms-grus) | Sequence modeling / time series | PyTorch, TensorFlow / Keras |
| 2.8 | 🟢 Core | [Attention & Transformers](2_dl/README.md#8-attention--transformers) | Attention from scratch, build a Transformer block | NumPy, PyTorch, Hugging Face |
| 2.9 | ⚪ Later | **Project** | Train & deploy a vision or NLP model | PyTorch Lightning, ONNX, TensorBoard / W&B |

## 3. Generative AI (`3_gen_ai/`)

[Go to 3_gen_ai/](3_gen_ai/)

| # | Level | Topic | Hands-On | Tools |
|---|-------|-------|----------|-------|
| 3.1 | 🟢 Core | Tokenization | BPE tokenizer from scratch | tiktoken, HF Tokenizers |
| 3.2 | 🟢 Core | [Embeddings](3_gen_ai/README.md#2-embeddings) | Semantic search, compare models & chunking | Sentence-Transformers, OpenAI / Voyage embeddings |
| 3.3 | 🟢 Core | [Large Language Models (LLMs)](3_gen_ai/README.md#3-large-language-models-llms) | Next-token probabilities, sampling, build a tiny GPT | PyTorch, Hugging Face, Ollama |
| 3.4 | 🟢 Core | Prompt engineering | Zero/few-shot, chain-of-thought, structured output | LLM APIs, Pydantic |
| 3.5 | 🟢 Core | Working with LLM APIs | Chat, streaming, tool calling | Anthropic SDK, OpenAI SDK, Ollama |
| 3.6 | 🟢 Core | [Vector databases](3_gen_ai/README.md#6-vector-databases) | Store & query embeddings, hybrid search, reranking | Chroma, FAISS, pgvector, Qdrant |
| 3.7 | 🟢 Core | [LangChain](3_gen_ai/README.md#7-langchain) | Chains, structured output, RAG with LCEL | LangChain, LangSmith |
| 3.8 | ⚪ Later | [LlamaIndex](3_gen_ai/README.md#8-llamaindex) | RAG over documents, query & chat engines | LlamaIndex, LlamaParse |
| 3.9 | 🟢 Core | Retrieval-Augmented Generation (RAG) | Chat-with-your-docs app | LangChain / LlamaIndex, vector DB |
| 3.10 | ⚪ Later | Fine-tuning (LoRA / QLoRA) | Fine-tune an open model | HF Transformers, PEFT, TRL, bitsandbytes |
| 3.11 | 🟢 Core | Evaluation of LLM outputs | LLM-as-judge, eval datasets | RAGAS, DeepEval, promptfoo |
| 3.12 | ⚪ Later | Diffusion & multimodal models | Image generation basics | HF Diffusers |
| 3.13 | 🟢 Core | **Project** | Chat assistant with RAG (phases 1–2 of the capstone) | FastAPI, Streamlit / Gradio |

## 4. Agentic AI (`4_agentic_ai/`)

[Go to 4_agentic_ai/](4_agentic_ai/)

| # | Level | Topic | Hands-On | Tools |
|---|-------|-------|----------|-------|
| 4.1 | 🟢 Core | [What is an agent? Agent loop](4_agentic_ai/01_agent_loop/README.md) | Minimal agent from scratch | Python, LLM API |
| 4.2 | 🟢 Core | [Tool use / function calling](4_agentic_ai/02_tool_use/README.md) | Agent with search, calculator, code tools | Anthropic SDK, OpenAI SDK |
| 4.3 | 🟢 Core | [Memory & state](4_agentic_ai/03_memory/README.md) | Short-term & long-term memory | Vector DB, Redis, Mem0 |
| 4.4 | 🟢 Core | [Planning & reasoning patterns](4_agentic_ai/04_reasoning_patterns/README.md) | ReAct, plan-and-execute, reflection | LangGraph |
| 4.5 | 🟢 Core | [Agentic RAG](4_agentic_ai/05_agentic_rag/README.md) | Corrective RAG, routing, multi-hop retrieval | LangGraph, LlamaIndex, vector DB |
| 4.6 | ⚪ Later | [Model Context Protocol (MCP)](4_agentic_ai/06_mcp/README.md) | Build an MCP server | MCP Python SDK |
| 4.7 | 🟢 Core | [LangGraph](4_agentic_ai/07_langgraph/README.md) | State graphs, memory, human-in-the-loop, supervisor | LangGraph, LangSmith |
| 4.8 | ⚪ Later | [Other agent frameworks](4_agentic_ai/08_agent_frameworks/README.md) | Same agent in several frameworks | Claude Agent SDK, CrewAI, AutoGen |
| 4.9 | ⚪ Later | [Multi-agent systems](4_agentic_ai/09_multi_agent/README.md) | Orchestrator + worker agents | LangGraph, CrewAI |
| 4.10 | ⚪ Later | [Guardrails, safety & evaluation](4_agentic_ai/10_guardrails_evals/README.md) | Tracing, evals, human-in-the-loop | LangSmith, Langfuse, Guardrails AI |
| 4.11 | ⚪ Later | [Deployment & observability](4_agentic_ai/11_deployment/README.md) | API service, Docker, monitoring | FastAPI, Docker, OpenTelemetry |
| 4.12 | 🟢 Core | [Voice AI: STT, TTS & voice agents](4_agentic_ai/12_voice_ai/README.md) | Real-time voice agent with barge-in | Deepgram / Whisper, Cartesia / ElevenLabs, LiveKit / Pipecat |
| 4.13 | 🟢 Core | **Capstone** | [Chat & Voice Conversational Agent](projects/conversational_agent_design.md) | LangGraph, MCP, LiveKit, FastAPI, Docker |

---

## Tech Stack

| Area | Tools |
|------|-------|
| Language | Python 3.11+ |
| Data / ML | NumPy, Pandas, scikit-learn, XGBoost |
| Deep Learning | PyTorch, TensorFlow / Keras, Hugging Face Transformers |
| Computer Vision | OpenCV, torchvision, Ultralytics YOLO, Albumentations |
| Gen AI | LLM APIs, embeddings, LangChain, LlamaIndex |
| Vector DBs | Chroma, FAISS, pgvector, Qdrant |
| Agentic | LangGraph, Claude Agent SDK, MCP |
| Voice | Whisper / Deepgram (STT), Cartesia / ElevenLabs / Piper (TTS), LiveKit / Pipecat |
| Tooling | Jupyter, uv / pip, Git, Docker |

## Getting Started

```bash
git clone <repo-url>
cd ai_llm

python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS / Linux
source .venv/bin/activate

pip install -r requirements.txt   # add as tracks progress
```

## Progress Tracker

| Track | Status |
|-------|--------|
| Machine Learning | ⬜ Not started |
| Deep Learning | ⬜ Not started |
| Generative AI | ⬜ Not started |
| Agentic AI | ⬜ Not started |
| Capstone: Chat & Voice Agent | ⬜ Not started |

Legend: ⬜ Not started · 🟨 In progress · ✅ Done

## Resources

- **ML:** *Hands-On Machine Learning* (Aurélien Géron), Andrew Ng's ML Specialization
- **DL:** *Deep Learning* (Goodfellow et al.), fast.ai, Andrej Karpathy's *Neural Networks: Zero to Hero*
- **Gen AI:** Hugging Face course, *Attention Is All You Need* paper
- **Gen AI frameworks:** LangChain docs, LlamaIndex docs, MTEB leaderboard (embeddings)
- **Agentic:** Anthropic's *Building Effective Agents*, LangGraph docs (LangChain Academy), MCP docs
- **Voice:** LiveKit Agents docs, Pipecat docs
