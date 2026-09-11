# Enterprise Human-in-the-Loop (HITL) AI Content Engine

![Make.com](https://img.shields.io/badge/Make.com-Visual_Automation-purple)
![Notion API](https://img.shields.io/badge/Notion_API-Database_Staging-black)
![LLM API](https://img.shields.io/badge/OpenRouter-Multi--Modal_AI-blue)
![License](https://img.shields.io/badge/License-MIT-green)

An enterprise-grade, two-stage Human-in-the-Loop (HITL) content generation and delivery pipeline. The engine automatically ingests raw topics, generates personalized multi-modal copy and dynamic featured images, stages draft assets in a Notion editorial board, and dispatches rich HTML emails upon explicit human approval.

---

## 🛠️ Tech Stack & Integrations

* **Orchestration:** Make.com (formerly Integromat)
* **Editorial Interface:** Notion API (Databases & Status State Machine)
* **AI Generation:** OpenRouter LLM Endpoints (Copy) & Pollinations AI (Dynamic Image Rendering)
* **Data Sources & Delivery:** Google Sheets API & Gmail API

---

## 📐 Architecture & System Flow

```text
[ Phase 1: Ingestion & Asset Generation ]
Google Sheets (Raw Data) ➔ OpenRouter LLM (Copy) ➔ Pollinations AI (Image) ➔ Notion Staging Table
                                                                                   |
                                                                       [ Human Review Gate ]
                                                                      Editor Approves in Notion
                                                                                   |
                                                                                   v
[ Phase 2: Automated Dispatch ]
Notion Watcher (Status: Approved) ➔ HTML Email Compiler (Gmail) ➔ Notion Status Sync (Status: Sent)
```
---

### 🧩 Pipeline Breakdown

#### Scenario 1: Asset Generation & Staging (Ai automation H)
**Trigger:** Listens for new records in Google Sheets.

* **Copy Generation:** Calls OpenRouter LLM API endpoints to produce structured JSON containing campaign titles and draft body copy.
* **Image Synthesis:** Dynamically constructs and URL-encodes (encodeURL()) image generation prompts sent to Pollinations AI.
* **Database Staging:** Pushes generated assets directly into a Notion Content & Lead Review database with Status = "Needs Review".

#### Scenario 2: Approval Gate & Multi-Channel Dispatch (Make HITL Engine)
**Approval Polling:** Monitors Notion every 15 minutes for items meeting the strict execution filter Status = "Approved".

* **HTML Compilation:** Assembles dynamic raw HTML body code containing inline CSS styling and embedded tags.
* **Closed-Loop Sync:** Dispatches the email via Gmail and immediately updates the Notion record status to Sent to prevent duplicate execution loops.

#### 🛡️ Error Handling & System Hardening
**Image Generation Fallback:** A Set Variable error-handler route captures Pollinations API timeouts and injects a fallback static banner URL.

**Execution Directives:** Critical HTTP endpoints utilize Break retry strategies, while non-blocking status updates employ Commit/Skip directives to protect scenario uptime.

---

**Documentaion**

Scenario 1:Ingestion, AI Generation & Staging Engine
---
<img width="1824" height="947" alt="image" src="https://github.com/user-attachments/assets/0e87885f-7e22-47c1-a2ec-3f948f87ab62" />
---

Scenario 2:HITL Approval Gate & Multi-Channel Dispatch
---
<img width="1824" height="947" alt="image" src="https://github.com/user-attachments/assets/58a4078e-ef6a-464b-98d4-d06f5c82e871" />
---



