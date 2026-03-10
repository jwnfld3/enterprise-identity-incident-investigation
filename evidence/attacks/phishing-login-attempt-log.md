# Phishing Login Attempt Log

This log represents authentication attempts detected following a suspected phishing attack targeting user credentials.

Phishing attacks attempt to trick users into entering their credentials into a fraudulent login page.

---

## Authentication Attempts

| Timestamp (UTC) | Username | Source IP | Location | Result |
|-----------------|----------|-----------|----------|--------|
| 2026-03-19 13:12 | jsmith@company.com | 193.36.117.44 | Amsterdam, Netherlands | Failure |
| 2026-03-19 13:13 | jsmith@company.com | 193.36.117.44 | Amsterdam, Netherlands | Failure |
| 2026-03-19 13:14 | jsmith@company.com | 193.36.117.44 | Amsterdam, Netherlands | MFA Required |

---

## Observations

Authentication attempts occurred shortly after the user reported receiving a suspicious email requesting login verification.

The login attempts originated from a location outside the user's normal login pattern.

---

## Security Controls Triggered

Multi-Factor Authentication challenge

Suspicious login alert

Security investigation initiated
