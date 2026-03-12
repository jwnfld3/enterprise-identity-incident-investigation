# Impossible Travel Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

---

## Overview

Impossible travel is a detection scenario where a user account authenticates from two geographically distant locations within a timeframe that would be impossible for legitimate travel.

This behavior may indicate that an attacker has obtained valid user credentials and is attempting to access enterprise resources from a remote location.

---

## Purpose

The purpose of this detection is to identify suspicious authentication activity suggesting potential account compromise.

Early detection allows security analysts to investigate login activity, verify user behavior, and prevent unauthorized access to enterprise systems.

---

## Data Sources

The following log sources are commonly used for impossible travel detection:

- Microsoft Entra ID Sign-in Logs
- Azure AD Authentication Logs
- Microsoft Sentinel SigninLogs table

These logs contain authentication details including IP address, login location, timestamp, and authentication results.

---

## Detection Logic

Impossible travel scenarios typically include:

- Successful authentication attempts
- Logins from geographically distant locations
- A short timeframe between authentication events
- Identical user account across login attempts

---

## Detection Query

```kusto
SigninLogs
| where ResultType == 0
| summarize Locations = make_set(Location), LoginCount = count() by UserPrincipalName, bin(TimeGenerated, 1h)
| where array_length(Locations) > 1
| order by LoginCount desc
```

This query identifies successful authentication attempts where multiple geographic locations are associated with the same user account within a short timeframe.
