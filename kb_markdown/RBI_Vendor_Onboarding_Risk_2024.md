# RBI Vendor Onboarding Risk Guidelines 2024

**Source:** Reserve Bank of India (RBI)
**Reference:** Master Direction on Outsourcing of Information Technology Services (RBI Department of Supervision)
**Note:** This document summarizes provisions from RBI's Master Direction on Outsourcing of IT Services and related guidelines. Readers should verify specific circular reference numbers directly on the RBI website, as reference numbers are periodically updated.
**Related:** RBI Guidelines on Managing Risks and Code of Conduct in Outsourcing of Financial Services (2006, updated)
**Official URL:** https://www.rbi.org.in/Scripts/BS_ViewMasDirections.aspx
**Last Reviewed:** March 2026

---

## Overview

The Reserve Bank of India has issued comprehensive guidelines for **evaluating and managing third-party vendor risks**, particularly those providing **technology and IT services** to regulated entities (banks, NBFCs, payment system operators). The 2024 updated framework strengthens requirements around:

- **Due diligence** before vendor onboarding
- **Ongoing monitoring** of vendor performance and risk exposure
- **Business continuity and exit management** for critical technology vendors
- **Concentration risk** from over-reliance on a single vendor
- **Data security and privacy** obligations of vendors handling customer data

These guidelines are critical for any financial institution or fintech company that outsources technology services including cloud computing, data analytics, AI/ML platforms, cybersecurity, and payment processing.

---

## Key Rules

### 1. Board-Level Oversight
- The **Board of Directors** must approve and periodically review the outsourcing policy
- A **designated senior management committee** must oversee vendor relationships
- The Board must be informed of **all material outsourcing arrangements**, especially those involving:
  - Customer-facing services
  - Critical business operations
  - Sensitive data handling (payment, financial, personal data)
  - Cross-border service delivery

### 2. Pre-Onboarding Due Diligence
- **Mandatory risk assessment** before engaging any technology vendor:

| Assessment Area | Requirements |
|---|---|
| **Financial Stability** | Review audited financial statements (3 years), credit ratings, solvency ratios |
| **Operational Capability** | Verify technical infrastructure, staffing, certifications (ISO 27001, SOC 2) |
| **Regulatory Compliance** | Check vendor's regulatory track record, any enforcement actions |
| **Information Security** | Assess cybersecurity posture — VAPT reports, incident history, data protection practices |
| **Business Continuity** | Review BCP/DR plans, RTO/RPO capabilities, geographic redundancy |
| **Concentration Risk** | Evaluate if the vendor already serves multiple critical functions or competitors |
| **Country Risk** | For foreign vendors — assess geopolitical, legal, and data protection risks |
| **Sub-contracting** | Identify any sub-contractors and apply same due diligence standards |

### 3. Contractual Requirements
Contracts with technology vendors **must include** the following clauses:

1. **Scope of services** — Clear, detailed statement of services to be provided
2. **Service Level Agreements (SLAs)** — Measurable performance metrics with penalties for non-compliance
3. **Data ownership** — Explicit statement that **all customer data remains the property of the regulated entity**
4. **Data localization** — For payment/financial data, storage must be in India (per RBI data localization circular)
5. **Right to audit** — The regulated entity and RBI must have the right to audit the vendor at any time
6. **RBI access** — Vendor must cooperate with RBI inspections and provide requested information
7. **Confidentiality** — Strict confidentiality obligations surviving contract termination
8. **Incident reporting** — Vendor must report security incidents within **6 hours** of detection
9. **Business continuity** — Vendor must maintain tested BCP/DR plans
10. **Exit management** — Clear data return/destruction procedures, transition support obligations, minimum notice period
11. **Sub-contracting restrictions** — Prior approval required for any sub-contracting of services
12. **Indemnity** — Vendor indemnification for losses arising from vendor negligence or breach

### 4. Ongoing Monitoring Requirements
- **Annual vendor risk assessment** — Review and update the initial due diligence
- **Quarterly SLA review** — Monitor vendor performance against agreed metrics
- **Incident tracking** — Maintain a log of all vendor-related incidents, security events, and near-misses
- **On-site audits** — Conduct periodic on-site audits of critical vendors (at least annually)
- **Concentration risk review** — Semi-annual review of dependency on individual vendors
- **Regulatory compliance monitoring** — Track changes in vendor's regulatory status

### 5. Cloud Services — Specific Requirements
RBI has issued specific guidelines for **cloud outsourcing by regulated entities**:

1. **Data must reside in India** — Cloud providers must offer Indian data center options (Azure India Central/South, AWS Mumbai, etc.)
2. **Multi-cloud or hybrid strategy** — Avoid lock-in to a single cloud provider for critical services
3. **Encryption** — Customer data must be encrypted at rest (AES-256) and in transit (TLS 1.2+)
4. **Key management** — Encryption keys must be managed by the regulated entity, not the cloud provider
5. **Access controls** — Implement IAM with MFA for all cloud access, principle of least privilege
6. **Logging and monitoring** — Enable comprehensive audit logging; logs must be stored in India
7. **Incident response** — Cloud provider must support the regulated entity's incident response procedures
8. **Exit plan** — Documented plan for migrating away from the cloud provider within defined timelines

---

## Risks

### Vendor Risk Categories
| Risk Type | Description | Rating |
|---|---|---|
| **Operational Risk** | Vendor service disruption affecting business operations | Critical |
| **Data Security Risk** | Vendor data breach exposing customer data | Critical |
| **Compliance Risk** | Vendor non-compliance with RBI regulations affecting the regulated entity | High |
| **Concentration Risk** | Over-dependence on a single technology vendor | High |
| **Strategic Risk** | Vendor's business strategy diverging from the regulated entity's needs | Medium |
| **Reputational Risk** | Vendor's actions causing reputational harm to the regulated entity | High |
| **Country Risk** | Foreign vendor subject to adverse foreign regulatory or geopolitical changes | Medium-High |
| **Sub-contractor Risk** | Vendor's sub-contractors introducing unassessed risks | High |
| **Lock-in Risk** | Inability to switch vendors due to technical dependencies | Medium |
| **Financial Risk** | Vendor financial instability threatening service continuity | High |

### High-Risk Vendor Scenarios
1. **AI/ML vendor processing customer data abroad** — Violates data localization + creates cross-border transfer risk
2. **Single cloud provider for all critical workloads** — Creates concentration risk with no fallback
3. **Vendor with sub-contractors in restricted jurisdictions** — Introduces unknown country and data risks
4. **Startup vendor without adequate financial stability** — Risk of sudden business closure
5. **Vendor with history of security incidents** — Elevated risk of data breaches

---

## Mitigations

### Vendor Onboarding Framework
1. **Tiered risk classification** — Classify vendors as Critical, High, Medium, or Low risk based on:
   - Data sensitivity (payment data, PII, financial records)
   - Business criticality (core operations vs. support functions)
   - Replaceability (ease of switching to an alternate vendor)
   - Geographic location (domestic vs. foreign, restricted jurisdictions)

2. **Enhanced due diligence for Critical/High vendors:**
   - On-site security assessment
   - Independent third-party VAPT report
   - Reference checks with other clients
   - Background checks on key personnel
   - Review of disaster recovery capabilities via tabletop exercise

3. **Standard due diligence for Medium/Low vendors:**
   - Self-assessment questionnaire
   - Review of certifications (ISO 27001, SOC 2)
   - Financial statement review
   - Contract review

### Ongoing Controls
1. **Vendor scorecards** — Maintain quarterly performance scorecards tracking SLAs, incidents, compliance, and financials
2. **Risk register** — Document and track all identified vendor risks with mitigation owners and timelines
3. **Escalation matrix** — Define clear escalation paths for vendor issues (operational, security, compliance)
4. **Annual vendor summit** — Conduct formal annual business review with critical vendors
5. **Exit readiness** — Maintain and test exit plans for critical vendors at least annually

### Regulatory Compliance
1. **Register of outsourcing arrangements** — Maintain a complete register as required by RBI
2. **RBI reporting** — Report material outsourcing arrangements to RBI as directed
3. **Audit support** — Ensure vendors are contractually obligated to support RBI audits
4. **Board reporting** — Quarterly board updates on vendor risk posture

---

## Vendor Risk Scoring Template

> **Note:** The following scoring template is an **illustrative example** for organizations to adapt. The weights, scales, and thresholds below are NOT prescribed by RBI. RBI requires a risk-based classification approach but does not mandate specific scoring formulas or factor weights. Organizations should design their own methodology appropriate to their context.

| Factor | Weight (Illustrative) | Score (1-5) | Weighted Score |
|---|---|---|---|
| Data Sensitivity | 25% | __ | __ |
| Business Criticality | 20% | __ | __ |
| Financial Stability | 15% | __ | __ |
| Security Posture | 20% | __ | __ |
| Geographic Risk | 10% | __ | __ |
| Concentration Risk | 10% | __ | __ |
| **Total** | **100%** | | __ |

**Risk Rating:**
- **4.0 – 5.0:** Critical Risk — Board approval required, enhanced monitoring
- **3.0 – 3.9:** High Risk — Senior management approval, quarterly reviews
- **2.0 – 2.9:** Medium Risk — Standard monitoring, annual reviews
- **1.0 – 1.9:** Low Risk — Periodic review, standard controls
