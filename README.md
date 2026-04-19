# ⚙️ Automation Workflows – n8n Collection

This repository contains a curated collection of **production-ready AI automation workflows** built using **n8n**, **Gemini**, **Google APIs**, **Pinecone**, and other modern tooling.  
Each workflow lives in its own sub-folder with a dedicated README, architecture diagram, and the exported n8n `.json` file.

The goal of this repository is simple:  
**Modular, reusable, real-world AI systems — ready for deployment.**

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
| AI Agent | LangChain |
| Research Ideas | Tavily |
| Web Scraping | Firecrawl |
| Notion Database | Content Reader |

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
- Tavily Access Token (for research ideas)
- X Access Token (for creating media posts on X)
- LinkedIn OAuth2 (for creating posts on LinkedIn)
- Notion Integration Internal Secret (for Notion database and page content access)
- Telegram Access Token (for telegram-facing operations)

Each workflow's README contains step-by-step setup instructions.

---

## 📋 Workflow Orchestrated

| Feature | Daily Briefing | RAG Chatbot | Talk with Sheets | Chat with Sheets (Telegram) | Chat with Doc on Slack | Social Media Publishing Agent | Job Application Tracker Agent | RAG Doc Chatbot v2 |
|---------|---------------|-------------|------------------|----------------------------|-------|------|----------|-------------------|
| **Interface** | Email | n8n Chat | Telegram/n8n Chat | Telegram Only | Slack | n8n | Telegram | Telegram |
| **Data Source** | NewsAPI | Google Drive | Google Sheets | Google Sheets | File | Sheets | Notion | Google Drive |
| **LLM** | G-2.5 Flash | G-2.5 Flash | G-2.5 Flash | G-2.5 Flash | G-2.5 Flash | G-2.5 Flash | G-2.5 Flash/Mimo-v2-flash | G-2.5 Pro |
| **Read/Write** | Read Only | Read Only | Read Only | Read Only | Read Only | Read-Write | Read-Write | Read Only |
| **Automation** | Scheduled | On-Demand | On-Demand | On-Demand | On-Demand | On-Demand | On-Demand | Scheduled + On-Demand |

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