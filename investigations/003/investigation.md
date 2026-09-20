# Case 003 — Business Email Compromise / Executive Impersonation

## 1. Case Overview

A controlled Business Email Compromise (BEC) simulation was analyzed involving an email impersonating a company Chief Executive Officer and targeting a finance employee.

The message requested assistance with a confidential EUR 24,750 wire transfer allegedly related to an acquisition.

Unlike the previous phishing cases, the email contained no malicious link or attachment. The attack relied entirely on social engineering and executive impersonation.

**From:** daniel.morrison@company-executive.com  
**To:** finance@example.com  
**Reply-To:** dmorrison.executive@proton.me  
**Subject:** Confidential - Urgent Payment Request

This case was created as a controlled simulation. No real executive identity, attacker infrastructure, or financial transaction was involved.

---

## 2. Email Analysis

The message contained several indicators associated with Business Email Compromise.

### Financial Request

The recipient was asked to facilitate a wire transfer of:

`EUR 24,750`

Financial requests directed at finance personnel represent a significant business risk and require independent verification.

### Urgency

The sender stated that the transfer needed to be completed before the end of the business day and that they were entering a meeting shortly.

This creates artificial time pressure and may discourage normal verification procedures.

### Confidentiality

The recipient was instructed:

> "Please do not discuss this with anyone else yet because the transaction is confidential."

This attempts to isolate the recipient and reduce the likelihood that another employee will identify the impersonation attempt.

### Authority Impersonation

The sender claimed to be:

`Daniel Morrison — Chief Executive Officer`

Impersonating senior leadership can exploit organizational authority and pressure employees into bypassing normal financial controls.

---

## 3. Sender and Reply-To Analysis

The apparent sender address was:

`daniel.morrison@company-executive.com`

However, the Reply-To address was:

`dmorrison.executive@proton.me`

This means that replying to the message would direct the conversation to the Proton Mail address rather than the apparent executive address.

This discrepancy is a significant investigation indicator because it creates a separate communication channel controlled by the party behind the Reply-To mailbox.

The use of a legitimate email provider does not establish that the mailbox belongs to the executive being impersonated.

---

## 4. Domain Analysis

### Apparent Sender Domain

`company-executive.com`

Investigation results:

- A record: NXDOMAIN
- MX record: NXDOMAIN
- TXT record: NXDOMAIN
- WHOIS: No match

The sender domain was created specifically for this controlled simulation. These results therefore do not represent independently observed malicious infrastructure.

### Reply-To Domain

`proton.me`

MX analysis returned valid mail infrastructure:

- `mail.protonmail.ch`
- `mailsec.protonmail.ch`

The existence of legitimate mail infrastructure does not validate the claimed sender identity.

---

## 5. Payload Analysis

The message contained:

- No URL
- No attachment
- No executable payload

Therefore, traditional payload-focused analysis such as attachment sandboxing, malware hashing, or malicious URL analysis is not applicable.

The primary indicators are behavioral and contextual rather than malware-based.

This demonstrates why BEC investigations require analysis of sender identity, communication patterns, financial context, and business processes.

---

## 6. Email Sample Integrity

SHA-256:

`3380720c5e66d2fc20f50493d6b217fdb9c5ceb6fa598a50deae4fa19fe80083`

The hash was recorded to maintain evidence integrity for the analyzed `.eml` sample.

---

## 7. MITRE ATT&CK Mapping

### T1566 — Phishing

The simulated message uses phishing/social engineering to initiate communication with the target.

### T1566.003 — Phishing: Spearphishing via Service

The Reply-To address directs communication to an account hosted through an external email service.

The mapping describes the simulated technique and does not indicate that compromise actually occurred.

---

## 8. Analyst Verdict

**Classification:** Simulated True Positive — Business Email Compromise  
**Category:** Executive Impersonation / Wire Transfer Fraud  
**Severity:** High

### Rationale

The message contains multiple BEC indicators:

1. Executive impersonation
2. Finance department targeting
3. EUR 24,750 wire-transfer request
4. Urgent deadline
5. Confidentiality request
6. Attempt to discourage discussion with other employees
7. From/Reply-To discrepancy
8. External Reply-To mailbox
9. No normal business documentation supporting the payment request

No evidence indicates that the recipient completed the requested transaction.

---

## 9. Recommended SOC Response

For an equivalent real-world BEC alert:

1. Do not reply to the suspicious message.
2. Quarantine the email.
3. Preserve the original `.eml`.
4. Independently verify the request with the alleged executive using a trusted communication channel.
5. Notify the finance/security teams.
6. Search the mail environment for messages containing the same sender, Reply-To address, subject, or similar language.
7. Determine whether other employees received or responded to the message.
8. Determine whether banking information was exchanged.
9. Determine whether any payment was initiated.
10. If a transfer occurred, immediately involve the organization's finance/fraud response process and relevant financial institution.
11. Block or monitor relevant indicators according to organizational policy.
12. Document and escalate the incident according to the organization's BEC response procedure.

---

## 10. Investigation Conclusion

The message represents a controlled simulation of a Business Email Compromise attempt targeting a finance employee through executive impersonation.

Unlike link- or attachment-based phishing, the message relies entirely on social engineering, authority, urgency, confidentiality, and financial pressure.

The investigation demonstrates that phishing analysis cannot rely exclusively on malicious URLs, file hashes, or malware indicators. Contextual indicators and independent verification of business requests are critical when investigating suspected BEC activity.

No actual compromise or financial loss occurred because this was a controlled simulation.
