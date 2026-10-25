
# Checkout Incident Detection & Automated Triage

### n8n | JavaScript | Google Sheets | Webhooks

**An event-driven incident monitoring and automated triage solution for e-commerce checkout operations.**

---

## Business Problem

Checkout failures can affect **revenue, customer experience, and platform reliability**.

## Solution Overview

The workflow automatically:

- **Monitors** checkout failure events every 15 minutes.
- **Evaluates** events against configurable baselines.
- **Classifies** incidents as `HIGH / ALERT` or `LOW / LOG`.
- **Publishes** structured incident commands through webhooks.
- **Maintains** processing state to track new events.

## Technology Stack

| Technology | Purpose |
|---|---|
| **n8n** | Workflow orchestration |
| **JavaScript** | Incident classification |
| **Google Sheets** | Data storage and audit trail |
| **Webhooks** | Downstream system integration |

## Workflow Architecture

![Workflow Overview](screenshots/workflow-overview.png)

**Schedule → Read State → Read Baselines → Evaluate Events → Publish Command → Update State**

