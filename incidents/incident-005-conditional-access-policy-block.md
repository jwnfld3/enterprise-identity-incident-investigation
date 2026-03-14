# Incident Report: Conditional Access Policy Block

## Case Metadata

Incident ID: IR-005  
Category: Access Control Enforcement  
Severity: Low  
Status: Resolved  

Detection Source: Microsoft Entra ID Conditional Access Monitoring  
Reported By: Automated Security Policy Alert  

Investigation Start Time: 2026-03-18 12:14 UTC  
Investigation End Time: 2026-03-18 12:40 UTC  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

A Conditional Access policy blocked an authentication attempt to Microsoft 365 services from a device that did not meet the organization's security compliance requirements.

The login attempt originated from an unmanaged device that was not enrolled in Microsoft Intune and therefore did not satisfy device compliance policies configured within the organization.

The Conditional Access policy successfully prevented access to corporate resources.

---

## Detection

The event was detected through Microsoft Entra ID Conditional Access monitoring alerts.

Indicators included:

- Login attempt from an unmanaged device
- Device not enrolled in Microsoft Intune
- Conditional Access policy enforcement triggered

---

## Investigation

### Step 1 – Review Authentication Logs

Security investigators reviewed Microsoft Entra ID sign-in logs for the affected user.

Evidence source: Microsoft Entra ID Sign-in Logs

Investigators analyzed authentication telemetry including login timestamps, device information, IP address data, and Conditional Access evaluation results.

Log analysis confirmed that the authentication attempt originated from a device that was not enrolled in Microsoft Intune and therefore failed to meet the organization’s device compliance requirements.

---

### Step 2 – Evaluate Conditional Access Policy Results

Security investigators reviewed Conditional Access policy evaluation details associated with the authentication attempt.

The policy evaluation indicated that the login request failed the device compliance requirement configured within the organization’s Conditional Access policy.

Because the device was not managed or compliant, the policy automatically blocked access to Microsoft 365 services.

---

### Step 3 – Verify Device Compliance Status

Investigators verified that the device used during the authentication attempt was not registered with the organization’s device management system.

Device checks confirmed that:

- The device was not enrolled in Microsoft Intune
- The device did not meet organizational compliance requirements
- Access from unmanaged devices was restricted by Conditional Access policy

---

### Step 4 – Confirm Policy Enforcement

Security investigators confirmed that the Conditional Access policy functioned as intended.

The policy successfully prevented authentication from a non compliant device and blocked access to corporate resources.

---

## Remediation

The following remediation actions were taken to maintain security and prevent similar access attempts.

- Conditional Access policies were reviewed for proper enforcement
- Device compliance requirements were verified
- Authentication logs were monitored for additional suspicious activity
- User was notified that access from unmanaged devices is restricted

These actions confirmed that the security controls were functioning correctly and prevented unauthorized access to enterprise resources.

---

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Attempted authentication using legitimate user credentials |
| Account Access Control | T1098 | Security controls restricting access based on device compliance and policy enforcement |

---

## Lessons Learned

This investigation demonstrates the importance of Conditional Access policies in protecting enterprise cloud environments.

Device compliance policies help ensure that only managed and secure devices are allowed to access corporate resources.

Conditional Access enforcement provides an effective method for preventing access from unmanaged or potentially insecure devices.

Regular review of identity access policies and monitoring of authentication logs helps organizations maintain strong access control protections.

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
