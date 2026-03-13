# Brute Force Login Log

## Overview

This log contains authentication activity captured during a simulated brute force login attempt against Microsoft 365 user accounts.

The activity represents repeated authentication attempts originating from a single external IP address targeting multiple accounts.

These logs were used as supporting evidence during the investigation of suspicious authentication activity.

## Evidence Source

Authentication activity was collected from Microsoft Entra ID sign in logs and exported as part of the investigation evidence.

| Timestamp (UTC) | Username | Source IP | Application | Result |
|-----------------|----------|-----------|-------------|--------|
| 2026-03-12 02:10 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:10 | mgarcia@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:11 | dlee@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:11 | awalker@company.com | 91.214.44.18 | Microsoft 365 | Failure |
| 2026-03-12 02:12 | jsmith@company.com | 91.214.44.18 | Microsoft 365 | Account Locked |

These authentication attempts demonstrate repeated login failures from a single external IP address targeting multiple accounts, which is commonly associated with automated credential attacks.

## Click by Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to Identity.
3. Selected Monitoring.
4. Opened Sign in Logs.
5. Filtered the results for failed authentication attempts.
6. Reviewed the timestamps of the failed logins.
7. Identified repeated login attempts originating from the same source IP address.
8. Reviewed the list of usernames targeted during the activity.
9. Documented the application involved in the authentication attempts.
10. Recorded the authentication results, including failed attempts and account lockout events.
11. Preserved the authentication log activity as supporting evidence for the investigation.
12. Linked the evidence to the related case file for incident documentation.

## Related Case File

Case 001 Password Spray Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-001-password-spray.md

## Documentation Sources

Microsoft Entra ID Sign in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

MITRE ATT&CK Brute Force  
https://attack.mitre.org/techniques/T1110/
