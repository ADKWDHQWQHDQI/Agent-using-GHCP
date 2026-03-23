# Introduction

> [!NOTE]
> This is a **90-minute** workshop that gives you hands-on experience building a **Compliance RAG Agent** using **Microsoft AI Foundry**, the **AI Toolkit (AITK)** for VS Code, and **GitHub Copilot**. You will go from zero to a fully deployed compliance assistant with a web UI.

---

## Learning Objectives

By the end of this workshop, you will be able to:

- **Provision Azure resources** (AI Foundry, Blob Storage, Azure AI Search) required for a RAG agent.
- **Upload and index compliance documents** into Azure AI Search from Azure Blob Storage.
- **Design and prototype an agent** in AI Toolkit Agent Builder with Azure AI Search as a grounding tool.
- **Export agent code** and debug real-world runtime errors using GitHub Copilot.
- **Extend the agent** with interactive input and a professional web UI using GitHub Copilot Agent mode.
- **Containerize the application** for deployment using Docker *(Optional)*.
- **Evaluate and refine** agent responses through structured test scenarios.

---

## Architecture Overview

```
┌────────────────────────────────────────────────────────────────────┐
│                        Compliance Compass                          │
├────────────────────────────────────────────────────────────────────┤
│                                                                    │
│   ┌──────────┐    ┌──────────────┐    ┌─────────────────────┐     │
│   │  User     │───▶│  Streamlit   │───▶│  Azure AI Foundry   │     │
│   │  Query    │    │  Web UI      │    │  Agent (gpt-4o)     │     │
│   └──────────┘    └──────────────┘    └─────────┬───────────┘     │
│                                                  │                 │
│                                         ┌────────▼────────┐       │
│                                         │  Azure AI Search │       │
│                                         │  (RAG Retrieval) │       │
│                                         └────────┬────────┘       │
│                                                  │                 │
│                                         ┌────────▼────────┐       │
│                                         │  Blob Storage    │       │
│                                         │  (KB Documents)  │       │
│                                         └─────────────────┘       │
│                                                                    │
│   Azure = Brain (Models + Search)                                  │
│   AI Toolkit = Agent Designer                                      │
│   GitHub Copilot = Builder + Debugger + Extender                   │
│                                                                    │
└────────────────────────────────────────────────────────────────────┘
```

---

## Business Scenario

### The Challenge

Compliance and risk teams in fintech, banking, and manufacturing organizations must evaluate regulatory risks across multiple jurisdictions before onboarding vendors, handling cross-border data transfers, or signing contracts. Today, this process involves manually searching dozens of regulatory documents, cross-referencing multiple policies, and writing compliance reports from scratch — leading to slow turnaround and inconsistent risk assessments.

### The Solution: Compliance Compass

You will build **Compliance Compass**, an intelligent compliance RAG agent that:

1. **Accepts natural language queries** — Users describe real-world compliance scenarios (e.g., "We are onboarding an AI vendor in China that will process customer payment data.")
2. **Retrieves relevant policies** — The agent searches a curated Knowledge Base of 12 compliance documents via Azure AI Search.
3. **Analyzes risks** — The agent reasons over retrieved policies to identify conflicts, obligations, and risks.
4. **Generates structured reports** — The output includes risk scores, referenced policies, immediate actions, and escalation options.

### Example Interaction

**User Prompt:**
> "Assessing risks for a new AI analytics vendor based in Singapore that will process our customer transaction data. Are there any RBI localization concerns?"

**Agent Report (summarized):**
- **Risk Score:** 7/10 (High)
- **Key Findings:** RBI mandates payment data storage in India; processing abroad allowed but data must return within 24 hours.
- **Recommended Actions:** Add data residency clause, conduct Transfer Impact Assessment, perform vendor cybersecurity audit.
- **References:** RBI Data Localization 2018 Guidelines, GDPR Article 44 Transfers.

---

## Workshop Flow

> [!TIP]
> Complete the modules in order — each builds on the previous one.

| Module | Title | What You Will Do | Duration |
|---|---|---|---|
| **I** | [Prerequisites and Environment Setup](./01_Prerequisites.md) | Install tools, authenticate with Azure, configure VS Code extensions | 10 min |
| **II** | [Provisioning Azure Resources](./02_Azure_Resources.md) | Create AI Foundry hub, deploy models, set up Blob Storage and AI Search | 15 min |
| **III** | [Designing the Agent in AI Toolkit](./03_Agent_Design.md) | Build the compliance agent visually with instructions and Azure AI Search tool | 10 min |
| **IV** | [Exporting Code and Debugging with Copilot](./04_Code_Export_Debug.md) | Export to Python, encounter a real Azure SDK error, debug with Copilot | 15 min |
| **V** | [Adding Interactive Input](./05_Interactive_Input.md) | Transform hardcoded queries into an interactive CLI with Copilot | 10 min |
| **VI** | [Building a Professional Web UI](./06_Web_UI.md) | Generate a complete Streamlit chat UI using Copilot Agent mode | 15 min |
| **VII** | [Containerization and Testing *(Optional)*](./07_Containerize_Test.md) | Dockerize the app with Docker *(optional)*, run quality tests, refine agent instructions | 15 min |

**Total Duration:** ~90 minutes

---

## How the Three Tools Work Together

| Technology | Role in Workshop |
|---|---|
| **Microsoft AI Foundry** | The brain — hosts GPT-4o (reasoning) and embedding model; manages agent deployment |
| **AI Toolkit for VS Code** | The designer — visual builder to configure agents, instructions, and tools without writing code |
| **GitHub Copilot (Agent Mode)** | The builder — debugs errors, generates code extensions, creates UI, writes Dockerfile |
| **Azure AI Search** | The memory — indexes and retrieves relevant compliance policies for RAG grounding |
| **Azure Blob Storage** | The storage — stores the 12 compliance Knowledge Base documents |

> [!NOTE]
> **Instructor Note:** Each module contains step-by-step instructions. Participants copy prompts and let GitHub Copilot generate the output — minimal manual coding is required.

---

Click **Next** to proceed to [Module I: Prerequisites and Environment Setup](./01_Prerequisites.md).
