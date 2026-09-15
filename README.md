# Thi Vinh Huy

**AI Engineer** — LLM workflow orchestration, retrieval systems, and agent evaluation.
Ho Chi Minh City, Vietnam. Open to roles in Vietnam or remote.

[![Email](https://img.shields.io/badge/Email-huythi121022%40gmail.com-333333?style=flat-square&logo=gmail&logoColor=white)](mailto:huythi121022@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-huytv122-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/huytv122/)

---

## About

I design and maintain **LLM workflows in production** — orchestrated chains of specialised LLM
calls with routing, retrieval, tool calling, and cost tracking, backed by deterministic code
wherever correctness matters more than fluency.

I have been an AI Engineer at **DFM Company since February 2025**, working on a
natural-language-to-3D-CAD system that is released and in active maintenance. I hold a B.Sc. in
Computer Science from the University of Information Technology (VNU-HCM) and began an M.Sc. there
in 2026, focusing on **evaluation and reliability of LLM agents for Vietnamese**.

Two convictions shape how I build:

**Deterministic code beats a confident model.** In the CAD system the LLM extracts parameters from
natural language, but the arithmetic runs in plain Python. When a retrieved rule has a mandatory
dependency the model forgot, code adds it back automatically. The model proposes; the code decides.

**A number you cannot reproduce is worse than no number.** I track cost and latency per chain, run
RAGAS on a golden set, trace every run through Langfuse, and use mutation testing because a green
test suite is not evidence. Most of what I have learned recently came from measurements that
contradicted my own design.

---

## Experience

### AI Engineer · DFM Company
**February 2025 – Present** · Text-to-CAD for sheet-metal manufacturing

A production system that turns a natural-language request into a 3D CAD model. One orchestrator
class coordinates roughly **ten specialised LLM chains** that share state: intent classification,
requirement analysis, manufacturability validation, RAG-based code generation, code editing,
step planning, shape-change detection, and clarification handling.

What I own and how it works:

| Area | Approach |
|---|---|
| **Orchestration** | Sequential chain composition over shared state, fully `async` with `asyncio.gather` fan-out and per-stage timing decorators |
| **Routing** | LLM-based intent classification returning structured JSON, branched in Python — not keyword rules |
| **Dual-context RAG** | Two deliberately **unmerged** retrieval paths — manufacturing rules and code examples — serving two different stages of generation |
| **Reranking** | Listwise LLM-as-judge: candidate previews and metadata go into one prompt; the model returns a ranking with scores and reasons. A smaller model reranks than generates |
| **Numeric safety** | The LLM extracts parameters; a pure-Python function computes the geometry. I do not let a language model do arithmetic |
| **Dependency safety net** | If a selected rule has a mandatory companion rule the model omitted, code re-inserts it before generation |
| **Ambiguity handling** | Every prompt carries a `missing_info` / `questions[]` contract so the system asks instead of guessing. On ambiguous edits the default is **add, never delete** |
| **Observability** | Per-chain token and cost accounting, plus latency percentiles and process-level resource monitoring |

Stack: LangChain · OpenAI API · FAISS · FastAPI · AWS S3 · Docker · FreeCAD

---

## Projects

### AuditFlow — agent for financial-statement tie-out
`in development` · Python · OpenAI API · Langfuse · pytest · mutation testing

An agent that cross-checks Vietnamese financial statements against the balance identities required
by Circular 200 — reading PDFs, including scanned ones via OCR, and deciding whether the numbers
reconcile or the case should be escalated to a human.

**Architecture.** A non-deterministic harness drives one LLM planner over **five contract-bound
tools** (`find_pages`, `read_pages`, `check_balance`, `report`, `escalate`) that wrap a fully
deterministic core. The boundary is the point: the planner chooses *what to look at*, while every
judgement about whether the books balance is made by code that behaves the same way every run.

**Engineering.** 318 passing tests, **41/41 mutants killed**, 53 commits. Every run is traced
through a self-hosted Langfuse instance. The whole repository is English-only after a deliberate
840-identifier refactor.

**What it actually taught me** — the findings that reversed my own decisions:

- A green suite proves very little. At one commit **242 passing tests** coexisted with five real
  bugs found by independent review, and mutation testing then exposed two more gaps that 263
  passing tests had missed. Both were tests passing for the wrong reason.
- The verifier was called at the *start* of the loop while extraction happened at the *end*, so
  OCR output — the only path that can read a scanned document — was never checked. The system was
  solving cases correctly and then reporting failure. Fixing the loop moved dev-set coverage from
  1/10 to 5/10, and none of that gain came from improving extraction.
- I measured the signal I was most confident in — the statutory form code — and it had only
  **60–80% recall**, partly because OCR reads `B01` as `BO1`. A cost optimisation projected to
  save 70–79% was built on that assumption, so I measured it and dropped it before writing code.
- The agent's action space contained exactly **one** element. It ranked hypotheses and then
  discarded the ranking, because nothing downstream could execute the action it chose. Naming that
  precisely was worth more than any feature I could have added that week.

### UIT Admission Chatbot — bilingual RAG assistant
`private repository` · LlamaIndex · Qdrant · OpenAI API · FastAPI · RAGAS · Langfuse

A Vietnamese/English admissions assistant combining retrieval with genuine OpenAI tool calling.

- **Function calling** with a required-tool contract across five tools — casual response, document
  search, admission-score lookup, and two major-filtering tools. One tool call per turn by design.
- **Query understanding** runs two mechanisms concurrently: conversational rewriting, which turns a
  context-dependent question into a standalone one, and **HyDE**, whose hypothetical passage is used
  only as a search query and never enters the answer context.
- **Speculative execution** — routing, query expansion, and retriever preload start together; once
  the router resolves, the branches that lost are cancelled.
- **Evaluation** with RAGAS (`faithfulness`, `answer_relevancy`) over a stored result set, and
  post-hoc faithfulness scoring on live traffic logged to Langfuse as measurement rather than as a
  blocking gate.
- **CI/CD** via GitHub Actions: tests gate the deployment push.

### ID Card Extraction Pipeline — document CV
`private repository` · YOLOv8 · Detectron2 · Tesseract OCR · OpenCV · FastAPI

Two-stage extraction for Vietnamese citizen ID cards: locate the card and its chip region, then
extract nine structured fields with a detection ensemble and OCR post-processing, served behind a
FastAPI endpoint.

> Both project repositories are private. I am happy to walk through the architecture, the code, and
> the failure cases in an interview.

---

## How I work

- **Test-driven, and sceptical of tests.** Red-green cycles, then mutation testing to check the
  tests themselves. "All tests pass" is a starting point for review, not a conclusion.
- **Measure before building.** Several features in AuditFlow were designed, measured, and dropped
  before any implementation, because the measurement removed the reason to build them.
- **Independent verification.** For anything that becomes a decision, I check it against a second
  independent source rather than trusting a single read.
- **Write down what failed.** Reversed decisions and wrong estimates are recorded with dates
  alongside the successes, because that record is what stops the same mistake twice.

---

## Stack

**LLM & orchestration** — LangChain · OpenAI API · function/tool calling · prompt contracts ·
LLM-as-judge reranking · speculative execution

**Retrieval** — Qdrant · FAISS · LlamaIndex · HyDE · query rewriting · dual-context retrieval

**Evaluation & observability** — RAGAS · Langfuse (self-hosted) · golden datasets · per-chain cost
and latency tracking · mutation testing · pytest

**Backend & infrastructure** — Python · FastAPI · async/await · Docker · GitHub Actions ·
GitLab CI/CD · AWS S3 · PostgreSQL · SQLite · Linux

**ML & document processing** — PyTorch · Transformers · YOLOv8 · Detectron2 · OpenCV ·
Tesseract OCR · PDF coordinate-based extraction

---

## Education & research

**M.Sc. Computer Science** — University of Information Technology, VNU-HCM · 2026 – present
Research direction: **evaluation and reliability of LLM agents for Vietnamese** — measuring whether
an agent's decisions are correct, not only whether its output looks right.

**B.Sc. Computer Science** — University of Information Technology, VNU-HCM · 2021 – 2025
Member, AI Club UIT.

---

<div align="center">

**Open to AI Engineer roles — Ho Chi Minh City or remote.**

[![Email](https://img.shields.io/badge/Email-333333?style=for-the-badge&logo=gmail&logoColor=white)](mailto:huythi121022@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/huytv122/)

</div>
