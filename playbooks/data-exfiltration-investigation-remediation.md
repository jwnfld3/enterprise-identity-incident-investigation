# Data Exfiltration Investigation Remediation

| Field | Value |
|------|------|
| Playbook Type | Data Security Investigation |
| Threat Category | Data Exfiltration |
| Severity | High |
| Platform | Microsoft 365 / Microsoft Entra ID / Microsoft Sentinel |

---

## Objective

Investigate suspicious file access activity, determine whether sensitive data was downloaded or transferred outside the organization, and take remediation actions if unauthorized data exfiltration occurred.

---

## Overview

This playbook is used when suspicious file access or download activity is detected in Microsoft 365 services such as SharePoint or OneDrive.

Data exfiltration may occur when an attacker gains access to an account and downloads sensitive data from cloud storage platforms.

The goal of this playbook is to review file activity, determine whether the activity was legitimate, and prevent unauthorized data transfer.

---

## Detection Reference

This playbook may be triggered by alerts or detections that identify abnormal file activity.

Examples include:

- `detections/data-exfiltration-detection.md`
- `detections/phishing-login-detection.md`
- `detections/token-theft-detection.md`

These detections may indicate suspicious file downloads or abnormal user activity patterns.

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1041 | Exfiltration Over Command and Control Channel |
| T1537 | Transfer Data to Cloud Account |
| T1078 | Valid Accounts |

---

## Who

This procedure is typically performed by:

1. Security Operations Center analysts
2. Identity administrators
3. Microsoft 365 administrators
4. Incident response teams

---

## What

This procedure is used to:

1. Investigate suspicious file access activity
2. Identify users downloading large numbers of files
3. Determine whether data was accessed legitimately
4. Identify possible compromised accounts
5. Prevent unauthorized data transfer

---

## Where

This procedure is performed in:

1. Microsoft Sentinel
2. Microsoft 365 Defender portal
3. Microsoft Entra admin center

---

## When

Use this playbook when:

1. Unusual file downloads are detected
2. Large numbers of files are accessed quickly
3. Sensitive documents are accessed unexpectedly
4. A compromised account may be downloading data

---

## Why

Data exfiltration is one of the most damaging types of security incidents because it involves the loss of sensitive information.

Investigating abnormal file activity helps protect organizational data and prevent unauthorized disclosure.

---

# Step 1 Review File Access Activity

## Purpose

Identify which files were accessed or downloaded.

## Instructions

1. Open the Microsoft Sentinel portal.
2. Navigate to the workspace used for security monitoring.
3. Select Logs.
4. Query file activity logs.

Example query:

```
OfficeActivity
| where Operation == "FileDownloaded"
| summarize DownloadCount = count() by UserId, bin(TimeGenerated, 30m)
| where DownloadCount > 20
```

5. Identify users with high download counts.

## Explanation

Large numbers of downloads within a short timeframe may indicate data exfiltration activity.

---

# Step 2 Identify the User Account

## Purpose

Determine which account performed the activity.

## Instructions

1. Review the query results.
2. Identify the user account associated with the downloads.
3. Document the username and time of activity.

## Explanation

Compromised accounts are often used to access sensitive data.

---

# Step 3 Review Authentication Activity

## Purpose

Determine whether the account shows suspicious login behavior.

## Instructions

1. Open Microsoft Entra admin center.
2. Navigate to:

```
Identity
```

3. Select:

```
Monitoring & health
```

4. Click:

```
Sign in logs
```

5. Review authentication events for the user.

## Explanation

Unusual login locations or devices may indicate account compromise.

---

# Step 4 Verify User Intent

## Purpose

Confirm whether the user intentionally accessed the files.

## Instructions

1. Contact the user.
2. Ask whether they downloaded the files.
3. Confirm device and location used during access.
4. Document the response.

## Explanation

User confirmation helps determine whether the activity is legitimate.

---

# Step 5 Contain the Incident

## Purpose

Prevent further data access if the activity is malicious.

## Instructions

1. Reset the affected user password.
2. Revoke active sign in sessions.
3. Require multi factor authentication.
4. Monitor further login activity.

## Explanation

These steps help stop attackers from continuing to access data.

---

# Resolution

Suspicious file activity was reviewed, authentication behavior was investigated, and remediation actions were taken to prevent unauthorized data access.

---

# Documentation Sources

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

Microsoft 365 Audit Logs  
https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-search

MITRE ATT&CK Data Exfiltration  
https://attack.mitre.org/
