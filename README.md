# enrollment-buddy-pup

---

# 🎓 PUP Enrollment System Buddy  
*AI-Powered Enrollment Assistant Built with Langflow Playground*

An AI-driven conversational assistant designed to help students navigate the Polytechnic University of the Philippines (PUP) enrollment process.

This project was built entirely using **:contentReference[oaicite:0]{index=0} Playground** and powered by **:contentReference[oaicite:1]{index=1}**.

# 🎓 PUP Enrollment Buddy  
### RAG-Based AI Assistant Built with Langflow

An AI-powered enrollment assistant designed to guide students through the Polytechnic University of the Philippines (PUP) admission and enrollment process.

This system was built using **:contentReference[oaicite:0]{index=0} Playground**, powered by **:contentReference[oaicite:1]{index=1}**, and enhanced with Retrieval-Augmented Generation (RAG) using **:contentReference[oaicite:2]{index=2}**.

The entire architecture was created visually in Langflow — no traditional backend codebase required.

---

# 📌 Overview

The **PUP Enrollment Buddy** is a personalized AI assistant that:

- Answers admission and enrollment questions  
- Grounds responses in official PUP admission documents  
- Maintains session-based memory  
- Personalizes responses using student identity  
- Prevents hallucination through strict RAG grounding  

This project demonstrates how modern LLM systems can be built using visual orchestration tools.

---

# 🏗️ System Architecture

The system follows a **RAG (Retrieval-Augmented Generation)** architecture:

User
↓
Chat Input
↓
Astra DB (Vector Search)
↓
Parser (Context Formatter)
↓
Prompt Template
↓
Gemini 2.5 Flash Lite
↓
Chat Output


---

## 🧠 Core Components

### 1️⃣ Identity Layer
- **Text Input Node** → Acts as Global Student ID  
- Binds session history to a specific student  

### 2️⃣ Memory Layer
- **Message History Node**
- Stores conversation using Session ID
- Enables contextual follow-up questions  

### 3️⃣ Retrieval Layer (RAG)
- **Read File Node** → Upload PUP Admission PDF  
- **Split Text Node** → Chunking (1000 size / 200 overlap)  
- **Gemini Embeddings (`models/gemini-embedding-001`)**
- **Astra DB Vector Store**
  - Collection: `requirements_vector`
  - Dimension: 768  

### 4️⃣ Reasoning Layer
- **Prompt Template**
  - Structured persona
  - Context injection `{context}`
  - Memory injection `{history}`
  - Personalization `{student_name}`
- **Gemini 2.5 Flash Lite**
  - Fast inference
  - Lightweight model ideal for workshop/demo scale  

### 5️⃣ Output Layer
- **Chat Output Node**
  - Custom AI sender name (e.g., "PUP Buddy")
  - Structured responses (bullet points, bold deadlines)

---

# 🔄 Workflow Logic

## Document Ingestion Flow
Read File → Split Text → Gemini Embeddings → Astra DB (Ingest)

## Retrieval Flow
Chat Input → Astra DB (Search Query)
Astra DB → Parser → Prompt Template ({context})


## Generation Flow
Prompt Template → Gemini 2.5 Flash Lite → Chat Output


---

# ⚙️ Technology Stack

| Layer | Tool |
|-------|------|
| LLM Orchestration | :contentReference[oaicite:3]{index=3} |
| Language Model | :contentReference[oaicite:4]{index=4} |
| Embeddings | Gemini Embedding Model (`gemini-embedding-001`) |
| Vector Database | :contentReference[oaicite:5]{index=5} |
| Hosting Option | DataStax Cloud or Local Langflow |

---

# 🛡️ Guardrails & Prompt Engineering

The system uses:

- Grounded-only answering policy  
- Strict context usage  
- Structured formatting instructions  
- Anti-hallucination rules  
- Personalized addressing of student  

If information is not found in context, the assistant directs users to coordinate with the Admissions Office.

---

# 🎯 Use Case

This project is ideal for:

- Academic demonstrations  
- AI workshop showcases  
- University helpdesk automation prototypes  
- RAG architecture learning  
- LLM workflow engineering practice  

---

# ⚠️ Disclaimer

This project is for academic and demonstration purposes only.  
It is not officially affiliated with the Polytechnic University of the Philippines (PUP).

---

# 🧩 Future Improvements

- Deployment as a web chatbot  
- Role-based access (Freshman / Transferee / Graduate)  
- Intent classification routing  
- Analytics dashboard for frequently asked questions  
- Multi-document ingestion pipeline  

---

Built as part of a Langflow AI Workshop demonstrating practical RAG architecture using modern LLM tooling.

