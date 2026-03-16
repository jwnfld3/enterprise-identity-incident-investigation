# Incident Report: Suspicious Authentication Activity

## Case Metadata

Incident ID: IR-001  
Case ID: CASE-001  
Category: Identity Security Incident  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Entra ID Sign-in Monitoring  
Reported By: Automated Security Alert  

Investigation Start Time: 2026-03-10 09:10 UTC  
Investigation End Time: 2026-03-10 10:05 UTC  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

Suspicious authentication activity was detected targeting a Microsoft 365 user account. Security monitoring systems identified repeated authentication attempts originating from an unfamiliar geographic location that had not previously been associated with the user.

The authentication attempts resulted in multiple failed login events before Conditional Access policies blocked further attempts. The pattern of activity suggested a potential credential attack targeting the user account.

Security analysts initiated an investigation to determine whether the activity represented compromised credentials, automated attack activity, or legitimate user behavior.

---

## Timeline

Time (UTC) | Event
--- | ---
09:10 | Multiple failed authentication attempts detected
09:12 | Authentication attempts observed from foreign IP address
09:15 | Conditional Access policy blocked login attempt
09:18 | Microsoft Sentinel generated security alert
09:20 | Security investigation initiated
10:05 | Investigation completed and account secured

---

## Detection

The incident was detected through Microsoft Entra ID sign-in monitoring alerts.

Indicators included:

- Multiple failed authentication attempts
- Login attempts originating from a foreign IP address
- Authentication attempts outside the user's typical geographic region
- Abnormal authentication patterns identified by security monitoring systems

---

## Investigation

Security analysts followed a structured investigation process to analyze the authentication activity and determine whether the behavior represented malicious activity.

### Step 1 Review Entra ID Sign-in Logs

Investigators reviewed authentication logs to identify the source of the login attempts and determine whether the activity matched normal user behavior.

Authentication events were reviewed for:

- source IP address
- geographic location
- authentication result
- authentication method
- application access

### Step 2 Analyze Security Alerts in Microsoft Sentinel

Security analysts reviewed the alert generated in Microsoft Sentinel to identify the entities associated with the incident.

Alert details included:

- affected user account
- source IP address
- triggered detection rule
- related authentication events

### Step 3 Perform Authentication Log Analysis Using KQL

```kusto
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, Location, AppDisplayName, ResultType
| order by TimeGenerated desc
```

The query was used to identify abnormal authentication patterns and correlate related login events.

### Step 4 Review Cloud Activity Logs

```kusto
OfficeActivity
| where UserId == "jsmith@company.com"
| project TimeGenerated, Operation, ClientIP
| order by TimeGenerated desc
```

Cloud activity logs were reviewed to determine whether unauthorized actions occurred following the authentication attempts.

### Step 5 Validate IP Reputation

Investigators analyzed the reputation of the source IP address using external threat intelligence sources to determine whether the IP had been previously associated with malicious activity.

### Step 6 Confirm User Activity

The affected user was contacted to determine whether the authentication attempts were legitimate. The user confirmed that they had not initiated the login attempts.

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | jsmith@company.com | Targeted account
IP Address | 185.193.xxx.xxx | Foreign IP associated with login attempts
Authentication Result | Failed Sign-in Attempts | Multiple authentication failures
Target Application | Microsoft 365 | Targeted cloud service

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1110 | Brute Force
T1110.003 | Password Spraying
T1078 | Valid Accounts

These techniques represent common methods used by attackers attempting to gain access to enterprise identity systems.

---

## Security Recommendations

### Strengthen Conditional Access Policies

Implement Conditional Access rules that require additional authentication verification for login attempts originating from unfamiliar locations.

### Monitor Authentication Anomalies

Configure automated detection rules to identify abnormal authentication patterns such as repeated failed login attempts or impossible travel scenarios.

### Implement Identity Protection Policies

Enable identity risk detection policies that automatically block high-risk authentication attempts and require password resets when suspicious activity is detected.

### Improve Security Awareness

Provide security awareness training to help users recognize suspicious authentication notifications and potential credential compromise attempts.

---

## Documentation

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

Microsoft Entra ID Sign-in Logs Documentation  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Kusto Query Language Documentation  
https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/

MITRE ATT&CK Framework  
https://attack.mitre.org/
