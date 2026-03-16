# Incident Report: Impossible Travel Login

## Case Metadata

Incident ID: IR-003  
Case ID: CASE-003  
Category: Identity Security Incident  
Severity: Medium  
Status: Resolved  

Detection Source: Microsoft Entra ID Identity Protection  
Reported By: Automated Security Alert  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

An impossible travel alert was generated after two successful authentication events were recorded from geographically distant locations within a short period of time.

The login locations indicated that the user account authenticated from two regions that would be impossible to travel between within the observed timeframe.

---

## Timeline

Time (UTC) | Event
--- | ---
11:05 | Successful login from United States
11:10 | Successful login from Europe
11:12 | Impossible travel alert generated
11:15 | Security investigation initiated
11:40 | Authentication events reviewed

---

## Detection

Indicators included:

- login from multiple geographic regions
- authentication events occurring within minutes
- identity protection alert triggered

---

## Investigation

### Step 1 Review Sign in Logs

1. Open Azure Portal

2. Navigate to **Microsoft Entra ID**

3. Select **Sign in Logs**

4. Filter by user account

5. Review:

- login location
- IP address
- authentication result

---

### Step 2 Investigate Security Alert

1. Open **Microsoft Sentinel**

2. Navigate to **Incidents**

3. Locate impossible travel alert

4. Review associated entities

---

### Step 3 Query Authentication Logs

```kusto
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, Location, IPAddress, ResultType
| order by TimeGenerated desc
```

---

### Step 4 Confirm User Activity

Investigators contacted the user to confirm travel activity.

The user confirmed they had not traveled during the time of the authentication events.

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | jsmith@company.com | Targeted account
IP Address | 185.193.xxx.xxx | Suspicious login source
Location | Foreign Region | Abnormal login location

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1078 | Valid Accounts
T1110 | Brute Force

---

## Security Recommendations

- Enforce MFA for all sign ins
- Monitor impossible travel alerts
- Enable conditional access risk policies

---

## Documentation

Microsoft Entra ID Sign in Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins
