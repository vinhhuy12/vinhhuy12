<div align="center">

```
╔══════════════════════════════════════════════════════════════╗
║                                                              ║
║        T H I   V I N H   H U Y                              ║
║        AI Engineer  ·  RAG / LLM Systems                    ║
║        Building things that think                           ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

[![Gmail](https://img.shields.io/badge/huythi121022%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:huythi121022@gmail.com)
[![Location](https://img.shields.io/badge/Ho_Chi_Minh_City-1A2E4A?style=flat-square&logo=googlemaps&logoColor=white)]()
[![Phone](https://img.shields.io/badge/(+84)_333_670_249-25D366?style=flat-square&logo=whatsapp&logoColor=white)]()

</div>

---

## 🧠 What I build

I design and ship **multi-agent LLM systems** and **production RAG pipelines** — not demos, real systems serving real users.

```
Natural Language  →  [Multi-Agent Orchestrator]  →  Structured Output
                            ↕
              [Hybrid Retriever]  ·  [LLM Reranker]
              [Confidence Gate]   ·  [Self-Healing Loop]
```

**Current focus:** Legal AI — retrieval precision, citation-grounded generation, Vietnamese NLP.

---

## 🚀 Production Work

### Tolery API AI · DFM Company *(Feb 2025 – Present)*
> Multi-agent system: natural language (EN/FR/VI) → 3D CAD models

- Centralized decision engine routing across parallel async agents
- Dual-context FAISS retrieval + LLM query expansion + LLM-based reranking
- Self-healing code loop: auto-detects error → patches → re-executes
- 100+ concurrent users · SSE streaming · JWT auth

---

## 📦 Notable Projects

### [UIT Admission Chatbot](https://github.com/vinhhuy12) — Multi-Agent RAG
`LlamaIndex` `Elasticsearch` `GPT-4o` `FastAPI` `LangSmith` `RAGAS` `AWS`

| Metric | Result |
|--------|--------|
| Latency | 14s → **8s** (−40%) |
| Faithfulness guard | ≥ 0.6 |
| Evaluation | 4-metric RAGAS pipeline |
| Observability | Full LangSmith tracing |

- Parallel speculative execution: routing + query expansion + retriever pre-load run concurrently
- LLM-based reranker (GPT-4o-mini) tuned for Vietnamese semantics, zero RAM overhead
- Bilingual ConversationAgent: intent detection + reply in a **single LLM call**
- Golden eval dataset (15+ Q&A, Easy/Medium/Hard) with automated report generation

---

### ID Card Extraction Pipeline — Computer Vision
`YOLOv8` `Detectron2` `Tesseract OCR` `OpenCV` `FastAPI`

| Metric | Result |
|--------|--------|
| Accuracy | **94%** field extraction |
| Speed | 3 min → **5 sec** (−96%) |

Two-stage: CCCD chip detection → 9-class field extraction via YOLO ensemble + OCR post-processing.

---

## 🛠 Tech Stack

```yaml
RAG / Retrieval:   LlamaIndex · Elasticsearch · FAISS · BM25 + Dense Vector · Reranking
LLM:               OpenAI API · GPT-4o · HuggingFace · LangChain · LangSmith
Evaluation:        RAGAS · Faithfulness · Answer Relevancy · Golden Datasets
Backend:           Python · FastAPI · SQLAlchemy · RESTful API
ML / CV:           PyTorch · TensorFlow · YOLO · OpenCV · Transformers
Infrastructure:    Docker · GitLab CI/CD · AWS RDS/S3 · Linux
Databases:         FAISS · Elasticsearch · pgvector
```

---

## 🎓 Education

**University of Information Technology — VNU-HCM**
B.Sc. Computer Science · GPA 3.0/4.0 · 2021–2025
TOEIC 600 (L&R) · Member, AI Club UIT

---

<div align="center">

*"Retrieval precision, reasoning accuracy, output verifiability — that's the bar."*

</div>
