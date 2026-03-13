# Brute Force Login Authentication Log

## Overview

This log contains authentication activity captured during a brute force login attempt targeting Microsoft 365 user accounts.

Brute force attacks involve repeatedly attempting different passwords against a specific user account until the correct password is discovered.

These attacks generate large numbers of authentication failures within a short period of time.

## Evidence Source

Authentication events were collected from Microsoft Entra ID Sign-in Logs during the investigation.

| Timestamp (UTC) | Username | Source IP | Application | Result |
|-----------------|----------|-----------|-------------|--------|
| 2026-03-12 02:10 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:11 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:12 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:13 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Account Locked |

This authentication pattern shows repeated password attempts targeting a single account.

## Click-by-Click Learning Process

1. Signed in to Microsoft Entra Admin Center.
2. Navigated to Identity.
3. Selected Monitoring.
4. Opened Sign-in Logs.
5. Filtered results for failed authentication attempts.
6. Identified repeated login attempts targeting a single account.
7. Reviewed timestamps of authentication events.
8. Documented authentication failures and account lockout events.
9. Preserved the authentication logs as evidence.

## Related Case File

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

MITRE ATT&CK Brute Force  
https://attack.mitre.org/techniques/T1110/
