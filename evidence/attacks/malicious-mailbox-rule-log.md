# Malicious Mailbox Rule Activity Log

This log represents mailbox activity detected during an investigation of a suspected email account compromise.

Attackers often create hidden mailbox rules to automatically forward or hide incoming messages.

---

## Mailbox Rule Activity

| Timestamp (UTC) | User | Action | Rule Name | Result |
|-----------------|------|--------|----------|--------|
| 2026-03-20 16:02 | jsmith@company.com | Rule Created | ForwardToExternal | Success |
| 2026-03-20 16:03 | jsmith@company.com | Rule Modified | HideSuspiciousEmail | Success |

---

## Observations

A mailbox rule was created to forward messages to an external email address.

The rule also attempted to hide security notification emails from the user's inbox.

---

## Security Controls Triggered

Suspicious mailbox rule alert

Security investigation initiated

Mailbox rule removed
