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

Evidence file:

