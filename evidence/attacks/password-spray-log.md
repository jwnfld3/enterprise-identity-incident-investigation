# Password Spray Authentication Log

## Overview

This log contains authentication activity captured during a simulated password spray attack against multiple Microsoft 365 user accounts.

The activity shows repeated authentication attempts originating from a single external IP address targeting several user accounts within a short timeframe.

These logs were collected as supporting evidence during the investigation of suspicious authentication activity.

## Evidence Source

Authentication data was obtained from Microsoft Entra ID Sign-in Logs during the investigation.

| Timestamp (UTC) | Username | Source IP | Application | Result |
|-----------------|----------|-----------|-------------|--------|
| 2026-03-12 02:10 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:10 | mgarcia@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:11 | dlee@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:11 | awalker@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:12 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Account Locked |

## Click-by-Click Learning Process

1. Signed in to Microsoft Entra Admin Center.
2. Navigated to Identity.
3. Selected Monitoring.
4. Opened Sign-in Logs.
5. Filtered results for Failed authentication attempts.
6. Sorted events by IP address.
7. Identified repeated login attempts from a single IP.
8. Reviewed targeted user accounts.
9. Documented authentication results.
10. Preserved the log activity as investigation evidence.

## Related Case File

Case 001 Password Spray Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-001-password-spray.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

MITRE ATT&CK Password Spraying  
https://attack.mitre.org/techniques/T1110/003/
