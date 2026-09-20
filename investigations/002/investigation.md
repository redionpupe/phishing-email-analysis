# Case 002 — Suspicious Invoice Attachment

## 1. Case Overview

A simulated phishing email was analyzed after being presented as an urgent outstanding invoice notification.

The message claimed that invoice `INV-2026-0914` was overdue and instructed the recipient to review the attached invoice and confirm payment immediately to avoid account suspension.

This case was created as a controlled phishing simulation for static attachment analysis. No live malware or real attacker infrastructure was used.

**Sender:** billing@secure-invoice-support.com  
**Reply-To:** payments@secure-invoice-support.com  
**Subject:** URGENT: Outstanding Invoice INV-2026-0914  
**Attachment:** Invoice_INV-2026-0914.txt

---

## 2. Email Analysis

The email used several social-engineering techniques commonly associated with invoice phishing:

- Financial pretext involving an outstanding invoice
- Urgent language
- Threat of account suspension
- Request for immediate payment confirmation
- Attachment presented as an invoice
- Generic "Accounts Payable" targeting

The message attempts to create time pressure and encourage the recipient to interact with the attachment before independently validating the invoice.

---

## 3. Sender and Domain Analysis

The message used the following addresses:

**From:** billing@secure-invoice-support.com  
**Reply-To:** payments@secure-invoice-support.com

Domain investigated:

`secure-invoice-support.com`

DNS analysis performed during the investigation returned:

- A record: NXDOMAIN
- MX record: NXDOMAIN
- TXT record: NXDOMAIN

A WHOIS query returned no match for the domain.

Because the domain was created as part of this controlled simulation, these results are documented as investigation evidence but do not represent independently observed malicious infrastructure.

---

## 4. Attachment Analysis

The email contained the following MIME attachment:

`Invoice_INV-2026-0914.txt`

The attachment was extracted from the `.eml` file without executing it.

### File Identification

The `file` utility identified the attachment as:

`ASCII text`

ExifTool identified:

- File Type: TXT
- MIME Type: text/plain
- MIME Encoding: us-ascii
- Size: 159 bytes
- Line Count: 7

### SHA-256

`74866fd09995074c825170b2509b7570585d92e045a1516cd2a9eaffd1bb410f`

### Attachment Content

The attachment contained invoice-themed text referencing:

- Invoice INV-2026-0914
- Accounts Payable
- Amount due: $4,850.00
- Status: OVERDUE

The attachment also explicitly identifies itself as a controlled training attachment.

No executable content, macros, scripts, or malware were identified.

Therefore, the attachment itself should not be classified as malicious malware.

---

## 5. Email Sample Integrity

SHA-256 of the analyzed `.eml` sample:

`b186a6906d8f0778923833607483995a946b639e91a0357a09cf8355f65de014`

The hash was recorded to provide evidence integrity for the analyzed sample.

---

## 6. MITRE ATT&CK Mapping

### T1566.001 — Phishing: Spearphishing Attachment

The simulated email uses an attachment as the primary mechanism intended to encourage recipient interaction.

The attachment itself is benign and was intentionally created for training purposes.

The ATT&CK mapping describes the simulated delivery technique and does not indicate that malware execution or compromise occurred.

---

## 7. Analyst Verdict

**Classification:** Simulated True Positive — Phishing  
**Category:** Spearphishing Attachment  
**Severity:** Medium  
**MITRE ATT&CK:** T1566.001

### Rationale

The message demonstrates multiple phishing characteristics:

1. Invoice/payment pretext
2. Urgent subject line
3. Threat of account suspension
4. Request for immediate action
5. Invoice-themed attachment
6. Generic Accounts Payable targeting

However, static analysis confirmed that the attachment is a benign text file.

There is no evidence of:

- Malware execution
- Credential theft
- Payload execution
- Persistence
- Command-and-control activity
- Host compromise

---

## 8. Recommended SOC Response

For an equivalent real-world alert, recommended actions would include:

1. Quarantine the suspicious email.
2. Preserve the original `.eml` and attachment.
3. Calculate cryptographic hashes of attachments.
4. Identify the true file type rather than relying only on the filename extension.
5. Perform static attachment analysis before considering dynamic analysis.
6. Search the environment for matching sender addresses, domains, subjects, filenames, and hashes.
7. Determine whether other users received the same message.
8. Determine whether any recipient opened or executed the attachment.
9. Escalate for deeper malware analysis if suspicious executable content, scripts, macros, or other active content are identified.
10. Document investigation findings and preserve evidence.

---

## 9. Investigation Conclusion

The analyzed message is a controlled simulation of an invoice-themed spearphishing attachment campaign.

The investigation demonstrated safe MIME attachment extraction, file identification, metadata analysis, hashing, domain investigation, social-engineering analysis, MITRE ATT&CK mapping, and SOC response planning.

The attachment was confirmed to be benign and no evidence of actual compromise was identified.
