# SharePoint Mass Download Activity Log

## Overview

This log captures activity associated with a large number of files downloaded from Microsoft SharePoint within a short timeframe.

Mass download events may indicate data exfiltration attempts following account compromise or unauthorized access to organizational data.

These logs were collected as evidence during the investigation of suspicious SharePoint file access.

## Evidence Source

File activity was collected from Microsoft 365 audit logs.

| Timestamp (UTC) | Username | Operation | Site | Source IP |
|-----------------|----------|-----------|------|-----------|
| 2026-03-15 09:31 | jsmith@company.com | FileDownloaded | Finance-Site | 173.22.14.19 |
| 2026-03-15 09:32 | jsmith@company.com | FileDownloaded | Finance-Site | 173.22.14.19 |
| 2026-03-15 09:33 | jsmith@company.com | FileDownloaded | Finance-Site | 173.22.14.19 |

The activity shows repeated file downloads from the same SharePoint site within a short period of time.

## Click-by-Click Learning Process

1. Opened the Microsoft 365 Defender portal.
2. Navigated to Audit Logs.
3. Filtered results for SharePoint file operations.
4. Reviewed events associated with FileDownloaded operations.
5. Identified the user account performing the downloads.
6. Reviewed timestamps for download activity.
7. Examined the SharePoint site involved.
8. Identified the source IP address associated with the downloads.
9. Determined whether the activity represented mass file access.
10. Documented the activity and preserved the logs as evidence.

## Related Case File

Case 007 Data Exfiltration Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-007-data-exfiltration.md

## Documentation Sources

Microsoft SharePoint Activity Monitoring  
https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-search

Microsoft Defender for Cloud Apps  
https://learn.microsoft.com/en-us/defender-cloud-apps/
