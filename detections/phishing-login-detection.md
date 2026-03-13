# Phishing Login Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

## Overview

Phishing attacks attempt to steal user credentials through malicious emails or login pages.

Attackers may use stolen credentials to access enterprise systems.

## Purpose

Detect authentication activity that may occur after phishing credential theft.

## Data Sources

- Microsoft Defender for Office 365
- Microsoft Entra ID Sign-in Logs
- Email security logs

## Detection Logic

Indicators include:

- login following phishing email interaction
- authentication from suspicious locations
- login from unfamiliar devices

## Click by Click Learning Process

1. Open Microsoft Defender Portal.
2. Navigate to Threat Explorer.
3. Identify phishing emails.
4. Check user interaction.
5. Review sign-in logs.
6. Identify suspicious logins.
7. Document findings.

## Detection Query

```kql
SigninLogs
| where ResultType == 0
| where RiskLevelDuringSignIn != "none"
```

## Investigation Process

1. Review Sentinel alert.
2. Identify affected user.
3. Review phishing email event.
4. Review login activity.
5. Identify IP address and location.
6. Determine whether credentials were stolen.
7. Document findings.
8. Escalate incident if necessary.

## Related Case File

Case 005 Phishing Login Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-005-phishing-login.md

## Remediation Playbook

Phishing Attack Remediation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/phishing-attack-remediation.md

## Documentation Sources

Microsoft Defender for Office 365  
https://learn.microsoft.com/en-us/defender-office-365/
