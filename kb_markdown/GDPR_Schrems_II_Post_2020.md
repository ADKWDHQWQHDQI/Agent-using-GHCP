# GDPR Schrems II — Post-2020 Implications

**Source:** Court of Justice of the European Union (CJEU)
**Reference:** Case C-311/18 — Data Protection Commissioner v. Facebook Ireland Ltd and Maximillian Schrems (July 16, 2020)
**Related:** EDPB Recommendations 01/2020, EU Commission SCCs (June 2021), EU-U.S. Data Privacy Framework (July 2023)
**Last Reviewed:** March 2026

---

## Overview

On **July 16, 2020**, the Court of Justice of the European Union (CJEU) issued its landmark ruling in **Schrems II (Case C-311/18)**, which fundamentally reshaped international data transfers from the EU. The ruling:

1. **Invalidated the EU-US Privacy Shield** — The adequacy decision allowing transfers to Privacy Shield-certified US organizations was struck down, effective immediately, with no grace period.

2. **Upheld Standard Contractual Clauses (SCCs)** — SCCs remain valid as a transfer mechanism, but with an important condition: organizations must assess whether the SCCs can be given **practical effect** in the recipient country.

3. **Introduced a case-by-case assessment obligation** — Before relying on SCCs (or BCRs), organizations must assess the legal framework of the recipient country and determine if supplementary measures are needed.

This ruling has had far-reaching implications beyond US transfers, affecting **all transfers to any non-adequate country** including China, India, Singapore, Brazil, and others.

---

## Key Rules

### 1. Privacy Shield Invalidation
- The CJEU found that US surveillance laws (particularly **Section 702 of FISA** and **Executive Order 12333**) were not limited to what is "strictly necessary" and lacked adequate judicial oversight
- The **Privacy Shield Ombudsperson mechanism** was found insufficient to provide effective legal remedies to EU data subjects
- **All organizations relying on Privacy Shield had to immediately find an alternative legal basis** for their US data transfers

### 2. Enhanced Obligations When Using SCCs
While SCCs were upheld as valid, the court established that:

- **Data exporters must verify, on a case-by-case basis**, that the third country's legal framework does not impinge on the protection SCCs are designed to provide
- If the third country's laws (e.g., surveillance legislation) **prevent the SCC commitments from being fulfilled**, the exporter must implement **supplementary measures** to ensure equivalent protection
- If supplementary measures are also insufficient, the **transfer must be suspended or terminated**
- **Supervisory authorities** have a duty to suspend or prohibit transfers they find to be non-compliant

### 3. Transfer Impact Assessment (TIA) Requirements
Post-Schrems II, every SCC-based transfer requires a documented TIA covering:

| TIA Element | Assessment Requirements |
|---|---|
| **Data Transfer Mapping** | What personal data is being transferred? Volume, categories, sensitivity |
| **Recipient Country Assessment** | Legal framework analysis — government access laws, surveillance powers, rule of law |
| **Effectiveness of SCCs** | Can the specific SCC clauses be complied with in practice given the local legal framework? |
| **Supplementary Measures** | If SCCs alone are insufficient, what additional measures can bridge the gap? |
| **Residual Risk Assessment** | After supplementary measures, does residual risk remain? If so, transfer must be suspended |
| **Documentation** | All assessments must be documented and available for supervisory authority review |

### 4. Supplementary Measures (EDPB Recommendations 01/2020)

The EDPB identified three categories of supplementary measures:

**Technical Measures:**
- End-to-end encryption where the decryption key is retained solely by the EEA exporter
- Pseudonymization where only the EEA exporter holds the re-identification key
- Split or multi-party processing so no single entity in the third country can access complete personal data
- Transport encryption (TLS 1.3) combined with encryption at rest (AES-256)

**Organizational Measures:**
- Internal policies for governance of transfers
- Transparency and accountability requirements on the data importer
- Minimization of data transferred
- Restrictions on onward transfers
- Staff training and awareness programs

**Contractual Measures:**
- Obligation on the data importer to notify the exporter of any government access request
- Commitment to challenge disproportionate government access requests through legal channels
- Agreement to compensate data subjects for harm resulting from non-compliance
- Enhanced audit rights for the data exporter
- Obligation to inform the exporter if the data importer can no longer comply with SCCs

### 5. EU-U.S. Data Privacy Framework (DPF) — Post-Schrems II Resolution
- On **July 10, 2023**, the EU Commission adopted an **adequacy decision for the USA** under the EU-U.S. Data Privacy Framework
- This addresses the Schrems II concerns through:
  - **Executive Order 14086** (October 2022) — Limits US intelligence access to what is "necessary and proportionate"
  - **Data Protection Review Court (DPRC)** — Independent redress mechanism for EU data subjects
  - **Certification mechanism** — US organizations must self-certify compliance with DPF principles
- **Limitations:**
  - Only applies to transfers to **DPF-certified** US organizations
  - Subject to potential legal challenge (informally called "Schrems III")
  - Must be reviewed periodically by the EU Commission
  - Organizations should still conduct TIAs and have contingency plans

---

## Risks

### Post-Schrems II Risk Landscape
| Risk | Description | Severity |
|---|---|---|
| **Enforcement Fines** | DPAs actively enforcing Schrems II — fines up to €20M / 4% turnover | Critical |
| **Transfer Suspension Orders** | DPAs can order immediate suspension of non-compliant transfers | Critical |
| **Legal Uncertainty** | EU-US DPF may be challenged (Schrems III), creating renewed uncertainty | High |
| **Operational Disruption** | If transfers are suspended, business operations relying on third-country processing are disrupted | High |
| **Supply Chain Risk** | Even if your transfers comply, your processors'/sub-processors' transfers may not | High |
| **Reputation Risk** | NOYB and other advocacy groups actively filing complaints — public enforcement actions | Medium-High |

### Notable Schrems II Enforcement Actions
| Authority | Entity | Issue | Outcome |
|---|---|---|---|
| Austrian DPA | Austrian website operator | Google Analytics transfers to US | Found unlawful (January 2022) |
| French CNIL | French website operator | Google Analytics transfers to US | Found unlawful (February 2022) |
| Italian Garante | Italian website operator | Google Analytics transfers to US | Found unlawful (June 2022) |
| Irish DPC | Meta Platforms | Facebook EU-US data transfers | €1.2 billion fine (May 2023) — largest GDPR fine ever |
| EDPS | European Commission | Use of Microsoft 365 | Found to infringe GDPR transfer provisions (March 2024) |

### Countries of Particular Concern

> **Note:** The risk levels below are **editorial assessments** based on publicly known government access powers and data protection frameworks. They are NOT official ratings from the EDPB, any EU supervisory authority, or any other regulatory body. Organizations should conduct their own Transfer Impact Assessments.

| Country | Risk Level (Editorial) | Key Concerns |
|---|---|---|
| **China** | Very High | Broad government access powers under National Intelligence Law (2017), Cybersecurity Law, Data Security Law |
| **Russia** | Very High | Extensive surveillance, limited rule of law, data localization requirements |
| **India** | High | Government access powers under IT Act Section 69/69A, DPDP Act Section 36 |
| **USA** | Medium* | Addressed by EU-US DPF, but still subject to FISA Section 702, EO 12333 |
| **Singapore** | Medium | PDPA exists but no adequacy, limited government access oversight |
| **Brazil** | Medium | LGPD exists, ANPD established, but no adequacy decision yet |

*Medium risk for DPF-certified organizations; High for non-certified*

---

## Mitigations

### Immediate Actions Post-Schrems II
1. **Audit all international data transfers** — Create a comprehensive data transfer mapping
2. **Identify the legal basis for each transfer** — Adequacy decision, SCCs, BCRs, or derogation
3. **Conduct Transfer Impact Assessments** for all SCC/BCR-based transfers
4. **Implement supplementary measures** where TIA identifies gaps
5. **Update SCCs to the June 2021 version** — Deadline for existing contracts was December 27, 2022
6. **Review sub-processor chains** — Ensure processors' onward transfers also comply

### For US Transfers Specifically
1. **Verify DPF certification** of the US recipient at [dataprivacyframework.gov](https://www.dataprivacyframework.gov)
2. **Maintain contingency plans** in case DPF is invalidated (Schrems III)
3. **Consider data localization** to EEA where feasible (e.g., Azure EU Data Boundary, AWS EU sovereign cloud)
4. **Implement technical measures** — encryption with EEA-held keys, pseudonymization

### For China / India / Other Non-Adequate Country Transfers
1. **Use the June 2021 SCCs** with the appropriate module
2. **Conduct a thorough TIA** focusing on government access laws
3. **Implement robust technical measures** — end-to-end encryption, pseudonymization
4. **Explore EEA-based alternatives** where possible (e.g., EEA-based vendor, local data center)
5. **Minimize data transferred** — only send what is strictly necessary
6. **Document everything** — supervisory authorities expect detailed TIA documentation

### Governance and Compliance Framework
1. **DPO involvement** — Data Protection Officer should oversee all cross-border transfer compliance
2. **Regular TIA reviews** — Re-assess when laws change in recipient countries
3. **Vendor management** — Include Schrems II compliance in vendor onboarding and ongoing assessments
4. **Training** — Ensure relevant teams understand the Schrems II obligations
5. **Incident response** — Plan for scenarios where a transfer must be suspended immediately
6. **Board reporting** — Include cross-border data transfer risk in regular board/management reporting

---

## Timeline of Key Events

| Date | Event |
|---|---|
| **October 2015** | CJEU invalidates Safe Harbor (Schrems I) |
| **August 2016** | EU-US Privacy Shield adopted |
| **July 16, 2020** | CJEU invalidates Privacy Shield (Schrems II) |
| **November 2020** | EDPB publishes Recommendations 01/2020 (supplementary measures) |
| **June 4, 2021** | EU Commission adopts new SCCs |
| **June 18, 2021** | EDPB finalizes Recommendations 01/2020 |
| **September 27, 2021** | Deadline to use new SCCs for new contracts |
| **December 27, 2022** | Deadline to update existing contracts to new SCCs |
| **October 7, 2022** | US issues Executive Order 14086 |
| **July 10, 2023** | EU-U.S. Data Privacy Framework adequacy decision adopted |
| **May 22, 2023** | Meta fined €1.2 billion for non-compliant US transfers |
| **March 2024** | EDPS finds EU Commission's use of Microsoft 365 non-compliant |
| **2025–2026** | Ongoing monitoring for potential Schrems III challenge |
