# Impossible Travel Authentication Log

## Overview

This log captures authentication events associated with an impossible travel scenario detected within the Microsoft 365 environment.

Impossible travel occurs when a user account signs in from two geographically distant locations within a timeframe that would make travel between the locations physically impossible. This activity may indicate that an attacker is using stolen credentials from another location.

These authentication events were collected as supporting evidence during the investigation of suspicious login activity.

## Evidence Source

Authentication activity was collected from Microsoft Entra ID Sign-in Logs.

| Timestamp (UTC) | Username | Location | Source IP | Application | Result |
|-----------------|----------|----------|-----------|-------------|--------|
| 2026-03-15 08:12 | dlee@company.com | United States | 44.21.101.5 | Microsoft 365 | Success |
| 2026-03-15 08:16 | dlee@company.com | Germany | 91.44.211.8 | Microsoft 365 | Success |

The login events show successful authentication attempts from two different geographic locations within a short timeframe.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to Identity.
3. Selected Monitoring.
4. Opened Sign-in Logs.
5. Searched for the affected user account.
6. Reviewed authentication timestamps.
7. Examined geographic location data associated with each login.
8. Compared login locations and time differences.
9. Determined that travel between the locations was not possible within the timeframe.
10. Documented the authentication events as evidence.

## Related Case File

Case 004 Impossible Travel Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-004-impossible-travel.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Microsoft Entra Identity Protection Risk Detection  
https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-risks

MITRE ATT&CK Credential Access  
https://attack.mitre.org/
