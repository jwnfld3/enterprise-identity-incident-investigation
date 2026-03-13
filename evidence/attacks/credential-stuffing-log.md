# Credential Stuffing Authentication Log

## Overview

This log records authentication activity consistent with credential stuffing attacks targeting Microsoft 365 accounts.

Credential stuffing attacks occur when attackers attempt to authenticate using previously leaked username and password combinations obtained from external data breaches.

These attacks typically generate large numbers of authentication attempts from automated tools.

## Evidence Source

Authentication data was collected from Microsoft Entra ID Sign-in Logs.

| Timestamp (UTC) | Username | Source IP | Application | Result |
|-----------------|----------|-----------|-------------|--------|
| 2026-03-13 03:05 | awalker@company.com | 77.91.33.10 | Microsoft 365 | Failure |
| 2026-03-13 03:05 | jsmith@company.com | 77.91.33.10 | Microsoft 365 | Failure |
| 2026-03-13 03:06 | mgarcia@company.com | 77.91.33.10 | Microsoft 365 | Failure |
| 2026-03-13 03:06 | dlee@company.com | 77.91.33.10 | Microsoft 365 | Failure |

This authentication activity shows multiple login attempts against different accounts originating from the same IP address.

## Click-by-Click Learning Process

1. Signed in to Microsoft Entra Admin Center.
2. Navigated to Identity.
3. Selected Monitoring.
4. Opened Sign-in Logs.
5. Filtered results for failed authentication attempts.
6. Identified repeated login attempts from the same IP address.
7. Reviewed targeted usernames.
8. Documented authentication failures.
9. Preserved logs as investigation evidence.

## Related Case File

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

MITRE ATT&CK Credential Stuffing  
https://attack.mitre.org/techniques/T1110/004/
