# RBI Cross-Border Transactions Circular 2023

**Source:** Reserve Bank of India (RBI)
**Reference:** Multiple RBI circulars under FEMA — including A.P. (DIR Series) Circulars on cross-border payments, Liberalised Remittance Scheme (LRS), and Payment Aggregator Cross-Border (PA-CB) framework
**Official URL:** https://www.rbi.org.in/Scripts/BS_CircularIndexDisplay.aspx
**Note:** This document consolidates provisions from multiple RBI circulars issued during 2023–2024. Readers should verify specific circular references directly on the RBI website.
**Related Regulations:** Foreign Exchange Management Act (FEMA), 1999; Liberalised Remittance Scheme (LRS)
**Last Reviewed:** March 2026

---

## Overview

The Reserve Bank of India has issued multiple circulars governing **cross-border payment transactions, forex regulations, and international vendor engagements** under the Foreign Exchange Management Act (FEMA), 1999. The 2023 updates consolidate and tighten requirements for entities making or receiving cross-border payments, particularly for technology services, SaaS subscriptions, and vendor payments to foreign entities.

These regulations are critical for organizations that:
- Engage **international vendors** for technology, analytics, or cloud services
- Make **payments in foreign currency** to overseas service providers
- Operate in **multiple jurisdictions** and need to transfer funds cross-border
- Use **Payment Aggregators (PAs)** for facilitating cross-border transactions

The key objective is to ensure that all cross-border transactions comply with FEMA provisions, are conducted through authorized channels, and support India's regulatory oversight of capital flows.

---

## Key Rules

### 1. Authorized Dealer (AD) Bank Requirements
- All cross-border payments **must be routed through Authorized Dealer (AD) Category-I banks**
- AD banks must verify the purpose of the remittance against the **FEMA permissible list**
- Transactions must fall within the **Liberalised Remittance Scheme (LRS)** limits for individuals (currently USD 250,000 per financial year)
- For corporate transactions, there is **no upper limit**, but proper documentation and purpose codes are mandatory

### 2. Purpose Code Compliance
- Every outward remittance must be classified with a valid **RBI Purpose Code**
- Common purpose codes for technology/vendor transactions:
  | Purpose Code | Description |
  |---|---|
  | S0802 | Software/IT services |
  | S0806 | Information services (database, web portal) |
  | S0305 | Business and management consultancy |
  | S0803 | Hardware consultancy/implementation |
  | S0805 | Maintenance and repair of computers |
- **Incorrect purpose coding** can result in transaction rejection or regulatory scrutiny

### 3. Tax Compliance for Cross-Border Payments
- **Tax Collected at Source (TCS)** of 20% applies to LRS remittances exceeding ₹7 lakh per financial year (effective October 1, 2023)
- **Withholding Tax (TDS)** under Section 195 of the Income Tax Act applies to payments to non-residents
- Companies must obtain a **Lower Deduction Certificate** from the Income Tax Department if the vendor is in a country with a Double Taxation Avoidance Agreement (DTAA)
- **Goods and Services Tax (GST)** on reverse charge basis applies to import of services

### 4. Cross-Border Payment Aggregator Framework (2023)
- RBI issued guidelines for **Payment Aggregators handling cross-border transactions** (PA-CB framework)
- Key requirements:
  - PA-CB entities must obtain **RBI authorization**
  - Must maintain a **minimum net worth of ₹15 crore** (increasing to ₹25 crore by March 2026)
  - Must comply with **KYC/AML norms** for merchants
  - Must ensure **settlement in INR** within India
  - Export-related transactions must be reported to **EDPMS (Export Data Processing and Monitoring System)**
  - Import-related transactions must be reported to **IDPMS (Import Data Processing and Monitoring System)**

### 5. Vendor Due Diligence for Foreign Payments
- Organizations must conduct **FEMA compliance due diligence** before engaging foreign vendors
- Required documentation:
  - Valid contract/agreement with clearly stated scope of services
  - Invoice with detailed description of services rendered
  - Certificate from a Chartered Accountant (where required)
  - Tax residency certificate of the foreign vendor
  - FEMA declaration forms (A2 form for outward remittances)

---

## Risks

### Regulatory Risk Matrix
| Risk | Description | Impact |
|---|---|---|
| **FEMA Violation** | Unauthorized cross-border payments or incorrect purpose codes | Penalties up to 3x the amount involved |
| **TCS/TDS Non-Compliance** | Failure to deduct/collect taxes on cross-border payments | Tax demand + interest (12% p.a.) + penalty |
| **AML/KYC Failure** | Inadequate vendor screening for anti-money laundering | Criminal prosecution under PMLA |
| **Unauthorized PA-CB Operations** | Facilitating cross-border payments without RBI authorization | Business closure + penalties |
| **Trade-Based Money Laundering (TBML)** | Over/under-invoicing in vendor payments | Criminal investigation + asset seizure |
| **Contractual Risk** | Contracts not aligned with FEMA permitted activities | Transactions voided + regulatory action |

### Common Compliance Failures
1. **Paying foreign vendors through non-banking channels** (e.g., crypto, peer-to-peer)
2. **Splitting transactions to avoid LRS thresholds** (structuring)
3. **Using incorrect purpose codes** to circumvent restrictions
4. **Failing to obtain TDS certificates** before remittance
5. **Not maintaining proper documentation** for AD bank requirements
6. **Engaging unlicensed Payment Aggregators** for cross-border collections

---

## Mitigations

### Process Controls
1. **Centralized payment process** — Route all cross-border payments through a dedicated Treasury/Finance team
2. **Pre-payment checklist** — Verify purpose code, tax obligations, documentation, and FEMA compliance before initiating any remittance
3. **AD Bank coordination** — Maintain an established relationship with an AD Category-I bank with cross-border expertise
4. **Quarterly FEMA compliance audit** — Engage external auditors to review cross-border payment flows

### Vendor Onboarding Controls
1. **Foreign vendor registration policy** — Mandatory registration with Tax Residency Certificate, FEMA status, and bank details
2. **Country risk assessment** — Evaluate sanctions lists (OFAC, UN, EU) and FATF grey/black list status
3. **Contract review** — Legal team to verify all vendor contracts include FEMA-compliant payment terms
4. **Ongoing monitoring** — Periodic review of vendor payment patterns for anomalies

### Technology Safeguards
1. **ERP integration** — Configure SAP/Oracle/Tally with mandatory purpose code fields for cross-border payments
2. **Automated TDS/TCS calculation** — System-level withholding before payment release
3. **Transaction monitoring** — Alert-based system for unusual payment patterns or threshold breaches
4. **Audit trail** — Complete digital record of all cross-border transactions with supporting documents

### Regulatory Reporting
1. **EDPMS/IDPMS reporting** — Ensure all export/import service payments are reported within prescribed timelines
2. **LRS annual disclosure** — Report all LRS transactions in the annual ITR filing
3. **Annual FEMA compliance certificate** — Board-level acknowledgment of FEMA compliance status
4. **Suspicious Transaction Reports (STR)** — File with FIU-India if any transactions appear suspicious

---

## Key FEMA Restrictions on Cross-Border Vendor Payments

### Prohibited Transactions
- Payments for lottery, racing, gambling, or prohibited activities
- Remittances to countries on the **UN Security Council sanctions list**
- Capital account transactions without specific RBI approval
- Payments exceeding contracted amounts without documentation

### Restricted Transactions (Require Specific Approval)
- Payments to entities in **FATF grey-listed countries** (enhanced due diligence required)
- Multi-year advance payments to foreign vendors (typically limited to 1 year)
- Payments for intangible assets or intellectual property (require valuation certificate)
- Related-party cross-border transactions (require transfer pricing documentation)

---

## Impact on Technology Vendor Engagement

| Scenario | FEMA Requirement | Action Needed |
|---|---|---|
| SaaS subscription to US vendor | Purpose Code S0802, TDS u/s 195 | CA certificate, lower deduction certificate if DTAA applies |
| Cloud hosting (AWS/Azure/GCP) | Purpose Code S0802/S0806 | Standard AD bank remittance with documentation |
| AI/ML vendor in Singapore | Purpose Code S0802, check DTAA | Tax residency certificate of vendor |
| Data analytics vendor in China | Enhanced due diligence | Country risk assessment + FEMA compliance check |
| Payments to offshore subsidiary | Transfer pricing norms apply | TP documentation + Form 3CEB + CA certificate |
