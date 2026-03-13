# MFA Fatigue Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

## Overview

MFA fatigue attacks occur when attackers repeatedly send authentication prompts to a user in hopes that the user eventually approves one of the requests.

These attacks commonly occur after attackers obtain a user's password.

## Purpose

The purpose of this detection is to identify repeated authentication attempts that generate excessive MFA prompts.

Detecting these attacks early helps prevent unauthorized access.

## Data Sources

- Microsoft Entra ID Sign-in Logs
- Authentication logs
- Conditional Access logs

## Detection Logic

Indicators include:

- repeated MFA challenges for the same account
- multiple authentication attempts within a short timeframe
- authentication attempts from unfamiliar locations

## Click by Click Learning Process

1. Open Microsoft Entra Admin Center.
2. Navigate to Sign-in Logs.
3. Search for the affected user account.
4. Review authentication attempts requiring MFA.
5. Identify repeated MFA prompts.
6. Review originating IP addresses.
7. Confirm whether the user reported unexpected MFA requests.
8. Document findings.

## Detection Query

```kql
SigninLogs
| where AuthenticationRequirement == "multiFactorAuthentication"
| summarize MFAAttempts = count() by UserPrincipalName, bin(TimeGenerated, 15m)
| where MFAAttempts > 10
| order by MFAAttempts desc
```

## Investigation Process

1. Review the Sentinel alert.
2. Identify the targeted user account.
3. Examine authentication attempts.
4. Identify IP address and location.
5. Determine whether attempts came from multiple locations.
6. Check whether any MFA prompts were approved.
7. Contact the user if necessary.
8. Confirm whether the activity is legitimate.
9. Document findings.
10. Escalate if compromise is suspected.

## Related Case File

Case 003 MFA Fatigue Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-003-mfa-fatigue.md

## Remediation Playbook

MFA Fatigue Attack Remediation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/mfa-fatigue-attack-incident-remediation.md

## Documentation Sources

Microsoft MFA Security Guidance  
https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks
