# Bank Mock API Documentation for Inya.ai Integration

This repository contains mock API documentation for 20 banking scenarios created using Beeceptor. This README explains how to use the documentation and endpoints in Inya.ai.

---

## **1. Repository Contents**

* `Bank_Mock_API_Doc.docx`: Word document containing:

  * 20 mock endpoints
  * HTTP methods (GET/POST)
  * JSON responses for each scenario
  * Variables to extract for Inya.ai integration

* Base URL for Beeceptor: `https://<your-beeceptor-base-url>`

---

## **2. How to Use This in Inya.ai**

### Step 1: Open Inya.ai

* Log in to your Inya.ai account.
* Navigate to **Actions / API Integrations / Custom API**.

### Step 2: Add Each API Endpoint

For each of the 20 scenarios:

1. Click **Add API / Create Action**.
2. Fill in the following fields:

| Field              | Value Example                           |
| ------------------ | --------------------------------------- |
| Name / Description | e.g., `Get Account Balance`             |
| Method             | GET (or POST if specified)              |
| URL                | `https://<beeceptor-base-url>/balance`  |
| Headers            | `Content-Type: application/json`        |
| Body / Parameters  | Only if required (usually GET has none) |
| Response Variables | See Word doc for variable mapping       |

### Step 3: Map Response Variables

Use the JSON paths provided in the Word document to map API response fields to Inya.ai agent variables. Examples:

```
{{body.account}} -> account_number
{{body.balance}} -> balance
{{body.date}} -> as_of_date
{{body.message}} -> message
```

### Step 4: Connect Endpoint to Intent

* Map each API action to the corresponding **intent** in your chatbot.
* Example:

  * Intent: `Check Balance` → Action: `/balance`
  * Intent: `Raise Dispute` → Action: `/raise_dispute`

### Step 5: Test Each Scenario

* Open the **chat simulator** in Inya.ai.
* Trigger each intent and verify that:

  * The correct endpoint is called.
  * The AI agent responds with the correct message.
  * All variables are mapped correctly.

### Step 6: Maintain and Update

* If any changes are made to the mock APIs in Beeceptor, update the Word document.
* Share the updated repo with your team so everyone stays in sync.

---

## **3. Notes**

* **Base URL**: Share the Beeceptor base URL with your team. They can append each endpoint from the doc.
* **Testing**: Make sure all GET/POST methods are consistent with the Word doc.
* **Dynamic Responses**: You can enable dynamic response rules in Beeceptor if needed for advanced scenarios.

---

By following this guide and using the provided document, your team can fully integrate the mock banking APIs into Inya.ai with minimal setup.
