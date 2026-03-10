# Suspicious IP Address Authentication Log

This log represents authentication attempts originating from a known malicious IP address detected during the investigation.

---

## Authentication Attempts

| Timestamp (UTC) | Username | Source IP | Location | Result |
|-----------------|----------|-----------|----------|--------|
| 2026-03-17 05:22 | jsmith@company.com | 103.244.72.90 | Moscow, Russia | Failure |
| 2026-03-17 05:22 | jsmith@company.com | 103.244.72.90 | Moscow, Russia | Failure |
| 2026-03-17 05:23 | jsmith@company.com | 103.244.72.90 | Moscow, Russia | Blocked |

---

## Observations

Authentication attempts originated from an IP address associated with suspicious activity.

The login attempts targeted corporate Microsoft 365 resources.

---

## Security Controls Triggered

Conditional Access policy enforcement

Sign-in risk detection

Access blocked due to location policy
