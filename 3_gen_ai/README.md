# Generative AI

[← Back to main README](../README.md)

## 📖 Book Index — Part 3: Generative AI

**Chapters:** [1. Tokenization](#chapter-1-tokenization) · [2. Embeddings](#chapter-2-embeddings) · [3. Large Language Models (LLMs)](#chapter-3-large-language-models-llms) · [4. Prompt engineering](#chapter-4-prompt-engineering) · [5. Working with LLM APIs](#chapter-5-working-with-llm-apis) · [6. Vector databases](#chapter-6-vector-databases) · [7. LangChain](#chapter-7-langchain) · [8. LlamaIndex](#chapter-8-llamaindex) · [9. Retrieval-Augmented Generation (RAG)](#chapter-9-retrieval-augmented-generation-rag) · [10. Fine-tuning (LoRA / QLoRA)](#chapter-10-fine-tuning-lora--qlora) · [11. Evaluation of LLM outputs](#chapter-11-evaluation-of-llm-outputs) · [12. Diffusion & multimodal models](#chapter-12-diffusion--multimodal-models) · [13. Project: chat assistant with RAG](#chapter-13-project-chat-assistant-with-rag)

### Chapter 1: Tokenization

🟢 Core · 📝 Notes coming

- **1.1** Why LLMs read tokens, not words
- **1.2** BPE, WordPiece & SentencePiece
- **1.3** Vocabulary size & special tokens
- **1.4** Counting tokens & estimating cost
- **1.5** Tokenization across languages

**🔑 Key terms:** token, vocabulary, BPE, special token, context length  
**🎯 You'll learn:** How text becomes the numbers an LLM reads, and why it affects cost  
**🛠️ You can build:** A BPE tokenizer from scratch and a token-cost calculator

### Chapter 2: Embeddings

🟢 Core · [📄 Read the notes](#2-embeddings)

- **2.1** How embeddings work
- **2.2** Similarity: cosine, dot product, Euclidean
- **2.3** Embedding models
- **2.4** Chunking for embeddings

**🔑 Key terms:** embedding, vector, dimension, cosine similarity, dense vs. sparse, chunk  
**🎯 You'll learn:** Represent meaning as numbers so you can search by meaning  
**🛠️ You can build:** A semantic FAQ search without any database

### Chapter 3: Large Language Models (LLMs)

🟢 Core · [📄 Read the notes](#3-large-language-models-llms)

- **3.1** How an LLM generates text
- **3.2** Training: pre-training → SFT → preference tuning
- **3.3** Sampling: temperature, top-k, top-p
- **3.4** Context window & KV cache
- **3.5** Model families: closed, open-weight, local
- **3.6** Limitations

**🔑 Key terms:** autoregressive, base model, instruct model, RLHF, temperature, top-p, context window, hallucination  
**🎯 You'll learn:** What an LLM really does and which knobs change its output  
**🛠️ You can build:** A tiny GPT trained on Shakespeare

### Chapter 4: Prompt engineering

🟢 Core · 📝 Notes coming

- **4.1** System vs. user prompts
- **4.2** Zero-shot & few-shot
- **4.3** Chain-of-thought
- **4.4** Structured output (JSON)
- **4.5** Prompt templates
- **4.6** Prompt-injection basics

**🔑 Key terms:** system prompt, few-shot, chain-of-thought, delimiter, structured output  
**🎯 You'll learn:** Get reliable, well-formatted answers from a model  
**🛠️ You can build:** A JSON extractor that pulls fields out of emails

### Chapter 5: Working with LLM APIs

🟢 Core · 📝 Notes coming

- **5.1** The messages API
- **5.2** Streaming
- **5.3** Tool calling
- **5.4** Multi-turn chat
- **5.5** Errors, rate limits & retries
- **5.6** Cost & prompt caching
- **5.7** Local models with Ollama

**🔑 Key terms:** API key, message roles, streaming, input / output tokens, rate limit  
**🎯 You'll learn:** Call LLMs from code the way real apps do  
**🛠️ You can build:** A streaming terminal chatbot

### Chapter 6: Vector databases

🟢 Core · [📄 Read the notes](#6-vector-databases)

- **6.1** How vector search works
- **6.2** Index types: flat, HNSW, IVF, PQ
- **6.3** Popular vector databases
- **6.4** Choosing one

**🔑 Key terms:** vector store, nearest neighbour, top-k, HNSW, metadata filter, hybrid search, reranker  
**🎯 You'll learn:** Store millions of embeddings and search them fast  
**🛠️ You can build:** A searchable document store with metadata filters

### Chapter 7: LangChain

🟢 Core · [📄 Read the notes](#7-langchain)

- **7.1** Core components
- **7.2** LCEL: chaining with pipes
- **7.3** The LangChain ecosystem
- **7.4** When to use it

**🔑 Key terms:** chain, prompt template, retriever, output parser, LCEL  
**🎯 You'll learn:** Assemble LLM apps from ready-made building blocks  
**🛠️ You can build:** A RAG chain over your PDFs

### Chapter 8: LlamaIndex

⚪ Later · [📄 Read the notes](#8-llamaindex)

- **8.1** Documents, nodes & indexes
- **8.2** Query & chat engines
- **8.3** Index types
- **8.4** Advanced retrieval

**🔑 Key terms:** node, index, query engine, chat engine, LlamaParse  
**🎯 You'll learn:** A data-first framework for high-quality retrieval  
**🛠️ You can build:** A 5-line RAG, then a router over several indexes

### Chapter 9: Retrieval-Augmented Generation (RAG)

🟢 Core · 📝 Notes coming

- **9.1** Why RAG
- **9.2** Ingestion: load → chunk → embed → store
- **9.3** Retrieval: top-k, hybrid, reranking
- **9.4** Prompting with context & citations
- **9.5** Common failure modes
- **9.6** Improvements: query rewriting, parent documents

**🔑 Key terms:** retriever, chunk, top-k, context, grounding, citation, reranker  
**🎯 You'll learn:** Let an LLM answer from your own documents instead of guessing  
**🛠️ You can build:** A chat-with-your-documents app

### Chapter 10: Fine-tuning (LoRA / QLoRA)

⚪ Later · 📝 Notes coming

- **10.1** Prompting vs. RAG vs. fine-tuning
- **10.2** Full fine-tuning vs. PEFT
- **10.3** LoRA & QLoRA
- **10.4** Preparing a dataset
- **10.5** Evaluating the result

**🔑 Key terms:** PEFT, LoRA, adapter, quantization, epoch, overfitting  
**🎯 You'll learn:** Adapt an open model's style or skills to your task  
**🛠️ You can build:** A small model fine-tuned for one task or tone

### Chapter 11: Evaluation of LLM outputs

🟢 Core · 📝 Notes coming

- **11.1** Why LLM evaluation is hard
- **11.2** Reference-based metrics
- **11.3** LLM-as-judge
- **11.4** RAG metrics: faithfulness, relevance
- **11.5** Eval datasets & regression testing

**🔑 Key terms:** ground truth, judge, faithfulness, answer relevance, regression test  
**🎯 You'll learn:** Know whether a change made your app better or worse  
**🛠️ You can build:** An eval suite for your RAG app

### Chapter 12: Diffusion & multimodal models

⚪ Later · 📝 Notes coming

- **12.1** How diffusion generates images
- **12.2** Stable Diffusion
- **12.3** Vision-language models
- **12.4** Speech models (Whisper)

**🔑 Key terms:** noise, denoising, latent space, VLM, multimodal  
**🎯 You'll learn:** Models that create and understand images and audio  
**🛠️ You can build:** An image generator and a describe-this-image app

### Chapter 13: Project: chat assistant with RAG

🟢 Core · [📄 Read the notes](../projects/conversational_agent_design.md)

- **13.1** Streaming chat UI
- **13.2** RAG over your documents
- **13.3** Basic evaluation

**🎯 You'll learn:** Combine everything from this part into one app (phases 1–2 of the capstone)  
**🛠️ You can build:** A document Q&A chat assistant

Legend: 🟢 Core = study now · ⚪ Later = after the core ([Core Path](../README.md#core-path))

**Comparison:** [LangChain vs. LlamaIndex vs. LangGraph](#langchain-vs-llamaindex-vs-langgraph)

---

## 2. Embeddings

An embedding turns text (or an image or audio clip) into a list of numbers, a **vector**, so that things with similar meaning end up close together. Embeddings power semantic search, RAG, clustering, recommendations and deduplication.

**Prerequisites:** tokenization (1).

**In this section:** [How embeddings work](#how-embeddings-work) · [Similarity measures](#similarity-measures) · [Embedding models](#embedding-models) · [Chunking for embeddings](#chunking-for-embeddings) · [Hands-On: Embeddings](#hands-on-embeddings)

### How embeddings work

```
"How do I reset my password?"  → [0.12, -0.83, 0.45, ...]  ┐
"I forgot my login password"   → [0.10, -0.80, 0.47, ...]  ┘ close together
"Best pizza in town"           → [-0.66, 0.21, -0.09, ...]   far away
```

- **Dimension:** the length of the vector, usually 384–3072.
- **Dense vs. sparse:** dense vectors capture meaning, while sparse vectors (BM25, SPLADE) capture exact keywords. **Hybrid search** combines both.

### Similarity measures

| Measure | Idea | When to use |
|---|---|---|
| **Cosine similarity** | Angle between vectors | The default for text |
| **Dot product** | Angle and length | Normalized vectors (equals cosine) |
| **Euclidean (L2)** | Straight-line distance | Some image models |

### Embedding models

| Model | Type | Notes |
|---|---|---|
| **all-MiniLM-L6-v2** | Open, local | Small and fast, good for learning |
| **BGE / E5 / GTE** | Open, local | Strong on the MTEB leaderboard |
| **Nomic Embed** | Open, local | Long context |
| **OpenAI text-embedding-3** | API | Small and large sizes |
| **Voyage AI** | API | Strong retrieval quality |
| **Cohere Embed** | API | Multilingual |
| **CLIP** | Open | Text and images in the same space |

Compare models on the **MTEB leaderboard**, and always test on your own data.

### Chunking for embeddings

| Strategy | Idea |
|---|---|
| **Fixed size + overlap** | e.g. 500 tokens with 50 overlapping. Simple baseline |
| **Recursive** | Split on paragraphs, then sentences, then words |
| **Semantic** | Split where the meaning changes |
| **Document-aware** | Respect headings, tables and code blocks |

### Hands-On: Embeddings

| # | Exercise | Tools |
|---|---|---|
| 2.1 | Embed sentences and find the most similar pairs | Sentence-Transformers |
| 2.2 | Visualize embeddings in 2D | UMAP / t-SNE, Matplotlib |
| 2.3 | Semantic search over FAQs without a vector DB | NumPy, cosine similarity |
| 2.4 | Compare 3 embedding models on your own questions | Sentence-Transformers, an API model |
| 2.5 | Compare chunking strategies on retrieval quality | LangChain text splitters |

---

## 3. Large Language Models (LLMs)

An LLM is a big **decoder-only Transformer** trained to do one thing: **predict the next token**. Done at huge scale on huge amounts of text, that simple task produces models that can write, reason, code and hold a conversation.

**Prerequisites:** Transformers (`2_dl/` 8), tokenization (1), embeddings (2).

**In this section:** [How an LLM generates text](#how-an-llm-generates-text) · [How LLMs are trained](#how-llms-are-trained) · [Sampling & decoding](#sampling--decoding) · [Context window & KV cache](#context-window--kv-cache) · [Model families](#model-families) · [Limitations](#llm-limitations) · [Hands-On: LLMs](#hands-on-llms)

### How an LLM generates text

```
"The cat sat on the" → tokenize → Transformer → probabilities for next token
                                                  mat 0.41 · floor 0.22 · sofa 0.10 ...
                                     pick "mat" → append → repeat
```

Generation is a loop: predict one token, append it, predict the next. This is **autoregressive** generation, and it's why responses stream in word by word.

### How LLMs are trained

| Stage | Data | Result |
|---|---|---|
| **1. Pre-training** | Trillions of tokens of web, books, code | **Base model**: great at continuing text, but doesn't follow instructions |
| **2. Supervised fine-tuning (SFT)** | Thousands of example instruction → good answer pairs | **Instruct model**: follows instructions and chats |
| **3. Preference tuning** (RLHF, DPO, Constitutional AI) | Human or AI rankings of better vs. worse answers | Helpful, honest, safer **assistant** |

Ask a base model *"What is the capital of France?"* and it may continue with *"What is the capital of Germany?"*. An instruct model answers *"Paris."*

### Sampling & decoding

| Setting | What it does | Typical use |
|---|---|---|
| **Greedy** | Always pick the most likely token | Deterministic, but can be repetitive |
| **Temperature** | < 1 sharpens choices, > 1 flattens them | 0–0.3 for facts and code, 0.7–1 for creative writing |
| **Top-k** | Sample only from the k most likely tokens | Cuts off unlikely tokens |
| **Top-p (nucleus)** | Sample from the smallest set covering p of the probability | Adapts to how confident the model is |
| **Max tokens / stop sequences** | When to stop | Control length and cost |

### Context window & KV cache

- **Context window:** the maximum number of tokens (prompt + answer) the model can see at once. Everything the model "knows" about your conversation must fit in it.
- **Cost & speed:** APIs charge per input and output token. Longer prompts mean more cost and latency.
- **KV cache:** during generation, the keys and values of earlier tokens are stored instead of recomputed, which is why each new token is fast.
- **Prompt caching:** APIs can reuse the cache for a repeated prefix, such as a long system prompt, making it cheaper and faster.

### Model families

| Type | Examples | Pros | Cons |
|---|---|---|---|
| **Closed / API** | Claude, GPT, Gemini | Strongest models, nothing to host | Pay per token, data leaves your machine |
| **Open-weight** | Llama, Mistral, Qwen, Gemma, DeepSeek | Run locally, fine-tune, free to use | Need a GPU, usually weaker at the same size |
| **Small / local** | Phi, Gemma 2B, Llama 3B via Ollama | Runs on a laptop, private | Limited reasoning |

**Size vs. quality:** parameters (7B, 70B …) roughly set capability and cost. **Quantization** (8-bit, 4-bit) shrinks models so they fit on smaller GPUs.

### LLM limitations

- **Hallucination:** confident but wrong answers. Ground answers with RAG (topic 9).
- **Knowledge cutoff:** no knowledge of recent events. Use tools or search.
- **No memory between calls:** your app has to send the history every time.
- **Weak at exact maths and counting:** give it a calculator or code tool.
- **Prompt sensitivity:** small wording changes can change the output (topic 4).

### Hands-On: LLMs

| # | Exercise | Tools |
|---|---|---|
| 3.1 | Count tokens for English, Hindi and code, and estimate API cost | tiktoken, Anthropic token counting |
| 3.2 | Generate with GPT-2 and print the top-5 next-token probabilities at each step | Hugging Face Transformers |
| 3.3 | Same prompt at temperature 0, 0.7 and 1.5, plus top-p. Compare outputs | Hugging Face / LLM API |
| 3.4 | Ask the same question to a base model and an instruct model | Hugging Face |
| 3.5 | Build and train a tiny character-level GPT on Shakespeare | PyTorch (Karpathy's *nanoGPT* / *Let's build GPT*) |
| 3.6 | Run an open model locally and compare it with an API model | Ollama, LLM API |
| 3.7 | Find hallucinations: ask about a made-up fact, then fix it by adding context | LLM API |

---

## 6. Vector Databases

A database built to store embeddings and quickly find the vectors **nearest** to a query vector, even among millions of them.

**Prerequisites:** embeddings (2).

**In this section:** [How vector search works](#how-vector-search-works) · [Index types](#index-types) · [Popular vector databases](#popular-vector-databases) · [Choosing a vector DB](#choosing-a-vector-db) · [Hands-On: Vector Databases](#hands-on-vector-databases)

### How vector search works

```
Ingest:  document → chunk → embed → store (vector + text + metadata)
Query:   question → embed → find top-k nearest vectors → filter by metadata → results
```

### Index types

| Index | Idea | Trade-off |
|---|---|---|
| **Flat (brute force)** | Compare against every vector | Exact but slow at scale |
| **HNSW** | Graph of neighbors, hop toward the closest | Fast and accurate. The most common default |
| **IVF** | Cluster the vectors, search only the nearest clusters | Fast, uses less memory |
| **PQ (product quantization)** | Compress the vectors | Much less memory, a little less accurate |

### Popular vector databases

| Database | Type | Good for |
|---|---|---|
| **Chroma** | Embedded / local | Learning and prototypes |
| **FAISS** | Library (Meta) | Fast local search, research |
| **pgvector** | Postgres extension | When you already use Postgres |
| **Qdrant** | Server / cloud | Production, strong filtering |
| **Weaviate** | Server / cloud | Built-in hybrid search |
| **Milvus** | Server / cloud | Very large scale |
| **Pinecone** | Managed cloud | No infrastructure to run |
| **Redis** | In-memory | Low latency, also caching |

### Choosing a vector DB

- **Learning:** Chroma or FAISS.
- **Already on Postgres:** pgvector.
- **Production with filters and hybrid search:** Qdrant or Weaviate.
- **No servers to manage:** Pinecone.

Things to check: metadata filtering, hybrid search, scale, cost, and whether you can run it locally.

### Hands-On: Vector Databases

| # | Exercise | Tools |
|---|---|---|
| 6.1 | Store and query documents locally | Chroma |
| 6.2 | Build flat vs. HNSW indexes and compare speed | FAISS |
| 6.3 | Add vector search to a Postgres database | pgvector |
| 6.4 | Metadata filtering + hybrid search | Qdrant |
| 6.5 | Add a reranker and measure the improvement | Cohere Rerank / BGE reranker |

---

## 7. LangChain

A Python and JavaScript framework that provides building blocks for LLM apps (models, prompts, retrievers, tools, output parsers) and a common interface across providers.

**Prerequisites:** LLM APIs (5), embeddings (2), vector databases (6).

**In this section:** [Core components](#core-components) · [LCEL: chaining with pipes](#lcel-chaining-with-pipes) · [The LangChain ecosystem](#the-langchain-ecosystem) · [When to use LangChain](#when-to-use-langchain) · [Hands-On: LangChain](#hands-on-langchain)

### Core components

| Component | What it does |
|---|---|
| **Chat models** | One interface for Claude, OpenAI, Ollama and more |
| **Prompt templates** | Reusable prompts with variables |
| **Output parsers / structured output** | Turn LLM text into JSON or Pydantic objects |
| **Document loaders** | Read PDFs, web pages, Notion, databases ... |
| **Text splitters** | Chunk documents |
| **Embeddings & vector stores** | Wrappers around embedding models and vector DBs |
| **Retrievers** | Fetch relevant documents for a query |
| **Tools** | Functions the LLM can call |

### LCEL: chaining with pipes

LangChain Expression Language connects components with `|`:

```python
chain = prompt | model | output_parser
chain.invoke({"question": "What is RAG?"})
```

A minimal RAG chain:

```
question → retriever → format docs → prompt → model → parser → answer
```

### The LangChain ecosystem

| Project | Role |
|---|---|
| **LangChain** | Building blocks and integrations |
| **LangGraph** | Stateful agents and workflows as graphs (see `4_agentic_ai` 4.7) |
| **LangSmith** | Tracing, debugging and evaluation |

### When to use LangChain

- **Good for:** quick prototypes, swapping providers, using its many integrations.
- **Watch out:** extra abstraction layers can make debugging harder. For simple apps, the provider SDK alone is often enough. For agents, use LangGraph.

### Hands-On: LangChain

| # | Exercise | Tools |
|---|---|---|
| 7.1 | Prompt template + chat model + parser chain | LangChain |
| 7.2 | Structured output into a Pydantic model | LangChain |
| 7.3 | Load PDFs, split, embed, store | LangChain, Chroma |
| 7.4 | Basic RAG chain with LCEL | LangChain |
| 7.5 | Chat with message history | LangChain |
| 7.6 | Trace the chain end to end | LangSmith |

---

## 8. LlamaIndex

A framework focused on **connecting LLMs to your data**: loading, indexing and querying documents. It is the go-to choice when retrieval quality is the main concern.

**Prerequisites:** embeddings (2), vector databases (6).

**In this section:** [Core concepts](#core-concepts) · [Index types in LlamaIndex](#index-types-in-llamaindex) · [Advanced retrieval](#advanced-retrieval) · [Hands-On: LlamaIndex](#hands-on-llamaindex)

### Core concepts

| Concept | What it does |
|---|---|
| **Readers / LlamaHub** | Load data from hundreds of sources |
| **Documents & Nodes** | Documents are split into nodes (chunks) with metadata |
| **Index** | Organizes nodes for retrieval |
| **Retriever** | Fetches relevant nodes |
| **Query engine** | Retrieval + LLM answer, for one question |
| **Chat engine** | Query engine with conversation memory |
| **Agents & workflows** | Tool-using agents and event-driven pipelines |
| **LlamaParse** | Parses complex PDFs (tables, layouts) |

A minimal RAG in about 5 lines:

```python
docs = SimpleDirectoryReader("data").load_data()
index = VectorStoreIndex.from_documents(docs)
engine = index.as_query_engine()
engine.query("What is our refund policy?")
```

### Index types in LlamaIndex

| Index | Use |
|---|---|
| **VectorStoreIndex** | Semantic search (most common) |
| **SummaryIndex** | Read everything, for summaries |
| **KeywordTableIndex** | Keyword lookup |
| **PropertyGraphIndex** | Knowledge graph (GraphRAG) |

### Advanced retrieval

- **Sentence window / auto-merging:** retrieve small chunks, then send the surrounding context.
- **Hybrid search + reranking.**
- **Sub-question query engine:** splits a complex question into smaller ones.
- **Router query engine:** picks the right index for each question.

### Hands-On: LlamaIndex

| # | Exercise | Tools |
|---|---|---|
| 8.1 | 5-line RAG over a folder of documents | LlamaIndex |
| 8.2 | Persist the index in a vector DB | LlamaIndex, Qdrant / Chroma |
| 8.3 | Chat engine with memory | LlamaIndex |
| 8.4 | Parse complex PDFs with tables | LlamaParse |
| 8.5 | Sub-question and router query engines | LlamaIndex |
| 8.6 | Evaluate retrieval quality | LlamaIndex evals, RAGAS |

---

## LangChain vs. LlamaIndex vs. LangGraph

| | **LangChain** | **LlamaIndex** | **LangGraph** |
|---|---|---|---|
| Focus | General LLM building blocks | Data & retrieval | Stateful agents & workflows |
| Best for | Chains, integrations, prototypes | RAG over many documents | Agents with loops, branches, memory, human-in-the-loop |
| Abstraction | Components + LCEL pipes | Indexes + query engines | Graph of nodes, edges and state |
| Covered in | `3_gen_ai` 7 | `3_gen_ai` 8 | `4_agentic_ai` 7 |

They work together: a common stack uses **LlamaIndex for retrieval**, **LangGraph for the agent** and **LangChain integrations** for models and tools.
