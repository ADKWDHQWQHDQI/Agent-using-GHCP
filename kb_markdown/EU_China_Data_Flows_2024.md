# EU-China Data Flows 2024

**Sources:**
- European Data Protection Board (EDPB): https://edpb.europa.eu
- European Commission — Trade Policy: https://ec.europa.eu
- People's Republic of China — Cyberspace Administration of China (CAC): http://www.cac.gov.cn
**Related Legislation:**
- EU: GDPR (Chapter V), EU-China Comprehensive Agreement on Investment (CAI) — suspended
- China: Personal Information Protection Law (PIPL), Data Security Law (DSL), Cybersecurity Law (CSL)
**Last Reviewed:** March 2026

---

## Overview

Data transfers between the **European Union and China** are among the most complex and high-risk cross-border data flow scenarios globally. Organizations must navigate **two overlapping and sometimes conflicting regulatory regimes**:

1. **EU Side (GDPR):** China does **not** have an adequacy decision from the EU Commission. All transfers of personal data from the EU to China require **Standard Contractual Clauses (SCCs)**, **Transfer Impact Assessments (TIAs)**, and potentially **supplementary measures**.

2. **China Side (PIPL/DSL/CSL):** China's data protection framework imposes its own **outbound data transfer restrictions**, including requirements for **security assessments**, **standard contracts**, and **certification** for transferring Chinese personal information abroad.

This creates a **dual compliance challenge**: organizations must simultaneously satisfy EU requirements to protect data sent to China AND Chinese requirements to protect data sent out of China.

---

## Key Rules

### 1. EU → China Transfers (GDPR Perspective)

**No Adequacy Decision:**
- China is **not recognized as providing adequate data protection** under GDPR Article 45
- EU considers Chinese government surveillance powers (particularly under the National Intelligence Law, Cybersecurity Law, and Counter-Espionage Law) as problematic for data protection

**Required Safeguards:**
| Requirement | Details |
|---|---|
| **Standard Contractual Clauses (SCCs)** | Must use the June 2021 EU Commission SCCs (appropriate module) |
| **Transfer Impact Assessment (TIA)** | Must assess Chinese legal framework, particularly government access laws |
| **Supplementary Measures** | Likely required — encryption with EU-held keys, pseudonymization, data minimization |
| **Documentation** | TIA and supplementary measures must be documented and available for DPA review |

**Key Chinese Laws Impacting TIA:**
| Chinese Law | Concern for EU Transfers |
|---|---|
| **National Intelligence Law (2017)** | Article 7: All organizations and citizens shall support, assist, and cooperate with national intelligence work |
| **Cybersecurity Law (2017)** | Article 28: Network operators shall provide technical support and assistance to public security organs |
| **Data Security Law (2021)** | Article 36: Approval required for providing data stored in China to foreign judicial or enforcement bodies |
| **Counter-Espionage Law (2023, amended)** | Broadened definition of espionage and data access powers |
| **PIPL (2021)** | Article 41: Government access to personal information for law enforcement purposes |

### 2. China → EU Transfers (PIPL Perspective)

China's **Personal Information Protection Law (PIPL)**, effective November 1, 2021, imposes restrictions on transferring personal information outside of China:

**Three Pathways for Outbound Transfers:**
| Pathway | Description | Trigger |
|---|---|---|
| **CAC Security Assessment** | Mandatory government review by Cyberspace Administration of China | Required for: Critical Information Infrastructure Operators (CIIOs); processing personal info of 1M+ individuals; transferring 100K+ persons' data or 10K+ persons' sensitive data since Jan 1 of preceding year |
| **Standard Contract Filing** | Sign China's own Standard Contract for outbound transfers and file with provincial CAC office | For below-threshold transfers (not CIIO; processing < 1M individuals' data) |
| **Personal Information Protection Certification** | Obtain certification from an accredited institution | Alternative for affiliated companies or below-threshold transfers |

**Additional PIPL Requirements for Cross-Border Transfers:**
- **Informed consent** — Separate consent for cross-border transfer (Article 39)
- **Personal Information Impact Assessment (PIIA)** — Mandatory before transfer (Article 55)
- **Data localization** — CIIOs must store personal information in China; outbound transfer is only permitted after security assessment
- **Necessity principle** — Transfer must be genuinely necessary for business purposes
- **Recipient obligations** — Foreign recipient must ensure equivalent protection level

### 3. Dual Compliance Matrix

| Requirement | EU (GDPR) | China (PIPL) | Conflict? |
|---|---|---|---|
| **Legal basis for transfer** | SCCs or other Article 46 safeguard | Security assessment, standard contract, or certification | Different mechanisms — must comply with both |
| **Impact assessment** | Transfer Impact Assessment (TIA) | Personal Information Impact Assessment (PIIA) | Separate assessments required |
| **Government access** | Must assess and mitigate | Government has broad access rights (not negotiable) | Direct conflict — TIA likely finds Chinese laws problematic |
| **Data localization** | No requirement (but transfer must comply) | CIIOs must localize; others recommended | China may require data to stay in China |
| **Consent** | Not specifically required for SCCs | Separate consent required for cross-border transfer | China has stricter consent requirement |
| **Contractual obligations** | EU SCCs | China Standard Contract | Organizations may need to sign both |
| **Regulatory approval** | Not required (but DPA can intervene) | Required for large-scale or CIIO transfers | China requires affirmative approval |

---

## Risks

### Risk Assessment for EU-China Data Flows
| Risk | Description | Severity |
|---|---|---|
| **Regulatory impossibility** | Compliance with both GDPR and Chinese data access laws may be mutually exclusive in some scenarios | Critical |
| **EU enforcement** | GDPR fines up to €20M / 4% global turnover for non-compliant transfers to China | Critical |
| **Chinese enforcement** | PIPL fines up to ¥50M (~€6.5M) or 5% of annual revenue; potential business suspension | Critical |
| **Government access conflict** | Chinese law may compel disclosure of personal data that GDPR prohibits | High |
| **Data localization** | China may prevent data from leaving; EU may object to data being stored in China | High |
| **Dual compliance cost** | Maintaining parallel compliance regimes increases operational costs significantly | Medium-High |
| **Geopolitical risk** | Deteriorating EU-China relations may lead to further restrictions | Medium-High |
| **Vendor supply chain risk** | Vendors with Chinese subsidiaries or sub-processors create indirect transfer risks | High |

### Worst-Case Scenarios

> **Note:** The scenarios below are **hypothetical illustrations** of how regulatory conflicts could manifest in practice. They are not descriptions of actual events, but are based on the real legal provisions described above.

1. **Chinese government requests access to EU personal data** stored by a Chinese vendor → Complying violates GDPR; refusing may violate Chinese law
2. **EU DPA orders suspension of transfers** to Chinese processor → Business disruption if the processing is critical
3. **CAC denies security assessment** for outbound transfer → Cannot transfer Chinese data to EU systems for analytics
4. **Chinese vendor discloses EU data** to Chinese authorities → GDPR breach, potential enforcement action in EU

---

## Mitigations

### Architecture Strategies
1. **Data localization by region** — Process EU data in the EU; process Chinese data in China; minimize cross-border flows
2. **Federated processing** — Train models locally in each region rather than centralizing data
3. **Pseudonymization before transfer** — Remove direct identifiers before any cross-border transfer; retain mapping keys in the originating region
4. **Encryption with region-specific keys** — Encrypt data before transfer; decryption keys held in the originating region
5. **Proxy/gateway architecture** — Use an intermediary service in a neutral third country (e.g., Singapore, Japan) with adequacy/bilateral agreements with both EU and China

### Legal and Contractual Measures
1. **Execute both EU SCCs AND China Standard Contract** — May need to manage parallel contractual frameworks
2. **Conduct parallel TIA (GDPR) and PIIA (PIPL)** — Document assessments for both regimes
3. **Include government access notification clauses** — Require Chinese partners to notify of any government data requests (to the extent legally possible)
4. **Implement a data disclosure protocol** — Pre-agreed procedure for handling conflicting government access requests
5. **Engage local counsel in both jurisdictions** — EU data protection counsel + Chinese PIPL counsel

### Operational Controls
1. **Minimize transfers** — Transfer only the absolute minimum personal data necessary
2. **Regular compliance reviews** — Quarterly review of EU-China data flow compliance
3. **Vendor risk assessments** — Enhanced due diligence for any vendor with Chinese operations
4. **Employee awareness** — Training on dual compliance requirements for teams handling EU-China data
5. **Incident response** — Specific playbooks for government access requests affecting cross-border data
6. **Regulatory monitoring** — Track changes in both EU and Chinese data regulations

---

## Reference: China's Data Governance Framework

| Law | Effective Date | Key Focus |
|---|---|---|
| **Cybersecurity Law (CSL)** | June 1, 2017 | Network security, data localization for CIIOs, government access |
| **Data Security Law (DSL)** | September 1, 2021 | National data security review, important data categorization, cross-border restrictions |
| **Personal Information Protection Law (PIPL)** | November 1, 2021 | Personal data protection, cross-border transfer restrictions, consent requirements |
| **CAC Standard Contract Measures** | June 1, 2023 | Standard contract for cross-border personal information transfers |
| **Counter-Espionage Law (Amended)** | July 1, 2023 | Broadened espionage definitions, increased government investigatory powers |
| **CAC Security Assessment Measures** | September 1, 2022 | Mandatory security assessment for large-scale cross-border transfers |
