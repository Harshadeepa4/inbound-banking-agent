# Inbound Banking Support Agent

**Team:** Wisdom Loop
**Date:** 30.09.2025

---

## Project Overview

This project implements an **AI Banking Support Agent** using **Inya.ai** and **Beeceptor mock APIs**. The agent can:

* Provide account information (balance, transactions, KYC, loans)
* Manage cards (block, disputes)
* Handle complaints
* Locate branches/ATMs
* Escalate complex queries to a live agent
* Support multilingual responses (English & Hindi)

All API calls use **mock endpoints on Beeceptor**, so no real banking data is used.

---

## Repository Contents

* `Bank_Mock_API_Doc.docx` → 20 scenarios with JSON responses
* `Concept_Note.docx` → Project concept, objectives, and methodology
* `README.md` → Setup and usage instructions

---

## Setup & Run Instructions

### 1. Clone Repository

```bash
git clone https://github.com/<username>/inbound-banking-agent.git
cd inbound-banking-agent
```

### 2. Use Beeceptor Mock APIs

* Open Beeceptor: [https://beeceptor.com](https://beeceptor.com)
* Use the **base URL** from your workspace:

```
https://<your-beeceptor-base-url>
```

* Each scenario has its endpoint:

| Scenario                          | Endpoint                |
| --------------------------------- | ----------------------- |
| Account Balance                   | `/balance`              |
| Last 5 Transactions               | `/transactions`         |
| Block My Card                     | `/block_card`           |
| Block Card Ending 9012            | `/block_card_confirm`   |
| Raise a Dispute                   | `/raise_dispute`        |
| Complaint Status                  | `/check_complaint`      |
| I Want to Complain                | `/create_complaint`     |
| Nearest Branch                    | `/find_branch`          |
| ATM Near Pincode                  | `/find_atm`             |
| KYC Status                        | `/check_kyc`            |
| Cheque Status                     | `/check_cheque`         |
| FD Rates                          | `/fd_rates`             |
| Loan Status                       | `/check_loan`           |
| Speak to Agent                    | `/escalate_to_agent`    |
| Card Problem Ambiguous            | `/card_issue_ambiguous` |
| Balance in Hindi                  | `/balance_hi`           |
| Branch in Fort Mumbai Two Options | `/choose_branch_fort`   |
| Dispute for Transaction Not Found | `/dispute_not_found`    |
| API Timeout on Balance            | `/balance_timeout`      |
| Frustrated User                   | `/escalate_frustration` |

### 3. Configure Inya.ai Actions

1. Log in to **Inya.ai**.
2. Go to **Actions → API Integrations → Create Action**.
3. For each scenario:

   * **Name:** e.g., `Get Account Balance`
   * **Method:** GET (or POST if required)
   * **URL:** `https://<beeceptor-base-url>/balance`
   * **Headers:** `Content-Type: application/json`
   * **Map response fields to variables:**

| Variable Name  | JSON Path          |
| -------------- | ------------------ |
| account_number | `{{body.account}}` |
| balance        | `{{body.balance}}` |
| as_of_date     | `{{body.date}}`    |
| message        | `{{body.message}}` |

* Repeat variable mapping for other endpoints as defined in your Word doc.

### 4. Test the Agent

* Use **Inya.ai simulator**:

  * Trigger intents for all 20 scenarios.
  * Verify correct response mapping.
  * Ensure bot prompts for missing info (e.g., last 4 digits of card).
  * Test escalation to live agent for complex or abusive queries.

### 5. Environment Requirements

* **Inya.ai account**
* **Beeceptor account**
* No local backend required

### 6. Notes

* All endpoints are **mock APIs**; no real banking data is used.
* Follow the **Bank_Mock_API_Doc.docx** for example responses and testing.
* Share the **Beeceptor base URL** with teammates to allow integration.
