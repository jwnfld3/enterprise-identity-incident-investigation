# Incident Report: MFA Fatigue Attack

## Case Metadata

Incident ID: IR-002  
Case ID: CASE-002  
Category: Identity Security Incident  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Entra ID Identity Protection  
Reported By: Automated Security Alert  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

An MFA fatigue attack was detected targeting a Microsoft 365 user account. The attacker repeatedly attempted to authenticate using valid credentials, triggering multiple MFA push notifications.

The repeated authentication prompts were intended to pressure the user into approving one of the authentication requests.

Security monitoring systems detected abnormal authentication behavior and triggered an alert within Microsoft Sentinel.

---

## Timeline

Time (UTC) | Event
--- | ---
10:05 | First authentication attempt observed
10:06 | Multiple MFA push notifications triggered
10:07 | Repeated authentication attempts detected
10:10 | Microsoft Sentinel alert generated
10:15 | Security investigation initiated
10:45 | User password reset and account secured

---

## Detection

Indicators of the attack included:

- repeated MFA push notifications
- multiple authentication attempts
- login attempts from unfamiliar location
- abnormal authentication frequency

---

## Investigation

### Step 1 Review Entra ID Sign in Logs

1. Open the Azure Portal  
https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign in Logs**

5. Filter results for the affected user.

6. Review:

- authentication result
- authentication method
- location
- client IP address

---

### Step 2 Investigate Security Alerts

1. Navigate to **Microsoft Sentinel**

2. Select **Incidents**

3. Locate the MFA fatigue alert.

4. Review:

- alert details
- affected entities
- related authentication attempts

---

### Step 3 Query Authentication Logs Using KQL

```kusto
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, Location, AuthenticationRequirement, ResultType
| order by TimeGenerated desc
```

---

### Step 4 Confirm User Activity

Security investigators contacted the affected user to determine whether the MFA requests were legitimate.

The user confirmed they did not initiate the authentication requests.

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | jsmith@company.com | Targeted account
Authentication Method | MFA Push | Repeated MFA prompts
IP Address | 185.193.xxx.xxx | Suspicious login source

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1621 | MFA Request Generation
T1078 | Valid Accounts

---

## Security Recommendations

- Implement number matching MFA authentication
- Enable user risk policies
- Configure conditional access for high risk sign ins
- Monitor excessive authentication attempts

---

## Documentation

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

Microsoft Entra ID Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/
