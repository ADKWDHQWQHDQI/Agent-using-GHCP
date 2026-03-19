# RBI Data Localization 2018 Guidelines

**Source:** Reserve Bank of India (RBI)
**Reference:** RBI/2017-18/153, DPSS.CO.OD No.2785/06.08.005/2017-18, dated April 6, 2018
**Official URL:** https://www.rbi.org.in/Scripts/NotificationUser.aspx?Id=11244
**Last Reviewed:** March 2026

---

## Overview

The Reserve Bank of India issued a circular on April 6, 2018, titled **"Storage of Payment System Data"** directing all payment system operators to ensure that the **entire data relating to payment systems operated by them is stored in a system only in India**. This directive was issued under Section 18 read with Section 10(2) of the Payment and Settlement Systems Act, 2007.

The circular applies to all system providers authorized or approved by RBI to set up and operate a payment system in India under the Payment and Settlement Systems Act, 2007. This includes banks, non-bank entities, card networks (Visa, Mastercard, etc.), payment aggregators, and payment gateways.

The compliance deadline was originally set as **October 15, 2018**, by which all payment system operators were required to ensure complete data localization.

---

## Key Rules

### 1. Mandatory Data Storage in India
- **All data** relating to payment systems must be stored in a system located **only in India**.
- This includes the full end-to-end transaction details, including:
  - Card number / token
  - Transaction amount
  - Merchant details
  - Customer information (name, mobile, email, Aadhaar, PAN)
  - Payment credentials
  - OTP (One Time Password)
  - Transaction logs
  - Settlement data

### 2. Scope of "Payment System Data"
- The term covers **all data elements** forming part of the payment processing chain:
  - Data collected/generated/processed as part of a payment message or instruction
  - Customer data, payment-sensitive data, payment credentials, and transaction data
- Applies regardless of whether the data is at rest, in transit, or in processing

### 3. Processing Abroad — Conditional Permission
- **Processing of payment transactions** can occur outside India **during the transaction processing phase only**.
- However, the **data must be deleted from foreign systems** after processing.
- A **copy of the complete data must be stored in India** within 24 hours (one business day) of the transaction.

### 4. Compliance Reporting
- Payment system operators must submit a **System Audit Report (SAR)** conducted by a CERT-IN empaneled auditor to certify compliance.
- The audit report must confirm:
  - Data is stored only in India
  - No data is retained outside India post-processing
  - Adequate security measures are in place

### 5. Board-Approved Data Storage Policy
- Every payment system operator must have a **Board-approved policy** on data storage that explicitly addresses localization requirements.

---

## Risks

### Non-Compliance Risks
| Risk Category | Description | Severity |
|---|---|---|
| **Regulatory Penalty** | RBI can impose monetary penalties, restrict operations, or revoke authorization | Critical |
| **Operational Disruption** | Non-compliant operators may be barred from processing payments in India | High |
| **Reputational Damage** | Public enforcement actions damage brand trust | High |
| **Cross-Border Vendor Risk** | Using cloud providers with servers outside India creates non-compliance exposure | High |
| **Data Breach Liability** | If data stored outside India is breached, the operator faces compounded regulatory action | Critical |

### Common Areas of Non-Compliance
1. **Cloud infrastructure** hosting payment data on servers outside India (e.g., AWS US-East, Azure West Europe)
2. **Card networks** retaining transaction data in foreign data centers beyond the processing window
3. **Payment aggregators** sharing data with parent companies or vendors abroad without deletion/purge protocols
4. **Backup and disaster recovery** copies stored in foreign jurisdictions
5. **Analytics and reporting systems** that replicate payment data to overseas servers

---

## Mitigations

### Immediate Actions
1. **Audit current data flows** — Map all payment data from collection to storage and identify any foreign storage points
2. **Migrate data to Indian data centers** — Use Azure India (Central/South), AWS Mumbai, or GCP Mumbai regions
3. **Implement data purge protocols** — Ensure foreign processing nodes delete data within 24 hours post-processing
4. **Obtain SAR certification** — Engage a CERT-IN empaneled auditor to conduct a System Audit Report

### Technical Safeguards
1. **Data residency controls** — Configure cloud providers to restrict data replication to Indian regions only
2. **Encryption at rest and in transit** — Use AES-256 for data at rest and TLS 1.2+ for data in transit
3. **Access controls** — Implement role-based access ensuring only authorized Indian-based personnel can access payment data
4. **Automated monitoring** — Deploy DLP (Data Loss Prevention) tools to detect unauthorized data transfers outside India

### Contractual Safeguards
1. **Vendor contracts must include** data localization clauses specifying storage in India
2. **SLAs with cloud providers** must guarantee data residency within Indian geography
3. **Sub-processor agreements** must flow down localization requirements
4. **Right to audit** clauses enabling periodic verification of data storage location

### Governance
1. **Quarterly compliance reviews** by the Board or designated committee
2. **Annual SAR audit** submission to RBI
3. **Incident response plan** specifically addressing cross-border data leakage scenarios
4. **Training programs** for technology and operations teams on localization requirements

---

## Key Amendments and Updates

> **Note:** The April 6, 2018 original circular is the verified primary directive. Subsequent entries in this timeline reflect publicly reported regulatory developments; readers should verify specific dates and actions directly on the RBI website.

| Date | Update |
|---|---|
| **April 6, 2018** | Original circular issued (RBI/2017-18/153) |
| **2019** | RBI reinforced that the directive applies broadly to all payment system data, not limited to transaction data alone |
| **September 2019** | RBI sought compliance certificates from major card networks |
| **2020** | RBI tightened enforcement — restricted new product launches for non-compliant entities |
| **2021** | Master Direction on Payment Aggregators and Payment Gateways reaffirms localization requirements |
| **2024** | RBI guidance extended to cover tokenized payment data and digital lending data (verify specific circular on RBI website) |

---

## Frequently Referenced Clauses

> **"The entire data relating to payment systems operated by them is stored in a system only in India. This data should include the full end-to-end transaction details / information collected / carried / processed as part of the message / payment instruction."**
> — RBI Circular dated April 6, 2018

> **"In case the processing is done abroad, the data should be deleted from the systems abroad and brought back to India not later than the one business day or 24 hours from payment processing, whichever is earlier."**
> — Attributed to RBI clarifications on the April 6, 2018 circular (readers should verify the exact text on the RBI website)

---

## Applicability Matrix

| Entity Type | Applicable? | Notes |
|---|---|---|
| Banks (Scheduled & Non-Scheduled) | Yes | All payment data must be stored in India |
| Card Networks (Visa, Mastercard, RuPay) | Yes | Including tokenization data |
| Payment Aggregators | Yes | As per PA/PG Master Direction 2020 |
| Payment Gateways | Yes | When handling payment data |
| UPI Service Providers | Yes | NPCI and TPAPs included |
| Fintech Companies | Yes | If operating under RBI authorization |
| Foreign Banks Operating in India | Yes | Must comply for India transactions |
