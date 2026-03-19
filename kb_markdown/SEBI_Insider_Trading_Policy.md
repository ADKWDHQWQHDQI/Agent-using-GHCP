# SEBI Insider Trading Policy — Prohibition of Insider Trading Regulations

**Source:** Securities and Exchange Board of India (SEBI)
**Reference:** SEBI (Prohibition of Insider Trading) Regulations, 2015 (as amended through 2024)
**Official URL:** https://www.sebi.gov.in/legal/regulations/jan-2015/sebi-prohibition-of-insider-trading-regulations-2015-last-amended-on-march-15-2024-_31804.html
**Last Reviewed:** March 2026

---

## Overview

The **SEBI (Prohibition of Insider Trading) Regulations, 2015** (PIT Regulations) establish the framework for preventing insider trading in Indian securities markets. These regulations are critical for all **listed companies, intermediaries, fiduciaries, and their connected persons** in India.

The regulations are built on the principle that **asymmetric information access** in securities markets is unfair and undermines investor confidence. They require organizations to implement robust controls to prevent the misuse of **Unpublished Price Sensitive Information (UPSI)**.

These regulations are directly relevant to compliance teams managing:
- **Financial data handling** in technology systems
- **Vendor access** to financial reporting systems
- **AI/analytics platforms** processing company financial data
- **Employee data governance** for designated persons and connected persons
- **Communication monitoring** systems

---

## Key Rules

### 1. Unpublished Price Sensitive Information (UPSI) — Definition
UPSI means any information relating to a company or its securities, directly or indirectly, that is **not generally available** and which, upon becoming generally available, is **likely to materially affect the price** of the securities. Examples include:

| UPSI Category | Examples |
|---|---|
| **Financial Results** | Quarterly/annual revenue, profit/loss, earnings per share (before public disclosure) |
| **Dividends** | Declaration of dividends, buyback of securities |
| **Mergers & Acquisitions** | Proposed mergers, demergers, acquisitions, disposals |
| **Business Changes** | New product launches, major contract wins/losses, expansion/closure plans |
| **Management Changes** | Change of key managerial personnel, board composition changes |
| **Regulatory Actions** | Receipt of government orders, regulatory approvals/denials, litigation outcomes |
| **Fund Raising** | Issuance of securities, debt restructuring, credit rating changes |

### 2. Prohibition on Trading (Regulation 4)
- **No insider shall trade** in securities when in possession of UPSI
- Trading includes buying, selling, pledging, or dealing in any manner in securities
- **Presumption**: If a person trades while in possession of UPSI, it is presumed they traded on the basis of UPSI (rebuttable)
- **Defenses available** (Schedule B):
  - Trading pursuant to a pre-existing trading plan
  - Demonstrating the trade was not motivated by the UPSI
  - Trade executed pursuant to a legitimate exercise of stock options

### 3. Prohibition on Communication (Regulation 3)
- **No insider shall communicate, provide, or allow access to UPSI** to any person except:
  - In furtherance of legitimate purposes
  - Performance of duties
  - Discharge of legal obligations
- The entity receiving UPSI under "legitimate purpose" must be bound by confidentiality and non-trading obligations
- **Board of Directors** must maintain a list of persons with whom UPSI is shared for legitimate purposes

### 4. Code of Conduct — Listed Companies (Schedule B)
Every listed company must establish a **Code of Conduct** to regulate, monitor, and report trading by:

**Designated Persons:**
- Directors (Executive, Non-Executive, Independent)
- Key Managerial Personnel (CEO, CFO, Company Secretary)
- Employees in finance, accounting, legal, secretarial, and IT departments
- Employees with access to UPSI
- Promoters and members of the promoter group
- Immediate relatives of the above

**Code Requirements:**
| Requirement | Description |
|---|---|
| **Trading Window** | Closure of trading window at least 48 hours before board meetings for financial results |
| **Pre-clearance** | Designated persons must obtain pre-clearance before trading |
| **Holding Period** | Minimum holding period of 30 days for securities acquired |
| **Disclosure** | Continuous disclosure of trades by designated persons (within 2 trading days) |
| **Contra Trade** | No opposite trade within 6 months of a previous trade |
| **UPSI Digital Database** | Maintain a structured digital database of UPSI shared with any person |

### 5. Structured Digital Database (SDD) — Regulation 3(5)/(6)
- Every entity with UPSI must maintain a **Structured Digital Database** containing:
  - Nature of UPSI
  - Names of persons who have shared the UPSI
  - Names of persons with whom UPSI is shared
  - Date and time of sharing
  - Relationship with the person
- The database must be maintained with **adequate internal controls** and **audit trail logging**
- Records must be preserved for a minimum of **8 years** from the date of creation
- The database must have **time-stamping** that cannot be altered

### 6. Trading Plans (Regulation 5)
- An insider may trade pursuant to a **pre-approved trading plan** disclosed to the stock exchange
- The trading plan must cover a minimum period of **12 months** and no plan can overlap with another
- The plan must be disclosed to the stock exchange at least **6 months** before the first trade
- Trades must be executed as per the plan — no deviation allowed
- The compliance officer cannot approve any counter-trade during the plan period

---

## Risks

### Non-Compliance Risk Assessment
| Risk | Description | Consequence |
|---|---|---|
| **Insider Trading Penalty** | Trading while in possession of UPSI | Penalty up to ₹25 crore or 3x profit (whichever is higher); imprisonment up to 10 years |
| **Communication Violation** | Sharing UPSI with unauthorized persons | Penalty up to ₹25 crore; criminal prosecution |
| **Code of Conduct Failure** | Not maintaining proper code or failing to monitor trading | SEBI enforcement action against the company and compliance officer |
| **SDD Non-Compliance** | Not maintaining structured digital database | Penalty; adverse inference in investigation |
| **Disclosure Failure** | Not making required disclosures within timelines | SEBI penalty; trading restrictions |
| **Tipping** | Providing UPSI to enable someone else to trade | Criminal prosecution; penalty up to ₹25 crore |

### Technology-Specific Risks
1. **AI/ML systems processing financial data** — If an AI analytics vendor has access to pre-announcement financial data, this could constitute UPSI access
2. **Cloud storage of financial reports** — Financial results stored on cloud platforms where vendor employees may have access
3. **Communication platforms** — Emails, Slack, Teams messages containing UPSI without adequate access controls
4. **Outsourced IT systems** — Third-party IT vendors with administrative access to financial reporting systems
5. **Data analytics vendors** — Vendors analyzing transaction/revenue data that could constitute UPSI

---

## Mitigations

### Organizational Controls
1. **Appoint a Compliance Officer** — Senior-level person responsible for monitoring insider trading compliance
2. **Establish a Code of Conduct** — Board-approved code covering all designated persons
3. **Trading window management** — Automated system to open/close trading windows and communicate to designated persons
4. **Pre-clearance system** — Digital pre-clearance workflow for designated person trades
5. **UPSI classification policy** — Clear guidelines on what constitutes UPSI in the organization

### Technology Controls
1. **Structured Digital Database (SDD)** — Implement a tamper-proof, time-stamped database for UPSI tracking
2. **Access controls** — Role-based access to financial systems; restrict access to UPSI to only those with legitimate need
3. **DLP (Data Loss Prevention)** — Monitor and prevent unauthorized sharing of financial data via email, messaging, cloud storage
4. **Communication monitoring** — Surveillance of electronic communications for UPSI leakage (with appropriate privacy safeguards)
5. **Vendor access controls** — Restrict vendor/third-party access to financial systems; implement clean-room environments

### Vendor Management for UPSI Protection
1. **Vendor NDAs** — All vendors with potential access to financial data must sign confidentiality agreements specifically covering UPSI
2. **UPSI access lists** — Maintain and regularly update lists of vendor personnel with access to UPSI
3. **Vendor trading restrictions** — Include clauses in vendor contracts prohibiting trading based on client UPSI
4. **Periodic audits** — Audit vendor access logs to financial systems
5. **Vendor personnel screening** — Background checks on vendor employees with access to sensitive financial data

### Training and Awareness
1. **Annual mandatory training** for all designated persons on insider trading regulations
2. **Quarterly reminders** during trading window closure periods
3. **Vendor training** — Include insider trading awareness in vendor onboarding
4. **Whistleblower mechanism** — Anonymous reporting channel for suspected insider trading violations
5. **Board training** — Annual training for Board of Directors on UPSI responsibilities

---

## Disclosure Requirements

### Continuous Disclosures by Designated Persons
| Disclosure Type | Threshold | Timeline |
|---|---|---|
| **Acquisition/disposal** by promoters, directors, designated persons | Trades exceeding ₹10 lakh in a quarter | Within 2 trading days to the company; company to stock exchange within 2 trading days |
| **Large shareholding** | Holding/change exceeding 5%/10%/etc. | Within specified timelines under SEBI SAST Regulations |
| **Initial disclosure** | On appointment as designated person | Within 7 days of appointment |
| **Annual disclosure** | By all designated persons | Within 30 days of end of financial year |

### Company Disclosures to Stock Exchanges
- **Closure of trading window** dates along with results announcement schedule
- **UPSI sharing for legitimate purpose** — Maintain records, available to SEBI on demand
- **Code of Conduct** — Must be posted on company website
- **Compliance officer details** — Published and communicated to stock exchanges
