# Investigation 001

## 1. Alert Information

**Alert Type:** Suspicious email

**Date/Time:** February 6, 2026

**Reported By:** Email recipient

**Subject:** [Action Required] Unusual sign-in activity on your account

---

## 2. Initial Assessment

The email claims to originate from the Microsoft Account Team and reports unusual sign-in activity. Initial review identified several artifacts requiring investigation, including a Microsoft-themed sender domain, failed SPF/DKIM/DMARC authentication, external sending infrastructure, and a shortened URL.

No final verdict has been reached at this stage.

---

## 3. Sender Analysis

**Display Name:** Microsoft Account Team

**From Address:** noreply@microsoftonline-verify.com

**Reply-To:** Not present

**Return-Path:** noreply@microsoftonline-verify.com

**Sender Domain:** microsoftonline-verify.com

---

## 4. Header Analysis

### SPF

**Result:** FAIL

**Evidence:** Google reports that microsoftonline-verify.com does not designate 178.238.225.91 as a permitted sender.

### DKIM

**Result:** FAIL

**Evidence:** dkim=fail for microsoftonline-verify.com

### DMARC

**Result:** FAIL

**Evidence:** dmarc=fail for microsoftonline-verify.com

### Sending Infrastructure

**Sending IP:** 178.238.225.91

**Mail Server:** mail.microsoftonline-verify.com

**Received Chain:** mail.microsoftonline-verify.com → mx.google.com

---

## 5. URL Analysis

### URL 1

**URL:** https://bit.ly/3vF9xKz

**Domain:** bit.ly

**Final Destination:** Not yet determined

---

## 7. Indicators of Compromise

### Domains

- microsoftonline-verify.com
- bit.ly

### IP Addresses

- 178.238.225.91
- 91.234.99.42

### URLs

- https://bit.ly/3vF9xKz

### Email Addresses

- noreply@microsoftonline-verify.com

### File Hashes

- [SHA256 of case-001.eml]

---

## 8. Phishing Indicators

- Microsoft branding is used with a non-Microsoft sender domain.
- SPF authentication failed.
- DKIM authentication failed.
- DMARC authentication failed.
- The email uses a shortened bit.ly URL whose final destination has not yet been determined.

# Phishing Email Investigation — Case 001

## 1. Case Overview

**Sample:** `samples/case-001.eml`

**Investigation Type:** Phishing Email Analysis

**Initial Assessment:** Suspicious / Likely Phishing

## 2. Sender and Infrastructure Analysis

### Sender Information

- From: `Microsoft Account Team <noreply@microsoftonline-verify.com>`
- Return-Path: `noreply@microsoftonline-verify.com`
- Sender Domain: `microsoftonline-verify.com`

### Observed Sending Infrastructure

- Sending Host: `mail.microsoftonline-verify.com`
- Observed Sending IP: `178.238.225.91`
- Reverse/Provider Hostname: `vps-291847.contabo.net`

### Domain Investigation

DNS and WHOIS queries performed on `microsoftonline-verify.com` returned:

- A record: `NXDOMAIN`
- MX record: `NXDOMAIN`
- TXT record: `NXDOMAIN`
- WHOIS: `No match for domain`

This indicates that the sender domain does not currently resolve in DNS and does not currently have a registration record in the queried WHOIS database.

### Email Authentication

- SPF: `FAIL`
- DKIM: `FAIL`
- DMARC: `FAIL`

The authentication failures indicate that the message failed the sender-authentication checks performed by the recipient's mail infrastructure.

## 3. URL Analysis

### Extracted URL

- URL: `https://bit.ly/3vF9xKz`
- URL Type: Shortened URL
- Domain: `bit.ly`
- Path: `/3vF9xKz`

The URL was extracted directly from the HTML body of the email. No direct browser access was performed.

A DNS lookup for `bit.ly` from the analysis environment returned `NXDOMAIN`. The DNS response contained an RPZ-related authority record, indicating that DNS policy/filtering may be affecting resolution in the analysis environment.

The final redirect destination has not yet been determined.

## 4. Email Content Analysis

### Subject and Theme

The email presents itself as a Microsoft account security notification and claims that unusual sign-in activity was detected.

### Social Engineering Indicators

The message contains several characteristics commonly associated with phishing:

- **Impersonation:** The sender presents itself as the "Microsoft Account Team."
- **Security scare:** The recipient is told that unusual account activity was detected.
- **Urgency:** The message instructs the recipient to secure the account immediately.
- **Call to action:** The recipient is directed to "Review recent activity."
- **External link:** The call-to-action button links to a shortened `bit.ly` URL rather than an obvious Microsoft-owned domain.
- **Brand impersonation:** The email uses Microsoft-related branding and account-security language.

### Claimed Sign-In Information

The email displays:

- Country/region: `Russia`
- IP address: `91.234.99.42`
- Platform: `Windows 10`
- Browser: `Chrome 120.0`

These values are presented by the email itself and should not be treated as independently verified evidence of an actual Microsoft account login.

### Assessment

The combination of Microsoft impersonation, an urgent security-themed message, a call to action, and a shortened external URL is consistent with a phishing/social-engineering attempt.

## 5. MITRE ATT&CK Mapping

### T1566 — Phishing

The email attempts to persuade the recipient to interact with a link while impersonating Microsoft account security services.

### T1566.002 — Phishing: Spearphishing Link

The message contains a link presented as a way to review recent account activity:

`https://bit.ly/3vF9xKz`

The link is embedded behind the "Review recent activity" call-to-action.

### Technique Assessment

| Technique | Evidence | Confidence |
|---|---|---|
| T1566 | Phishing email impersonating Microsoft | High |
| T1566.002 | Link included in email to "Review recent activity" | High |

## 6. Analyst Verdict

**Classification:** True Positive — Phishing

**Severity:** High

### Rationale

The email contains multiple indicators consistent with a phishing attempt:

1. The sender claims to represent Microsoft but uses the domain `microsoftonline-verify.com`.
2. SPF, DKIM, and DMARC authentication checks all failed.
3. The sender domain currently returns `NXDOMAIN` and has no matching WHOIS registration.
4. The message uses an account-security scare and urgent language to encourage user interaction.
5. The email contains a shortened `bit.ly` URL rather than a clearly identifiable Microsoft-owned URL.
6. The URL is presented as the mechanism for reviewing recent account activity.

The available evidence is sufficient to classify the message as phishing.

### Limitations

The final destination of the shortened URL could not be determined from the analysis environment because DNS resolution for `bit.ly` was blocked by the local DNS infrastructure.

The IP address `91.234.99.42` shown in the email body was not independently verified and is therefore treated as claimed email content rather than confirmed attacker infrastructure.

## 7. Recommended SOC Response

1. Quarantine/remove the phishing email from affected mailboxes.
2. Search the mail environment for other messages containing the sender domain, sender address, or shortened URL.
3. Block or monitor the identified sender/domain and URL where appropriate.
4. Determine whether any recipients clicked the link.
5. If a user interacted with the link or entered credentials, initiate the appropriate account-security and incident-response procedures.
6. Preserve the original `.eml` file and investigation evidence for further analysis.

## 8. Investigation Conclusion

Case 001 was assessed as a phishing email impersonating Microsoft account security services. The investigation identified failed email authentication, suspicious sender infrastructure, social-engineering indicators, and a shortened external URL.

The available evidence supports a **True Positive — Phishing** classification.
