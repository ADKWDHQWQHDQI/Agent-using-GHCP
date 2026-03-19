# GDPR Article 44 — International Data Transfers

**Source:** European Parliament and Council of the European Union
**Reference:** Regulation (EU) 2016/679, Chapter V (Articles 44–49)
**Official URL:** https://gdpr-info.eu/art-44-gdpr/
**Enforcement Date:** May 25, 2018
**Last Reviewed:** March 2026

---

## Overview

**Chapter V of the GDPR (Articles 44–49)** establishes the legal framework for transferring personal data from the European Economic Area (EEA) to **third countries** (countries outside the EEA) or international organizations. The fundamental principle is that the **level of protection guaranteed by the GDPR must not be undermined** when personal data leaves the EEA.

Article 44 sets the **general principle**: any transfer of personal data to a third country or international organization shall take place **only if the conditions laid down in Chapter V are complied with** by the controller and processor, including for onward transfers.

This regulation is critical for any organization that:
- Uses cloud services hosted outside the EEA
- Engages vendors or sub-processors in non-EEA countries
- Transfers employee data to parent companies outside the EEA
- Shares data with international business partners
- Uses AI/analytics platforms that process data outside the EEA

---

## Key Rules

### 1. Article 44 — General Principle for Transfers
> "Any transfer of personal data which are undergoing processing or are intended for processing after transfer to a third country or to an international organisation shall take place only if, subject to the other provisions of this Regulation, the conditions laid down in this Chapter are complied with by the controller and processor, including for onward transfers of personal data from the third country or an international organisation to another third country or to another international organisation."

**Key points:**
- Applies to **all forms of personal data** (names, emails, IP addresses, device IDs, behavioral data, etc.)
- Covers both **active transfers** (sending data) and **passive access** (e.g., remote access by a team in a third country)
- Applies to **onward transfers** — if data is sent to Country A, and then forwarded to Country B, both transfers must comply
- The **controller bears primary responsibility** for ensuring compliant transfers

### 2. Article 45 — Adequacy Decisions
- The European Commission can **determine that a third country provides an adequate level of data protection**
- Transfers to adequate countries **do not require additional safeguards**
- Current adequacy decisions cover (as of March 2026):
  - Andorra, Argentina, Canada (PIPEDA), Faroe Islands, Guernsey, Israel, Isle of Man, Japan, Jersey, New Zealand, Republic of Korea, Switzerland, United Kingdom, Uruguay
  - **United States** — EU-U.S. Data Privacy Framework (adopted July 10, 2023)
- **China, India, Singapore, Brazil, and most other countries do NOT have adequacy decisions**

### 3. Article 46 — Appropriate Safeguards
In the absence of an adequacy decision, transfers may occur if **appropriate safeguards** are provided:

| Safeguard | Description | Approval Required? |
|---|---|---|
| **Standard Contractual Clauses (SCCs)** | EU Commission-approved contract templates (updated June 2021) | No |
| **Binding Corporate Rules (BCRs)** | Intra-group data transfer policies approved by supervisory authority | Yes — by Lead DPA |
| **Codes of Conduct** | Sector-specific codes with binding commitments by the third-country recipient | Yes — by DPA |
| **Certification Mechanisms** | Approved certification schemes under Article 42 | Yes — by DPA |
| **Ad Hoc Contractual Clauses** | Custom contractual clauses between parties | Yes — by DPA |
| **Administrative Arrangements** | Arrangements between public authorities/bodies | Yes — by DPA |

**Standard Contractual Clauses (SCCs)** are the most widely used safeguard mechanism. The June 2021 updated SCCs include four modules:
- **Module 1:** Controller → Controller
- **Module 2:** Controller → Processor
- **Module 3:** Processor → Sub-processor
- **Module 4:** Processor → Controller

### 4. Article 49 — Derogations
Transfers may occur without adequacy decisions or safeguards in **limited circumstances**:
- Explicit consent of the data subject (after being informed of risks)
- Necessary for performance of a contract with the data subject
- Necessary for important reasons of public interest
- Necessary for legal claims
- Necessary to protect vital interests
- Transfer from a public register

**These derogations are for occasional transfers only and cannot be used for systematic/repeated transfers.**

### 5. Transfer Impact Assessments (TIAs)
Post-Schrems II, organizations using SCCs or BCRs must conduct a **Transfer Impact Assessment** to evaluate:
- The laws and practices of the third country (particularly government surveillance powers)
- Whether the safeguards in the SCCs/BCRs are effective in practice
- Whether supplementary measures are needed (technical, organizational, or contractual)

---

## Risks

### Non-Compliance Risks
| Risk | Description | Potential Penalty |
|---|---|---|
| **Administrative Fines** | Up to **€20 million or 4% of global annual turnover** (whichever is higher) | Critical |
| **Data Transfer Ban** | Supervisory authority can order suspension of data transfers | Critical |
| **Reputational Damage** | Public enforcement actions, negative media coverage | High |
| **Contractual Liability** | Breach of data processing agreements with EEA clients | High |
| **Individual Claims** | Data subjects can claim compensation for damages | Medium-High |
| **Criminal Penalties** | Some EU member states impose criminal penalties for serious GDPR violations | High |

### High-Risk Transfer Scenarios
1. **Data processed by a vendor in China** — No adequacy decision, stringent Chinese data localization laws, government access concerns
2. **Data processed by a vendor in India** — No adequacy decision, DPDP Act in early implementation, government access powers under Section 36
3. **Cloud services with US-based infrastructure** — Covered by EU-US Data Privacy Framework (if the US organization is certified), but subject to ongoing legal challenges
4. **AI/ML training using EEA personal data in a third country** — Creates systematic transfer requiring robust safeguards
5. **Remote access by offshore support teams** — Constitutes a transfer even if data is not "sent" abroad

---

## Mitigations

### Step-by-Step Transfer Compliance

**Step 1: Map Your Data Transfers**
- Identify all personal data flows leaving the EEA
- Document: data categories, recipients, destination countries, legal basis, safeguards

**Step 2: Verify the Legal Basis**
- Check if the destination country has an adequacy decision
- If not, determine which safeguard mechanism applies (SCCs are most common)

**Step 3: Conduct a Transfer Impact Assessment (TIA)**
- Assess the legal framework of the destination country
- Evaluate government access powers, rule of law, data protection enforcement
- Document the assessment and conclusions

**Step 4: Implement Supplementary Measures (if needed)**
- **Technical:** End-to-end encryption (where the key is retained in the EEA), pseudonymization, split processing
- **Organizational:** Access limitations, transparency reporting, breach notification procedures
- **Contractual:** Additional clauses covering government access requests, audit rights, data minimization

**Step 5: Execute the Appropriate Safeguard**
- Sign SCCs (using the June 2021 modules)
- Implement BCRs (for intra-group transfers)
- Obtain certification or code of conduct commitment

**Step 6: Ongoing Monitoring**
- Reassess TIAs when laws change in the destination country
- Monitor enforcement actions and guidelines from EDPB
- Update SCCs or supplementary measures as needed

### Technical Safeguards for Cross-Border Transfers
1. **Encryption in transit and at rest** — AES-256 at rest, TLS 1.3 in transit
2. **Pseudonymization** — Replace identifiers with tokens; decryption key retained in EEA
3. **Data minimization** — Transfer only the minimum personal data necessary
4. **Access controls** — Restrict access by third-country personnel to what is strictly necessary
5. **Audit logging** — Log all access to personal data by third-country recipients
6. **Data segmentation** — Separate EEA personal data from other data in third-country systems

---

## Adequacy Decision Reference Table

| Country/Territory | Adequacy Status | Key Notes |
|---|---|---|
| United States | Adequate (EU-U.S. DPF) | Only for certified organizations; subject to legal challenge |
| United Kingdom | Adequate | Reviewed every 4 years; current decision valid until June 2025 (expected renewal) |
| Japan | Adequate | Mutual adequacy since January 2019 |
| South Korea | Adequate | Since December 2021 |
| Canada | Adequate (PIPEDA) | Limited to commercial organizations covered by PIPEDA |
| Israel | Adequate | Since January 2011 |
| Switzerland | Adequate | Since various dates |
| China | **Not Adequate** | Requires SCCs + TIA + supplementary measures |
| India | **Not Adequate** | Requires SCCs + TIA; DPDP Act may support future adequacy |
| Singapore | **Not Adequate** | Requires safeguards despite strong PDPA |
| Brazil | **Not Adequate** | LGPD exists but no adequacy decision yet |
| Australia | **Not Adequate** | Requires safeguards despite Privacy Act |
| Russia | **Not Adequate** | High risk — significant government access powers |

---

## Key EDPB Guidelines on Transfers

1. **Recommendations 01/2020** (adopted June 2021) — Supplementary measures for international transfers
2. **Recommendations 02/2020** — European Essential Guarantees for surveillance measures
3. **Guidelines 05/2021** — Interplay between Article 3 (territorial scope) and Chapter V (transfers)

> **Important:** The mere fact that a cloud provider is headquartered in a third country does not automatically constitute a transfer if the data is processed within the EEA. However, if the cloud provider's staff or systems in a third country can access the data, it constitutes a transfer.
