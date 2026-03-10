# Password Spray Attack Log

This log represents authentication activity detected during a password spray attack investigation.

Password spray attacks attempt to authenticate to multiple accounts using a small set of commonly used passwords.

---

## Authentication Attempts

| Timestamp (UTC) | Username | Source IP | Application | Result |
|-----------------|----------|-----------|-------------|--------|
| 2026-03-12 02:10 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:10 | mgarcia@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:11 | dlee@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:11 | awalker@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:12 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Account Locked |

---

## Observations

Multiple authentication attempts were detected across several user accounts originating from the same IP address.

The attack pattern indicates automated credential testing using common passwords.

---

## Security Controls Triggered

Account lockout policy activated

Sign-in risk alert generated

Security monitoring alert triggered
