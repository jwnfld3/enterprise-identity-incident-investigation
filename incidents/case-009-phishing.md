# Incident Report: Phishing Attack Investigation

## Case Metadata

Incident ID: IR-009  
Case ID: CASE-009  
Category: Phishing Attack  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Defender for Office 365  
Reported By: Security Alert  

Affected User: jsmith@company.com  
Affected Systems: Microsoft Entra ID, Microsoft 365  

---

## Incident Summary

A phishing attack targeting employee credentials was identified after suspicious authentication activity was detected within Microsoft Entra ID sign in logs.

The investigation revealed that the user received a phishing email containing a fraudulent login page designed to capture Microsoft 365 credentials.

After entering credentials into the phishing site, the attacker attempted to authenticate using the compromised credentials.

Security monitoring systems detected abnormal login activity and generated an alert within Microsoft Sentinel.

---

## Timeline

Time (UTC) | Event
--- | ---
09:12 | Phishing email delivered to user inbox
09:15 | User opened phishing email
09:17 | User entered credentials into phishing page
09:20 | Suspicious authentication attempt detected
09:22 | Sentinel alert generated
09:25 | Security investigation initiated
10:00 | Account secured

---

## Detection

Indicators included:

- suspicious login attempt
- authentication from unfamiliar IP address
- phishing email identified
- abnormal login behavior

---

## Investigation

### Step 1 Review Email Security Alerts

1. Open **Microsoft Defender Security Portal**

2. Navigate to **Email & Collaboration**

3. Select **Threat Explorer**

4. Locate the phishing email alert.

5. Review:

- sender address
- message headers
- malicious links

---

### Step 2 Review Entra ID Sign in Logs

1. Open Azure Portal

2. Navigate to **Microsoft Entra ID**

3. Select **Sign in Logs**

4. Filter by affected user.

5. Review:

- login location
- client IP
- authentication result

---

### Step 3 Query Authentication Logs Using KQL

```kusto
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, Location, AppDisplayName, ResultType
| order by TimeGenerated desc
```

---

### Step 4 Review Cloud Activity Logs

```kusto
OfficeActivity
| where UserId == "jsmith@company.com"
| project TimeGenerated, Operation, ClientIP
| order by TimeGenerated desc
```

Investigators reviewed user activity to determine whether unauthorized actions occurred after credential compromise.

---

### Step 5 Remediation Actions

Security analysts performed the following response actions:

- reset compromised password
- revoked active sessions
- blocked phishing domain
- enforced MFA authentication
- educated the user about phishing threats

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | jsmith@company.com | Compromised account
Malicious Domain | phishing-example.com | Phishing website
IP Address | 185.193.xxx.xxx | Suspicious login source

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1566 | Phishing
T1566.002 | Spear Phishing Link
T1078 | Valid Accounts

---

## Security Recommendations

- implement advanced phishing protection
- enable safe links and safe attachments
- provide phishing awareness training
- monitor suspicious authentication activity

---

## Documentation

Microsoft Defender for Office 365  
https://learn.microsoft.com/en-us/defender-office-365/

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

MITRE ATT&CK Framework  
https://attack.mitre.org/
