# 📊 Talk with Google Sheets 

This repository contains a conversational AI workflow built with **n8n**, allowing users to **query a Google Sheet in natural language** while also supporting **general conversational replies**. It works with both **n8n Chat** and **Telegram**, automatically merges sheet data with chat input, formats it, and passes it to a Gemini-powered AI Agent.

---

## 📋 Overview

The workflow fetches rows from Google Sheets, extracts a user’s chat message, formats all sheet data into readable text, and sends everything to an **AI Agent** that can:

- Respond as a friendly assistant
- Perform data analysis on the sheet
- Tell the user when the sheet is empty or missing required info
- Reply back via Telegram or n8n chat

### 🔧 Key Capabilities

- Dual chat-input support: **Telegram** + **n8n Chat Trigger**
- Fetches rows from a connected Google Sheet
- Converts sheet data into structured analysis text
- Uses Gemini LLM + LangChain Agent with system rules
- Supports conversation memory
- Responds back directly to Telegram users
- Automatically merges multi-source data (sheet + chat)

---

## 🏗️ Workflow Architecture

<img src="./assets/workflow.png" alt="AI Workflow Architecture" width="700"/>

### High-Level Flow

1. **Chat Trigger + Telegram Trigger**  
   Accepts user messages from either source. 
2. **Get Rows in Sheet (Google Sheets)**  
   Fetches all rows from the spreadsheet (up to ~65 rows).
3. **Merge Node (Append / Wait for both)**  
   Combines chat message + sheet rows into two clean arrays.  
4. **JavaScript Code Node**  
   - Detects whether message came from Telegram or n8n chat  
   - Extracts chatId (for Telegram replies)  
   - Formats sheet data into readable blocks  
   - Outputs: `userQuestion`, `sheetData`, `rowCount`, `chatId`   
5. **AI Agent (Gemini)**  
   System message enforces strict rules:  
   - Friendly assistant for general chat  
   - Analytical mode for sheet-related queries  
   - Uses only provided sheet data  
   - States limitations if data is missing  
   - Produces concise, factual replies  
6. **Simple Memory (Window Memory)**  
   Keeps recent conversation context.  
7. **Gemini Chat Model**  
   LLM powering the agent.  
8. **Telegram Send Message**  
   Sends the AI response back to the Telegram 

---

## 🧩 Workflow Nodes

| Node | Description |
|------|-------------|
| **Chat Trigger** | Receives chat messages via n8n’s native chat interface |
| **Telegram Trigger** | Receives user messages from Telegram bot |
| **Google Sheets – Get Rows** | Fetches sheet data for analysis |
| **Merge Node** | Combines sheet rows + chat input |
| **JavaScript Code Node** | Formats sheet data, extracts message text, prepares agent input |
| **Gemini Chat Model** | LLM used to generate outputs |
| **AI Agent** | Applies sheet-analysis rules + general chat handling |
| **Simple Memory** | Enables short-session conversational memory |
| **Telegram Send Message** | Replies back in Telegram |

(All derived directly from workflow JSON: :contentReference[oaicite:6]{index=6})

---

## 🤖 AI Logic Summary

The AI Agent follows strict logic:

- If the user says:  
  **“Hi”, “How are you?”, “Who are you?”** → respond normally as a conversational assistant.

- If the user asks something like:  
  **“What’s the total in column X?”  
  “Show me row 12”  
  “Which entries have status = pending?”**  
  → analyze **only the provided sheetData**.

- If sheet lacks info:  
  **“The sheet does not contain the information needed for this question.”**

- If sheet is empty:  
  **“The sheet is empty.”**

Every answer stays:  
✔ concise  
✔ factual  
✔ based on sheet rows or general chat  
✔ never hallucinated

---

## 💬 Supported Integrations

### **n8n Chat**
- Works instantly inside n8n UI  
- No IDs or reply routing needed

### **Telegram Bot**
- Extracts user question  
- Stores chatId  
- Replies back with final AI answer

---

## 📁 Repository Structure

```
Talk-with-Sheets/
│
├── workflow.json
├── assets/
│   └── workflow.png
└── README.md
```

---

## 🚀 Results

- Query a Google Sheet like a real database  
- Users can talk through Telegram or n8n Chat  
- Sheet automatically converted to human-readable format  
- Hybrid chatbot: general conversation + spreadsheet analytics  
- Zero hallucinations when data is missing — rules enforce honesty

---

## 🧩 Future Improvements

- Add write-back to Google Sheets (update rows, add rows)  
- Add multi-sheet support  
- Add support for exporting summaries to PDF or email  
- Add role-based restrictions (admin vs user mode)  

---


## 👤 Author

**Dhyan Patel**
Final-year Engineering Student | AI/ML & Automation Enthusiast
🔗 [LinkedIn](https://linkedin.com/in/dhyan2815) • [GitHub](https://github.com/dhyan2815)

---

> ⚙️ *Built entirely on n8n Cloud – orchestrating AI, data enrichment, and automation in one workflow.*
#
