# Incident Report: MFA Fatigue Attack

## Case Metadata

Incident ID: IR-002  
Category: Identity Security Incident  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Entra ID Sign-in Monitoring  
Reported By: User Security Alert  

Investigation Start Time: 2026-03-12 09:40 UTC  
Investigation End Time: 2026-03-12 10:20 UTC  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

A suspected Multi Factor Authentication (MFA) fatigue attack was identified targeting a Microsoft 365 user account.

The user reported receiving multiple unexpected authentication prompts on their mobile device within a short time period. Security monitoring confirmed repeated login attempts originating from a foreign IP address.

MFA prompts were repeatedly sent to the user in an attempt to trick the user into approving the authentication request.

---

## Detection

The incident was detected through a combination of user reporting and automated authentication monitoring.

Indicators included:

- Multiple MFA push notifications sent within a short time period
- Login attempts originating from an unfamiliar geographic location
- Repeated authentication failures followed by MFA challenges

---

## Investigation

### Step 1 – Review MFA Authentication Logs

Security investigators reviewed Multi Factor Authentication activity logs.

Evidence file:

