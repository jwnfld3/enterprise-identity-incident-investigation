# Suspicious IP Authentication Log

## Overview

This log records authentication activity associated with a suspicious IP address attempting to access Microsoft 365 user accounts.

Suspicious IP activity can indicate malicious login attempts originating from compromised infrastructure, automated attack tools, or previously identified malicious networks.

Security monitoring systems often flag authentication attempts originating from IP addresses associated with unusual geographic locations, known malicious activity, or abnormal login patterns.

These events were collected as supporting evidence during the investigation of suspicious authentication activity within the Microsoft 365 environment.

## Evidence Source

Authentication activity was collected from Microsoft Entra ID Sign-in Logs during the investigation.

| Timestamp (UTC) | Username | Source IP | Location | Application | Result |
|-----------------|----------|-----------|----------|-------------|--------|
| 2026-03-15 04:12 | jsmith@company.com | 185.201.33.19 | Russia | Microsoft 365 | Failure |
| 2026-03-15 04:13 | mgarcia@company.com | 185.201.33.19 | Russia | Microsoft 365 | Failure |
| 2026-03-15 04:14 | awalker@company.com | 185.201.33.19 | Russia | Microsoft 365 | Failure |

These login attempts show repeated authentication attempts originating from a single IP address that is not associated with the organization's typical user login locations.

Such patterns may indicate automated login attempts or malicious authentication activity.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to **Identity**.
3. Selected **Monitoring**.
4. Opened **Sign-in Logs**.
5. Filtered results for failed authentication attempts.
6. Reviewed the **Source IP address** associated with login attempts.
7. Identified repeated login attempts originating from the same external IP address.
8. Reviewed geographic location information associated with the IP address.
9. Determined whether the IP address matched trusted or known login locations.
10. Documented authentication activity and preserved the logs as evidence for the investigation.

## Related Case File

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

## Documentation Sources

Microsoft Entra Sign-in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Investigating Risky Sign-ins in Microsoft Entra ID  
https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk

MITRE ATT&CK Credential Access Techniques  
https://attack.mitre.org/
