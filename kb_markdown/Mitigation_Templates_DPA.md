# Mitigation Templates — Data Processing Agreements (DPA)

**Context:** Model clauses and templates for Data Processing Agreements aligned with GDPR, DPDP Act (India), and RBI guidelines
**Applicability:** Cross-border vendor agreements, cloud service contracts, data processor engagements
**Last Reviewed:** March 2026

---

## Overview

A **Data Processing Agreement (DPA)** is a legally binding contract between a **data controller** (the organization that determines the purposes and means of processing) and a **data processor** (the entity that processes personal data on behalf of the controller). DPAs are mandatory under:

- **GDPR Article 28** — Requires a binding contract governing the processor's processing activities
- **DPDP Act (India)** — Data Fiduciaries must ensure Data Processors implement appropriate security safeguards
- **RBI Guidelines** — Regulated entities must include specific data protection clauses in vendor contracts

This document provides **template clauses** and **model DPA structures** that can be adapted for specific vendor relationships.

> **Important:** The template clauses in this document are **illustrative models** intended as starting points for drafting. They are NOT regulatory text and do NOT constitute legal advice. Organizations must engage qualified legal counsel to draft DPAs tailored to their specific circumstances, applicable jurisdictions, and regulatory requirements. The GDPR Article 28 requirements listed below are factual; the template clause language is a model implementation of those requirements.

---

## Key Rules

### GDPR Article 28 — Mandatory DPA Contents
| Required Element | Description |
|---|---|
| **Subject matter and duration** | Clear description of what processing the processor will perform and for how long |
| **Nature and purpose** | Types of processing operations (collection, storage, analysis, deletion) |
| **Type of personal data** | Categories of data processed (names, financial data, health data, etc.) |
| **Categories of data subjects** | Whose data is being processed (customers, employees, vendors) |
| **Controller's obligations and rights** | Controller's instructions, oversight, and audit rights |
| **Processor's obligations** | Security measures, confidentiality, sub-processor management, assistance obligations |

---

## Template DPA Clauses

### Clause 1: Definitions

```
1.1 "Controller" means [Company Name], the entity that determines the purposes 
    and means of Processing of Personal Data.

1.2 "Processor" means [Vendor Name], the entity that Processes Personal Data on 
    behalf of the Controller.

1.3 "Personal Data" means any information relating to an identified or identifiable 
    natural person, as defined under applicable Data Protection Laws including 
    GDPR Article 4(1) and DPDP Act Section 2(t).

1.4 "Processing" means any operation performed on Personal Data, including 
    collection, storage, alteration, retrieval, use, disclosure, transfer, 
    erasure, or destruction.

1.5 "Data Protection Laws" means all applicable data protection and privacy 
    legislation including the EU General Data Protection Regulation (GDPR), 
    India's Digital Personal Data Protection Act 2023 (DPDP Act), and any 
    applicable RBI circulars and guidelines.

1.6 "Sub-processor" means any third party engaged by the Processor to process 
    Personal Data on behalf of the Controller.

1.7 "Data Breach" means a breach of security leading to the accidental or 
    unlawful destruction, loss, alteration, unauthorized disclosure of, or 
    access to, Personal Data.
```

### Clause 2: Scope and Purpose of Processing

```
2.1 The Processor shall process Personal Data only on documented instructions 
    from the Controller, including with regard to transfers of Personal Data 
    to a third country or an international organization.

2.2 The Processor shall process Personal Data only for the following purposes:
    [Specify purposes — e.g., "provision of cloud hosting services," 
    "analytics processing," "customer support operations"]

2.3 The categories of Personal Data processed shall include:
    [Specify — e.g., names, email addresses, transaction records, 
    customer identifiers]

2.4 The categories of Data Subjects shall include:
    [Specify — e.g., Controller's customers, employees, business contacts]

2.5 The duration of processing shall be for the term of the Agreement, 
    plus any retention period required by law or as specified in 
    Schedule [X].
```

### Clause 3: Data Localization and Cross-Border Transfers

```
3.1 The Processor shall store all Personal Data within the following 
    geographic locations: [Specify — e.g., "India (for RBI-regulated data)," 
    "European Economic Area (for GDPR-governed data)"]

3.2 The Processor shall not transfer Personal Data to any country or 
    territory outside the approved locations without the prior written 
    consent of the Controller.

3.3 Where cross-border transfers are necessary and approved, the Processor 
    shall ensure that appropriate safeguards are in place, including:
    (a) Standard Contractual Clauses (SCCs) as adopted by the European 
        Commission (for GDPR-governed data);
    (b) Compliance with RBI data localization requirements (for payment 
        and financial data);
    (c) Compliance with DPDP Act cross-border transfer provisions 
        (for Indian personal data).

3.4 The Processor shall conduct and document a Transfer Impact Assessment 
    (TIA) for any transfer of GDPR-governed data to a country without an 
    adequacy decision, and shall implement supplementary measures as 
    identified in the TIA.

3.5 For RBI-regulated data (payment data, customer financial data):
    (a) All data must be stored on systems located only in India;
    (b) If processing occurs outside India, data must be deleted from 
        foreign systems within 24 hours;
    (c) A copy of all data must be maintained in India at all times.
```

### Clause 4: Security Measures

```
4.1 The Processor shall implement appropriate technical and organizational 
    measures to ensure a level of security appropriate to the risk, including:

    (a) Encryption of Personal Data at rest using AES-256 or equivalent;
    (b) Encryption of Personal Data in transit using TLS 1.2 or higher;
    (c) Role-based access controls with principle of least privilege;
    (d) Multi-factor authentication for all access to systems containing 
        Personal Data;
    (e) Regular vulnerability assessments and penetration testing 
        (at least annually);
    (f) Comprehensive audit logging of all access to Personal Data;
    (g) Business continuity and disaster recovery plans with tested 
        RTO/RPO targets;
    (h) Physical security controls for data center facilities.

4.2 The Processor shall maintain certifications including:
    [Specify — e.g., ISO 27001, SOC 2 Type II, PCI DSS (if applicable)]

4.3 The Processor shall conduct periodic security assessments and provide 
    results to the Controller upon request.
```

### Clause 5: Sub-Processor Management

```
5.1 The Processor shall not engage any Sub-processor without prior written 
    authorization from the Controller.

5.2 The Processor shall maintain a current list of all Sub-processors and 
    shall notify the Controller of any intended changes at least 30 days 
    in advance.

5.3 The Processor shall impose the same data protection obligations on 
    Sub-processors as set out in this Agreement, by way of a binding 
    contract.

5.4 The Processor shall remain fully liable to the Controller for the 
    performance of any Sub-processor's obligations.

5.5 The Controller shall have the right to object to any new Sub-processor 
    within 14 days of notification. If the objection is not resolved, the 
    Controller may terminate the affected services.
```

### Clause 6: Data Breach Notification

```
6.1 The Processor shall notify the Controller of any Data Breach without 
    undue delay, and in any event within:
    (a) 6 hours of becoming aware of the breach (for RBI-regulated entities);
    (b) 24 hours of becoming aware of the breach (for other data).

6.2 The notification shall include:
    (a) Description of the nature of the breach;
    (b) Categories and approximate number of Data Subjects affected;
    (c) Categories and approximate number of Personal Data records affected;
    (d) Description of the likely consequences of the breach;
    (e) Description of measures taken or proposed to address the breach;
    (f) Contact details of the Processor's data protection contact.

6.3 The Processor shall cooperate with the Controller in investigating 
    the breach, mitigating its effects, and meeting any regulatory 
    notification obligations.

6.4 The Processor shall not inform any third party about the breach 
    without the Controller's prior written consent, unless required by law.
```

### Clause 7: Audit Rights

```
7.1 The Processor shall make available to the Controller all information 
    necessary to demonstrate compliance with this Agreement and applicable 
    Data Protection Laws.

7.2 The Controller (or an appointed third-party auditor) shall have the 
    right to conduct audits, including inspections, of the Processor's 
    processing activities covered by this Agreement.

7.3 The Processor shall allow and contribute to audits conducted by the 
    Controller or a supervisory authority (including RBI, SEBI, and EU 
    data protection authorities).

7.4 The Processor shall provide:
    (a) Annual SOC 2 Type II report;
    (b) Annual ISO 27001 surveillance/recertification audit results;
    (c) Results of annual penetration tests;
    (d) Access to the processing premises for on-site audits with 
        30 days' notice.
```

### Clause 8: Data Subject Rights Assistance

```
8.1 The Processor shall assist the Controller in responding to requests 
    from Data Subjects exercising their rights under applicable Data 
    Protection Laws, including:
    (a) Right to access (GDPR Art. 15; DPDP Act Sec. 11);
    (b) Right to rectification (GDPR Art. 16; DPDP Act Sec. 12);
    (c) Right to erasure (GDPR Art. 17; DPDP Act Sec. 12);
    (d) Right to data portability (GDPR Art. 20);
    (e) Right to withdraw consent (DPDP Act Sec. 6(9)).

8.2 The Processor shall promptly notify the Controller if it receives a 
    request directly from a Data Subject and shall not respond to the 
    request without the Controller's instructions.
```

### Clause 9: Data Return and Deletion

```
9.1 Upon termination or expiry of this Agreement, the Processor shall, 
    at the Controller's election:
    (a) Return all Personal Data to the Controller in a commonly used, 
        machine-readable format; or
    (b) Securely delete all Personal Data and certify such deletion 
        in writing.

9.2 Deletion shall include all copies, backups, and archived data, 
    unless retention is required by applicable law.

9.3 The Processor shall complete the return or deletion within 30 days 
    of termination, unless a different period is agreed.

9.4 For RBI-regulated data, the Processor shall ensure that no payment 
    or customer data is retained outside India after contract termination.
```

### Clause 10: Government Access Requests

```
10.1 The Processor shall notify the Controller promptly if it receives 
     any request from a government authority or law enforcement agency 
     to access Personal Data processed under this Agreement, unless 
     prohibited by law from doing so.

10.2 The Processor shall not disclose Personal Data to any government 
     authority unless:
     (a) Required by law; and
     (b) After notifying the Controller (where legally permitted); and
     (c) Limiting the disclosure to the minimum data legally required.

10.3 The Processor shall challenge any request it considers disproportionate 
     or unlawful through available legal channels.

10.4 The Processor shall maintain a transparency report documenting 
     the number and nature of government access requests received.
```

---

## Risks of Inadequate DPAs

| Risk | Description | Regulatory Impact |
|---|---|---|
| **No DPA in place** | Processing without a binding agreement | GDPR: Fine up to €10M / 2% turnover; DPDP Act: penalty for inadequate safeguards |
| **Missing mandatory clauses** | DPA missing required GDPR Art. 28 elements | Regulatory enforcement; contract may be deemed insufficient |
| **No sub-processor controls** | Processor engages sub-processors without authorization | Controller liable for unauthorized processing chain |
| **No data localization clause** | Data stored outside permitted jurisdictions | RBI penalty; GDPR transfer breach |
| **No breach notification clause** | Delayed breach notification | DPDP Act: up to ₹200 crore; GDPR: enforcement action |
| **No exit provisions** | Data trapped with vendor after termination | Operational risk; potential ongoing compliance exposure |

---

## DPA Checklist

- [ ] Definitions aligned with GDPR, DPDP Act, and RBI terminology
- [ ] Processing purpose, scope, and duration clearly defined
- [ ] Data categories and data subject categories specified
- [ ] Data localization requirements addressed (India/EU/other)
- [ ] Cross-border transfer safeguards included (SCCs, TIA)
- [ ] Security measures specified (encryption, access controls, certifications)
- [ ] Sub-processor management clause with notification and objection rights
- [ ] Breach notification timelines defined (6 hours for RBI, 24-72 hours for GDPR)
- [ ] Audit rights for Controller and regulators
- [ ] Data subject rights assistance obligations
- [ ] Data return and deletion provisions
- [ ] Government access request handling protocol
- [ ] Confidentiality obligations surviving termination
- [ ] Indemnification for data protection breaches
- [ ] Governing law and dispute resolution specified
