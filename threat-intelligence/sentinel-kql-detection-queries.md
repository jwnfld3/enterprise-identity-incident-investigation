# Microsoft Sentinel KQL Detection Queries

## Overview

This document contains example Kusto Query Language (KQL) detection queries used to identify suspicious activity within Microsoft Sentinel.

KQL is the primary query language used in Microsoft Sentinel to analyze log data collected from sources such as Microsoft Entra ID, Microsoft 365, and other cloud services.

Security analysts use KQL queries to perform threat hunting, detect abnormal activity patterns, and support incident investigations.

The queries included in this document demonstrate detection logic used to identify authentication anomalies and potential credential attacks.

## Evidence Source

Detection queries analyze log data stored within Microsoft Sentinel Log Analytics workspaces.

Common log sources include:

- Microsoft Entra ID Sign-in Logs
- Microsoft 365 Activity Logs
- OfficeActivity table
- AuditLogs table
- Azure Monitor Log Analytics data

These log sources provide authentication events, administrative activity, file access records, and other security related telemetry used for investigation and detection.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Sentinel portal.
2. Navigated to **Microsoft Sentinel**.
3. Selected the appropriate **Log Analytics Workspace**.
4. Opened the **Logs** query editor.
5. Selected the relevant data table such as **SigninLogs** or **OfficeActivity**.
6. Entered a Kusto Query Language (KQL) detection query.
7. Executed the query to analyze log data.
8. Reviewed query results for suspicious activity patterns.
9. Adjusted filters and thresholds to improve detection accuracy.
10. Saved the query for use in threat hunting or detection rules.

## Detection Queries

### Failed Sign-in Activity

This query identifies failed authentication attempts recorded in Microsoft Entra ID sign-in logs.

```kusto
SigninLogs
| where ResultType != 0
| project TimeGenerated, UserPrincipalName, IPAddress, Location
| order by TimeGenerated desc
```

This query helps identify suspicious login failures that may indicate credential attacks.

---

### Password Spray Detection

This query identifies repeated authentication failures from a single IP address targeting multiple user accounts.

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count(), TargetedUsers = dcount(UserPrincipalName) by IPAddress, bin(TimeGenerated, 15m)
| where FailedAttempts >= 15 and TargetedUsers >= 5
| order by FailedAttempts desc
```

This detection logic identifies patterns commonly associated with password spray attacks.

---

### Impossible Travel Detection

This query identifies login events where a user signs in from different geographic locations within a short timeframe.

```kusto
SigninLogs
| summarize Locations = make_set(Location), LoginCount = count() by UserPrincipalName, bin(TimeGenerated, 30m)
| where array_length(Locations) > 1
```

Such behavior may indicate compromised credentials or account misuse.

---

### Large File Download Activity

This query identifies unusually large numbers of file downloads that may indicate data exfiltration activity.

```kusto
OfficeActivity
| where Operation == "FileDownloaded"
| summarize DownloadCount = count() by UserId, bin(TimeGenerated, 30m)
| where DownloadCount > 20
| order by DownloadCount desc
```

This query helps identify abnormal file access patterns within Microsoft 365 cloud storage services.

## Documentation Sources

Microsoft Sentinel KQL Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

Kusto Query Language Overview  
https://learn.microsoft.com/en-us/kusto/query/

Microsoft Entra Sign-in Logs Reference  
https://learn.microsoft.com/en-us/azure/azure-monitor/reference/tables/signinlogs
