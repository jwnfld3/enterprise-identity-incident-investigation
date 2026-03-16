# Incident Report: Disabled Account Login Attempts

## Case Metadata

Incident ID: IR-004  
Category: Unauthorized Authentication Attempt  
Severity: Medium  
Status: Resolved  

Detection Source: Microsoft Entra ID Sign-in Monitoring  
Reported By: Automated Security Alert  

Investigation Start Time: 2026-03-16 06:22 UTC  
Investigation End Time: 2026-03-16 07:05 UTC  

Affected User: former.employee@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

Repeated authentication attempts were detected targeting a disabled user account within the Microsoft 365 environment.

The account belonged to a former employee whose access had been revoked during offboarding procedures. Security monitoring systems flagged multiple login attempts originating from an external IP address.

Since the account had already been disabled, authentication attempts were automatically rejected.

---

## Detection

The incident was detected through Microsoft Entra ID sign-in monitoring alerts.

Indicators included:

- Login attempts targeting a disabled account
- Authentication attempts originating from an external IP address
- Repeated login attempts over a short time period

---

# Investigation

Security analysts conducted a structured investigation to determine whether the authentication activity represented a credential attack attempt or unauthorized access attempt.

---

## Step 1 – Review Microsoft Entra ID Sign-in Logs

Evidence Source: Microsoft Entra ID Sign-in Logs

1. Open the Azure Portal  
   https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign-in Logs**

5. Apply the following filters:

   - User: `former.employee@company.com`
   - Time Range: Set to incident timeframe

6. Review the following fields:

   - Client IP Address
   - Location
   - Application Accessed
   - Sign-in Status
   - Device Information

Investigators observed repeated authentication attempts targeting the disabled account. Each authentication attempt originated from an external IP address and was rejected due to the account’s disabled status.

---

## Step 2 – Query Authentication Logs Using KQL

Security investigators queried authentication telemetry to review login attempts associated with the disabled account.

```kql
SigninLogs
| where UserPrincipalName == "former.employee@company.com"
| project TimeGenerated, IPAddress, Location, AppDisplayName, ResultType
| order by TimeGenerated desc
```

Query results confirmed repeated login attempts originating from the same external IP address within a short timeframe.

The authentication attempts were rejected because the account had already been disabled.

---

## Step 3 – Identify Suspicious Authentication Behavior

The authentication activity demonstrated characteristics commonly associated with credential abuse attempts.

Observed indicators included:

- Repeated login attempts targeting a disabled account
- Authentication attempts originating from an unfamiliar IP address
- Login activity occurring after the employee had already been offboarded

These indicators suggested that an attacker may have attempted to access the account using previously obtained credentials.

---

## Step 4 – Verify Account Status

Security investigators verified the account status within Microsoft Entra ID.

1. Navigate to **Microsoft Entra Admin Center**

2. Select **Users**

3. Search for the user account `former.employee@company.com`

4. Review the **Account Enabled Status**

Investigators confirmed:

- The account was **disabled**
- Authentication access had been revoked
- No active authentication sessions existed

Because the account was disabled, all authentication attempts were automatically blocked.

---

## Step 5 – Evaluate Security Controls

Investigators reviewed identity security policies and offboarding procedures to ensure proper access controls had been implemented.

Security controls verified included:

- Account disabled status
- Conditional Access enforcement
- Identity protection monitoring
- Sign-in activity monitoring

These security controls successfully prevented unauthorized access to enterprise resources.

---

## Step 6 – Determine Incident Impact

Investigators confirmed that:

- No successful authentication occurred
- No Microsoft 365 resources were accessed
- No active sessions were established

Because the account had already been disabled, the attempted authentication activity did not result in unauthorized access.

---

# Remediation

The following remediation actions were taken to ensure continued protection of the environment.

- Disabled account status was confirmed
- Authentication logs were reviewed for additional suspicious activity
- Offboarding procedures were verified to ensure proper account deactivation
- Security monitoring was continued to detect additional login attempts
- External IP address associated with the attempts was documented for further monitoring

These actions confirmed that the attempted authentication activity did not result in unauthorized access.

---

# MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Attempted authentication using previously valid credentials |
| Brute Force | T1110 | Repeated authentication attempts targeting an account |

---

# Lessons Learned

This investigation highlights the importance of proper user offboarding procedures and identity access management controls.

Promptly disabling accounts during employee offboarding significantly reduces the risk of unauthorized access using previously issued credentials.

Continuous monitoring of authentication activity allows security teams to detect suspicious login attempts even when accounts are no longer active.

Maintaining strong identity governance and monitoring authentication telemetry are critical components of enterprise security operations.

---

# Conclusion

The investigation confirmed that repeated authentication attempts targeted a disabled account belonging to a former employee. Because proper offboarding procedures had already disabled the account, the authentication attempts were automatically rejected.

Identity monitoring systems successfully detected the suspicious login activity, and security investigators verified that no unauthorized access occurred.

This incident demonstrates the importance of maintaining strong offboarding procedures and continuous authentication monitoring within enterprise identity environments.

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
