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

Evidence file:

