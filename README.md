# 🚀 Enterprise Human-in-the-Loop (HITL) AI Content Engine

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

Documentaion

Scenario 1:Ingestion, AI Generation & Staging Engine
<img width="1824" height="947" alt="image" src="https://github.com/user-attachments/assets/0e87885f-7e22-47c1-a2ec-3f948f87ab62" />


Scenario 2:HITL Approval Gate & Multi-Channel Dispatch
<img width="1824" height="947" alt="image" src="https://github.com/user-attachments/assets/58a4078e-ef6a-464b-98d4-d06f5c82e871" />


