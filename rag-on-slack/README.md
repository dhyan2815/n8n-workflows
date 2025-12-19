# 📚 Chat with Document on Slack — RAG System

An end-to-end **Retrieval-Augmented Generation (RAG)** workflow built in **n8n** that allows users to upload documents in Slack and ask questions directly in the channel. The system ingests documents, stores semantic embeddings in Pinecone, and answers questions using Google Gemini — all automatically.

---

## ✨ What This Workflow Does

This workflow turns a Slack channel into an intelligent document assistant.

- Users upload PDF documents in Slack
- Documents are automatically processed, chunked, and embedded
- Embeddings are stored in Pinecone for semantic search
- Users ask questions in the same Slack channel
- The system retrieves relevant document context and answers accurately using RAG

No manual indexing. No copy-paste. No hallucinations.

---

## 🧠 Architecture Overview

The workflow is divided into **two clearly separated phases**, both handled by a **single Slack Event Subscription URL**.

### Phase 1 — Document Ingestion & Indexing
Triggered when a file is uploaded in Slack.

### Phase 2 — Retrieval & Question Answering
Triggered when a user posts a message (question) in Slack.

Routing between the two phases is handled internally inside n8n using conditional logic.

---

## 🔄 Phase 1 — Document Ingestion & Indexing

**Trigger Condition**
- Slack message event with `subtype = file_share`

**What Happens**
1. Slack detects a file upload in the channel
2. File metadata is fetched and the file is downloaded
3. PDF text is extracted and cleaned
4. Text is split into overlapping chunks
5. Metadata is attached to each chunk
6. Embeddings are generated using Google Gemini
7. Vectors are stored in Pinecone

**Outcome**
- The document becomes searchable knowledge for future questions

---

## 💬 Phase 2 — Retrieval & Question Answering (RAG)

**Trigger Condition**
- Slack message event without `file_share` subtype

**What Happens**
1. User question is cleaned and normalized
2. Query embedding is generated
3. Pinecone retrieves the most relevant document chunks (Top-K)
4. Retrieved chunks are injected as context
5. Google Gemini generates an answer using only the retrieved context
6. The answer is sent back to Slack

**Outcome**
- Accurate, document-grounded answers inside Slack

---

## 🛠 Tech Stack

- **Workflow Engine:** n8n
- **Vector Database:** Pinecone
- **Embeddings:** Google Gemini
- **LLM:** Google Gemini
- **Integration Layer:** Slack Events API
- **Parsing:** PDF text extraction
- **Approach:** Retrieval-Augmented Generation (RAG)

---

## 🔐 Security & Safety

- Uses a **single Slack Request URL** (Slack-compliant)
- Credentials are managed securely via n8n Credentials
- No raw documents or API keys are exposed in responses
- Bot messages are ignored to prevent infinite loops
- Answers are generated **only from retrieved document context**

---

## ✅ Key Design Decisions

- **Single Slack Trigger** with internal routing (recommended Slack pattern)
- File uploads handled via `message + file_share subtype`
- No reliance on unreliable `file_shared` Slack events
- Strict context-only answering to avoid hallucinations
- Clean separation between ingestion and Q&A logic

---

## 📦 Workflow Contents

The workflow includes:
- Slack Trigger (single entry point)
- Conditional routing (file vs question)
- PDF ingestion pipeline
- Vector indexing pipeline
- Semantic retrieval pipeline
- RAG question-answering chain
- Slack response delivery

---

## 🚀 How to Use

1. Import the workflow JSON into n8n
2. Configure credentials:
   - Slack
   - Pinecone
   - Google Gemini
3. Set the Slack Event Subscription URL to the Slack Trigger webhook
4. Upload a PDF in the configured Slack channel
5. Ask questions in the same channel

That’s it.

---

## 🧩 Possible Extensions

- File-scoped Q&A (answer only from latest upload)
- Thread-based replies
- Multiple document namespaces
- User-specific memory
- Telegram / WhatsApp integration

---

## 📌 Final Note

This workflow is designed to be:
- **Slack-native**
- **Production-safe**
- **Easily extensible**
- **Free from prompt hacks**

If you understand this README, you understand the workflow.

Happy building 🚀
