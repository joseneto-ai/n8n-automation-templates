# 💬 WhatsApp Autoresponder

An intelligent, context-aware WhatsApp autoresponder powered by
an LLM — responds instantly to any incoming message with
personalized, human-quality replies.

---

## The Problem This Solves

Businesses using WhatsApp as a customer channel face a hard choice:
hire staff to monitor 24/7, or let messages go unanswered.
Both options are expensive — one in money, one in lost customers.

This template eliminates that tradeoff entirely.

---

## How This Workflow Works

**Trigger:** Incoming WhatsApp message via Business API webhook

**Step 1 — Message Parsing**
Extracts sender ID, message content, and timestamp from the
WhatsApp API payload.

**Step 2 — Context Load**
Retrieves the full conversation history for that sender.
If it's a first message, starts a fresh context.

**Step 3 — LLM Response Generation**
Sends the full conversation history and current message to
GPT-4o with a custom system prompt tailored to the business.
Returns a personalized, context-aware reply.

**Step 4 — Response Delivery**
Sends the generated reply back to the customer via
WhatsApp Business API.

**Step 5 — Context Save**
Updates and persists the conversation history for the next
message cycle.

---

## Workflow Structure
```
[WhatsApp Webhook]
        │
        ▼
[Message Parser]
        │
        ▼
[Context Manager — Load]
        │
        ▼
[OpenAI — Response Generator]
        │
        ▼
[WhatsApp API — Send Reply]
        │
        ▼
[Context Manager — Save]
```

---

## Stack

- **n8n** — Orchestration
- **OpenAI GPT-4o** — Response generation
- **WhatsApp Business API (Meta)** — Message channel
- **Context store** — Session persistence per sender

---

## Files

- `README.md` — This documentation
- `workflow.json` — Importable n8n workflow

---

## Setup Instructions

1. Import `workflow.json` into your n8n instance
2. Replace the following placeholders:

| Placeholder | What to replace with |
|---|---|
| `[OPENAI_API_KEY]` | Your OpenAI API key |
| `[META_ACCESS_TOKEN]` | Your WhatsApp Business API token |
| `[PHONE_NUMBER_ID]` | Your WhatsApp Business phone number ID |
| `[WEBHOOK_PATH]` | Your chosen webhook path |
| `[SYSTEM_PROMPT]` | Your business-specific instructions for the AI |

3. Configure the Meta webhook to point to your n8n instance
4. Activate the workflow
```
