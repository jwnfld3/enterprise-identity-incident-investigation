# Incident Report: Data Exfiltration Activity

## Case Metadata

Incident ID: IR-007  
Category: Data Exfiltration  
Severity: Critical  
Status: Contained  

Detection Source: Microsoft Sentinel  
Reported By: Automated Security Alert  

Investigation Start Time: 2026-03-22 08:20 UTC  
Investigation End Time: 2026-03-22 08:45 UTC  

Affected User: jsmith@company.com  
Affected Systems: Microsoft OneDrive, SharePoint Online  

---

## Incident Summary

A potential data exfiltration incident was detected following abnormal file download activity originating from a user account within the Microsoft 365 environment.

Security monitoring tools identified a large number of file downloads occurring within a short timeframe from the organization’s OneDrive and SharePoint services.

Initial investigation determined that the activity did not align with the user's normal behavior patterns. Further analysis revealed authentication activity from an unfamiliar external IP address prior to the file download activity.

The incident was escalated to the Security Operations Center for investigation and containment.

---

## Detection

The suspicious activity was detected through security monitoring within Microsoft Sentinel.

Automated alerts identified unusually high file download activity within a limited time window.

### Detection Query Example

```kql
OfficeActivity
| where Operation in ("FileDownloaded","FileSyncDownloadedFull","FileCopied")
| summarize DownloadCount = count() by UserId, ClientIP, bin(TimeGenerated, 30m)
| where DownloadCount >= 20
| order by DownloadCount desc
