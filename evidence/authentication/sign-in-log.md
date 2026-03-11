# Authentication Sign In Log

This log represents authentication activity reviewed during the investigation of suspicious login attempts within the Microsoft Entra ID environment.

The following events were extracted from authentication monitoring logs during the investigation period.

---

## Sign In Activity

| Timestamp (UTC) | User | Application | IP Address | Location | Device | Status |
|-----------------|------|-------------|-----------|----------|--------|--------|
| 2026-03-10 08:11 | jsmith@company.com | Microsoft 365 | 73.142.55.20 | Seattle, USA | Windows 11 | Success |
| 2026-03-10 08:14 | jsmith@company.com | Outlook Online | 73.142.55.20 | Seattle, USA | Windows 11 | Success |
| 2026-03-10 08:52 | jsmith@company.com | Microsoft Teams | 73.142.55.20 | Seattle, USA | Windows 11 | Success |
| 2026-03-10 09:10 | jsmith@company.com | SharePoint Online | 185.199.110.42 | Warsaw, Poland | Unknown | Failure |
| 2026-03-10 09:11 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Unknown | Failure |
| 2026-03-10 09:11 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Unknown | Failure |
| 2026-03-10 09:12 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Unknown | MFA Challenge |
| 2026-03-10 09:13 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Unknown | Blocked |
| 2026-03-10 09:16 | jsmith@company.com | Microsoft 365 | 73.142.55.20 | Seattle, USA | Windows 11 | Success |

---

## Observations

A series of authentication attempts originated from a foreign IP address not previously associated with the user account.

The login attempts occurred shortly after normal activity from the user’s known device and location.

Multiple failed login attempts triggered a security monitoring alert.

---

## Security Controls Triggered

Multi Factor Authentication challenge

Conditional Access location restriction

Sign in risk alert generated

Suspicious authentication activity flagged for investigation
