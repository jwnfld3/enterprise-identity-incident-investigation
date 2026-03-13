# Microsoft 365 Sign-in Authentication Log

## Overview

This log records authentication activity observed within the Microsoft 365 environment during security monitoring operations.

Sign-in logs provide detailed information about authentication events including the user account, IP address, application accessed, device information, and authentication results.

Security analysts review these logs to identify suspicious login behavior, failed authentication attempts, and unusual access patterns that may indicate credential compromise or unauthorized access.

## Evidence Source

Authentication activity was collected from Microsoft Entra ID Sign-in Logs.

| Timestamp (UTC) | Username | Source IP | Location | Application | Result |
|-----------------|----------|-----------|----------|-------------|--------|
| 2026-03-15 02:05 | jsmith@company.com | 44.21.101.5 | United States | Microsoft 365 | Success |
| 2026-03-15 02:08 | jsmith@company.com | 44.21.101.5 | United States | Microsoft 365 | Success |
| 2026-03-15 02:12 | mgarcia@company.com | 77.91.33.10 | Poland | Microsoft 365 | Failure |

These authentication records provide evidence of both successful and failed login attempts that may require further investigation.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to Identity.
3. Selected Monitoring.
4. Opened Sign-in Logs.
5. Filtered authentication events by time range.
6. Reviewed user account login activity.
7. Identified IP addresses associated with login attempts.
8. Examined geographic location information.
9. Reviewed authentication results for each login attempt.
10. Documented relevant authentication activity for investigation.

## Related Case File

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

## Documentation Sources

Microsoft Entra Sign-in Logs Documentation  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Microsoft Entra Monitoring and Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/
