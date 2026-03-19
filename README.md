# Compliance Compass — Build AI Agents with Microsoft Foundry, AI Toolkit & GitHub Copilot

> **Audience:** Developers, Compliance Engineers, Tech Leads, Architects
> **Duration:** ~90 minutes (7 modules)
> **Prerequisites:** VS Code, Python 3.10+, Azure subscription, GitHub Copilot access

---

## What You Will Build

**Compliance Compass** — a Retrieval-Augmented Generation (RAG) agent that helps compliance and risk teams evaluate regulatory risks for vendors, data transfers, and cross-border operations.

The agent is powered by:
- **Microsoft AI Foundry** (GPT-4o + embedding model)
- **Azure AI Search** (knowledge retrieval from 12 compliance documents)
- **AI Toolkit for VS Code** (visual agent design)
- **GitHub Copilot** (code generation, debugging, UI creation, containerization)

```
Azure = Brain (Models + Search)
AI Toolkit = Agent Designer
GitHub Copilot = Builder + Debugger + Extender
```

---

## Workshop Flow

```
┌─────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│  Module I    │───▶│  Module II   │───▶│  Module III  │───▶│  Module IV   │
│  Setup &     │    │  Azure       │    │  AI Toolkit  │    │  Export Code │
│  Prerequisites│   │  Resources   │    │  Agent Design│    │  + Debug     │
└─────────────┘    └──────────────┘    └──────────────┘    └──────┬───────┘
                                                                   │
┌─────────────┐    ┌──────────────┐    ┌──────────────┐           │
│  Module VII  │◀──│  Module VI   │◀──│  Module V    │◀──────────┘
│  Docker +    │    │  Streamlit   │    │  Interactive │
│  Testing     │    │  Web UI      │    │  Input       │
└─────────────┘    └──────────────┘    └──────────────┘
```

---

## Modules

| # | Module | Description | Duration |
|---|---|---|---|
| **I** | [Prerequisites & Environment Setup](lab/instructions/01_Prerequisites.md) | Install tools, configure Azure CLI, sign in to Copilot & AI Toolkit | 10 min |
| **II** | [Provisioning Azure Resources](lab/instructions/02_Azure_Resources.md) | Create AI Foundry hub, deploy models, set up Blob Storage & AI Search | 15 min |
| **III** | [Designing the Agent in AI Toolkit](lab/instructions/03_Agent_Design.md) | Build the compliance agent visually with instructions & Azure AI Search tool | 10 min |
| **IV** | [Exporting Code & Debugging with Copilot](lab/instructions/04_Code_Export_Debug.md) | Export to Python, encounter real Azure SDK error, debug with Copilot | 15 min |
| **V** | [Adding Interactive Input](lab/instructions/05_Interactive_Input.md) | Transform hardcoded queries into interactive CLI with Copilot | 10 min |
| **VI** | [Building a Professional Web UI](lab/instructions/06_Web_UI.md) | Generate a complete Streamlit chat UI with Copilot Agent mode | 15 min |
| **VII** | [Containerization & Testing](lab/instructions/07_Containerize_Test.md) | Dockerize the app, run quality tests, refine agent instructions | 15 min |

---

## Key GitHub Copilot Features Demonstrated

| Feature | Where Used |
|---|---|
| **Agent Mode** | Modules IV–VII: Debugging, code generation, UI creation, Docker |
| **Ask Mode** | Module IV: Understanding generated code |
| **Structured Prompting** | Module IV: Error diagnosis with constraints |
| **Code Extension** | Module V: Adding interactive input loop |
| **Full App Generation** | Module VI: Complete Streamlit UI from a single prompt |
| **DevOps Generation** | Module VII: Dockerfile and test suite creation |

---

## Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                     Compliance Compass                        │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌──────────┐    ┌────────────┐    ┌────────────────────┐   │
│  │ User     │───▶│ Streamlit  │───▶│ Azure AI Foundry   │   │
│  │ Query    │    │ Web UI     │    │ Agent (GPT-4o)     │   │
│  └──────────┘    └────────────┘    └────────┬───────────┘   │
│                                              │               │
│                                     ┌────────▼────────┐     │
│                                     │ Azure AI Search  │     │
│                                     │ (RAG Retrieval)  │     │
│                                     └────────┬────────┘     │
│                                              │               │
│                                     ┌────────▼────────┐     │
│                                     │ Blob Storage     │     │
│                                     │ (12 KB Docs)     │     │
│                                     └─────────────────┘     │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## Knowledge Base

12 compliance documents covering:
- **RBI** — Data localization, cross-border transactions, vendor onboarding
- **GDPR** — Article 44 transfers, Schrems II, Standard Contractual Clauses
- **DPDP Act** — India's Digital Personal Data Protection Act 2023
- **SEBI** — Insider trading compliance
- **Export Controls** — US/EU/India technology restrictions
- **Frameworks** — Risk scoring, incident response, DPA templates

See [kb_markdown/](kb_markdown/) for all documents.

---

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/ADKWDHQWQHDQI/Agent-using-GHCP.git
   cd Agent-using-GHCP
   ```

2. Open in VS Code:
   ```bash
   code .
   ```

3. Start with the [Introduction](lab/instructions/00_Introduction.md) or jump directly to [Module I](lab/instructions/01_Prerequisites.md).

---

## Repository Structure

```
Agent-using-GHCP/
├── README.md                          ← This file
├── lab/
│   └── instructions/
│       ├── 00_Introduction.md
│       ├── 01_Prerequisites.md
│       ├── 02_Azure_Resources.md
│       ├── 03_Agent_Design.md
│       ├── 04_Code_Export_Debug.md
│       ├── 05_Interactive_Input.md
│       ├── 06_Web_UI.md
│       └── 07_Containerize_Test.md
├── kb_markdown/                       ← 12 compliance Knowledge Base documents
├── kb_source_pdfs/                    ← Source reference index
└── idea.txt                           ← Original concept document
```

---

## Contributing

This is a workshop repository. For feedback or improvements, open an issue or pull request.

---

## License

This workshop is for educational purposes. All compliance documents are sourced from public regulatory sources. No proprietary or confidential data is included.
