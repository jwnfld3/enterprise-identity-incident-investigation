# Password Spray Detection

Detection Type: Identity Threat Detection  
Platform: Microsoft Sentinel  
Query Language: Kusto Query Language (KQL)

---

## Overview

Password spraying is a credential access attack technique in which an attacker attempts to authenticate against many user accounts using a small number of commonly used passwords. Instead of repeatedly attempting passwords against a single account, the attacker distributes login attempts across multiple accounts to avoid triggering account lockout policies.

This detection identifies patterns of repeated failed authentication attempts targeting multiple users from a single source IP address within a short timeframe.

---

## Purpose

The purpose of this detection is to identify potential credential access attacks against enterprise identity systems. Early detection allows security analysts to investigate authentication activity and prevent unauthorized access before attackers successfully compromise accounts.

---

## Data Sources

The following log sources are commonly used for password spray detection in Microsoft Sentinel:

- Microsoft Entra ID Sign-in Logs
- Azure AD Authentication Logs
- Microsoft Sentinel SigninLogs table

These logs provide authentication details such as user account activity, source IP address, login results, and timestamps.

---

## Detection Logic

Password spraying attacks often generate a recognizable pattern within authentication logs. Common indicators include:

- Multiple failed login attempts
- Authentication attempts against many different user accounts
- Login attempts originating from the same IP address
- Activity occurring within a short time window

By analyzing failed authentication attempts across multiple accounts from a single IP address, analysts can detect activity consistent with password spraying behavior.

---

## Detection Query

The following KQL query identifies repeated failed authentication attempts targeting multiple user accounts from a single IP address within a defined time window.

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count(), TargetedUsers = dcount(UserPrincipalName) by IPAddress, bin(TimeGenerated, 15m)
| where FailedAttempts >= 15 and TargetedUsers >= 5
| order by FailedAttempts desc
