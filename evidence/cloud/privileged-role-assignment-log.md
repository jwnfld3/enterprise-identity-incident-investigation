# Privileged Role Assignment Log

This log represents administrative role assignment activity investigated during a privileged access review.

Unauthorized role escalation can indicate account compromise or malicious insider activity.

---

## Role Assignment Activity

| Timestamp (UTC) | Admin Account | Target User | Role Assigned | Result |
|-----------------|--------------|-------------|---------------|--------|
| 2026-03-23 11:15 | admin@company.com | jsmith@company.com | Global Reader | Success |
| 2026-03-23 11:18 | admin@company.com | jsmith@company.com | Global Administrator | Attempted |

---

## Observations

A privileged role assignment attempt was detected outside normal administrative activity hours.

The role escalation request triggered a security alert due to policy restrictions.

---

## Security Controls Triggered

Privileged Identity Management alert

Role assignment monitoring alert

Administrative activity investigation initiated
