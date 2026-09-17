# SOC Phishing Incident Report — Case 001

## Incident Summary

A phishing email impersonating Microsoft Account Security was analyzed.

The message claimed that unusual sign-in activity had been detected and instructed the recipient to review recent account activity through an embedded link.

The investigation identified multiple indicators consistent with phishing, including failed email authentication, a suspicious sender domain, suspicious sending infrastructure, social-engineering language, and a shortened external URL.

## Classification

- **Verdict:** True Positive — Phishing
- **Severity:** High
- **Technique:** T1566.002 — Phishing: Spearphishing Link

## Key Indicators

| Type | Indicator |
|---|---|
| Sender | `noreply@microsoftonline-verify.com` |
| Domain | `microsoftonline-verify.com` |
| Sending IP | `178.238.225.91` |
| Sending Host | `mail.microsoftonline-verify.com` |
| Infrastructure Host | `vps-291847.contabo.net` |
| URL | `https://bit.ly/3vF9xKz` |
| Email SHA-256 | `a267f23a5bea8159eee0155a7fea3b0306f7a326d09bef51a0ce8ca296b6c2aa` |

## Authentication Results

- SPF: **FAIL**
- DKIM: **FAIL**
- DMARC: **FAIL**

## Evidence

The email used Microsoft branding and presented a security-related scenario designed to encourage immediate user action.

The sender domain `microsoftonline-verify.com` returned `NXDOMAIN` during the investigation and the WHOIS query returned no matching domain registration.

The email contained a shortened Bitly URL presented as the method for reviewing recent account activity.

The final destination of the shortened URL was not determined because DNS resolution for `bit.ly` was blocked by the analysis environment.

## Recommended Response

1. Quarantine the email.
2. Search for additional messages containing the identified sender, domain, and URL.
3. Determine whether any users clicked the link.
4. If users interacted with the link or submitted credentials, initiate the appropriate account-security response.
5. Preserve the original email and investigation evidence.
6. Monitor for additional activity involving the identified indicators.

## Analyst Conclusion

Based on the available evidence, Case 001 is classified as a True Positive phishing email attempting to impersonate Microsoft account security services.

The investigation identified multiple independent indicators supporting the classification, including failed sender authentication, suspicious domain infrastructure, social-engineering characteristics, and a shortened external URL.
