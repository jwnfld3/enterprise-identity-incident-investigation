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

Evidence file:

