# Phishing Email Analysis

A SOC-style phishing email investigation project focused on analyzing suspicious email messages, identifying indicators of compromise (IOCs), validating email authentication, investigating sender infrastructure, and documenting analyst findings.

## Project Objectives

- Analyze raw `.eml` email samples
- Investigate email headers and sender infrastructure
- Analyze SPF, DKIM, and DMARC results
- Investigate suspicious domains and IP addresses
- Extract and document URLs and other IOCs
- Identify phishing and social-engineering indicators
- Map observed behavior to MITRE ATT&CK
- Produce structured SOC investigation reports
- Document recommended response actions

## Tools & Techniques

- Linux / Kali Linux
- Email header analysis
- `dig`
- WHOIS
- `grep`
- `curl`
- SHA-256 hashing
- DNS analysis
- IOC extraction
- MITRE ATT&CK
- Git / GitHub

## Case Studies

### Case 001 — Microsoft Account Phishing

**Classification:** True Positive — Phishing  
**Severity:** High  
**MITRE ATT&CK:** T1566.002 — Phishing: Spearphishing Link

#### Summary

Investigated an email impersonating Microsoft Account Security that claimed unusual sign-in activity had been detected.

The investigation included:

- Raw email and header analysis
- Sender and Return-Path analysis
- SPF, DKIM, and DMARC validation
- DNS and WHOIS investigation
- Sending infrastructure analysis
- URL and domain extraction
- Social-engineering analysis
- IOC extraction
- MITRE ATT&CK mapping
- SOC response recommendations

#### Key Findings

- Sender used `microsoftonline-verify.com` while impersonating Microsoft.
- SPF, DKIM, and DMARC all failed.
- The sender domain returned `NXDOMAIN` during investigation.
- The email originated from observed infrastructure at `178.238.225.91`.
- The message contained a shortened `bit.ly` URL.
- The email used urgency and account-security concerns to encourage user interaction.

#### Investigation Files

- [Investigation](investigations/001/investigation.md)
- [SOC Report](reports/001/report.md)
- [IOC List](iocs/iocs.csv)
- [Email Headers](evidence/001/headers/email-headers.txt)
- [Domain Analysis](evidence/001/extracted/domain-analysis.txt)


### Case 002 — Invoice Attachment Phishing Simulation

**Classification:** Simulated True Positive — Phishing  
**Severity:** Medium  
**MITRE ATT&CK:** T1566.001 — Phishing: Spearphishing Attachment

#### Summary

Analyzed a controlled invoice-themed phishing simulation targeting an Accounts Payable recipient.

The investigation included:

- MIME attachment extraction
- SHA-256 hashing
- File type verification
- Metadata analysis
- DNS and WHOIS investigation
- Sender and Reply-To analysis
- Social-engineering analysis
- IOC extraction
- MITRE ATT&CK mapping
- SOC response recommendations

#### Key Findings

- The message used an overdue invoice as a financial pretext.
- Urgency and the threat of account suspension were used to encourage immediate action.
- The attachment was extracted without execution.
- Static analysis identified the attachment as a 159-byte ASCII text file.
- No executable content, scripts, macros, or malware were identified.
- The case demonstrates safe attachment triage using a controlled benign sample.

#### Investigation Files

- [Investigation](investigations/002/investigation.md)
- [SOC Report](reports/002/report.md)
- [IOC List](iocs/iocs.csv)
- [Email Headers](evidence/002/headers/email-headers.txt)
- [Domain Analysis](evidence/002/extracted/domain-analysis.txt)
- [File Hashes](evidence/002/file-hashes.txt)


## Repository Structure

## Repository Structure

```text
phishing-email-analysis/
├── evidence/
│   ├── 001/
│   └── 002/
├── investigations/
│   ├── 001/
│   └── 002/
├── iocs/
│   └── iocs.csv
├── reports/
│   ├── 001/
│   └── 002/
├── samples/
│   ├── case-001.eml
│   └── case-002.eml
└── README.md
```
