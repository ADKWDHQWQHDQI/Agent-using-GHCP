# Risk Assessment Frameworks — Regulatory and Standards-Based Approaches

**Sources:**
- **ISO 31000:2018** — Risk Management Guidelines (International Organization for Standardization)
- **NIST SP 800-30 Rev 1** — Guide for Conducting Risk Assessments (National Institute of Standards and Technology, September 2012)
- **GDPR Article 35** — Data Protection Impact Assessment (Regulation (EU) 2016/679)
- **EDPB Guidelines on DPIA** — WP248 rev.01, adopted October 4, 2017
- **RBI Risk Management Guidelines** — Guidelines on Risk Management and Inter-Bank Dealings (RBI/2016-17/11)
- **COSO ERM 2017** — Enterprise Risk Management — Integrating with Strategy and Performance
**Last Reviewed:** March 2026

---

## Overview

This document summarizes the **actual risk assessment methodologies** prescribed by international standards bodies and regulatory authorities. These are the frameworks that compliance teams should reference when designing risk assessment processes for regulatory compliance.

**Important:** No single universal "compliance risk score formula" exists. Each standard and regulator defines its own approach. This document describes what each framework actually prescribes, with direct citations.

---

## 1. ISO 31000:2018 — Risk Management Guidelines

### What ISO 31000 Actually Prescribes

ISO 31000:2018 provides **principles and a generic framework** for managing risk. It does NOT prescribe:
- Specific numerical scales (1–5, etc.)
- Specific formulas for calculating risk scores
- Specific risk rating thresholds

**ISO 31000 Risk Management Process (Clause 6):**

```
6.1 Communication and consultation
6.2 Scope, context, and criteria
6.3 Risk assessment
    6.3.1 Risk identification
    6.3.2 Risk analysis
    6.3.3 Risk evaluation
6.4 Risk treatment
6.5 Monitoring and review
6.6 Recording and reporting
```

### Key Definitions from ISO 31000:2018

| Term | ISO 31000 Definition |
|---|---|
| **Risk** | "Effect of uncertainty on objectives" (Clause 3.1) |
| **Risk assessment** | "Overall process of risk identification, risk analysis, and risk evaluation" (Clause 3.4) |
| **Risk analysis** | "Process to comprehend the nature of risk and to determine the level of risk" (Clause 6.3.2) |
| **Likelihood** | "Chance of something happening" (ISO Guide 73:2009, 3.6.1.1) |
| **Consequence** | "Outcome of an event affecting objectives" (ISO Guide 73:2009, 3.6.1.3) |

### ISO 31000 Risk Analysis Guidance (Clause 6.3.2)

ISO 31000:2018, Clause 6.3.2 states that risk analysis involves:
- Considering the **causes and sources of risk**, their positive and negative consequences, and the likelihood that those consequences can occur
- Factors that affect consequences and likelihood should be identified
- Risk analysis can be undertaken with **varying degrees of detail** depending on the risk, the purpose of the analysis, and the information, data, and resources available
- Analysis can be **qualitative, semi-quantitative, or quantitative**, or a combination, depending on the circumstances

**The standard explicitly allows organizations to choose their own scales and thresholds appropriate to their context.** It does not mandate any specific scoring system.

### ISO 31000:2018 — Risk Evaluation (Clause 6.3.3)

Risk evaluation involves comparing the results of risk analysis with established **risk criteria** to determine:
- Which risks need treatment
- The priority for implementing treatment
- Whether an activity should be undertaken at all

---

## 2. NIST SP 800-30 Rev 1 — Guide for Conducting Risk Assessments

### NIST's Actual Risk Model

NIST SP 800-30 Rev 1 (September 2012) provides a specific risk assessment methodology used by US federal agencies and widely adopted in the private sector.

**NIST Risk Definition:**

> "Risk is a function of the likelihood of a threat event's occurrence and potential adverse impact should the event occur."
> — NIST SP 800-30 Rev 1, p. 8

### NIST Qualitative Likelihood Scale (Table D-3)

| Value | Level | Description |
|---|---|---|
| **96-100** | Very High | "The threat event is almost certain to be initiated or to occur." |
| **80-95** | High | "The threat event is highly likely to be initiated or to occur." |
| **21-79** | Moderate | "The threat event is somewhat likely to be initiated or to occur." |
| **5-20** | Low | "The threat event is unlikely to be initiated or to occur." |
| **0-4** | Very Low | "The threat event is highly unlikely to be initiated or to occur." |

### NIST Impact Scale — Adverse Impact Levels (Table H-3)

| Value | Level | Description (per NIST SP 800-30 Table H-3) |
|---|---|---|
| **96-100** | Very High | "Multiple severe or catastrophic adverse effects on organizational operations, organizational assets, individuals, other organizations, or the Nation." |
| **80-95** | High | "Severe or catastrophic adverse effect on organizational operations, organizational assets, individuals, other organizations, or the Nation." |
| **21-79** | Moderate | "Serious adverse effect on organizational operations, organizational assets, individuals, other organizations, or the Nation." |
| **5-20** | Low | "Limited adverse effect on organizational operations, organizational assets, individuals, other organizations, or the Nation." |
| **0-4** | Very Low | "Negligible adverse effect on organizational operations, organizational assets, individuals, other organizations, or the Nation." |

### NIST Risk Determination Matrix (Table I-2)

NIST SP 800-30 Rev 1, Table I-2 provides the following risk determination:

|  | Very Low Impact | Low Impact | Moderate Impact | High Impact | Very High Impact |
|---|---|---|---|---|---|
| **Very High Likelihood** | Very Low | Low | Moderate | High | Very High |
| **High Likelihood** | Very Low | Low | Moderate | High | Very High |
| **Moderate Likelihood** | Very Low | Low | Moderate | Moderate | High |
| **Low Likelihood** | Very Low | Low | Low | Low | Moderate |
| **Very Low Likelihood** | Very Low | Very Low | Very Low | Low | Low |

*Source: NIST SP 800-30 Rev 1, Table I-2, p. I-2*

### NIST SP 800-30 Risk Assessment Process (Four Steps)

1. **Prepare for assessment** — Derive purpose, scope, assumptions, constraints, risk model, analytic approach
2. **Conduct assessment** — Identify threat sources/events, vulnerabilities, likelihood, impact, risk
3. **Communicate results** — Communicate risk assessment results and share risk-related information
4. **Maintain assessment** — Monitor risk factors, update the assessment as needed

---

## 3. GDPR Article 35 — Data Protection Impact Assessment (DPIA)

### What GDPR Actually Requires

GDPR Article 35(1):
> "Where a type of processing in particular using new technologies, and taking into account the nature, scope, context and purposes of the processing, is likely to result in a **high risk** to the rights and freedoms of natural persons, the controller shall, prior to the processing, carry out an assessment of the impact of the envisaged processing operations on the protection of personal data."

### When a DPIA Is Mandatory (Article 35(3))

A DPIA is required in particular for:
- **(a)** Systematic and extensive evaluation of personal aspects relating to natural persons, based on automated processing, including **profiling**, on which decisions are based that produce legal effects or similarly significant effects
- **(b)** Processing on a large scale of **special categories of data** (Art. 9) or personal data relating to criminal convictions and offences (Art. 10)
- **(c)** Systematic monitoring of a publicly accessible area on a **large scale**

### EDPB/WP29 Nine Criteria for DPIA (WP248 rev.01)

The Article 29 Working Party (now EDPB) identified nine criteria. Processing meeting **two or more** criteria generally requires a DPIA:

1. **Evaluation or scoring** (including profiling and predicting)
2. **Automated decision-making with legal or similar significant effect**
3. **Systematic monitoring** (observation, monitoring, or control of data subjects)
4. **Sensitive data or data of a highly personal nature** (special categories, financial, location, etc.)
5. **Data processed on a large scale** (volume of data subjects, data items, geographic extent, duration)
6. **Matching or combining datasets** (from different controllers or different purposes)
7. **Data concerning vulnerable data subjects** (children, employees, patients, elderly)
8. **Innovative use or applying new technological or organisational solutions** (fingerprint + face recognition, IoT)
9. **Processing that prevents data subjects from exercising a right or using a service or contract** (e.g., screening by bank against a credit reference database)

*Source: EDPB Guidelines on DPIA, WP248 rev.01, adopted 4 October 2017*

### Mandatory DPIA Content (Article 35(7))

The assessment must contain at least:
- **(a)** A systematic description of the envisaged processing operations and purposes, including legitimate interest pursued
- **(b)** An assessment of the **necessity and proportionality** of the processing
- **(c)** An assessment of the **risks to the rights and freedoms** of data subjects
- **(d)** The **measures envisaged to address the risks**, including safeguards, security measures, and mechanisms to ensure protection of personal data

### GDPR Risk Concepts

GDPR itself does NOT prescribe numerical risk scores. It uses the following terminology:
- **"Risk"** — GDPR Recital 75 describes risks as "physical, material or non-material damage" including discrimination, identity theft, financial loss, damage to reputation, reversal of pseudonymization, etc.
- **"High risk"** — The threshold for DPIA requirements (Art. 35) and for notification to data subjects of breaches (Art. 34)
- **"Likely to result in a risk"** — The threshold for notification to supervisory authority of breaches (Art. 33)

GDPR requires a **risk-based approach** but leaves the specific risk assessment methodology to the controller.

---

## 4. RBI Risk Management Framework

### RBI Guidelines on Risk Management (Actual Requirements)

RBI has issued risk management guidelines for regulated entities through multiple circulars and master directions:

**Risk Categories Defined by RBI:**
| Risk Type | RBI Description |
|---|---|
| **Credit Risk** | Risk of loss arising from a borrower's failure to repay |
| **Market Risk** | Risk of loss from movements in market prices (interest rates, foreign exchange, equity) |
| **Operational Risk** | Risk of loss from inadequate or failed internal processes, people, and systems, or from external events |
| **Liquidity Risk** | Risk that a bank cannot meet its obligations as they come due |
| **IT Risk** | Risk arising from use of information technology (part of operational risk) |
| **Outsourcing Risk** | Risk from third-party service providers (per Master Direction on Outsourcing of IT Services) |

**RBI's Approach to Operational Risk (Basel Framework):**
RBI follows the Basel Committee on Banking Supervision (BCBS) framework for operational risk. Under Basel III:
- **Basic Indicator Approach (BIA):** Operational risk capital = 15% of average annual gross income (over 3 years)
- **Standardised Approach (TSA):** Different beta factors (12–18%) applied to gross income across 8 business lines
- **Advanced Measurement Approaches (AMA):** Banks develop internal models subject to RBI approval

*Source: RBI Master Circular on Basel III Capital Regulations*

**RBI IT Risk Assessment Requirements (Master Direction on IT Governance):**
- Regulated entities must establish an **IT risk management framework** approved by the Board
- IT risk assessment must be conducted **annually** at minimum
- Must cover: confidentiality, integrity, and availability of information assets
- Risk assessment results must be reported to the **IT Strategy Committee** and Board

### RBI's Actual Vendor Risk Requirements

Per the Master Direction on Outsourcing of IT Services, RBI requires regulated entities to:
- Classify outsourcing arrangements by **materiality** (material vs. non-material)
- Maintain a **register of outsourcing arrangements** with risk assessments
- Conduct **due diligence** proportionate to the risk and materiality of the outsourcing arrangement

RBI does NOT prescribe specific numerical vendor risk scoring weights or formulas. It requires risk-based classification and proportionate controls.

---

## 5. SEBI Risk Management Requirements

### SEBI Operational Risk Framework for Market Infrastructure

SEBI circulars require:
- Stock exchanges, clearing corporations, and depositories to maintain **Enterprise Risk Management (ERM)** frameworks
- Listed companies (per SEBI LODR Regulation 21) must constitute a **Risk Management Committee** of the Board
- The RMC must define a **risk management policy**, monitor and review the risk management plan, and report to the Board

### SEBI LODR Regulation 21 — Risk Management Committee

Per SEBI (Listing Obligations and Disclosure Requirements) Regulations, 2015:
- Top 1000 listed entities by market capitalization must constitute a Risk Management Committee
- The committee must have a minimum of **three members**, with at least **two-thirds being members of the Board**
- The committee must meet at least **twice a year**
- Must monitor and review the risk management plan including **cyber security risks**

---

## 6. COSO ERM 2017 — Enterprise Risk Management

### COSO Framework Components (Actual)

The COSO ERM 2017 framework ("Enterprise Risk Management — Integrating with Strategy and Performance") defines **five interrelated components** and **20 principles**:

| Component | Principles |
|---|---|
| **1. Governance and Culture** | 1. Exercises Board Risk Oversight; 2. Establishes Operating Structures; 3. Defines Desired Culture; 4. Demonstrates Commitment to Core Values; 5. Attracts, Develops, and Retains Capable Individuals |
| **2. Strategy and Objective-Setting** | 6. Analyzes Business Context; 7. Defines Risk Appetite; 8. Evaluates Alternative Strategies; 9. Formulates Business Objectives |
| **3. Performance** | 10. Identifies Risk; 11. Assesses Severity of Risk; 12. Prioritizes Risks; 13. Implements Risk Responses; 14. Develops Portfolio View |
| **4. Review and Revision** | 15. Assesses Substantial Change; 16. Reviews Risk and Performance; 17. Pursues Improvement in ERM |
| **5. Information, Communication, and Reporting** | 18. Leverages Information and Technology; 19. Communicates Risk Information; 20. Reports on Risk, Culture, and Performance |

*Source: COSO, Enterprise Risk Management — Integrating with Strategy and Performance, June 2017*

### COSO's Risk Assessment Approach (Principle 11)

COSO Principle 11 states that organizations should "assess severity of risk." COSO's approach:
- Assess risk at **multiple levels** (entity, division, operating unit, function)
- Consider **inherent risk** (risk in the absence of any actions) and **residual risk** (risk remaining after management responses)
- Use a combination of **qualitative and quantitative** techniques
- Severity is assessed across **impact** and **likelihood** dimensions

COSO does NOT prescribe specific numerical scales or formulas. It provides a conceptual framework for risk severity assessment.

---

## 7. DPDP Act Risk Provisions

### Data Protection Impact Assessment (DPDP Act Section 10)

Under Section 10 of the DPDP Act 2023, **Significant Data Fiduciaries** must:
- Conduct a **Data Protection Impact Assessment** (the Act uses this term)
- Conduct **periodic audits** of data processing activities
- Appoint a **Data Protection Officer** based in India
- Appoint an **independent data auditor**

The DPDP Act does NOT prescribe:
- Specific risk scoring methodologies
- Quantitative thresholds
- Specific assessment templates

The Data Protection Board of India is expected to issue further guidance on DPIA requirements through rules and regulations.

---

## Regulatory Penalty Reference (Factual Maximums)

For context when assessing potential impact of compliance failures:

| Regulation | Maximum Penalty (Statutory) | Source |
|---|---|---|
| **GDPR** | €20 million or 4% of total worldwide annual turnover (whichever is higher) | GDPR Article 83(5) |
| **GDPR (lower tier)** | €10 million or 2% of total worldwide annual turnover | GDPR Article 83(4) |
| **DPDP Act — Security breach** | ₹250 crore | DPDP Act 2023, Schedule, Item 1 |
| **DPDP Act — Breach notification failure** | ₹200 crore | DPDP Act 2023, Schedule, Item 2 |
| **DPDP Act — Children's data** | ₹200 crore | DPDP Act 2023, Schedule, Item 3 |
| **DPDP Act — SDF obligations** | ₹150 crore | DPDP Act 2023, Schedule, Item 4 |
| **DPDP Act — Other** | ₹50 crore | DPDP Act 2023, Schedule, Item 5 |
| **SEBI (Insider Trading)** | ₹25 crore or 3× profit made (whichever is higher); imprisonment up to 10 years | SEBI Act Sections 15G, 24 |
| **FEMA** | Up to 3× the amount involved | FEMA Section 13 |
| **US EAR** | Up to $1,000,000 per violation; imprisonment up to 20 years | 50 USC §1705 |
| **PIPL (China)** | Up to ¥50 million or 5% of previous year's revenue | PIPL Article 66 |

---

## Key Takeaways for Compliance Teams

1. **No universal risk score formula exists.** ISO 31000, COSO, and GDPR deliberately avoid prescribing specific formulas, leaving organizations to choose methodologies appropriate to their context.

2. **NIST SP 800-30 Rev 1 is the most prescriptive.** It provides actual likelihood and impact scales (Very Low through Very High) with specific numerical ranges and a risk determination matrix.

3. **Regulators require risk-based approaches, not specific scores.** GDPR requires DPIAs for "high risk" processing; RBI requires risk-proportionate controls for outsourcing; SEBI requires Risk Management Committees. None mandate a specific scoring formula.

4. **Choose and document your methodology.** Organizations should select a risk assessment methodology, document it, and apply it consistently. The methodology should be defensible to regulators and appropriate for the organization's context.

5. **Actual regulatory penalties should inform impact assessment.** The statutory maximum penalties listed above provide a factual basis for assessing financial impact in risk assessments.
