# Investigation Notes

## Overview

These investigation notes document observations made during the analysis of identity related security events within the Microsoft 365 environment.

Security investigations often involve reviewing authentication logs, audit logs, and activity reports in order to determine whether suspicious behavior represents legitimate user activity or potential unauthorized access.

The notes recorded here summarize investigative steps, observations, and findings discovered while analyzing authentication activity associated with the incident scenarios documented in this repository.

## Evidence Source

Investigation observations were derived from the following evidence sources:

- Microsoft Entra ID Sign-in Logs
- Microsoft Entra ID Audit Logs
- Microsoft 365 Activity Logs
- Microsoft Sentinel detection alerts
- Supporting authentication and cloud activity logs stored in the repository evidence folders

These sources provide detailed information about authentication events including timestamps, user accounts, applications accessed, source IP addresses, and authentication outcomes. :contentReference[oaicite:1]{index=1}

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to **Identity**.
3. Selected **Monitoring**.
4. Opened **Sign-in Logs** to review authentication events.
5. Filtered login activity based on timeframe and user account.
6. Reviewed authentication details such as source IP address, device information, and geographic location.
7. Cross-referenced authentication events with Microsoft Sentinel detection alerts.
8. Examined Microsoft Entra Audit Logs for related administrative or configuration changes.
9. Reviewed additional evidence logs stored in the repository for supporting activity.
10. Documented observations and investigative findings during the analysis process.

## Related Case Files

Case 001 Password Spray Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-001-password-spray.md

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

Case 003 MFA Fatigue Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-003-mfa-fatigue.md

Case 004 Impossible Travel Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-004-impossible-travel.md

Case 005 Phishing Login Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-005-phishing-login.md

Case 006 Token Theft Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-006-token-theft.md

Case 007 Data Exfiltration Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-007-data-exfiltration.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Microsoft Entra Audit Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs

Microsoft Entra Identity Protection Investigation Guidance  
https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk
