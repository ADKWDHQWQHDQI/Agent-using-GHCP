# Export Control Regulations — US, EU, and India (2025)

**Sources:**
- **US:** Bureau of Industry and Security (BIS), Department of Commerce — Export Administration Regulations (EAR)
- **EU:** European Commission — EU Dual-Use Regulation (EU 2021/821, updated 2024)
- **India:** Directorate General of Foreign Trade (DGFT) — Foreign Trade (Development and Regulation) Act, 1992; SCOMET List
**Official URLs:**
- US BIS: https://www.bis.doc.gov
- EU: https://ec.europa.eu/trade/import-and-export-rules/export-from-eu/dual-use-controls/
- India DGFT: https://www.dgft.gov.in
**Last Reviewed:** March 2026

---

## Overview

Export control regulations govern the **transfer of sensitive technologies, goods, software, and technical data** across national borders. These regulations are designed to prevent the proliferation of weapons of mass destruction, maintain national security, and restrict the flow of sensitive technologies to adversarial entities or sanctioned countries.

For technology companies and manufacturers, export controls are particularly relevant when:
- **Sharing software, source code, or technical documentation** with foreign entities
- **Transferring encryption technology** or cybersecurity tools across borders
- **Exporting AI/ML models** trained on sensitive data or having dual-use capabilities
- **Engaging foreign vendors** who may have access to controlled technology
- **Manufacturing and shipping** goods with dual-use potential
- **Cloud computing** — hosting controlled data or technology on servers accessible from sanctioned countries

---

## Key Rules

### 1. US Export Administration Regulations (EAR)

**Scope:**
- Applies to all items (goods, software, technology) **made in the US** or containing more than a **de minimis share** of US-origin components (typically 25%)
- Applies to **foreign-made items** incorporating US technology (Foreign Direct Product Rule — FDPR)
- Applies to **US persons** regardless of location

**Key Concepts:**
| Concept | Description |
|---|---|
| **Export** | Actual shipment or transmission of items out of the US |
| **Re-export** | Shipment from one foreign country to another of US-origin or US-controlled items |
| **Deemed Export** | Release of controlled technology/source code to a foreign national within the US |
| **Deemed Re-export** | Release of controlled technology to a foreign national outside the US |
| **ECCN** | Export Control Classification Number — categorizes items on the Commerce Control List (CCL) |
| **EAR99** | Items subject to the EAR but not specifically listed on the CCL (generally low-risk) |

**Commerce Control List (CCL) — Relevant Categories:**
| Category | Description | Technology Examples |
|---|---|---|
| **Cat 3** | Electronics | Semiconductors, integrated circuits |
| **Cat 4** | Computers | High-performance computing, quantum computing components |
| **Cat 5 Part 1** | Telecommunications | 5G equipment, network security tools |
| **Cat 5 Part 2** | Information Security | Encryption software, cybersecurity tools, intrusion software |
| **Cat 7** | Navigation and Avionics | GPS systems, inertial navigation |
| **Cat 9** | Aerospace and Propulsion | Aircraft engines, spacecraft components |

**Key Restrictions (2024–2025 Updates):**
- **Advanced AI chips** — Export restrictions on high-performance AI chips (e.g., NVIDIA A100, H100) to China, Russia, and certain other countries
- **Semiconductor manufacturing equipment** — Expanded restrictions on tools used to manufacture advanced semiconductors
- **Quantum computing** — Controls on quantum computing technology and components
- **Entity List** — Over 700 Chinese entities restricted from receiving US technology without specific licenses

### 2. EU Dual-Use Regulation (EU 2021/821)

**Scope:**
- Applies to export of **dual-use items** from the EU (items that can be used for both civilian and military purposes)
- Updated in September 2021 with stronger controls on **cyber-surveillance technology** and new **human rights** considerations

**Key Features:**
| Feature | Description |
|---|---|
| **EU Control List** | Based on international export control regimes (Wassenaar, MTCR, NSG, Australia Group) |
| **Catch-All Clause** | Allows authorities to control exports of unlisted items if there is a WMD proliferation risk |
| **Cyber-Surveillance Controls** | New controls on technologies that could enable human rights violations (e.g., deep packet inspection, lawful intercept) |
| **Internal Compliance Programme (ICP)** | Companies should implement ICPs to manage export compliance |
| **EU General Export Authorizations** | Pre-approved authorizations for low-risk exports to certain countries |
| **Due Diligence** | Exporters must conduct due diligence on the end-use and end-user |

**Recent Updates (2024–2025):**
- Expanded restrictions on **technology transfers to Russia** (in response to Ukraine conflict)
- Enhanced controls on **semiconductor equipment** exports
- New guidance on **AI-related dual-use technologies**
- Updated sanctions lists affecting China, Iran, Russia, North Korea

### 3. India — SCOMET Controls

**Scope:**
- India's export control regime is governed by the **Foreign Trade (Development and Regulation) Act, 1992** and administered by DGFT
- The **SCOMET List** (Special Chemicals, Organisms, Materials, Equipment and Technologies) covers items requiring export licenses

**Key Features:**
| Feature | Description |
|---|---|
| **SCOMET Categories** | 0: Nuclear materials; 1: Toxic agents; 2: Munitions; 3: Dual-use (missile tech); 4–8: Various dual-use categories |
| **Category 6** | Dual-use items relevant to **nuclear technology** |
| **Category 7** | **Electronics, computers, and information technology** |
| **Category 8** | **Special materials and related equipment** |
| **IEC Requirement** | Importer-Exporter Code mandatory for all exports |
| **End-User Certificate** | Required for SCOMET items — must verify end-use and end-user |

---

## Risks

### Cross-Jurisdictional Risk Matrix
| Risk | US Impact | EU Impact | India Impact |
|---|---|---|---|
| **Unauthorized Technology Transfer** | Criminal penalties up to $1M fine and 20 years imprisonment (per violation) | Up to €10M or imprisonment depending on member state | Penalties under FEMA and FTDR Act |
| **Entity List Violation** | Loss of export privileges + criminal prosecution | Sanctions for listed entities | DGFT penalties + blacklisting |
| **Deemed Export Violation** | Sharing controlled tech with foreign nationals without license | Member state enforcement | SCOMET violation penalties |
| **Sanctions Violation** | OFAC enforcement — severe monetary penalties + imprisonment | EU sanctions regime — asset freezing + trade ban | UN sanctions + India-specific restrictions |
| **Re-export Violation** | BIS enforcement even for non-US persons/entities | EU re-export controls | India SCOMET re-export requirements |

### Technology-Specific Risk Scenarios
1. **AI/ML Model Exports** — Advanced AI models may be subject to export controls, especially if trained for dual-use purposes (military, surveillance)
2. **Encryption Software** — Category 5 Part 2 controls on encryption technology (key length, algorithm strength)
3. **Cloud Computing** — Hosting controlled technology on cloud platforms accessible from sanctioned countries may constitute a deemed export/re-export
4. **Open Source** — While generally exempt from EAR, certain open-source encryption software may still be subject to notification requirements
5. **Technical Presentations** — Sharing controlled technical data at international conferences can constitute a deemed export
6. **Manufacturing Technology Transfers** — Sharing manufacturing processes with foreign vendors (e.g., in China or India) may require licenses

### Sanctioned Countries (High-Risk)
| Country | US Restrictions | EU Restrictions | India Restrictions |
|---|---|---|---|
| **China** | Entity List restrictions, AI chip ban, semiconductor equipment ban | Enhanced dual-use controls | Generally aligned with Wassenaar |
| **Russia** | Comprehensive sanctions since 2022 | Comprehensive sanctions since 2022 | Selective alignment |
| **Iran** | Comprehensive embargo | Comprehensive sanctions | UN sanctions compliance |
| **North Korea** | Total embargo | Total embargo | UN sanctions compliance |
| **Myanmar** | Targeted sanctions | Targeted sanctions | Limited restrictions |

---

## Mitigations

### Export Control Compliance Program (ECCP)

**1. Management Commitment**
- Board-level ownership of export compliance
- Dedicated export compliance officer/team
- Budget allocation for compliance tools and training

**2. Risk Assessment**
- Classify all products, software, and technology against:
  - US CCL (ECCN classification)
  - EU Control List
  - India SCOMET List
- Screen all customers, vendors, and partners against:
  - US Entity List, Denied Persons List, SDN List
  - EU Consolidated Sanctions List
  - UN Security Council sanctions
- Conduct end-use/end-user assessments for controlled items

**3. Operational Controls**
| Control | Description |
|---|---|
| **Classification Review** | All new products/technologies classified before export |
| **License Management** | Track and manage all export licenses; ensure conditions are met |
| **Screening** | Automated screening of all parties against denial lists (weekly updates) |
| **Deemed Export Controls** | Track foreign nationals' access to controlled technology; obtain licenses as needed |
| **Record Keeping** | Maintain export records for minimum 5 years (US: 5 years; EU: varies; India: as prescribed) |
| **Technology Access Controls** | Restrict access to controlled technology (physical and digital access controls) |
| **Training** | Annual export compliance training for all relevant employees |

**4. Technology-Specific Controls**
- **Source code access** — Restrict repository access based on nationality/jurisdiction screening
- **Encryption** — Classify encryption capabilities; obtain TSU (Technology and Software Unrestricted) exception or license as needed
- **AI models** — Assess dual-use potential; document classification rationale
- **Cloud deployments** — Ensure controlled technology is not accessible from sanctioned countries; use data residency controls
- **Vendor due diligence** — Screen foreign vendors and their personnel; include export compliance clauses in contracts

**5. Audit and Monitoring**
- Annual internal audit of export compliance program
- Periodic external audit by export control specialists
- Continuous monitoring of regulatory changes (BIS Federal Register notices, EU Official Journal, DGFT notifications)
- Immediate incident investigation and voluntary self-disclosure for violations

---

## Recent Regulatory Developments (2024–2025)

> **Note:** The entries below describe the general direction of regulatory developments. Specific dates, entity counts, and policy details should be verified against official government publications (US Federal Register, EU Official Journal, India DGFT notifications). This area is evolving rapidly.

| Period | Development | Impact |
|---|---|---|
| **2024** | US BIS has progressively tightened AI chip export controls, including expanded restrictions on advanced AI GPUs to certain countries | Affects sales to China and other countries; introduces performance-based thresholds |
| **2024** | EU has continued to expand Russia sanctions packages with additional technology restrictions | Further restricts dual-use technology transfers to Russia |
| **Ongoing (2024–2025)** | US BIS periodically adds entities to the Entity List, particularly in semiconductor and AI sectors | Over 700 Chinese entities on Entity List as of 2024 (approximate count) |
| **2024–2025** | EU and member states reviewing controls on AI-related dual-use technologies | Potential new regulation under discussion |
| **Ongoing** | India periodically updates the SCOMET List via DGFT notifications | Organizations should monitor DGFT website for current list |
| **Ongoing** | US-EU coordination on semiconductor export controls | Aligned approach to restricting advanced chip technology exports |
