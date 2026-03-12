# Data Exfiltration Incident Report

**Incident Type:** Data Exfiltration  
**Severity:** Critical  
**Environment:** Microsoft Entra ID / Microsoft 365  
**Detection Source:** Microsoft Sentinel  
**Status:** Contained

---

## Incident Summary

A potential data exfiltration incident was detected following abnormal file download activity originating from a user account in the Microsoft 365 environment. Security monitoring tools identified a large number of file downloads occurring within a short timeframe from the organization’s OneDrive and SharePoint services.

Initial investigation determined that the activity did not align with the user's normal behavior patterns. Further analysis revealed authentication activity from an unfamiliar external IP address prior to the file download activity.

The incident was escalated to the Security Operations Center (SOC) for investigation and containment.

---

## Detection

The suspicious activity was detected through security monitoring within Microsoft Sentinel. Automated alerts identified unusually high file download activity within a limited time window.

### Detection Query Example

```kusto
OfficeActivity
| where Operation in ("FileDownloaded","FileSyncDownloadedFull","FileCopied")
| summarize DownloadCount = count() by UserId, ClientIP, bin(TimeGenerated, 30m)
| where DownloadCount >= 20
| order by DownloadCount desc
```

The query identified abnormal file download patterns associated with a specific user account and IP address.

---

## Timeline of Events

| Time | Event |
|-----|------|
| 08:12 | Suspicious login detected from external IP address |
| 08:14 | Multiple file downloads initiated from OneDrive |
| 08:18 | File download activity exceeded normal thresholds |
| 08:20 | Security alert triggered in Microsoft Sentinel |
| 08:23 | SOC investigation initiated |
| 08:30 | User sessions revoked |
| 08:32 | Account password reset |
| 08:35 | Conditional access restrictions applied |
| 08:45 | Incident contained |

---

## Investigation Process

### Step 1: Review Authentication Logs

1. Open the Azure portal.
2. Navigate to Microsoft Entra Admin Center.
3. Select **Monitoring & Health**.
4. Click **Sign-in Logs**.
5. Filter logs by the affected user account.
6. Identify the source IP address and location of the login.

Suspicious authentication attempts were observed from an unfamiliar geographic location.

---

### Step 2: Review Cloud Activity Logs

1. Navigate to **Microsoft Sentinel**.
2. Select **Logs**.
3. Query the **OfficeActivity** table.
4. Filter results by the affected user account.

The results revealed a high volume of file download activity.

---

### Step 3: Identify Accessed Files

Investigators reviewed file activity associated with the user account and identified the following behaviors:

- Large number of file downloads
- Access to sensitive document libraries
- Download activity outside normal working hours
- Access from an external IP address

---

### Step 4: Validate Threat Intelligence

The external IP address was checked against threat intelligence sources including:

- AbuseIPDB
- AlienVault OTX
- Microsoft Security Intelligence

The IP address had previously been reported for malicious activity.

---

## Indicators of Compromise

The following indicators were identified during the investigation:

- Suspicious external IP address
- Abnormal authentication location
- High volume of file downloads
- Access to sensitive SharePoint and OneDrive documents
- Login activity outside normal working hours

---

## Containment Actions

The following containment actions were executed:

1. User account password reset
2. Active sessions revoked
3. Conditional access policies enforced
4. Suspicious IP address blocked
5. User account temporarily restricted

These actions prevented further unauthorized access to company resources.

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1041 | Exfiltration Over Command and Control Channel |
| T1078 | Valid Accounts |
| T1537 | Transfer Data to Cloud Account |

---

## Lessons Learned

The investigation highlighted the importance of monitoring abnormal cloud activity and authentication behavior. Implementing stronger access controls and improving automated detection capabilities can significantly reduce the risk of data exfiltration incidents.

---

## Recommended Security Improvements

The following defensive measures are recommended:

- Enforce multi-factor authentication for all users
- Implement Conditional Access policies restricting risky locations
- Monitor abnormal file download behavior
- Configure automated alerts for mass download activity
- Enable Microsoft Entra ID Identity Protection
- Conduct regular security awareness training

---

## Conclusion

The investigation confirmed abnormal cloud activity consistent with potential data exfiltration. Rapid detection and containment actions prevented further data loss and secured the affected account.

Continued monitoring and improved identity security controls are recommended to prevent similar incidents in the future.
