# MFA Authentication Activity Log

## Overview

This log records authentication events involving multi-factor authentication (MFA) within the Microsoft 365 environment.

Multi-factor authentication requires users to verify their identity using an additional authentication factor during the sign-in process. Security analysts review MFA authentication events to determine whether authentication requests were legitimate or potentially associated with suspicious login activity.

These authentication records were collected as supporting evidence during the investigation of identity-related security incidents documented within this repository.

## Evidence Source

Authentication activity was collected from Microsoft Entra ID Sign-in Logs.

| Timestamp (UTC) | Username | Source IP | Location | Authentication Method | Result |
|-----------------|----------|-----------|----------|-----------------------|--------|
| 2026-03-15 06:02 | awalker@company.com | 185.33.12.19 | Poland | Push Notification | Denied |
| 2026-03-15 06:03 | awalker@company.com | 185.33.12.19 | Poland | Push Notification | Denied |
| 2026-03-15 06:05 | jsmith@company.com | 44.21.101.5 | United States | Microsoft Authenticator | Success |

These events demonstrate authentication attempts requiring multi-factor authentication verification. Repeated MFA prompts or unusual authentication locations may indicate suspicious login activity.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to **Identity**.
3. Selected **Monitoring**.
4. Opened **Sign-in Logs**.
5. Filtered authentication activity for events requiring multi-factor authentication.
6. Reviewed authentication method details associated with each sign-in event.
7. Examined the timestamps of MFA authentication attempts.
8. Identified source IP addresses associated with authentication activity.
9. Reviewed geographic login locations.
10. Documented the authentication events and preserved the logs as investigation evidence.

## Related Case File

Case 003 MFA Fatigue Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-003-mfa-fatigue.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Microsoft Entra Multifactor Authentication Reporting  
https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-reporting

MITRE ATT&CK Credential Access Techniques  
https://attack.mitre.org/
