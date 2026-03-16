# Incident Report: Data Exfiltration Investigation

## Case Metadata

Incident ID: IR-007  
Case ID: CASE-007  
Category: Data Security Incident  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Sentinel Monitoring  
Reported By: Automated Security Alert  

Affected System: Microsoft 365  

---

## Incident Summary

Unusual cloud activity was detected suggesting potential data exfiltration from a Microsoft 365 account.

Security monitoring systems identified abnormal download activity involving large volumes of files accessed within a short timeframe.

The activity triggered a Sentinel alert indicating possible data exfiltration.

---

## Timeline

Time (UTC) | Event
--- | ---
15:05 | Large file download activity detected
15:08 | Sentinel alert generated
15:10 | Security investigation initiated
15:20 | Cloud activity logs reviewed
16:00 | Investigation completed

---

## Detection

Indicators included:

- large file download activity
- abnormal OneDrive access
- unusual SharePoint document access

---

## Investigation

### Step 1 Review Microsoft 365 Activity Logs

1. Open Azure Portal

2. Navigate to **Microsoft Sentinel**

3. Select **Logs**

4. Query Microsoft 365 activity.

---

### Step 2 Run Activity Log Query

```kusto
OfficeActivity
| where Operation == "FileDownloaded"
| project TimeGenerated, UserId, ClientIP
| order by TimeGenerated desc
```

---

### Step 3 Review File Access Activity

Investigators reviewed file access logs to determine whether the user downloaded an abnormal number of files.

---

### Step 4 Validate User Activity

Security analysts contacted the user to determine whether the downloads were legitimate.

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | jsmith@company.com | Account performing downloads
Operation | FileDownloaded | File download activity
Application | OneDrive / SharePoint | Targeted services

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1567 | Exfiltration Over Web Services
T1537 | Transfer Data to Cloud Account

---

## Security Recommendations

- monitor abnormal download behavior
- implement data loss prevention policies
- enable download anomaly detection

---

## Documentation

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/
