# MFA Fatigue Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

---

## Overview

Multi-Factor Authentication (MFA) fatigue attacks occur when an attacker repeatedly attempts to authenticate to a user account using stolen credentials. Each authentication attempt triggers a push notification to the user's authentication device.

Attackers hope the user eventually approves the request, granting unauthorized access.

---

## Purpose

The purpose of this detection is to identify repeated authentication attempts generating excessive MFA prompts for a user account.

Detecting this activity early allows security teams to intervene before a user mistakenly approves a malicious authentication request.

---

## Data Sources

Relevant log sources include:

- Microsoft Entra ID Sign-in Logs
- Azure AD Authentication Logs
- Microsoft Sentinel SigninLogs table

These logs provide authentication attempt details and MFA verification activity.

---

## Detection Logic

MFA fatigue attacks typically generate:

- multiple authentication attempts for a single user
- repeated MFA challenges
- login attempts from unfamiliar IP addresses
- authentication attempts occurring within a short timeframe

---

## Detection Query

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by UserPrincipalName, bin(TimeGenerated, 10m)
| where FailedAttempts > 10
| order by FailedAttempts desc
```

This query identifies accounts experiencing repeated failed authentication attempts within a short time period, which may indicate an MFA fatigue attack.
