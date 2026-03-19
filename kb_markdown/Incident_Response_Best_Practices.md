# Incident Response Best Practices — Data Breach & Regulatory Notification

**Context:** Framework for responding to personal data breaches, cybersecurity incidents, and regulatory notification requirements
**Applicability:** GDPR (Art. 33-34), DPDP Act (India), RBI IT Governance Framework, SEBI Cyber Security Circular, CERT-In Rules 2022
**Last Reviewed:** March 2026

---

## Overview

An effective **Incident Response Plan (IRP)** is critical for organizations processing personal data across multiple jurisdictions. Data protection regulations worldwide mandate not only prevention but also **timely detection, containment, notification, and remediation** of data breaches.

Key regulatory notification timelines:
- **GDPR:** Notification to supervisory authority within **72 hours** of becoming aware of the breach
- **DPDP Act (India):** Notification to the Data Protection Board of India **without undue delay**
- **CERT-In (India):** Notification within **6 hours** of becoming aware of the incident (Rule 2022)
- **RBI:** Notification of cybersecurity incidents within **6 hours** to CERT-In and to RBI as per reporting framework
- **SEBI:** Listed entities must notify stock exchanges within **24 hours** for material cybersecurity incidents

---

## Key Rules

### 1. Regulatory Notification Requirements Matrix

| Regulation | Authority | Timeline | Scope | Penalty for Non-Compliance |
|---|---|---|---|---|
| **GDPR Art. 33** | Lead supervisory authority (DPA) | 72 hours | Personal data breaches | Up to €10M / 2% annual turnover |
| **GDPR Art. 34** | Affected data subjects | Without undue delay | High-risk breaches | Up to €20M / 4% annual turnover |
| **DPDP Act Sec. 8(6)** | Data Protection Board of India | Without undue delay | Personal data breaches | Up to ₹200 crore |
| **CERT-In 2022** | CERT-In | 6 hours | Cybersecurity incidents | Criminal penalty under IT Act |
| **RBI Cyber Framework** | RBI via CERT-In | 6 hours | Cyber incidents affecting banks/NBFCs | Regulatory action, license risk |
| **SEBI Circular** | Stock exchanges, SEBI | 24 hours (material events) | Cyber incidents affecting listed entities | Listing agreement violation |
| **US State Laws** | State AG (varies) | Varies by state: typically 30–90 days (e.g., Colorado 30 days, Connecticut 60 days, most states 30–60 days; some states have no specific deadline) | Personal data of state residents | State-specific penalties |

### 2. GDPR Breach Notification Content Requirements (Article 33)

The notification to the supervisory authority must include:

1. **Nature of the breach:** Categories and approximate number of data subjects and records affected
2. **Contact details:** Name and contact of the Data Protection Officer or designated contact
3. **Likely consequences:** Description of the likely consequences of the breach
4. **Measures taken:** Description of measures taken or proposed to address the breach and mitigate adverse effects

### 3. CERT-In Reportable Incident Types

Under the April 2022 directions, the following must be reported within **6 hours**:

- Targeted scanning/probing of critical networks or systems
- Compromise of critical systems or information
- Unauthorized access to IT systems or data
- Defacement of websites or intrusion into websites
- Malicious code attacks (e.g., spreading of virus/worm/Trojan/ransomware)
- Attacks on servers, databases, network infrastructure, and IoT devices
- Identity theft, spoofing, and phishing attacks
- Denial of Service (DoS) and Distributed Denial of Service (DDoS) attacks
- Attacks on critical infrastructure and cloud computing platforms
- Data breaches and data leaks
- Attacks through malicious mobile apps
- Fake mobile apps
- Unauthorized access to social media accounts

---

## Incident Response Framework

### Phase 1: Preparation (Pre-Incident)

| Activity | Description | Responsible |
|---|---|---|
| **IRP Documentation** | Maintain a written Incident Response Plan reviewed quarterly | CISO / DPO |
| **Response Team Formation** | Designate cross-functional Incident Response Team (IRT) including IT Security, Legal, Compliance, PR, and Business | CISO |
| **Contact Lists** | Maintain up-to-date contact lists for regulators, law enforcement, legal counsel, and communication channels | Compliance |
| **Tabletop Exercises** | Conduct simulated breach exercises at least twice per year | CISO |
| **Detection Tools** | Deploy SIEM, EDR, DLP, and network monitoring tools | IT Security |
| **Playbooks** | Create specific playbooks for common scenarios (ransomware, data exfiltration, insider threat, third-party breach) | IT Security |
| **Insurance** | Review cyber insurance coverage and notification requirements | Legal / Finance |
| **Vendor Coordination** | Ensure DPAs include breach notification obligations with defined timelines | Legal / Procurement |

### Phase 2: Detection and Analysis (0–2 Hours)

| Step | Action | Team |
|---|---|---|
| **2.1** | Identify and confirm the incident through monitoring alerts, user reports, or external notification | IT Security |
| **2.2** | Classify incident severity: Critical / High / Medium / Low | IRT Lead |
| **2.3** | Determine if personal data is affected (if yes → activate data breach track) | DPO |
| **2.4** | Determine affected jurisdictions and applicable notification regulations | Legal / Compliance |
| **2.5** | Preserve evidence — create forensic images, secure logs, document chain of custody | IT Security / Forensics |
| **2.6** | Activate IRT and escalate to senior management (if Critical/High) | CISO |

#### Severity Classification

| Level | Description | Example |
|---|---|---|
| **Critical** | Active data exfiltration, ransomware propagating, systemic compromise | Ransomware encrypting production DBs; mass data exfiltration detected |
| **High** | Confirmed breach with personal data exposure | Unauthorized access to customer database; insider data theft |
| **Medium** | Confirmed incident without evidence of data compromise | Phishing campaign targeting employees; malware detected and contained |
| **Low** | Attempted or minor incident, no data impact | Failed brute-force attempts; isolated malware blocked by AV |

### Phase 3: Containment (2–6 Hours)

| Step | Action | Team |
|---|---|---|
| **3.1** | Implement short-term containment (isolate affected systems, block malicious IPs/accounts) | IT Security |
| **3.2** | Prevent further data loss (revoke compromised credentials, enable enhanced monitoring) | IT Security |
| **3.3** | Assess scope: what data was accessed/exfiltrated, how many records, which jurisdictions | Forensics / DPO |
| **3.4** | Engage external forensics firm if needed | CISO / Legal |
| **3.5** | **CERT-In notification** if applicable (within 6 hours) | Compliance |
| **3.6** | **RBI notification** if applicable (within 6 hours for RBI-regulated entities) | Compliance |
| **3.7** | Document all containment actions with timestamps | IRT Coordinator |

### Phase 4: Notification (6–72 Hours)

| Step | Action | Team |
|---|---|---|
| **4.1** | Prepare breach assessment report for each applicable jurisdiction | DPO / Legal |
| **4.2** | **GDPR: Notify lead supervisory authority** within 72 hours (or document reasons for delay) | DPO |
| **4.3** | **DPDP Act: Notify Data Protection Board of India** without undue delay | DPO / Compliance |
| **4.4** | **SEBI: Notify stock exchanges** within 24 hours for material incidents (if listed entity) | Company Secretary |
| **4.5** | Assess if high risk to individuals → notify affected data subjects (GDPR Art. 34) | DPO / Legal |
| **4.6** | Notify cyber insurance provider | Legal / Finance |
| **4.7** | Engage external legal counsel for cross-border notification coordination | Legal |
| **4.8** | Prepare public communication if required or appropriate | PR / Communications |

#### GDPR 72-Hour Decision Tree

```
Breach detected
  └─ Is personal data affected?
       ├─ NO → Document internally; no DPA notification required
       └─ YES → Is there a risk to rights and freedoms?
              ├─ NO → Document internally; no DPA notification required
              └─ YES → Notify supervisory authority within 72 hours
                    └─ Is there HIGH risk to individuals?
                         ├─ NO → No individual notification required
                         └─ YES → Notify affected individuals
                               └─ Exception: Technical measures render
                                  data unintelligible (e.g., encrypted)
```

### Phase 5: Eradication and Recovery (72 Hours – 2 Weeks)

| Step | Action | Team |
|---|---|---|
| **5.1** | Identify root cause of the incident | Forensics |
| **5.2** | Remove threat actor artifacts (malware, backdoors, compromised accounts) | IT Security |
| **5.3** | Patch exploited vulnerabilities | IT Operations |
| **5.4** | Rebuild affected systems from known-good backups | IT Operations |
| **5.5** | Implement enhanced monitoring on affected systems | IT Security |
| **5.6** | Verify system integrity before restoration to production | IT Security / QA |
| **5.7** | Restore services in prioritized order | IT Operations |

### Phase 6: Post-Incident Review (2–4 Weeks)

| Step | Action | Team |
|---|---|---|
| **6.1** | Conduct post-incident review ("lessons learned") meeting with all stakeholders | CISO / IRT |
| **6.2** | Document complete incident timeline | IRT Coordinator |
| **6.3** | Identify process improvements and update IRP | CISO / DPO |
| **6.4** | Update risk assessments and security controls | IT Security / Compliance |
| **6.5** | Report to Board / senior management | CISO / DPO |
| **6.6** | File any supplementary regulatory reports as required | Compliance |
| **6.7** | Retain all incident documentation for:  — GDPR: Per retention policy — RBI: 5 years minimum — SEBI: 5 years minimum — CERT-In: As directed | Legal / Compliance |

---

## Risks

| Risk | Description | Impact |
|---|---|---|
| **Delayed detection** | Average breach detection time is 204 days (IBM Cost of a Data Breach Report 2023); the 2024 report cites approximately 194 days | More data compromised; higher remediation costs |
| **Missed notification deadline** | Failing to notify within required timelines | Regulatory fines on top of breach costs |
| **Multi-jurisdiction conflicts** | Different notification timelines across jurisdictions (6h CERT-In, 72h GDPR) | Must plan for the shortest applicable deadline |
| **Evidence destruction** | Failing to preserve evidence during containment | Inability to determine breach scope; forensic failure |
| **Inadequate communication** | Poorly worded or premature public disclosure | Reputational damage; legal liability |
| **Third-party breaches** | Vendor breach where notification obligations are unclear | Delayed response; contract disputes |
| **Regulatory reporting inconsistency** | Different reports to different regulators contradicting each other | Enforcement scrutiny; loss of credibility |

---

## Mitigations

1. **Mandatory 6-hour internal escalation path** — Even if GDPR allows 72 hours, design internal processes to escalate within 6 hours (aligning with CERT-In) to ensure the shortest regulatory deadline is always met
2. **Pre-drafted notification templates** — Maintain jurisdiction-specific notification templates ready for GDPR (DPA and data subjects), DPDP Board, CERT-In, RBI, and SEBI
3. **Annual tabletop exercises** — Simulate multi-jurisdiction breach scenarios twice annually with full IRT participation
4. **24/7 monitoring** — Deploy SIEM with automated alerting to reduce detection gap
5. **Regulatory contact database** — Maintain current contact details for all applicable regulators, updated quarterly
6. **Legal privilege protocol** — Engage external counsel early to maintain attorney-client privilege over forensic findings where applicable
7. **Breach log** — Maintain GDPR Article 33(5) breach register documenting all breaches, their effects, and remedial action — even for breaches that do not require notification
