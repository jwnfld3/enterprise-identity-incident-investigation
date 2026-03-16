# Incident Report: Phishing Attack Investigation

## Case Metadata

Incident ID: IR-009  
Category: Credential Phishing Attack  
Severity: High  
Status: Contained  

Detection Source: Microsoft Sentinel / Microsoft Entra ID Sign-in Monitoring  
Reported By: Automated Security Alert  

Affected User: jsmith@company.com  
Affected Systems: Microsoft Entra ID, Microsoft 365  

---

## Incident Summary

A phishing attack targeting employee credentials was identified after suspicious authentication activity was detected within Microsoft Entra ID sign-in logs.

Investigation revealed that a user interacted with a malicious email containing a fraudulent login page designed to capture Microsoft 365 credentials. The phishing message impersonated a legitimate Microsoft security notification and directed the user to a fake authentication portal.

Shortly after the user entered their credentials into the fraudulent login page, an authentication attempt was detected originating from an external IP address. Security monitoring systems flagged abnormal login behavior originating from a geographic region not previously associated with the affected user.

Immediate containment actions were taken to prevent unauthorized access to enterprise resources.

---

## Timeline of Events

| Time (UTC) | Event |
|---|---|
| 09:12 | Phishing email delivered to user inbox |
| 09:15 | User opened phishing email |
| 09:17 | User entered credentials into fraudulent login page |
| 09:20 | External authentication attempt detected |
| 09:22 | Security alert triggered for suspicious login |
| 09:25 | SOC analyst initiated investigation |
| 09:30 | User account sessions revoked |
| 09:33 | Password reset enforced |
| 09:35 | Malicious IP address blocked |

---

## Detection

The incident was detected through authentication monitoring and SIEM analysis within Microsoft Sentinel.

Security alerts identified the following indicators:

- Successful login attempt from an unfamiliar geographic location  
- Authentication originating from an IP address not previously associated with the user  
- Login activity occurring shortly after interaction with a suspicious email  

These indicators triggered a Security Operations Center investigation.

---

# Investigation

Security analysts conducted a structured investigation to determine whether the authentication activity represented legitimate user behavior or the result of stolen credentials.

---

## Step 1 – Review Microsoft Entra ID Sign-in Logs

Evidence Source: Microsoft Entra ID Sign-in Logs

1. Open the Azure Portal  
https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign-in Logs**

5. Apply the following filters:

- User: `jsmith@company.com`  
- Time Range: Incident timeframe  

6. Review authentication telemetry including:

- Client IP Address  
- Location  
- Application Accessed  
- Sign-in Result  

Investigators observed a login attempt originating from an unfamiliar IP address shortly after the phishing email interaction.

---

## Step 2 – Query Authentication Logs Using KQL

Security investigators analyzed authentication activity using Microsoft Sentinel.

```kql
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, Location, AppDisplayName, ResultType
| order by TimeGenerated desc
```

Query results confirmed authentication attempts from an external IP address not previously associated with the user.

---

## Step 3 – Examine User Activity

SOC analysts reviewed user activity across Microsoft 365 services to determine whether the attacker accessed corporate data.

Investigators reviewed:

- Mailbox activity  
- File downloads  
- SharePoint access  
- OneDrive activity  

No evidence of large-scale data access or exfiltration was identified.

---

## Step 4 – Analyze Source IP Address

The external IP address associated with the authentication attempt was investigated using threat intelligence platforms.

Sources reviewed included:

- https://www.abuseipdb.com  
- https://otx.alienvault.com  
- https://www.microsoft.com/en-us/security/business/security-intelligence  

Threat intelligence analysis indicated that the IP address had previously been associated with credential harvesting activity.

---

## Step 5 – Review Phishing Email

The phishing email was analyzed to determine how the credentials were captured.

Investigators identified the following indicators:

- Domain impersonation  
- Misleading sender information  
- Embedded login page designed to mimic Microsoft authentication portals  

The message contained a malicious link directing the user to a fraudulent Microsoft login page designed to harvest credentials.

---

## Step 6 – Determine Incident Impact

Security investigators evaluated whether the attacker successfully accessed enterprise resources.

Investigators confirmed:

- Suspicious authentication attempt occurred  
- Credentials were exposed through phishing  
- No large-scale data access occurred  

Immediate remediation actions prevented further unauthorized access.

---

# Indicators of Compromise

| Indicator Type | Value |
|---|---|
| Malicious IP Address | 185.220.xxx.xxx |
| Attack Technique | Credential Phishing |
| Target Platform | Microsoft 365 |
| Suspicious Login Location | Foreign Region |
| Phishing Domain | login-security-check.example |

---

# Remediation

The following containment actions were executed to mitigate the incident.

- Affected user account password reset  
- Active authentication sessions revoked  
- Suspicious IP address blocked using Conditional Access policies  
- Phishing email removed from affected mailboxes  
- Multi Factor Authentication enforcement verified  

These actions prevented further unauthorized access to enterprise systems.

---

# MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Phishing | T1566 | Use of phishing emails to obtain user credentials |
| Valid Accounts | T1078 | Unauthorized use of legitimate credentials |
| Credential Access Attempts | T1110 | Attempts to gain access using compromised credentials |

Mapping attack activity to MITRE ATT&CK helps security teams understand adversary techniques and improve defensive strategies.

---

# Lessons Learned

Phishing attacks remain one of the most common techniques used by attackers to obtain user credentials.

Early detection through authentication monitoring and threat intelligence correlation allowed the security team to quickly contain the threat before sensitive data was accessed.

Continued user education and identity security controls are essential to preventing similar incidents.

---

# Recommended Security Improvements

The following defensive measures are recommended to strengthen organizational security.

- Expand phishing awareness training for employees  
- Implement stricter Conditional Access policies  
- Monitor authentication logs for suspicious activity  
- Enable automated alerts for risky sign-in events  
- Improve email filtering rules to block phishing attempts  

---

# Conclusion

The phishing attack successfully captured user credentials but was detected quickly through abnormal authentication monitoring.

Security controls prevented further compromise, and remediation actions restored secure account access.

Ongoing monitoring and defensive improvements will reduce the likelihood of similar attacks targeting enterprise identity systems in the future.

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
