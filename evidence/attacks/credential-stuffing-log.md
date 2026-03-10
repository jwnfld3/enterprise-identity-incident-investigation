# Credential Stuffing Attack Log

Credential stuffing attacks occur when attackers attempt to authenticate using username and password combinations obtained from previous data breaches.

---

## Authentication Attempts

| Timestamp (UTC) | Username | Source IP | Application | Result |
|-----------------|----------|-----------|-------------|--------|
| 2026-03-15 03:45 | jsmith@company.com | 185.193.89.11 | Microsoft 365 | Failure |
| 2026-03-15 03:45 | jsmith@company.com | 185.193.89.11 | Microsoft 365 | Failure |
| 2026-03-15 03:46 | jsmith@company.com | 185.193.89.11 | Microsoft 365 | Failure |
| 2026-03-15 03:46 | jsmith@company.com | 185.193.89.11 | Microsoft 365 | Failure |

---

## Observations

Repeated login attempts targeting a single account were detected within a short time period.

The authentication attempts originated from an IP address associated with known malicious activity.

---

## Security Controls Triggered

Risk-based authentication alert

Login attempt monitoring

Account lockout protection
