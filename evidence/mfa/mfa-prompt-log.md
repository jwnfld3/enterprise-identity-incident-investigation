# Multi Factor Authentication Prompt Log

This log represents Multi Factor Authentication prompt activity reviewed during an investigation of suspicious authentication attempts.

Repeated MFA prompts may indicate an MFA fatigue attack, where an attacker repeatedly attempts to authenticate hoping the user accidentally approves the request.

---

## MFA Authentication Events

| Timestamp (UTC) | User | Application | IP Address | Location | Authentication Method | Result |
|-----------------|------|-------------|-----------|----------|----------------------|--------|
| 2026-03-12 09:40 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Push Notification | Sent |
| 2026-03-12 09:41 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Push Notification | Sent |
| 2026-03-12 09:41 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Push Notification | Sent |
| 2026-03-12 09:42 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Push Notification | Sent |
| 2026-03-12 09:42 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Push Notification | Denied |
| 2026-03-12 09:43 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Push Notification | Denied |
| 2026-03-12 09:44 | jsmith@company.com | Microsoft 365 | 185.199.110.42 | Warsaw, Poland | Push Notification | Blocked |

---

## Observations

Multiple MFA prompts were triggered within a short time window.

The authentication requests originated from a location outside the user's normal login pattern.

The user reported receiving unexpected authentication prompts.

---

## Security Controls Triggered

Multi Factor Authentication enforcement

Sign in risk alert generated

Conditional Access policy triggered

Account sign in temporarily blocked during investigation
