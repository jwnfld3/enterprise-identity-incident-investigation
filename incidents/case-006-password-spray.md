# Incident Report: Password Spray Attack

## Case Metadata

Incident ID: IR-006  
Case ID: CASE-006  
Category: Credential Attack  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Sentinel Analytics Rule  
Reported By: Automated Security Alert  

Affected System: Microsoft Entra ID  

---

## Incident Summary

A password spray attack was detected targeting multiple user accounts within the Microsoft 365 environment.

The attacker attempted to authenticate against numerous accounts using a small set of common passwords. This technique is commonly used to avoid account lockout policies.

Security monitoring systems detected abnormal authentication patterns and generated an alert within Microsoft Sentinel.

---

## Timeline

Time (UTC) | Event
--- | ---
14:05 | Multiple authentication attempts detected
14:07 | Failed login attempts across several accounts
14:10 | Sentinel analytics rule triggered
14:15 | Security investigation initiated
14:50 | Investigation completed

---

## Detection

Indicators included:

- multiple authentication failures
- repeated login attempts across accounts
- single IP address targeting many users

---

## Investigation

### Step 1 Review Authentication Logs

1. Open Azure Portal

2. Navigate to **Microsoft Entra ID**

3. Select **Sign in Logs**

4. Filter authentication attempts by time range.

5. Identify repeated login attempts across multiple user accounts.

---

### Step 2 Investigate Security Alert

1. Open **Microsoft Sentinel**

2. Select **Incidents**

3. Locate the password spray alert.

4. Review:

- affected users
- source IP
- authentication events

---

### Step 3 Run Detection Query

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by IPAddress
| order by FailedAttempts desc
```

---

### Step 4 Correlate Affected Accounts

Investigators identified several targeted accounts and confirmed that all login attempts failed.

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
Source IP | 185.193.xxx.xxx | Attacker IP address
Authentication Failures | Multiple | Repeated login attempts
Target Accounts | Multiple Users | Credential attack targets

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1110 | Brute Force
T1110.003 | Password Spraying

---

## Security Recommendations

- enforce MFA for all user accounts
- monitor authentication failures
- block suspicious IP addresses
- enable smart lockout policies

---

## Documentation

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

MITRE ATT&CK  
https://attack.mitre.org/
