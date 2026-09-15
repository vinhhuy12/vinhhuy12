<div align="center">
  <img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=0,2,2,5,30&height=220&section=header&text=Thi%20Vinh%20Huy&fontSize=54&fontColor=ffffff&animation=fadeIn&fontAlignY=34&desc=AI%20Engineer%20%C2%B7%20Multi-Agent%20LLM%20%26%20Production%20RAG&descAlignY=54&descSize=18" />
</div>

<div align="center">
  <a href="https://github.com/vinhhuy12">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1200&color=58A6FF&center=true&vCenter=true&width=680&lines=I+build+LLM+systems+where+being+wrong+is+expensive.;Retrieval+precision+%3E+prompt+engineering.;Currently+shipping+multi-agent+RAG+at+DFM+Company." alt="Typing SVG" />
  </a>
</div>

<div align="center">

[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:huythi121022@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/YOUR-HANDLE)
[![Portfolio](https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://YOUR-SITE.com)
[![Location](https://img.shields.io/badge/Ho_Chi_Minh_City-4285F4?style=for-the-badge&logo=googlemaps&logoColor=white)](#)

<img src="https://komarev.com/ghpvc/?username=vinhhuy12&style=for-the-badge&color=58A6FF&label=PROFILE+VIEWS" alt="views" />

</div>

<br>

## 👋 Về tôi / About me

<img align="right" width="380" src="https://user-images.githubusercontent.com/74038190/229223263-cf2e4b07-2615-4f87-9c38-e37600f8381a.gif" />

```yaml
name:      Thi Vinh Huy
role:      AI Engineer @ DFM Company
based_in:  Ho Chi Minh City, Vietnam
focus:     Multi-agent orchestration · RAG · Vietnamese NLP
next:      M.Sc. Computer Science @ UIT - VNU-HCM (2026)
```

- 🔭 **Hiện tại** — xây hệ multi-agent biến ngôn ngữ tự nhiên (EN/FR/VI) thành **mô hình CAD 3D**, phục vụ 100+ người dùng đồng thời.
- 🧠 **Tôi làm gì** — tôi không ghép prompt. Tôi thiết kế phần *quyết định xem câu trả lời có đủ tốt để trả về hay không*: hybrid retrieval, LLM reranking, confidence gate, self-healing loop.
- 🌱 **Đang học** — LLM self-hosting, agent evaluation, và chuẩn bị hướng nghiên cứu Thạc sĩ: **citation-grounded generation cho tiếng Việt**.
- 💬 **Hỏi tôi về** — RAG chạy thật trong production, vì sao chatbot của bạn "ảo giác", cách đo chất lượng agent bằng số thay vì cảm tính.
- ⚡ **Niềm tin nghề nghiệp** — *phần lớn "hallucination" chỉ là một cú trượt retrieval đội lốt.*

<br clear="right"/>

---

## 🏗️ Hệ thống tôi xây trông như thế nào

```mermaid
flowchart LR
    Q([User Query]) --> R{Router<br/>Agent}
    R --> QE[Query<br/>Expansion]
    R --> HR[Hybrid Retriever<br/>BM25 + Dense]
    QE --> HR
    HR --> RR[LLM Reranker<br/>GPT-4o-mini]
    RR --> G[Generator]
    G --> CG{Confidence<br/>Gate}
    CG -->|faithfulness ≥ 0.6| A([Grounded Answer])
    CG -->|too low| R
    CG -->|no evidence| REF([Refuse to answer])

    style Q fill:#1f6feb,stroke:#58a6ff,color:#fff
    style A fill:#238636,stroke:#3fb950,color:#fff
    style REF fill:#9e6a03,stroke:#d29922,color:#fff
    style CG fill:#8957e5,stroke:#a371f7,color:#fff
    style R fill:#1f2937,stroke:#58a6ff,color:#fff
```

> **Vòng lặp ngược mới là phần khó.** Một hệ thống không biết nói *"tôi không biết"* thì chưa sẵn sàng cho production.

---

## 💼 Kinh nghiệm / Experience

<table>
<tr>
<td width="130" align="center" valign="top">
<br>
<img src="https://img.shields.io/badge/Feb_2025-Present-238636?style=flat-square" /><br><br>
<b>AI<br>Engineer</b>
</td>
<td valign="top">

### Tolery API AI — **DFM Company**

Hệ multi-agent chuyển **ngôn ngữ tự nhiên → mô hình CAD 3D**, đa ngôn ngữ EN/FR/VI.

| Tôi đóng góp gì | Kết quả |
|---|---|
| Decision engine điều phối các agent async chạy song song | 100+ concurrent users |
| Dual-context FAISS retrieval + LLM query expansion + reranking | Truy hồi đúng ngữ cảnh kỹ thuật |
| **Self-healing loop**: phát hiện lỗi thực thi → tự vá → chạy lại | Giảm can thiệp thủ công |
| SSE streaming + JWT auth, deploy Docker + GitLab CI/CD | Phản hồi real-time |

</td>
</tr>
</table>

---

## 🚀 Dự án / Projects

<table>
<tr>
<td width="50%" valign="top">

### 🎓 UIT Admission Chatbot
**Multi-Agent RAG · Song ngữ**

[![Repo](https://img.shields.io/badge/View_Repo-171515?style=flat-square&logo=github)](https://github.com/vinhhuy12/REPO-NAME)

Chatbot tư vấn tuyển sinh, kiến trúc multi-agent với cổng kiểm chứng trước khi trả lời.

**⚡ Latency 14s → 8s (−40%)**

Chạy song song *speculative*: routing + query expansion + preload retriever cùng lúc, bỏ nhánh thua.

| | |
|---|---|
| Faithfulness | **≥ 0.6** enforced tại serve-time |
| Reranker | GPT-4o-mini cho tiếng Việt, **0 RAM** |
| Conversation | Intent + trả lời song ngữ trong **1 LLM call** |
| Eval | RAGAS 4 metric · golden set 15+ Q&A |
| Trace | LangSmith full tracing |

`LlamaIndex` `Elasticsearch` `GPT-4o` `FastAPI` `RAGAS` `AWS`

</td>
<td width="50%" valign="top">

### 🪪 ID Card Extraction Pipeline
**Computer Vision · OCR**

[![Repo](https://img.shields.io/badge/View_Repo-171515?style=flat-square&logo=github)](https://github.com/vinhhuy12/REPO-NAME)

Pipeline 2 tầng đọc CCCD: phát hiện chip → trích xuất 9 trường thông tin.

**🎯 94% accuracy · 3 phút → 5 giây (−96%)**

Thay thế hoàn toàn khâu nhập liệu thủ công.

| | |
|---|---|
| Tầng 1 | Detect chip CCCD |
| Tầng 2 | YOLO ensemble, 9-class field |
| Hậu xử lý | OCR correction + validation |
| Phục vụ | FastAPI endpoint |

`YOLOv8` `Detectron2` `Tesseract` `OpenCV` `FastAPI`

<br>

### 🧾 AuditFlow `đang làm`
**Multi-agent audit review**

Hệ agent rà soát hồ sơ kiểm toán. Nguyên tắc thiết kế: **độ tin cậy tỉ lệ nghịch với mức độ LLM tham gia.**

</td>
</tr>
</table>

---

## 🛠️ Công nghệ / Tech Stack

<div align="center">

**Dùng hằng ngày**

<img src="https://skillicons.dev/icons?i=py,fastapi,docker,elasticsearch,postgres,aws,git,linux&theme=dark" />

![LlamaIndex](https://img.shields.io/badge/LlamaIndex-8A2BE2?style=flat-square)
![OpenAI](https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-0467DF?style=flat-square&logo=meta&logoColor=white)
![LangSmith](https://img.shields.io/badge/LangSmith-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![RAGAS](https://img.shields.io/badge/RAGAS-FF6F00?style=flat-square)

**Thành thạo**

<img src="https://skillicons.dev/icons?i=pytorch,tensorflow,flask,mysql,github,gitlab,vscode,anaconda&theme=dark" />

![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![pgvector](https://img.shields.io/badge/pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![YOLO](https://img.shields.io/badge/YOLOv8-00FFFF?style=flat-square&logo=yolo&logoColor=black)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)

</div>

---

## 📊 Thống kê GitHub

<div align="center">

<img width="49%" src="https://github-readme-stats.vercel.app/api?username=vinhhuy12&show_icons=true&count_private=true&include_all_commits=true&hide_border=true&theme=tokyonight&title_color=58A6FF&icon_color=58A6FF&cache_seconds=86400" />
<img width="41%" src="https://streak-stats.demolab.com?user=vinhhuy12&hide_border=true&theme=tokyonight&ring=58A6FF&fire=58A6FF&currStreakLabel=58A6FF" />

<img width="41%" src="https://github-readme-stats.vercel.app/api/top-langs/?username=vinhhuy12&layout=compact&langs_count=8&hide_border=true&theme=tokyonight&title_color=58A6FF&cache_seconds=86400" />

<br><br>

<img width="92%" src="https://github-readme-activity-graph.vercel.app/graph?username=vinhhuy12&theme=tokyo-night&hide_border=true&area=true&color=58A6FF&line=58A6FF&point=ffffff" />

<img width="92%" src="https://github-profile-trophy.vercel.app/?username=vinhhuy12&theme=tokyonight&no-frame=true&no-bg=true&column=7&margin-w=8&margin-h=8" />

</div>

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/vinhhuy12/vinhhuy12/output/github-contribution-grid-snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/vinhhuy12/vinhhuy12/output/github-contribution-grid-snake.svg" />
    <img alt="contribution snake" src="https://raw.githubusercontent.com/vinhhuy12/vinhhuy12/output/github-contribution-grid-snake.svg" />
  </picture>
</div>

---

## 🎓 Học vấn / Education

<table>
<tr>
<td align="center" width="50%">

### M.Sc. Computer Science
**UIT — VNU-HCM** · `2026 →`

Hướng nghiên cứu: retrieval precision &
citation-grounded generation cho tiếng Việt

</td>
<td align="center" width="50%">

### B.Sc. Computer Science
**UIT — VNU-HCM** · `2021 – 2025`

GPA 3.0/4.0 · TOEIC 600 (L&R)
Thành viên **AI Club UIT**

</td>
</tr>
</table>

---

<div align="center">

### 💬 Đang mở cơ hội **AI Engineer** — TP.HCM hoặc remote

[![Email](https://img.shields.io/badge/Liên_hệ_Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:huythi121022@gmail.com)
[![LinkedIn](https://img.shields.io/badge/Kết_nối_LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/YOUR-HANDLE)

<br>

> *"Retrieval precision, reasoning accuracy, output verifiability — that's the bar."*

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=0,2,2,5,30&height=120&section=footer" />

</div>
