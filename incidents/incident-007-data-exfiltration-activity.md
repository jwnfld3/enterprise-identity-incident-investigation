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
```

---

## Timeline of Events

| Time (UTC) | Event |
|---|---|
| 08:12 | Suspicious login detected from external IP address |
| 08:14 | Multiple file downloads initiated from OneDrive |
| 08:18 | File download activity exceeded normal thresholds |
| 08:20 | Security alert triggered in Microsoft Sentinel |
| 08:23 | SOC investigation initiated |
| 08:30 | User sessions revoked |
| 08:32 | Account password reset |
| 08:35 | Conditional Access restrictions applied |
| 08:45 | Incident contained |

---

# Investigation

Security analysts conducted a structured investigation to determine whether the file download activity represented legitimate user behavior or potential data exfiltration.

---

## Step 1 – Review Authentication Logs

Evidence Source: Microsoft Entra ID Sign-in Logs

1. Open the Azure Portal  
https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign-in Logs**

5. Apply the following filters:

- User: `jsmith@company.com`
- Time Range: Incident timeframe

6. Review the following authentication telemetry fields:

- Client IP Address  
- Location  
- Application Accessed  
- Authentication Result  

Investigators observed that the user authenticated from an unfamiliar external IP address shortly before the file download activity began.

The login location did not match the user’s normal geographic authentication patterns.

---

## Step 2 – Review Cloud Activity Logs

Evidence Source: Microsoft Sentinel OfficeActivity logs

1. Open **Microsoft Sentinel**

2. Select **Logs**

3. Query the OfficeActivity table to identify file download behavior.

```kql
OfficeActivity
| where UserId == "jsmith@company.com"
| where Operation in ("FileDownloaded","FileSyncDownloadedFull","FileCopied")
| project TimeGenerated, Operation, ClientIP, SiteUrl, SourceFileName
| order by TimeGenerated desc
```

Log analysis revealed a high volume of file downloads from SharePoint and OneDrive within a short time window.

The download activity exceeded typical usage patterns for the user account.

---

## Step 3 – Identify Accessed Files

Security investigators reviewed file activity associated with the user account.

Investigators identified several suspicious behaviors:

- Large number of file downloads
- Access to sensitive document libraries
- Download activity occurring outside normal working hours
- File access originating from an external IP address

These indicators strongly suggested potential data exfiltration activity.

---

## Step 4 – Validate Threat Intelligence

The external IP address associated with the authentication activity was evaluated using threat intelligence platforms.

Sources reviewed included:

- https://www.abuseipdb.com
- https://otx.alienvault.com
- https://www.microsoft.com/en-us/security/business/security-intelligence

Threat intelligence checks indicated that the IP address had previously been associated with malicious activity.

---

## Step 5 – Determine Incident Impact

Security investigators evaluated the scope of the activity.

Investigators confirmed:

- Multiple file downloads occurred
- Sensitive SharePoint and OneDrive documents were accessed
- The authentication activity originated from an unfamiliar external IP address

These indicators suggested potential data exfiltration behavior.

---

## Indicators of Compromise

The following indicators were identified during the investigation:

- Suspicious external IP address
- Abnormal authentication location
- High volume of file downloads
- Access to sensitive SharePoint and OneDrive documents
- Login activity occurring outside normal working hours

---

# Remediation

The following remediation actions were taken to mitigate the incident and secure the affected account.

- User account password reset
- Active authentication sessions revoked
- Conditional Access policies enforced
- Suspicious IP address activity documented and monitored
- User account temporarily restricted
- Security monitoring increased for additional abnormal activity

These actions prevented further unauthorized access to company resources.

---

# MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Exfiltration Over Command and Control Channel | T1041 | Data transferred from enterprise environment |
| Valid Accounts | T1078 | Unauthorized use of legitimate user credentials |
| Transfer Data to Cloud Account | T1537 | Data transferred to external cloud storage |

---

# Lessons Learned

This investigation highlights the importance of monitoring abnormal cloud activity and authentication behavior within enterprise environments.

Abnormal file download activity combined with suspicious authentication events may indicate credential compromise and potential data exfiltration.

Rapid detection and response are critical in preventing data loss and protecting sensitive corporate information.

Organizations should maintain continuous monitoring of identity activity and cloud service usage to detect suspicious behavior.

---

# Recommended Security Improvements

The following defensive measures are recommended to strengthen identity and data protection controls.

- Enforce Multi Factor Authentication for all users
- Implement Conditional Access policies restricting risky login locations
- Monitor abnormal file download activity
- Configure automated alerts for mass file download events
- Enable Microsoft Entra ID Identity Protection
- Conduct regular user security awareness training

---

# Conclusion

The investigation confirmed that abnormal file download activity occurred following authentication from an unfamiliar external IP address. The activity demonstrated characteristics consistent with potential data exfiltration behavior.

Security monitoring systems detected the anomaly quickly, allowing investigators to revoke user sessions and reset credentials before further data exposure occurred.

This incident demonstrates the importance of monitoring both authentication telemetry and cloud activity logs to identify potential data exfiltration attempts within enterprise environments.

---

# Documentation

The investigation techniques and remediation procedures documented in this incident report were developed through review of publicly available cybersecurity documentation and vendor guidance.

**Microsoft Sentinel Documentation**  
https://learn.microsoft.com/en-us/azure/sentinel/

**Microsoft Entra ID Sign-in Logs Documentation**  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

**Kusto Query Language Documentation**  
https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/

**Microsoft Entra Conditional Access Documentation**  
https://learn.microsoft.com/en-us/entra/identity/conditional-access/

**Microsoft Defender Security Documentation**  
https://learn.microsoft.com/en-us/defender/

**MITRE ATT&CK Framework**  
https://attack.mitre.org/
