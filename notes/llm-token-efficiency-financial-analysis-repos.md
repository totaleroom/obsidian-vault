# LLM Token Efficiency & Financial Analysis — GitHub Repo Research

## KV-Cache Quantization (Infrastructure Layer)

### 1. [huawei-csl/KVarN](https://github.com/huawei-csl/KVarN) ⭐ 507
**What it does:** Native vLLM KV-cache quantization backend — 3–5× more context capacity, ~1.3× throughput vs FP16, FP16-level accuracy.
**Techniques:**
- Variance-normalized KV-cache quantization (K4V2 with group size 128)
- Calibration-free, one flag to enable: `--kv-cache-dtype kvarn_k4v2_g128`
- Supports MLA (Multi-head Latent Attention) models — int4 quantization of compressed KV latent
- Built as a vLLM fork; plug-and-play, no model changes needed
- Tile size 128 (default) or 64 for finer granularity

---

### 2. [SqueezeAILab/KVQuant](https://github.com/SqueezeAILab/KVQuant) ⭐ 436
**What it does:** KV-cache quantization for LLM inference supporting up to 10M context length.
**Techniques:**
- Per-channel quantization of KV caches
- Low-bit quantization (down to 4-bit) with minimal accuracy loss
- Designed for long-context workloads (paper: NeurIPS 2024)

---

### 3. [FastMAS/KVCOMM](https://github.com/FastMAS/KVCOMM) ⭐ 191
**What it does:** Online cross-context KV-cache communication for efficient multi-agent LLM systems.
**Techniques:**
- KV-cache sharing across agents in multi-agent systems
- Reduces redundant KV-cache computation
- NeurIPS 2025 publication

---

### 4. [ByteDance-Seed/ShadowKV](https://github.com/ByteDance-Seed/ShadowKV) ⭐ 314
**What it does:** KV cache in shadows for high-throughput long-context LLM inference.
**Techniques:**
- Shadow KV approach to memory-efficient long-context inference
- ICML 2025 Spotlight

---

### 5. [microsoft/RetrievalAttention](https://github.com/microsoft/RetrievalAttention) ⭐ 152
**What it does:** Scalable long-context LLM decoding leveraging sparsity via KV cache as vector storage.
**Techniques:**
- Treats KV cache as vector database for retrieval-based attention
- VLDB 2026, NeurIPS 2025

---

### 6. [VectifyAI/ConDB](https://github.com/VectifyAI/ConDB) ⭐ 63
**What it does:** KV-cache native context database.
**Techniques:**
- KV cache as a native context database — indexing and retrieving KV entries
- Designed for long-context RAG-style workloads

---

### 7. [NVlabs/RocketKV](https://github.com/NVlabs/RocketKV) ⭐ 54
**What it does:** Two-stage KV cache compression for long-context LLM inference.
**Techniques:**
- Two-stage compression pipeline for KV cache
- ICML 2025

---

## Prompt / Context Compression

### 8. [Huzaifa785/context-compressor](https://github.com/Huzaifa785/context-compressor) ⭐ 90
**What it does:** AI-powered text compression for RAG systems and API calls — reduces token usage 50–60% while preserving semantic meaning.
**Techniques:**
- Semantic compression strategies for RAG
- Embedding-aware token reduction
- Preserves meaning during compression

---

### 9. [synchronic1/TokenRanger](https://github.com/synchronic1/TokenRanger) ⭐ 7
**What it does:** Context compression extension for OpenClaw — reduces cloud LLM token costs 50–80%.
**Techniques:**
- Local SLM (Small Language Model) summarization for compression
- Extractive token selection before LLM call

---

### 10. [Silicon-based-Life/ContextLease](https://github.com/Silicon-based-Life/ContextLease) ⭐ 1
**What it does:** Dynamic LLM context budgeting with revocable token leases, prompt compression, pluggable summarizers, and real-time observability.
**Techniques:**
- Dynamic token leasing system for context budgets
- Pluggable summarizers (any summarization model)
- Real-time token usage observability
- Revocable token allocation

---

### 11. [dakshjain-1616/Agent-Memory-Compressor](https://github.com/dakshjain-1616/Agent-Memory-Compressor)
**What it does:** Memory compressor for long-running LLM agents — prevents context-window exhaustion while preserving task-critical facts.
**Techniques:**
- Summarization + embedding-based retrieval hybrid
- Tunable compression ratios
- Fact preservation via embedding similarity

---

## Financial / Trading Analysis with RAG

### 12. [Arushi-Srivastava-16/FinanceRAG](https://github.com/Arushi-Srivastava-16/FinanceRAG) ⭐ 4
**What it does:** Financial analysis platform combining RAG with multi-agent AI for stock market insights.
**Techniques:**
- RAG for financial document retrieval
- Multi-agent AI system for collaborative reasoning
- Real-time news + sentiment analysis + technical indicators
- Query decomposition for financial signals

---

### 13. [Yigtwxx/OracleX](https://github.com/Yigtwxx/OracleX) ⭐ 2
**What it does:** Open-source financial intelligence terminal with ChromaDB vector memory.
**Techniques:**
- ChromaDB vector memory for semantic recall
- Provider-agnostic reasoning (Ollama or 12+ cloud providers)
- Real-time market data + LLM news analysis

---

### 14. [btaruns22/RAGs-to-Riches](https://github.com/btaruns22/RAGs-to-Riches) ⭐ 0
**What it does:** RAG for structured financial signal analysis in trading.
**Techniques:**
- Evaluating RAG for structured financial signals
- Directly applicable to trading decision pipelines

---

### 15. [Gaurav-171/Advanced_Ultimate_Stock_analysis](https://github.com/Gaurav-171/Advanced_Ultimate_Stock_analysis) ⭐ 4
**What it does:** AI-powered stock trading decision system using CrewAI, RAG, and real-time market data.
**Techniques:**
- CrewAI multi-agent orchestration
- RAG for financial document retrieval
- Real-time market data integration
- Multi-agent financial analysis + strategy

---

### 16. [petermartens98/GPT4-LangChain-Stock-Market-Analysis-Agent](https://github.com/petermartens98/GPT4-LangChain-Stock-Market-Analysis-Agent) ⭐ 81
**What it does:** LangChain + Streamlit stock market analysis agent with SQLite auth.
**Techniques:**
- LangChain for agent orchestration
- Multi-stock selection and analysis
- Python Streamlit UI

---

### 17. [vansh-121/Multi-Agent-AI-Finance-Assistant](https://github.com/vansh-121/Multi-Agent-AI-Finance-Assistant) ⭐ 27
**What it does:** Multi-agent AI finance assistant for intelligent financial analysis.
**Techniques:**
- Hierarchical multi-agent system
- Real-time financial data integration

---

### 18. [psrane8/Market-Research-Agent](https://github.com/psrane8/Market-Research-Agent) ⭐ 25
**What it does:** Comprehensive company financial/market analysis via multi-agent application.
**Techniques:**
- Multi-agent financial research
- Comprehensive market analysis

---

## Summary Table

| Repo | Stars | Focus | Key Technique |
|------|-------|-------|---------------|
| huawei-csl/KVarN | 507 | KV-cache quantization | Variance-normalized KV quant, vLLM backend |
| SqueezeAILab/KVQuant | 436 | KV-cache quantization | 10M context via per-channel KV quant |
| ByteDance-Seed/ShadowKV | 314 | KV-cache | Shadow KV for long-context throughput |
| FastMAS/KVCOMM | 191 | KV-cache multi-agent | Cross-context KV communication |
| microsoft/RetrievalAttention | 152 | KV-cache as vector DB | Retrieval-based attention |
| Huzaifa785/context-compressor | 90 | Prompt compression | 50–60% token reduction, semantic preserve |
| VectifyAI/ConDB | 63 | KV-cache DB | KV cache as native context database |
| NVlabs/RocketKV | 54 | KV-cache compression | Two-stage KV compression |
| TokenRanger | 7 | Prompt compression | Local SLM summarization, 50–80% reduction |
| Silicon-based-Life/ContextLease | 1 | Dynamic context budget | Revocable token leases, pluggable summarizers |
| FinanceRAG (Arushi) | 4 | Financial RAG | Multi-agent + sentiment + technical |
| OracleX | 2 | Financial vector memory | ChromaDB vector memory + LLM |
| GPT4-LangChain-Stock | 81 | Financial agent | LangChain + Streamlit multi-stock |
| Multi-Agent-AI-Finance | 27 | Financial agent | Hierarchical multi-agent finance |
