# ⚡ n8n Automation Templates — zNeto.AI

Production-ready workflow templates built with n8n for AI-powered
business automation. Each template is documented, structured, and
ready to import and adapt.

These workflows are extracted and sanitized from real client deployments
at zNeto.AI. All credentials, API keys, and client-specific data have
been replaced with clearly labeled placeholders.

---

## 📁 Available Templates

### 1. 🎯 Lead Qualification Agent
Automatically scores and routes incoming leads based on intent signals
collected via conversational AI — no human triage required.

→ [`/lead-qualification`](./lead-qualification/README.md)

---

### 2. 💬 WhatsApp Autoresponder
Instant, intelligent WhatsApp response system with context memory
and LLM-powered personalization for any business vertical.

→ [`/whatsapp-autoresponder`](./whatsapp-autoresponder/README.md)

---

### 3. 🔄 CRM Sync Pipeline
Automated bidirectional sync between communication channels and CRM —
every lead interaction logged, scored, and routed in real time.

→ [`/crm-sync-pipeline`](./crm-sync-pipeline/README.md)

---

## ⚙️ How to Use These Templates

1. Navigate to the template folder of your choice
2. Read the `README.md` inside — it explains the workflow logic
3. Open the `workflow.json` file
4. Copy the raw JSON content
5. In your n8n instance: **Import from JSON** → paste and import
6. Replace all `[PLACEHOLDER]` values with your actual credentials
7. Activate the workflow

---

## 🛠️ Stack Requirements

- n8n (self-hosted or cloud) — v1.0+
- OpenAI API key (for AI-powered templates)
- WhatsApp Business API access (for messaging templates)
- A running CRM with webhook support (for sync templates)

---

## 👤 Author

**José Neto** — AI Automation Engineer & Founder @zNeto.AI

[![LinkedIn](https://img.shields.io/badge/LinkedIn-José%20Neto-0077B5?style=flat&logo=linkedin)](https://www.linkedin.com/in/jos%C3%A9-neto-b88558398)
[![GitHub](https://img.shields.io/badge/GitHub-joseneto--ai-181717?style=flat&logo=github)](https://github.com/joseneto-ai)
```
