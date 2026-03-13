# Authentication Log Example

## Overview

This log demonstrates a sample authentication record captured from Microsoft Entra ID sign-in logs.

Authentication logs provide detailed records of login activity within Microsoft 365 environments. Each sign-in event typically includes the timestamp of the login attempt, the user account involved, the source IP address, the application accessed, and the authentication result.

Security analysts use authentication logs to investigate suspicious login attempts, identify potential credential attacks, and verify legitimate user access patterns.

## Evidence Source

Authentication activity was collected from Microsoft Entra ID Sign-in Logs.

| Timestamp (UTC) | Username | Source IP | Location | Application | Result |
|-----------------|----------|-----------|----------|-------------|--------|
| 2026-03-15 01:12 | jsmith@company.com | 44.21.101.5 | United States | Microsoft 365 | Success |
| 2026-03-15 01:15 | mgarcia@company.com | 77.91.33.10 | Poland | Microsoft 365 | Failure |
| 2026-03-15 01:17 | dlee@company.com | 91.214.44.18 | Germany | Microsoft 365 | Success |

These authentication events demonstrate both successful and failed login attempts recorded within the Microsoft 365 environment.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to **Identity**.
3. Selected **Monitoring**.
4. Opened **Sign-in Logs**.
5. Filtered authentication events by time range.
6. Reviewed user login activity.
7. Identified source IP addresses associated with authentication attempts.
8. Examined geographic location information for login events.
9. Reviewed authentication results for each event.
10. Documented the relevant authentication activity for investigation purposes.

## Related Case File

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Microsoft Entra Monitoring and Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/

MITRE ATT&CK Credential Access Techniques  
https://attack.mitre.org/
