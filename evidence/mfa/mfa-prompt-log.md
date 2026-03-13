# MFA Prompt Authentication Log

## Overview

This log captures authentication activity involving repeated multi-factor authentication (MFA) prompts generated for a user account within the Microsoft 365 environment.

MFA prompts occur when an additional authentication factor is required during the sign-in process. In some cases, attackers who possess valid credentials may attempt to trigger repeated MFA prompts in an attempt to convince the user to approve one of the requests.

These authentication events were collected as supporting evidence during the investigation of suspicious login activity.

## Evidence Source

Authentication activity was collected from Microsoft Entra ID Sign-in Logs.

| Timestamp (UTC) | Username | Source IP | Location | MFA Prompt | Result |
|-----------------|----------|-----------|----------|------------|--------|
| 2026-03-15 07:10 | awalker@company.com | 185.33.12.19 | Poland | Sent | Denied |
| 2026-03-15 07:11 | awalker@company.com | 185.33.12.19 | Poland | Sent | Denied |
| 2026-03-15 07:12 | awalker@company.com | 185.33.12.19 | Poland | Sent | Denied |

These events show multiple MFA prompts being generated within a short timeframe from the same external IP address.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to **Identity**.
3. Selected **Monitoring**.
4. Opened **Sign-in Logs**.
5. Filtered authentication activity for the affected user account.
6. Reviewed sign-in events that required multi-factor authentication.
7. Examined timestamps associated with each MFA challenge.
8. Identified repeated MFA prompts originating from the same IP address.
9. Reviewed geographic location information associated with the login attempts.
10. Documented the authentication activity and preserved the logs as investigation evidence.

## Related Case File

Case 003 MFA Fatigue Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-003-mfa-fatigue.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Microsoft Entra Multifactor Authentication Overview  
https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks

MITRE ATT&CK Credential Access Techniques  
https://attack.mitre.org/
