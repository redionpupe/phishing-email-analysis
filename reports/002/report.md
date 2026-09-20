# SOC Incident Report — Case 002

## Incident Summary

A controlled phishing simulation was analyzed involving an invoice-themed email sent to an Accounts Payable recipient.

The message claimed that invoice `INV-2026-0914` was overdue and used urgency and the threat of account suspension to encourage interaction with an attached invoice.

**Classification:** Simulated True Positive — Phishing  
**Severity:** Medium  
**Technique:** T1566.001 — Phishing: Spearphishing Attachment

## Key Indicators

| Type | Value |
|---|---|
| Sender | billing@secure-invoice-support.com |
| Reply-To | payments@secure-invoice-support.com |
| Domain | secure-invoice-support.com |
| Subject | URGENT: Outstanding Invoice INV-2026-0914 |
| Attachment | Invoice_INV-2026-0914.txt |
| Attachment SHA-256 | 74866fd09995074c825170b2509b7570585d92e045a1516cd2a9eaffd1bb410f |
| Email SHA-256 | b186a6906d8f0778923833607483995a946b639e91a0357a09cf8355f65de014 |

## Attachment Analysis

The MIME attachment was extracted without execution.

Static analysis identified the file as:

- ASCII text
- MIME type `text/plain`
- 159 bytes
- No executable content
- No scripts or macros
- No malicious payload identified

The attachment is intentionally benign and was created as part of the controlled simulation.

## Domain Analysis

At investigation time:

- A query: NXDOMAIN
- MX query: NXDOMAIN
- TXT query: NXDOMAIN
- WHOIS: No match

The domain is simulation infrastructure and these results should not be interpreted as evidence of real-world attacker infrastructure.

## Social Engineering Indicators

The message used:

- Financial/invoice pretext
- Urgent language
- Threat of account suspension
- Immediate-action request
- Invoice attachment
- Accounts Payable targeting

## Recommended Response

For an equivalent real-world incident:

1. Quarantine the message.
2. Preserve the original email and attachment.
3. Search for related messages across the environment.
4. Search for the sender, domain, subject, filename, and file hash.
5. Determine whether recipients interacted with the attachment.
6. Perform additional malware analysis if active or suspicious content is discovered.
7. Escalate if evidence of execution or compromise is identified.

## Analyst Conclusion

The message demonstrates an invoice-themed spearphishing attachment scenario.

Static analysis confirmed that the attachment used in this controlled simulation is benign. No malware execution, credential theft, or host compromise was observed.
