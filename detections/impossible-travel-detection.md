# Impossible Travel Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

## Overview

Impossible travel occurs when a user signs in from two geographically distant locations within a timeframe that would make travel between those locations impossible.

This may indicate compromised credentials.

## Purpose

The purpose of this detection is to identify suspicious authentication patterns based on geographic location changes.

## Data Sources

- Microsoft Entra ID Sign-in Logs
- Azure AD SigninLogs table
- IP address geolocation data

## Detection Logic

Indicators include:

- logins from different countries within minutes
- authentication events from distant locations
- unusual login patterns

## Click by Click Learning Process

1. Open Microsoft Entra Admin Center.
2. Navigate to Sign-in Logs.
3. Identify login events for the user.
4. Review geographic location of logins.
5. Compare timestamps.
6. Determine whether travel was possible.
7. Document findings.

## Detection Query

```kql
SigninLogs
| summarize Locations = makeset(Location) by UserPrincipalName, bin(TimeGenerated, 1h)
| where array_length(Locations) > 1
```

## Investigation Process

1. Review Sentinel alert.
2. Identify affected user account.
3. Review authentication timestamps.
4. Compare geographic locations.
5. Confirm whether travel is possible.
6. Review device information.
7. Identify suspicious IP addresses.
8. Document findings.
9. Confirm legitimacy with user.
10. Escalate if compromise suspected.

## Related Case File

Case 004 Impossible Travel Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-004-impossible-travel.md

## Remediation Playbook

Impossible Travel Login Remediation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/impossible-travel-login-remediation.md

## Documentation Sources

Microsoft Entra Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/
