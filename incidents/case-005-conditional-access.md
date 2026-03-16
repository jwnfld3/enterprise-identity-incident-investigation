# Incident Report: Conditional Access Policy Block

## Case Metadata

Incident ID: IR-005  
Case ID: CASE-005  
Category: Identity Security Incident  
Severity: Low  
Status: Resolved  

Detection Source: Microsoft Entra ID Conditional Access  
Reported By: Automated Security Alert  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

A login attempt targeting a Microsoft 365 user account was blocked by a Conditional Access policy.

The authentication attempt originated from a device and location that did not meet the organization's access requirements. Conditional Access policies prevented the login attempt from successfully authenticating.

Security monitoring systems flagged the event for investigation to confirm whether the login attempt represented malicious activity.

---

## Timeline

Time (UTC) | Event
--- | ---
13:05 | Authentication attempt detected
13:06 | Conditional Access policy blocked sign in
13:08 | Security alert generated
13:10 | Security investigation initiated
13:30 | Investigation completed

---

## Detection

The event was detected by Conditional Access monitoring.

Indicators included:

- login attempt from non compliant device
- authentication from unfamiliar location
- Conditional Access policy enforcement

---

## Investigation

### Step 1 Review Conditional Access Sign In Logs

1. Open the Azure Portal  
https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign in Logs**

5. Filter by the affected user account.

6. Review:

- Conditional Access status
- login location
- device compliance
- authentication result

---

### Step 2 Investigate Security Alert

1. Open **Microsoft Sentinel**

2. Navigate to **Incidents**

3. Locate the Conditional Access alert.

4. Review:

- alert entities
- authentication details
- policy enforcement results

---

### Step 3 Query Authentication Logs Using KQL

```kusto
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, ConditionalAccessStatus, IPAddress, Location
| order by TimeGenerated desc
```

---

### Step 4 Validate Authentication Attempt

Investigators confirmed that the Conditional Access policy successfully blocked the login attempt.

No unauthorized access occurred.

---

## Indicators of Compromise

Indicator Type | Value | Description
--- | --- | ---
User Account | jsmith@company.com | Targeted account
Authentication Result | Blocked | Conditional Access enforcement
IP Address | 185.193.xxx.xxx | Suspicious login source

---

## MITRE ATT&CK Mapping

Technique | Description
--- | ---
T1078 | Valid Accounts
T1110 | Brute Force

---

## Security Recommendations

- enforce Conditional Access policies for all external sign ins
- require MFA for risky sign ins
- monitor blocked authentication attempts

---

## Documentation

Microsoft Entra Conditional Access  
https://learn.microsoft.com/en-us/entra/identity/conditional-access/
