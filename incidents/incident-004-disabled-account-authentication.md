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

## Investigation

### Step 1 – Review Authentication Logs

Security investigators reviewed Microsoft Entra ID sign-in logs for the disabled account.

Evidence source: Microsoft Entra ID Sign-in Logs

Investigators analyzed authentication telemetry including login timestamps, IP addresses, device information, and geographic location data.

Log analysis confirmed repeated login attempts targeting the disabled account. Each authentication attempt originated from an external IP address and was automatically rejected due to the account’s disabled status.

---

### Step 2 – Identify Suspicious Authentication Behavior

The authentication activity demonstrated characteristics commonly associated with credential abuse attempts.

Observed indicators included:

- Repeated login attempts targeting a disabled account
- Authentication attempts originating from an unfamiliar IP address
- Login activity occurring after the employee had already been offboarded

These indicators suggested that an attacker may have attempted to access the account using previously obtained credentials.

---

### Step 3 – Verify Account Status

Security investigators confirmed that the account had been disabled during the employee offboarding process.

Account status checks verified that:

- The account was disabled in Microsoft Entra ID
- Authentication access had been revoked
- No active sessions remained associated with the account

Because the account was disabled, authentication attempts were automatically blocked.

---

### Step 4 – Evaluate Security Controls

Investigators reviewed identity security policies and offboarding procedures to ensure proper access controls had been implemented.

Security controls successfully prevented unauthorized access because the disabled account could not authenticate to Microsoft 365 services.

---

## Remediation

The following remediation actions were taken to ensure continued protection of the environment.

- Disabled account status was confirmed
- Authentication logs were reviewed for additional suspicious activity
- Offboarding procedures were verified to ensure proper account deactivation
- Security monitoring was continued to detect additional login attempts
- External IP address associated with the attempts was documented for further monitoring

These actions confirmed that the attempted authentication activity did not result in unauthorized access.

---

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Attempted authentication using previously valid credentials |
| Brute Force | T1110 | Repeated authentication attempts targeting an account |

---

## Lessons Learned

This investigation highlights the importance of proper user offboarding procedures and identity access management controls.

Promptly disabling accounts during employee offboarding significantly reduces the risk of unauthorized access using previously issued credentials.

Continuous monitoring of authentication activity allows security teams to detect suspicious login attempts even when accounts are no longer active.

Maintaining strong identity governance and monitoring authentication telemetry are critical components of enterprise security operations.

---

## Documentation

The investigation techniques and remediation procedures documented in this incident report were developed through review of publicly available cybersecurity documentation and vendor guidance.

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
