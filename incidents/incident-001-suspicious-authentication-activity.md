# Incident Report: Suspicious Authentication Activity

## Case Metadata

Incident ID: IR-001  
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

Suspicious authentication attempts were detected targeting a user account within the Microsoft 365 environment.

Authentication attempts originated from a foreign IP address that had not previously been associated with the user. Multiple failed login attempts were recorded before Conditional Access policies blocked further attempts.

Security monitoring systems flagged the activity due to abnormal login patterns and geographic location anomalies.

---

## Detection

The incident was detected through Microsoft Entra ID sign-in monitoring alerts.

Indicators included:

- Multiple failed login attempts
- Authentication attempts from a foreign IP address
- Login attempts originating from an unusual geographic location

---

## Investigation

### Step 1 – Review Authentication Logs

Security investigators reviewed Microsoft Entra ID sign-in logs for the affected user account.

Evidence source: Microsoft Entra ID Sign-in Logs

Investigators analyzed authentication telemetry including login timestamps, IP addresses, and geographic location data.

Log analysis confirmed that multiple authentication attempts originated from an unfamiliar IP address associated with a foreign geographic region. The login attempts failed due to incorrect credentials and Conditional Access restrictions.

---

### Step 2 – Identify Indicators of Suspicious Activity

The authentication attempts demonstrated several characteristics commonly associated with credential abuse attempts.

Observed indicators included:

- Multiple authentication failures targeting a single user account
- Login attempts originating from an unfamiliar geographic location
- Authentication attempts from an IP address not previously associated with the user

These indicators suggested a potential attempt to access the account using stolen or guessed credentials.

---

### Step 3 – Review Conditional Access Policy Results

Conditional Access policy logs confirmed that the authentication attempts were blocked by existing security controls.

The policy enforced multi-factor authentication and restricted access from unfamiliar locations, preventing the suspicious login attempts from successfully accessing the Microsoft 365 environment.

---

### Step 4 – Confirm Scope of Activity

Investigators reviewed authentication activity for additional user accounts to determine whether the activity represented a broader attack.

No additional suspicious login attempts were identified for other users, suggesting that the activity was isolated to the affected account.

---

## Remediation

The following remediation actions were taken to ensure the security of the affected account.

- User password was reset
- Active authentication sessions were revoked
- Conditional Access policies were reviewed
- User notified of suspicious login attempts
- Security monitoring continued for additional authentication anomalies

These remediation steps ensured that the attempted access did not result in unauthorized account compromise.

---

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Attempted authentication using legitimate user credentials |
| Brute Force | T1110 | Multiple failed authentication attempts targeting a user account |

---

## Lessons Learned

This investigation highlights the importance of monitoring authentication activity within enterprise identity platforms.

Authentication telemetry provides valuable insight into potential credential abuse attempts, particularly when login attempts originate from unfamiliar locations or IP addresses.

Conditional Access policies play a critical role in preventing unauthorized access by enforcing additional authentication requirements and restricting suspicious login activity.

Continuous monitoring and investigation of authentication anomalies are essential components of effective identity security operations.

---

## Documentation

The investigation techniques and remediation procedures documented in this repository were developed through review of publicly available cybersecurity documentation and vendor guidance.

The following documentation sources were referenced during the investigation process.

- **Microsoft Sentinel Documentation**  
  https://learn.microsoft.com/en-us/azure/sentinel/

- **Microsoft Entra ID Sign-in Logs Documentation**  
  https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

- **Kusto Query Language Documentation**  
  https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/

- **Microsoft Entra Conditional Access Documentation**  
  https://learn.microsoft.com/en-us/entra/identity/conditional-access/

- **Microsoft Defender Security Documentation**  
  https://learn.microsoft.com/en-us/defender/

- **MITRE ATT&CK Framework**  
  https://attack.mitre.org/
