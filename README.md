<div align="center">

# Thi Vinh Huy

**AI Engineer** · Multi-agent LLM systems & production RAG

Retrieval precision · Reasoning accuracy · Output verifiability

[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:huythi121022@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/YOUR-HANDLE)
[![Location](https://img.shields.io/badge/Ho_Chi_Minh_City-1A2E4A?style=flat-square&logo=googlemaps&logoColor=white)](#)

</div>

---

## What I work on

I build LLM systems where **being wrong is expensive** — so most of my work is the part
that decides whether an answer is good enough to return.

```
Query ──▶ Router ──▶ Hybrid Retriever ──▶ Reranker ──▶ Generator ──▶ Answer
             │         (BM25 + dense)       (LLM)          │
             └──────────── Confidence gate ◀───────────────┘
                           (retry / escalate / refuse)
```

Three things I care about, in order:

- **Retrieval beats prompting.** Most "hallucination" is a retrieval miss wearing a costume.
- **A system that can't say "I don't know" isn't production-ready.** Confidence gates, not vibes.
- **If it isn't measured, it didn't improve.** RAGAS, golden sets, tracing on every change.

---

## Currently

- **AuditFlow** — multi-agent system for audit document review. Verifier design where
  trust is *inversely* proportional to LLM involvement.
- **M.Sc. Computer Science, UIT — VNU-HCM** (from 2026). Research direction: retrieval
  precision and citation-grounded generation for Vietnamese.

---

## Production

### Tolery API AI — DFM Company · *Feb 2025 – Present*

**Natural language (EN/FR/VI) → 3D CAD models.** Multi-agent, 100+ concurrent users.

- Centralized decision engine routing across parallel async agents
- Dual-context FAISS retrieval + LLM query expansion + LLM reranking
- Self-healing code loop: detects execution error → patches → re-runs
- SSE streaming, JWT auth, deployed on Docker + GitLab CI/CD

---

## Selected projects

### UIT Admission Chatbot — Multi-agent RAG

`LlamaIndex` · `Elasticsearch` · `GPT-4o` · `FastAPI` · `LangSmith` · `RAGAS` · `AWS`

> 🔗 **[View repository →](https://github.com/vinhhuy12/REPO-NAME)**

**End-to-end latency 14s → 8s (−40%)** by running routing, query expansion, and retriever
pre-load concurrently instead of in sequence — speculative execution, discard the loser.

| | |
|---|---|
| **Faithfulness floor** | ≥ 0.6, enforced at serve time — below it, the answer is not returned |
| **Reranking** | GPT-4o-mini reranker tuned for Vietnamese semantics — no local model, no RAM cost |
| **Conversation** | Intent detection + bilingual reply in a **single** LLM call |
| **Evaluation** | 4-metric RAGAS pipeline over a golden set (15+ Q&A, Easy/Medium/Hard) |
| **Observability** | Full LangSmith tracing, automated report generation |

---

### ID Card Extraction Pipeline — Computer Vision

`YOLOv8` · `Detectron2` · `Tesseract OCR` · `OpenCV` · `FastAPI`

> 🔗 **[View repository →](https://github.com/vinhhuy12/REPO-NAME)**

Two-stage pipeline: CCCD chip detection, then 9-class field extraction via a YOLO ensemble
with OCR post-processing.

**94% field-level accuracy** · manual entry **3 min → 5 sec** per card (−96%)

---

## Stack

**Daily** — Python · FastAPI · LlamaIndex · OpenAI API · Elasticsearch · FAISS · RAGAS · LangSmith · Docker

**Comfortable** — LangChain · PyTorch · HuggingFace · pgvector · SQLAlchemy · AWS (RDS/S3) · GitLab CI/CD · Linux

**Have shipped with** — TensorFlow · YOLO · Detectron2 · OpenCV · Tesseract

---

## Education

**B.Sc. Computer Science** — University of Information Technology, VNU-HCM · 2021–2025
GPA 3.0/4.0 · TOEIC 600 (L&R) · Member, AI Club UIT

<div align="center">

<br>

*Open to AI Engineer roles — Ho Chi Minh City or remote.*

</div>
