# 🎯 Lead Qualification Agent

Automatically classifies and routes incoming leads based on intent
level — separating high-intent buyers from early-stage researchers
without any human involvement.

---

## The Problem This Solves

Sales and operations teams waste significant time manually reading
and sorting leads that come in through web forms, WhatsApp, or
landing pages. High-intent leads get lost in the queue. Low-intent
leads consume staff time that could be spent closing deals.

---

## How This Workflow Works

**Trigger:** New lead arrives via webhook (web form, landing page, or API)

**Step 1 — Data Extraction**
Pulls the lead's message, source, and any metadata from the payload.

**Step 2 — LLM Intent Analysis**
Sends the lead's message to GPT-4o with a classification prompt.
The model returns one of three scores:

- `HOT` — High intent, ready to buy or book
- `WARM` — Interested but needs nurturing
- `COLD` — Early research, low conversion probability

**Step 3 — Routing**
- `HOT` leads → Instant notification to sales team + CRM priority flag
- `WARM` leads → Added to automated nurture email/WhatsApp sequence
- `COLD` leads → Logged in CRM with low-priority tag

**Step 4 — CRM Logging**
All leads logged with full context, score, timestamp, and source.

---

## Workflow Structure
```
[Webhook Trigger]
      │
      ▼
[Data Extractor]
      │
      ▼
[OpenAI — Intent Classifier]
      │
      ▼
[Switch — HOT / WARM / COLD]
      │
   ┌──┴──────────────┐──────────────┐
   ▼                 ▼              ▼
[Sales Alert]   [Nurture Seq]  [Cold Log]
   │                 │              │
   └──────────┬──────┘──────────────┘
              ▼
         [CRM Logger]
```

---

## Stack

- **n8n** — Orchestration
- **OpenAI GPT-4o** — Intent classification
- **Webhook** — Lead intake
- **HTTP Request nodes** — CRM and notification integrations

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
| `[CRM_WEBHOOK_URL]` | Your CRM's webhook endpoint |
| `[SALES_ALERT_WEBHOOK]` | Slack, Teams, or email webhook |
| `[WEBHOOK_PATH]` | Your chosen webhook path |

3. Activate the workflow
4. Point your lead source to the n8n webhook URL
```
