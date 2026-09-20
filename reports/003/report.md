# SOC Incident Report — Case 003

## Incident Summary

A controlled Business Email Compromise (BEC) simulation was analyzed involving executive impersonation and an urgent wire-transfer request targeting a finance employee.

The message requested a EUR 24,750 payment related to an alleged confidential acquisition.

**Classification:** Simulated True Positive — Business Email Compromise  
**Severity:** High  
**Technique:** T1566 / T1566.003 — Phishing

## Key Indicators

| Type | Value |
|---|---|
| Apparent Sender | daniel.morrison@company-executive.com |
| Reply-To | dmorrison.executive@proton.me |
| Target | finance@example.com |
| Subject | Confidential - Urgent Payment Request |
| Amount Requested | EUR 24,750 |
| Email SHA-256 | 3380720c5e66d2fc20f50493d6b217fdb9c5ceb6fa598a50deae4fa19fe80083 |

## Key Findings

The investigation identified multiple indicators consistent with a simulated BEC attempt:

- Executive impersonation
- Finance employee targeting
- High-value wire-transfer request
- Artificial urgency
- Confidentiality request
- Attempt to discourage internal verification
- From/Reply-To discrepancy
- External Reply-To mailbox

The message contained no URL, attachment, or executable payload.

## Domain Analysis

The apparent sender domain `company-executive.com` returned NXDOMAIN for A, MX, and TXT queries and no WHOIS match.

This domain was created for the controlled simulation and does not represent observed real-world attacker infrastructure.

The Reply-To domain `proton.me` had valid MX infrastructure. Legitimate mail infrastructure does not establish that the mailbox belongs to the executive claimed in the message.

## Recommended Response

For an equivalent real-world incident:

1. Quarantine the message.
2. Do not reply to the suspicious sender.
3. Independently verify the payment request through a trusted communication channel.
4. Notify security and finance teams.
5. Search for related messages across the mail environment.
6. Determine whether other employees responded.
7. Determine whether banking information was exchanged.
8. Determine whether a payment was initiated.
9. Escalate immediately to fraud/finance response procedures if funds were transferred.
10. Preserve the original email and investigation evidence.

## Analyst Conclusion

The message represents a controlled BEC simulation based on executive impersonation and wire-transfer fraud.

The investigation demonstrates how phishing can rely entirely on social engineering without malicious links, attachments, or malware.

No actual financial loss or compromise occurred.
