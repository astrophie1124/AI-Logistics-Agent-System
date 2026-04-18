# AI-Powered Logistics Automation & Customer Service Agent

##  Overview
This project is an AI-driven logistics automation system that integrates customer service, order tracking, and financial reporting into a unified workflow.

It leverages LLM-based agents, workflow orchestration (n8n), and RAG (Retrieval-Augmented Generation) to automate real-world logistics operations. The system is capable of handling user queries, retrieving structured data, and executing actions across multiple external services.

---

##  Features

-  AI-powered customer service agent with intent classification  
-  Automated order tracking via Google Sheets integration  
-  Financial report generation and delivery (Email + WhatsApp)  
-  RAG-based logistics knowledge retrieval (Vector Store + Embeddings)  
-  Multi-step reasoning using ReAct framework  
-  OCR-based document processing  
-  Multi-channel communication (Webhook, WhatsApp API)  

---

##  System Architecture
User → Webhook → AI Agent → Tools (Sheets / Vector DB / OCR) → Output

---

##  Tech Stack

- Node.js (WhatsApp Bridge API)  
- n8n (Workflow Automation)  
- LLM (Google Gemini / Tool Calling)  
- Google Sheets API  
- WhatsApp Web API  
- Vector Database (for RAG)  
- OCR API  

---

##  Highlights

- Designed a multi-agent workflow with dynamic routing (A/B/C/D logic)  
- Integrated LLM reasoning with external tools for real-world automation  
- Built end-to-end pipeline: input → reasoning → action → response  
- Implemented structured JSON outputs for reliable automation  
- Combined automation + AI agent design in a production-like system  

---

##  Workflow Preview

(Add your screenshot here)

Example:

---

##  Setup & Usage

### Phase 1: Configure the WhatsApp Bridge Program (Node.js)

This script acts as a gateway, connecting your WhatsApp account with the n8n workflow.

1. Install Environment  
   Ensure Node.js (v18+) is installed.

2. Initialize Project  
   Open the `wa-local-api` folder in terminal and run:
   npm install
   
3. Configure Webhook  
Open `index.js` and locate:
N8N_WEBHOOK_URL
- Local: `http://localhost:5678/webhook/whatsapp-webhook`
- Cloud: replace with your deployed webhook URL

---

### Phase 2: Configure the n8n Workflow

1. Import Workflow  
- Open n8n  
- Click top-right (⋯) → Import from File  
- Upload `logistics-agent-workflow.json`

2. Configure Credentials  
- Create:
  - Google Gemini API
  - Google Sheets API  
- Assign credentials to nodes with warnings

3. Configure Data Source  
- Update Google Sheets nodes  
- Ensure column names match original schema

4. Configure Sender API  
- Locate final HTTP Request node  
- Set:
  - URL: `http://localhost:3000/send`
  - Method: POST  
  - Body: `{ number, text }`

4. Initialize Vector Database  
- Upload logistics documents (FAQs / policies)  
- Required for RAG functionality

---

### Phase 3: System Startup

1. Start n8n  
- Activate workflow OR enable webhook listening

2. Start WhatsApp Gateway
node index.js

3. Authenticate  
- Scan QR code via WhatsApp → Linked Devices

4. Test System  
- Send message from another account  
- Verify automated response

---

##  Security Notes

- All credentials and API keys have been removed  
- Replace with your own configuration before running  
- Never expose service account keys in public repositories  

---

##  Notes

- This project simulates a real-world logistics automation system  
- Designed to demonstrate AI Agent + Workflow + Backend integration  
- Can be extended to other domains (customer support, operations, automation)  

---

##  Author

Nazy

---

##  If you find this project useful, feel free to star it!
