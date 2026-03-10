# Brute Force Authentication Attack Log

This log represents authentication attempts detected during a brute force login attack.

Brute force attacks involve repeated login attempts targeting a specific account.

---

## Authentication Attempts

| Timestamp (UTC) | Username | Source IP | Application | Result |
|-----------------|----------|-----------|-------------|--------|
| 2026-03-16 01:12 | jsmith@company.com | 45.142.122.55 | Microsoft 365 | Failure |
| 2026-03-16 01:13 | jsmith@company.com | 45.142.122.55 | Microsoft 365 | Failure |
| 2026-03-16 01:13 | jsmith@company.com | 45.142.122.55 | Microsoft 365 | Failure |
| 2026-03-16 01:14 | jsmith@company.com | 45.142.122.55 | Microsoft 365 | Failure |

---

## Observations

Multiple login attempts targeting a single account occurred in rapid succession.

The attack pattern suggests automated password guessing.

---

## Security Controls Triggered

Account lockout policy

Suspicious sign-in alert

Identity protection monitoring
