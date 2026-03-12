# Data Exfiltration Detection

Detection Type: Data Security Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

---

## Overview

Data exfiltration occurs when an attacker transfers sensitive data outside the organization's environment without authorization.

Attackers may attempt to download or move large amounts of data from cloud storage services such as SharePoint or OneDrive.

---

## Purpose

The purpose of this detection is to identify abnormal file access or download activity that may indicate unauthorized data transfer.

Early detection helps security teams prevent sensitive information from leaving the environment.

---

## Data Sources

The following log sources are commonly used:

- Microsoft 365 Activity Logs
- OfficeActivity table in Microsoft Sentinel
- SharePoint file access logs
- OneDrive activity logs

---

## Detection Logic

Indicators of potential data exfiltration include:

- large numbers of file downloads
- repeated file access within a short timeframe
- unusual user activity patterns
- downloads occurring from unfamiliar IP addresses

---

## Detection Query

```kusto
OfficeActivity
| where Operation == "FileDownloaded"
| summarize DownloadCount = count() by UserId, bin(TimeGenerated, 30m)
| where DownloadCount > 20
| order by DownloadCount desc
```

This query identifies users downloading an unusually large number of files within a short timeframe.
