# Token Theft Authentication Log

This log represents authentication activity associated with a suspected token theft attack.

Token theft occurs when an attacker obtains a valid authentication token and attempts to reuse it to access enterprise resources without re-entering credentials.

---

## Authentication Activity

| Timestamp (UTC) | User | Source IP | Application | Session Type | Result |
|-----------------|------|-----------|-------------|--------------|--------|
| 2026-03-18 09:10 | jsmith@company.com | 73.142.55.20 | Microsoft 365 | Interactive Login | Success |
| 2026-03-18 09:42 | jsmith@company.com | 185.199.110.42 | SharePoint Online | Token Reuse | Success |
| 2026-03-18 09:43 | jsmith@company.com | 185.199.110.42 | OneDrive | Token Reuse | Success |

---

## Observations

Authentication tokens issued to the user session were reused from a different geographic location.

The login originated from an IP address not previously associated with the user.

---

## Security Controls Triggered

Sign-in risk alert generated

Session anomaly detected

Security investigation initiated
