# Phishing Authentication Attempt Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

---

## Overview

Phishing attacks attempt to steal user credentials by tricking users into entering their username and password into fraudulent login pages.

After obtaining credentials, attackers attempt to authenticate to enterprise systems.

---

## Purpose

The purpose of this detection is to identify suspicious authentication attempts following potential credential phishing events.

---

## Data Sources

Relevant log sources include:

- Microsoft Entra ID Sign-in Logs
- Azure AD Authentication Logs
- Microsoft Sentinel SigninLogs table

---

## Detection Logic

Indicators of phishing-based login attempts include:

- login attempts from unfamiliar locations
- authentication attempts following credential reset
- unusual device or application activity

---

## Detection Query

```kusto
SigninLogs
| where ResultType == 0
| summarize LoginCount = count() by UserPrincipalName, IPAddress, bin(TimeGenerated, 30m)
| where LoginCount > 5
| order by LoginCount desc
```

This query identifies repeated successful authentication attempts from the same IP address within a short timeframe, which may indicate credential abuse following phishing.
