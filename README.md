# ⚙️ Automation Workflows – n8n Collection

This repository contains a curated collection of **production-ready AI automation workflows** built using **n8n**, **Gemini**, **Google APIs**, **Pinecone**, and other modern tooling.  
Each workflow lives in its own sub-folder with a dedicated README, architecture diagram, and the exported n8n `.json` file.

The goal of this repository is simple:  
**Modular, reusable, real-world AI systems — ready for deployment.**

---

## 📁 Repository Structure
```
/
├── Daily-AI-Briefing/
│   ├── README.md
│   ├── workflow.json
│   └── assets/
│
├── RAG-Chatbot/
│   ├── README.md
│   ├── workflow.json
│   └── assets/
│
├── Talk-with-Sheets/
│   ├── README.md
│   ├── workflow.json
│   └── assets/
│
└── Chat-with-Sheets-via-Telegram/
    ├── README.md
    ├── workflow.json
    └── assets/
```

Each folder includes:
- the workflow export (`workflow.json`)
- a dedicated README with architecture details  
- optional diagrams under `/assets`

---

## 🚀 Workflows Included

### **1. 📰 Daily AI Briefing**
Automates a full AI-powered news briefing pipeline:
- Fetches latest AI news via NewsAPI  
- Summarizes using **Google Gemini**  
- Converts markdown → HTML  
- Sends automated daily emails via Gmail  

**Useful for:**
- AI news reporting  
- Daily brief generation  
- Automated content summarization  

---

### **2. 📚 RAG Chatbot – Internal Document QA**
A full Retrieval-Augmented Generation (RAG) system using:
- Google Drive document ingestion  
- Recursive text splitting  
- Gemini embeddings  
- Pinecone vector store (index + retrieval)  
- LangChain Agent with retrieval tool  
- Conversational memory  

**Useful for:**
- Internal knowledge assistants  
- Company documentation chatbot  
- Enterprise search systems  

---

### **3. 📊 Talk with Google Sheets**
A hybrid chatbot capable of:
- General conversation  
- On-the-fly Google Sheets data analysis  
- Telegram + n8n Chat integration  
- Sheet row formatting + structured analysis  
- AI Agent using Gemini with strict reasoning rules  

**Useful for:**
- Spreadsheet analytics via chat  
- Team dashboards  
- Chat-driven reporting and lookup  

---

### **4. 🤖 Chat with Google Sheets via Telegram**
A Telegram-based conversational interface for Google Sheets analytics:
- Accepts messages exclusively through Telegram bot
- Fetches and formats spreadsheet rows into AI-readable structured text
- Uses Gemini-powered AI Agent with strict behavioral rules
- Distinguishes between general chat and sheet-specific queries
- **Read-only analytics** – does not modify spreadsheet data
- Row-level referencing using actual row numbers
- Automatic handling of empty or insufficient data

**Workflow Architecture:**
1. Telegram Trigger → receives user messages
2. Google Sheets Get Row(s) → fetches spreadsheet data
3. Merge Node → synchronizes message and sheet data
4. JavaScript Code Node → formats data and extracts question
5. AI Agent (LangChain) → enforces behavioral rules
6. Gemini Chat Model → generates intelligent responses
7. Telegram Send Message → replies to user

**Key Constraints:**
- Limited to ~50 rows per query (token control)
- Single sheet support only
- No hallucinations or assumptions
- Strict data-only analysis

**Useful for:**
- Natural language spreadsheet queries
- Team data lookup via Telegram
- Quick analytics without opening sheets
- Conversational data exploration

---

## 🧠 Tech Stack

| Category | Tools |
|---------|--------|
| Workflow Automation | n8n |
| LLM / Summarization / QA | Google Gemini |
| Vector Database (RAG) | Pinecone |
| File Storage | Google Drive |
| Spreadsheet Ops | Google Sheets |
| Messaging | Telegram + n8n Chat |
| Logic | JavaScript (n8n Code nodes) |
| AI Framework | LangChain |

---

## 🎯 Purpose

This repository is meant to serve as:
- A **portfolio** of real AI automation systems  
- A **reference library** for workflows and patterns  
- A **plug-and-play collection** for building complex AI agents and pipelines  
- A **learning resource** for anyone working with n8n + AI  

Each workflow is intentionally **modular**, **maintainable**, and **self-contained**.

---

## 🔧 Setup Requirements

Before using any workflow, ensure you have:

- n8n Cloud account **or** self-hosted instance  
- Google API credentials (Sheets, Drive, Gmail depending on workflow)  
- Gemini API key  
- Pinecone account (for RAG workflows)  
- Telegram Bot token (for chat-based workflows)  
- NewsAPI key (for briefing workflow)

Each workflow's README contains step-by-step setup instructions.

---

## 📋 Workflow Comparison

| Feature | Daily Briefing | RAG Chatbot | Talk with Sheets | Chat with Sheets (Telegram) |
|---------|---------------|-------------|------------------|----------------------------|
| **Interface** | Email | n8n Chat | Telegram/n8n Chat | Telegram Only |
| **Data Source** | NewsAPI | Google Drive | Google Sheets | Google Sheets |
| **LLM** | Gemini | Gemini | Gemini | Gemini |
| **Read/Write** | Read Only | Read Only | Read Only | Read Only |
| **Automation** | Scheduled | On-Demand | On-Demand | On-Demand |

---

## 👤 Author

**Dhyan Patel**  
AI/ML Engineering • Automation Systems • Workflow Design  
🔗 [LinkedIn](https://linkedin.com/in/dhyan2815) 🔗 [GitHub](https://github.com/dhyan2815)

---

## ⭐ Feedback & Contributions

Feel free to open issues, suggest improvements, or request new automation workflows.  
This repository will continue expanding with more AI-driven systems.

---