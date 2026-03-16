# Incident Report: Identity Compromise

## Case Metadata

Incident ID: IR-008  
Category: Identity Compromise  
Severity: Critical  
Status: Contained  

Detection Source: Microsoft Sentinel / Microsoft Entra ID Sign-in Monitoring  
Reported By: Automated Security Alert  

Affected User: jsmith@company.com  
Affected Systems: Microsoft Entra ID, Microsoft 365  

MITRE ATT&CK Techniques: T1078 Valid Accounts, T1110.003 Password Spraying, T1528 Steal Application Access Token  

---

## Incident Summary

An identity compromise incident was identified after suspicious authentication activity was detected within the Microsoft Entra ID environment. Security monitoring systems flagged abnormal login behavior involving multiple failed authentication attempts followed by a successful login from an unfamiliar IP address.

Initial investigation indicated that an attacker likely obtained valid user credentials and attempted to gain access to enterprise cloud services including Microsoft 365.

The activity was escalated to the Security Operations Center for investigation and containment.

---

## Detection

The incident was detected through authentication monitoring and SIEM analysis within Microsoft Sentinel.

Security alerts identified:

- Repeated failed login attempts
- Authentication attempts from unfamiliar geographic locations
- Successful authentication following multiple failed attempts
- Suspicious cloud activity shortly after login

These indicators suggested a possible credential based attack.

---

## Timeline of Events

| Time (UTC) | Event |
|---|---|
| 08:12 | Multiple failed login attempts detected |
| 08:14 | Authentication attempts from external IP address |
| 08:16 | Successful login recorded |
| 08:17 | Suspicious cloud activity initiated |
| 08:18 | Security alert generated in SIEM |
| 08:25 | SOC analyst begins investigation |
| 08:35 | Incident confirmed as identity compromise |
| 08:40 | Incident response procedures initiated |

---

## Indicators of Compromise

The following indicators were identified during the investigation.

**Suspicious IP Address**

185.220.101.17

**Abnormal Login Location**

Login attempts originated from a geographic location inconsistent with the user's normal login patterns.

**Authentication Pattern**

- Multiple failed login attempts  
- Successful authentication after repeated failures  
- Authentication originating from unfamiliar infrastructure  

**Suspicious User Activity**

Shortly after successful authentication, the account initiated cloud activity including file access and mailbox interactions.

---

# Investigation

Security analysts conducted a structured investigation to determine whether the authentication activity represented a legitimate login or a compromised identity.

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

Authentication telemetry confirmed multiple failed login attempts followed by a successful authentication originating from an unfamiliar external IP address.

---

## Step 2 – Query Authentication Logs Using KQL

Security investigators analyzed authentication telemetry using Microsoft Sentinel.

```kql
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, Location, AppDisplayName, ResultType
| order by TimeGenerated desc
```

Query results confirmed repeated authentication failures followed by a successful login originating from an unfamiliar external IP address.

---

## Step 3 – Verify Login Location

Security analysts evaluated geographic login data associated with the authentication events.

Investigators confirmed that the login originated from a location inconsistent with the user's normal login behavior.

This abnormal location was identified as a potential indicator of credential compromise.

---

## Step 4 – Review User Activity

Security investigators analyzed Microsoft 365 activity logs to determine actions performed after the successful authentication.

Observed activity included:

- File access activity within SharePoint
- Mailbox interactions
- Cloud resource access shortly after authentication

The activity suggested that the attacker attempted to interact with enterprise cloud services immediately after gaining access.

---

## Step 5 – Validate Threat Intelligence

The suspicious IP address was evaluated using external threat intelligence platforms.

Sources reviewed included:

- https://www.abuseipdb.com  
- https://otx.alienvault.com  
- https://www.microsoft.com/en-us/security/business/security-intelligence  

Threat intelligence analysis indicated that the IP address had previously been associated with credential attack activity.

---

## Step 6 – Determine Incident Impact

Security investigators assessed the potential impact of the compromised account.

Investigators confirmed:

- Unauthorized authentication occurred
- Suspicious cloud activity followed the login
- Identity protection alerts triggered immediately

The activity indicated a confirmed identity compromise event.

---

# Remediation

The following containment and remediation actions were implemented to secure the affected account.

- User account password reset
- Active authentication sessions revoked
- Suspicious IP address blocked using Conditional Access policies
- Multi Factor Authentication enforced
- User mailbox and cloud storage activity reviewed for unauthorized access
- Security monitoring increased for additional suspicious authentication attempts

These actions prevented further unauthorized access to enterprise systems.

---

# MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Use of legitimate credentials to gain unauthorized access |
| Password Spraying | T1110.003 | Attempted authentication using common passwords across multiple accounts |
| Steal Application Access Token | T1528 | Abuse or theft of authentication tokens for persistence |

---

# Lessons Learned

This incident highlights the importance of continuous authentication monitoring and rapid incident response.

Credential based attacks remain one of the most common methods used by attackers to gain unauthorized access to cloud environments.

Early detection of suspicious login patterns allowed the security team to contain the compromise before significant damage occurred.

---

# Recommended Security Improvements

The following defensive measures are recommended to reduce the likelihood of similar incidents.

- Enforce Multi Factor Authentication for all users
- Implement Conditional Access policies restricting risky login locations
- Configure automated alerts for abnormal authentication behavior
- Monitor authentication logs for credential attack patterns
- Implement identity protection risk detection policies

---

# Conclusion

The investigation confirmed that the suspicious authentication activity was the result of an identity compromise involving valid user credentials.

Rapid response actions including password reset, session revocation, and Conditional Access enforcement successfully contained the incident.

Ongoing monitoring and improved identity security controls are recommended to strengthen the organization’s security posture against credential based attacks.

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
