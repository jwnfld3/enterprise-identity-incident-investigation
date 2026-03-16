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

# Investigation

Security analysts conducted a structured investigation to verify that the Conditional Access policy correctly blocked authentication from a non compliant device.

---

## Step 1 – Review Microsoft Entra ID Sign-in Logs

Evidence Source: Microsoft Entra ID Sign-in Logs

1. Open the Azure Portal  
https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign-in Logs**

5. Apply the following filters:

- User: `jsmith@company.com`
- Time Range: Incident timeframe

6. Review the following authentication telemetry fields:

- Client IP Address
- Device Information
- Application Accessed
- Conditional Access Status
- Sign-in Result

Investigators observed that the authentication request failed due to Conditional Access policy enforcement.

---

## Step 2 – Query Authentication Logs Using KQL

Security investigators queried authentication telemetry to review Conditional Access evaluation results.

```kql
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, DeviceDetail, ConditionalAccessStatus, ResultType
| order by TimeGenerated desc
```

Query results confirmed that the authentication attempt failed because the device did not meet the Conditional Access policy requirements.

---

## Step 3 – Evaluate Conditional Access Policy Results

Investigators reviewed Conditional Access policy evaluation details associated with the authentication attempt.

1. Navigate to **Microsoft Entra Admin Center**

2. Select **Protection**

3. Click **Conditional Access**

4. Review the policy evaluation results in the authentication event.

The evaluation confirmed that the login request failed the **device compliance requirement** configured within the organization’s Conditional Access policy.

Because the device was not managed or compliant, access to Microsoft 365 services was automatically blocked.

---

## Step 4 – Verify Device Compliance Status

Investigators verified the device status within the organization’s device management system.

1. Navigate to **Microsoft Intune Admin Center**

2. Select **Devices**

3. Search for the device associated with the authentication attempt.

4. Review device enrollment and compliance status.

Device checks confirmed:

- The device was **not enrolled in Microsoft Intune**
- The device did **not meet organizational compliance requirements**
- Access from unmanaged devices was **restricted by Conditional Access policy**

---

## Step 5 – Confirm Policy Enforcement

Security investigators confirmed that the Conditional Access policy functioned as intended.

The policy successfully prevented authentication from a non compliant device and blocked access to corporate resources.

---

## Step 6 – Determine Incident Impact

Investigators confirmed that:

- Authentication was blocked
- No access to Microsoft 365 resources occurred
- No sensitive data was accessed
- No active session was established

Because the Conditional Access policy blocked the login attempt, no security breach occurred.

---

# Remediation

The following remediation actions were taken to maintain security and prevent similar access attempts.

- Conditional Access policies were reviewed for proper enforcement
- Device compliance requirements were verified
- Authentication logs were monitored for additional suspicious activity
- User was notified that access from unmanaged devices is restricted

These actions confirmed that the security controls were functioning correctly and prevented unauthorized access to enterprise resources.

---

# MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Attempted authentication using legitimate user credentials |
| Account Access Control | T1098 | Security controls restricting access based on device compliance and policy enforcement |

---

# Lessons Learned

This investigation demonstrates the importance of Conditional Access policies in protecting enterprise cloud environments.

Device compliance policies help ensure that only managed and secure devices are allowed to access corporate resources.

Conditional Access enforcement provides an effective method for preventing access from unmanaged or potentially insecure devices.

Regular review of identity access policies and monitoring of authentication logs helps organizations maintain strong access control protections.

---

# Conclusion

The investigation confirmed that a Conditional Access policy successfully blocked authentication from a non compliant device attempting to access Microsoft 365 services.

Because the device was not enrolled in Microsoft Intune and did not meet organizational compliance requirements, the login attempt failed the Conditional Access policy evaluation.

Security monitoring systems detected the event, and investigators verified that the policy functioned correctly. No unauthorized access occurred and no corporate resources were exposed.

This incident demonstrates the effectiveness of Conditional Access policies in enforcing device compliance and protecting enterprise cloud environments.

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
