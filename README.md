# Swapnil Sahu

**ML Engineer · LLMs, RAG & Computer Vision**

<p>
  <a href="https://huggingface.co/SwapnilS-15"><img src="https://img.shields.io/badge/Hugging_Face-SwapnilS--15-24292f?style=for-the-badge&logo=huggingface&logoColor=white" alt="Hugging Face" height="32"></a>
  <a href="mailto:YOUR-EMAIL"><img src="https://img.shields.io/badge/Email-Contact-24292f?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" height="32"></a>
  <a href="YOUR-RESUME-LINK"><img src="https://img.shields.io/badge/Resume-View-24292f?style=for-the-badge&logo=readdotcv&logoColor=white" alt="Resume" height="32"></a>
</p>

I fine-tune, evaluate and ship language and vision models. I've trained on an A100 and built full systems that run on a 6 GB consumer GPU. Either way, I pick the setup with numbers, track every experiment, and trace every request, so I can show what actually improved and why.

Open to **AI/ML engineer roles** in India or remote.

## How I work

**⚡ Hardware-aware.** I match the method to the machine: LoRA fine-tuning on an A100 in industry, and QLoRA, Unsloth and memory-saving DPO (the adapter-disabled policy doubles as the reference model) on consumer GPUs. All of my portfolio systems run end-to-end on 6 GB of VRAM.

**🧪 Measured, not guessed.** Every choice is backed by an experiment: frozen test sets, hand-labelled golden sets, identical scoring across baselines, confidence intervals and significance tests. Runs are tracked in MLflow. I also check the benchmark itself; I caught Ollama's KV-cache reuse inflating prefill timings by about 10×.

**📊 Observable by default.** Structured per-request logs, per-stage latency and token metrics, `/metrics` and readiness endpoints, and OpenTelemetry traces in Grafana correlated by `trace_id`, plus Langfuse for LLM calls.

## Selected results

| Project | Result | Context |
|---|---|---|
| **Toolcaller-SLM** | **61.6% → 80.0%** tool-call exact match | Qwen2.5-0.5B, base vs. SFT + DPO on 2,929 held-out questions (McNemar p = 0.0003 vs. SFT) |
| **Toolcaller-SLM** | **0% → 82.3%** correct abstention | DPO taught the model to answer `[]` when no tool fits |
| **OKF** | **89% vs. 26%** answers with all key facts | Curated knowledge bundle vs. a knowledge graph, on 5 landmark AI papers (775 pages) |
| **OKF** | **~30 min vs. 10+ hours** to build | Knowledge bundle vs. knowledge graph on a 6 GB GPU, about 20× faster |
| **PDFinsights** | **97% Hit@5** retrieval | Hybrid search + reranking on a 69-question hand-labelled golden set |
| **PDFinsights** | **290 ms** time to first token, **0.90** faithfulness | llama3.2:3b, chosen from 5 LLMs on speed and faithfulness |
| **Enterprise-RAG** | **~2 GB** smaller serving image | Reranking moved server-side to Qdrant, so the image ships without torch |
<!-- Add an internship row here, e.g. | **DRDO project** | **XX%** accuracy | Drone vs. bird classification, … | -->

## Experience

**AI & ML Intern, [Logic Fruit Technologies](https://www.logic-fruit.com/)** · Gurugram · 2025 – 2026
- **DRDO project:** built drone vs. bird classification models, with experiments tracked and compared in MLflow
- **Internal company chatbot:** fine-tuned Gemma 3 (270M) with LoRA/PEFT on company data on an A100

## Projects

| Project | What it is | Stack |
|---|---|---|
| **[Toolcaller-SLM](https://github.com/SwapnilS-15/Toolcaller-SLM)**<br>[model](https://huggingface.co/SwapnilS-15/qwen2.5-0.5b-instructv2-fc) · [live demo](https://huggingface.co/spaces/SwapnilS-15/toolcaller-demo) | A 0.5B function-calling model: QLoRA SFT on xLAM-60k, then DPO on its own mistakes. Served with vLLM behind a LangGraph gateway with guardrails. | `TRL` `Unsloth` `vLLM` `LangGraph` `Langfuse` |
| **[OKF](https://github.com/SwapnilS-15/OKF)** | A local multi-agent research assistant over 5 landmark AI papers. It gives cited answers, searches arXiv and writes reports. LangGraph agents talk over A2A + MCP, with guardrails and a streaming Chainlit UI. | `LangGraph` `A2A` `MCP` `Qdrant` `Postgres` |
| **[Enterprise-RAG](https://github.com/SwapnilS-15/Enterprise-RAG)** | Cited Q&A over PDF, DOCX and XLSX on a local model. It uses hybrid retrieval with ColBERT reranking, and an agent that routes between search, SQL and live tools. Traces, metrics and logs flow into Grafana. | `FastAPI` `Qdrant` `LangGraph` `Grafana` `MLflow` |
| **[PDFinsights](https://github.com/SwapnilS-15/PDFinsights)** | Local PDF question answering where every choice is measured, from retrieval to model selection. It has a streaming FastAPI backend and a Streamlit UI, and ships with Docker, Kubernetes manifests and CI. | `FastAPI` `ChromaDB` `Ollama` `DeepEval` `K8s` |

**In progress:** vision-language work with **SigLIP**, and **diffusion models**.

## Stack

**Models & training:** PyTorch · Transformers · TRL (SFT, DPO) · PEFT / LoRA / QLoRA · Unsloth
**LLM systems:** LangGraph · LangChain · MCP · A2A · vLLM · Ollama
**Retrieval:** Qdrant · ChromaDB · BM25 · ColBERT / cross-encoder reranking
**Evaluation & observability:** MLflow · DeepEval · Langfuse · Grafana (OpenTelemetry) · Prometheus
**Backend & deployment:** FastAPI · Postgres · Docker · Kubernetes · GitHub Actions
