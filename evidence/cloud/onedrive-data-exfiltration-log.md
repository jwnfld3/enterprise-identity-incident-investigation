# OneDrive Data Exfiltration Activity Log

## Overview

This log records file activity associated with a potential data exfiltration event within Microsoft OneDrive.

Data exfiltration incidents often involve a compromised account accessing or downloading large numbers of files from cloud storage services. Attackers may attempt to transfer sensitive documents outside the organization after gaining access to a user account.

These events were collected as supporting evidence during the investigation of suspicious OneDrive activity.

## Evidence Source

File activity was collected from Microsoft 365 audit logs and the OfficeActivity table in Microsoft Sentinel.

| Timestamp (UTC) | Username | Operation | File Name | Source IP |
|-----------------|----------|-----------|-----------|-----------|
| 2026-03-15 10:05 | jsmith@company.com | FileDownloaded | financial-report.xlsx | 173.22.14.19 |
| 2026-03-15 10:06 | jsmith@company.com | FileDownloaded | payroll-data.csv | 173.22.14.19 |
| 2026-03-15 10:07 | jsmith@company.com | FileDownloaded | customer-database.xlsx | 173.22.14.19 |

The activity shows multiple sensitive files downloaded within a short timeframe from a single external IP address.

## Click-by-Click Learning Process

1. Opened the Microsoft 365 Defender portal.
2. Navigated to Audit Logs.
3. Filtered activity for OneDrive file operations.
4. Reviewed events for FileDownloaded operations.
5. Identified the user account performing the downloads.
6. Reviewed timestamps of file access activity.
7. Examined source IP addresses associated with downloads.
8. Determined whether the activity involved sensitive files.
9. Documented the file access activity.
10. Preserved the logs as investigation evidence.

## Related Case File

Case 007 Data Exfiltration Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-007-data-exfiltration.md

## Documentation Sources

Microsoft 365 Audit Logs  
https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-search

Microsoft OneDrive Activity Monitoring  
https://learn.microsoft.com/en-us/microsoft-365/compliance/monitor-onedrive-activity
