# Token Theft Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

## Overview

Token theft occurs when attackers obtain authentication tokens used to maintain access to cloud services.

These tokens allow attackers to bypass password authentication.

## Purpose

Detect suspicious authentication sessions indicating stolen authentication tokens.

## Data Sources

- Microsoft Entra ID Sign-in Logs
- Azure AD SigninLogs
- Application authentication logs

## Detection Logic

Indicators include:

- login sessions persisting across devices
- authentication tokens used from new IP addresses
- unusual application access

## Click by Click Learning Process

1. Open Microsoft Entra Admin Center.
2. Navigate to Sign-in Logs.
3. Identify active sessions.
4. Review device and location data.
5. Identify suspicious token usage.
6. Document findings.

## Detection Query

```kql
SigninLogs
| where AuthenticationRequirement == "singleFactorAuthentication"
| summarize SessionCount = count() by UserPrincipalName, IPAddress
| where SessionCount > 10
```

## Investigation Process

1. Review Sentinel alert.
2. Identify user account.
3. Review session activity.
4. Compare device information.
5. Identify suspicious access.
6. Document findings.
7. Escalate if compromise suspected.

## Related Case File

Case 006 Token Theft Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-006-token-theft.md

## Remediation Playbook

Identity Compromise Remediation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/identity-compromise-remediation.md

## Documentation Sources

Microsoft Entra Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/
