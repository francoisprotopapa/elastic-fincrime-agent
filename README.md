# 🕵️‍♂️ Elastic AI Financial Crime Investigator # elastic-fincrime-agent
AI-powered Financial Crime Investigator built with Elastic Agent Builder. Uses Agentic RAG to orchestrate AML, Sanctions, and Entity Resolution workflows across distributed datasets.
This repository contains the datasets, prompts, and configuration logic to build an **Agentic RAG** solution for Anti-Money Laundering (AML) and Financial Fraud detection using **Elastic Agent Builder**.

## 🚀 Overview

Traditional rule-based systems generate 95%+ False Positives. This project demonstrates how an AI Agent can orchestrate **4 specialized tools** to:
1.  **Reduce False Positives:** By cross-referencing alerts with External News (e.g., verifying a source of wealth).
2.  **Detect Hidden Risks:** By using Semantic Search on unstructured transaction notes (e.g., Sanctions evasion).
3.  **Unify Identities:** By performing Entity Resolution across global client databases (Single Client View).

## 📂 Dataset Structure (Indices)

The solution relies on 4 Elasticsearch indices. Source files are located in the `/data` folder:

| Index Name | File Source | Description | Search Tech |
| :--- | :--- | :--- | :--- |
| `global-clients` | `data/clients.ndjson` | KYC profiles across EMEA, AMER, APJ. | Hybrid Search |
| `transactions` | `data/transactions.ndjson` | Transaction logs with unstructured notes. | Hybrid Search |
| `internal-policies` | `data/policies.ndjson` | Compliance PDFs and Rulebooks. | Hybrid Search |
| `external-news` | `data/news.ndjson` | OSINT, Adverse Media, and Leaks. | Hybrid Search |

## 🤖 Agent Configuration

To replicate this agent in Elastic:

### 1. System Prompt
Copy the content from `prompts/system_prompt.md` into the Agent's System Prompt configuration. This defines the "Chain of Thought" logic (Identify -> Analyze -> Contextualize -> Adjudicate).

### 2. Tools Definition
Create 4 tools in Elastic Agent Builder mapped to the indices above:

* **Tool:** `search_global_client_database` (Index: `global-clients`)
* **Tool:** `analyze_transaction_patterns` (Index: `transactions`)
* **Tool:** `consult_compliance_handbook` (Index: `internal-policies`)
* **Tool:** `scan_adverse_media` (Index: `external-news`)

## 🎬 Demo Scenarios

Detailed prompts for live demonstrations are available in `prompts/demo_scenarios.md`.

* **Scenario 1:** The Baker (False Positive reduction via News).
* **Scenario 2:** Eastern Logistics (Sanctions detection via Semantic Search).
* **Scenario 3:** The Volkov Cluster (Global Entity Resolution).

---
*Built with Elastic AI Assistant.*
