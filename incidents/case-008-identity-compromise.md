# Incident Report: Identity Account Compromise

## Case Metadata

Incident ID: IR-008  
Case ID: CASE-008  
Category: Identity Security Incident  
Severity: Critical  
Status: Resolved  

Detection Source: Microsoft Entra ID Identity Protection  
Reported By: Automated Security Alert  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

Security monitoring systems detected high risk authentication activity associated with a Microsoft 365 user account. The authentication events suggested that an attacker may have successfully authenticated using compromised credentials.

Identity Protection risk signals indicated abnormal login behavior, including authentication from unfamiliar geographic locations and unusual sign in patterns.

Security analysts initiated an investigation to determine whether the account had been compromised and whether unauthorized activity occurred within the Microsoft 365 environment.

---

## Timeline

Time (UTC) | Event
--- | ---
16:05 | Suspicious authentication detected
16:07 | High risk sign in alert generated
16:10 | Microsoft Sentinel incident created
16:15 | Security investigation initiated
16:30 | User account secured and password reset
17:00 | Investigation completed

---

## Detection

Indicators of compromise included:

- high risk sign in alert
- abnormal login location
- unfamiliar IP address
- unusual authentication pattern

---

## Investigation

### Step 1 Review Entra ID Sign in Logs

1. Open the Azure Portal  
https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign in Logs**

5. Filter the logs by the affected user account.

6. Review the following fields:

- authentication result
- sign in location
- client IP address
- device information

---

### Step 2 Review Identity Protection Risk Alerts

1. In **Microsoft Entra ID**, navigate to **Identity Protection**

2. Select **Risky Sign ins**

3. Identify alerts associated with the user account.

4. Review:

- risk level
- authentication details
- sign in location

---

### Step 3 Investigate Sentinel Incident

1. Open **Microsoft Sentinel**

2. Navigate to **Incidents**

3. Locate the incident associated with the risky sign in alert.

4. Review:

- entities
- related alerts
- investigation graph

---

### Step 4 Query Authentication Logs Using KQL

```kusto
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, Location, ResultType
| order by TimeGenerated desc
```

---

### Step 5 Review Cloud Activity Logs

```kusto
OfficeActivity
| where UserId == "jsmith@company.com"
| project TimeGenerated, Operation, ClientIP
| order by TimeGenerated desc
```

Investigators reviewed the activity logs to determine whether unauthorized activity occurred following the authentication.

---

### Step 6 Secure the Account

Security analysts performed the following remediation actions:

- reset user password
- revoked active sessions
- enforced MFA authentication
- reviewed user activity

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | jsmith@company.com | Compromised account
IP Address | 185.193.xxx.xxx | Suspicious login source
Authentication Result | Successful Login | Possible credential compromise
Application | Microsoft 365 | Targeted cloud service

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1078 | Valid Accounts
T1110 | Brute Force
T1110.003 | Password Spraying

---

## Security Recommendations

- enable identity protection risk policies
- enforce MFA for all users
- monitor risky authentication activity
- implement conditional access risk policies

---

## Documentation

Microsoft Entra Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

MITRE ATT&CK Framework  
https://attack.mitre.org/
