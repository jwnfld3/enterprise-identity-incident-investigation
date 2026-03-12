# Authentication Token Theft Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

---

## Overview

Authentication token theft occurs when attackers capture authentication tokens used by applications or services to maintain access to user accounts.

These tokens allow attackers to access resources without repeatedly entering credentials.

---

## Purpose

The purpose of this detection is to identify suspicious authentication activity that may indicate stolen or reused authentication tokens.

---

## Data Sources

Relevant log sources include:

- Microsoft Entra ID Sign-in Logs
- Azure AD Authentication Logs
- Microsoft Sentinel SigninLogs table

---

## Detection Logic

Indicators of token theft may include:

- authentication activity without password entry
- login attempts from unfamiliar devices
- unusual authentication patterns
- multiple sessions from different locations

---

## Detection Query

```kusto
SigninLogs
| summarize LoginLocations = make_set(Location), LoginDevices = make_set(DeviceDetail) by UserPrincipalName, bin(TimeGenerated, 1h)
| where array_length(LoginLocations) > 1
| order by UserPrincipalName
```

This query identifies accounts accessing resources from multiple locations or devices within a short timeframe.
