# Incident Report: Disabled Account Authentication

## Case Metadata

Incident ID: IR-004  
Case ID: CASE-004  
Category: Identity Security Incident  
Severity: Medium  
Status: Resolved  

Detection Source: Microsoft Sentinel  
Reported By: Automated Security Alert  

Affected System: Microsoft Entra ID  

---

## Incident Summary

Authentication attempts were detected against a disabled user account within the Microsoft 365 environment.

Attempts to authenticate using disabled accounts may indicate automated credential attacks or malicious activity attempting to enumerate valid user accounts.

---

## Timeline

Time (UTC) | Event
--- | ---
12:00 | Authentication attempt against disabled account
12:02 | Multiple failed login attempts detected
12:05 | Microsoft Sentinel alert generated
12:10 | Security investigation initiated

---

## Detection

Indicators included:

- login attempts against disabled account
- repeated authentication failures
- abnormal login pattern

---

## Investigation

### Step 1 Review Sign in Logs

1. Open Azure Portal

2. Navigate to **Microsoft Entra ID**

3. Select **Sign in Logs**

4. Filter by disabled account

5. Review:

- authentication result
- login location
- IP address

---

### Step 2 Investigate Security Alerts

1. Open **Microsoft Sentinel**

2. Select **Incidents**

3. Review alert details

---

### Step 3 Query Authentication Logs

```kusto
SigninLogs
| where ResultType == "50057"
| project TimeGenerated, UserPrincipalName, IPAddress
| order by TimeGenerated desc
```

---

### Step 4 Evaluate Security Controls

Security analysts confirmed that the account remained disabled and that no successful authentication occurred.

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | disabled.user@company.com | Disabled account targeted
Authentication Result | Failed Login | Attempted authentication
IP Address | 185.193.xxx.xxx | Suspicious login source

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1110 | Brute Force
T1078 | Valid Accounts

---

## Security Recommendations

- Monitor authentication attempts against disabled accounts
- enable automated account lockout detection
- implement detection rules for account enumeration activity

---

## Documentation

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/
