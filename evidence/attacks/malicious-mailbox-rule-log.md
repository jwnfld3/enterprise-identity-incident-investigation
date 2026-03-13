# Malicious Mailbox Rule Activity Log

## Overview

This log captures activity associated with the creation of a malicious mailbox rule within a Microsoft 365 user mailbox.

Attackers commonly create mailbox rules after compromising an account in order to hide phishing responses, redirect sensitive communications, or maintain persistence within the compromised mailbox.

These mailbox rules often automatically forward emails to external addresses or move messages to hidden folders.

## Evidence Source

Mailbox activity was obtained from Microsoft 365 audit logs during the investigation.

| Timestamp (UTC) | User | Action | Rule Name | Destination | Result |
|-----------------|------|--------|-----------|-------------|--------|
| 2026-03-14 09:21 | jsmith@company.com | New-InboxRule | Hide-Incoming | archive-folder | Success |
| 2026-03-14 09:22 | jsmith@company.com | New-InboxRule | Forward-All | attacker@externalmail.com | Success |

These mailbox rule creations indicate suspicious activity consistent with mailbox persistence techniques used by attackers.

## Click-by-Click Learning Process

1. Opened the Microsoft 365 Defender portal.
2. Navigated to Audit Logs.
3. Filtered activity for mailbox rule operations.
4. Identified actions related to New-InboxRule events.
5. Reviewed the rule name and destination settings.
6. Identified rules forwarding email to external addresses.
7. Documented the suspicious mailbox rule activity.
8. Preserved the logs as evidence for the investigation.

## Related Case File

Case 005 Phishing Login Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-005-phishing-login.md

## Documentation Sources

Microsoft 365 Mailbox Auditing  
https://learn.microsoft.com/en-us/microsoft-365/compliance/mailbox-audit-logging

MITRE ATT&CK Email Collection  
https://attack.mitre.org/techniques/T1114/
