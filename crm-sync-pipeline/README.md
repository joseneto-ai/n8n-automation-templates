# 🔄 CRM Sync Pipeline

Automated pipeline that captures every customer interaction from
communication channels and syncs structured lead data to your CRM
in real time — with zero manual data entry.

---

## The Problem This Solves

Customer interactions happen across WhatsApp, web forms, email,
and landing pages. Without automation, data either gets lost,
entered manually with errors, or logged too late to be useful.
Sales teams operate blind.

---

## How This Workflow Works

**Trigger:** Any customer interaction event (message, form, API call)

**Step 1 — Event Capture**
Receives the interaction payload via webhook from any source.

**Step 2 — Data Normalization**
Standardizes the data structure regardless of source —
same schema whether coming from WhatsApp or a web form.

**Step 3 — Lead Enrichment**
Optionally enriches the contact with additional data
(location from phone prefix, interaction history, etc).

**Step 4 — Duplicate Check**
Checks the CRM for an existing record with the same
identifier before creating or updating.

**Step 5 — CRM Write**
Creates a new contact or updates the existing one with:
- Full interaction transcript
- Lead score
- Source channel
- Timestamp
- Next action tag

**Step 6 — Confirmation Log**
Logs the sync result (success / failure) for audit purposes.

---

## Workflow Structure
```
[Webhook — Any Source]
         │
         ▼
[Data Normalizer]
         │
         ▼
[Lead Enrichment]
         │
         ▼
[CRM Duplicate Check]
         │
    ┌────┴────┐
    ▼         ▼
[Create]  [Update]
    │         │
    └────┬────┘
         ▼
[Confirmation Logger]
```

---

## Stack

- **n8n** — Orchestration
- **HTTP Request nodes** — CRM API integration
- **Function nodes** — Data normalization logic
- **Compatible CRMs** — Any CRM with REST API or webhook support

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
| `[WEBHOOK_PATH]` | Your chosen webhook path |
| `[CRM_API_URL]` | Your CRM's API base URL |
| `[CRM_API_KEY]` | Your CRM API key |
| `[CRM_CREATE_ENDPOINT]` | Endpoint for creating new contacts |
| `[CRM_UPDATE_ENDPOINT]` | Endpoint for updating existing contacts |
| `[LOG_WEBHOOK]` | Your logging or monitoring endpoint |

3. Activate the workflow
4. Point your interaction sources to the n8n webhook URL
```
