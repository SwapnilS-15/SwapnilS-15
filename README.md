<img src="assets/banner.png" alt="Swapnil Sahu: ML Engineer, LLMs, RAG & Computer Vision" width="100%">

<p>
  <a href="https://www.linkedin.com/in/YOUR-HANDLE"><img src="https://img.shields.io/badge/LinkedIn-0d1117?style=flat-square&logo=linkedin&logoColor=a855f7" alt="LinkedIn"></a>
  <a href="https://huggingface.co/SwapnilS-15"><img src="https://img.shields.io/badge/Hugging%20Face-0d1117?style=flat-square&logo=huggingface&logoColor=a855f7" alt="Hugging Face"></a>
  <a href="mailto:YOUR-EMAIL"><img src="https://img.shields.io/badge/Email-0d1117?style=flat-square&logo=gmail&logoColor=a855f7" alt="Email"></a>
  <a href="YOUR-RESUME-LINK"><img src="https://img.shields.io/badge/Resume-0d1117?style=flat-square&logo=readdotcv&logoColor=a855f7" alt="Resume"></a>
</p>

I'm an ML engineer who fine-tunes, evaluates and ships language and vision models, mostly on a **6 GB laptop GPU**. That constraint shaped how I work: small models pushed hard, every experiment logged, and every request traced, so I can tell what actually improved and why.

Currently open to **AI/ML engineer roles** in India or remote.

## How I work

**⚡ Built for constrained hardware.** I fine-tune on an RTX 4050 (6 GB) with QLoRA and Unsloth. For DPO I reuse the policy with its adapter disabled as the reference model, so no second model has to fit in memory. Serving stacks are CPU-first where possible.

**🧪 Experiments I can defend.** I use frozen test sets, greedy decoding, the same scoring code across baselines, confidence intervals, and significance tests. Experiments are tracked in MLflow, so a result can always be traced back to the run that produced it.

**📊 Observable by default.** I add structured per-request JSON logs, latency and token metrics for each pipeline stage, and Langfuse tracing. When something breaks or slows down, the logs show where.

## Selected results

| | Result | Context |
|---|---|---|
| 🎯 Tool-call exact match | **61.6% → 80.0%** | Qwen2.5-0.5B, base vs. SFT + DPO, 2,929 held-out questions |
| 🚫 "No tool fits" abstention | **0% → 82.3%** | DPO on the SFT model's own mistakes, 300 questions |
| 📐 Significance | **p = 0.0003** | McNemar test, DPO vs. SFT |
| 💻 Footprint | **0.5B params** | Runs on a laptop CPU or a 6 GB GPU |

## Experience

**AI & ML Intern, [Logic Fruit Technologies](https://www.logic-fruit.com/)** · Gurugram · 2025 – 2026
- Computer vision for a defence project: drone vs. bird classification, with experiments tracked in MLflow
- Fine-tuned Gemma 3 (270M) with LoRA on company data on an A100 to power an internal company chatbot

## Projects

| Project | What it is | Stack |
|---|---|---|
| **[Toolcaller-SLM](https://github.com/SwapnilS-15/Toolcaller-SLM)**<br>[🤗 model](https://huggingface.co/SwapnilS-15/qwen2.5-0.5b-instructv2-fc) · [demo](https://huggingface.co/spaces/SwapnilS-15/Toolcaller_Demo) | A 0.5B function-calling model: QLoRA SFT on xLAM-60k, then DPO on its own mistakes. Served with vLLM behind a LangGraph gateway with guardrails. | `TRL` `Unsloth` `vLLM` `LangGraph` `Langfuse` |
| **[Enterprise-RAG](https://github.com/SwapnilS-15/Enterprise-RAG)** | A fully local RAG service with hybrid retrieval (dense + BM25), a cross-encoder reranker, and Qwen3 via Ollama. It adds Pydantic-validated answers, retries, per-request metrics, and DeepEval evaluation. | `FastAPI` `ChromaDB` `LangChain` `Ollama` `Docker` |
| **[OKF](https://github.com/SwapnilS-15/OKF)** | _One line: what it does and what's interesting about it._ | `…` |
| **[PDFinsights](https://github.com/SwapnilS-15/PDFinsights)** | _One line: what it does and what's interesting about it._ | `…` |

**In progress:** vision-language work with **SigLIP**, and **diffusion models**.

## Stack

**Models & training:** PyTorch · Transformers · TRL (SFT, DPO) · PEFT / QLoRA · Unsloth
**Serving & apps:** vLLM · Ollama · FastAPI · LangChain · LangGraph · Gradio
**Retrieval:** ChromaDB · BM25 · cross-encoder rerankers
**Evaluation & observability:** MLflow · Langfuse · DeepEval · Ragas
**Infra:** Docker · Git
