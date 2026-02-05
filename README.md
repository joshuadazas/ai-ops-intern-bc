# AI Operations Intern - Business Case Challenge: Support Ticket Prioritization

## Overview

This repository contains synthetic support data from a global payroll platform processing 5,000+ monthly tickets across 150+ countries. The challenge: build a system that identifies at-risk customers more effectively than sentiment analysis alone.

## Business Context

**Current Problem:** Sentiment-based ticket prioritization generates 85% false positives. Customer Success wastes hours reviewing non-urgent alerts while real churn risks go undetected.

**Core Insight:** Sentiment ≠ Actionability. Frustrated customers aren't always urgent. Polite customers with delayed payouts are.

**Key Risk Signals:**

- Recurrence: Same client, same issue category, multiple occurrences in 30 days
- Resolution time: Tickets open 7+ days without resolution
- CS silence: Customer's last message unanswered for 5+ days
- Account value: High-MRR clients have higher churn cost
- Issue type: Payment/technical issues block workflows; general inquiries don't

## Dataset

### Files

**tickets.csv** (~200 rows)

- `ticket_id` — Unique identifier
- `client_id` — Foreign key to clients table
- `created_at` — Ticket creation timestamp
- `subject` — Ticket subject line
- `status` — open | pending | resolved
- `resolved_at` — Resolution timestamp (null if unresolved)
- `category` — payment | technical | onboarding | compliance | benefits | general
- `assigned_to` — Agent ID or null

**clients.csv** (~50 rows)

- `client_id` — Unique identifier
- `company_name` — Anonymized company name
- `mrr` — Monthly recurring revenue ($)
- `account_tier` — starter | growth | enterprise
- `signup_date` — Customer onboarding date
- `country` — Client location

**conversations.csv** (~800 rows)

- `message_id` — Unique identifier
- `ticket_id` — Foreign key to tickets table
- `sender_type` — customer | agent
- `sent_at` — Message timestamp
- `message_text` — Message content

**ticket_history.csv** (~300 rows)

- Historical tickets from prior 90 days
- Same schema as tickets.csv
- Used to detect recurrence patterns

### Data Relationships

```
clients.csv (1) ----< (many) tickets.csv
tickets.csv (1) ----< (many) conversations.csv
tickets.csv + ticket_history.csv → Recurrence analysis
```

## Challenge

Build a prioritization system that outperforms sentiment-only filtering. Solution format is open—this tests analytical thinking, not specific deliverable types.

**Constraints:**

- 48 hours completion time
- Any tools/technologies permitted

## Usage

1. Clone this repository
2. Load CSVs into your analysis environment
3. Build your prioritization model/system
4. Submit solution via GitHub repo or functional prototype

## License

Data is synthetic and anonymized. For interview/assessment purposes only.

---

**Questions?** Contact the hiring team for clarifications.# ai-ops-intern-bc
data for the ai ops intern business case challenge
