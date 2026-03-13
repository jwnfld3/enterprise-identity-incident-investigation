# Conditional Access Policy Activity Log

## Overview

This log captures authentication events where Microsoft Entra Conditional Access policies were applied during the sign-in process.

Conditional Access policies enforce security requirements such as multi-factor authentication, device compliance, trusted network locations, or application access restrictions. These policies evaluate authentication attempts and determine whether access should be allowed, blocked, or require additional verification.

These events were collected as supporting evidence during the investigation of authentication activity subject to Conditional Access policy enforcement.

## Evidence Source

Authentication and policy evaluation activity was collected from Microsoft Entra ID Sign-in Logs and Audit Logs.

| Timestamp (UTC) | Username | Source IP | Application | Conditional Access Result | Result |
|-----------------|----------|-----------|-------------|---------------------------|--------|
| 2026-03-15 05:12 | jsmith@company.com | 185.201.33.19 | Microsoft 365 | Policy Applied | Failure |
| 2026-03-15 05:13 | jsmith@company.com | 185.201.33.19 | Microsoft 365 | Policy Applied | Blocked |
| 2026-03-15 05:14 | jsmith@company.com | 185.201.33.19 | Microsoft 365 | Policy Applied | MFA Required |

These events show authentication attempts evaluated against Conditional Access policies that resulted in blocked or restricted access.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to **Identity**.
3. Selected **Monitoring**.
4. Opened **Sign-in Logs**.
5. Filtered authentication activity for the affected user account.
6. Selected a sign-in event associated with the suspicious activity.
7. Opened the **Conditional Access** tab within the sign-in event details.
8. Reviewed which Conditional Access policies were applied during the authentication attempt.
9. Examined the policy evaluation results and access control actions.
10. Documented the authentication event and preserved the log as investigation evidence.

## Related Case File

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Microsoft Entra Audit Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs

Conditional Access Policy Monitoring  
https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-insights-reporting

MITRE ATT&CK Credential Access Techniques  
https://attack.mitre.org/
