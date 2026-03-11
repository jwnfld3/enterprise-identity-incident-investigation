# Sentinel KQL Detection Queries

## Overview

This document contains example Kusto Query Language (KQL) detection queries that can be used in Microsoft Sentinel to identify suspicious authentication activity, cloud abuse, identity attacks, and privilege escalation events. These queries support Security Operations Center investigations by helping analysts detect patterns commonly associated with credential attacks, unauthorized access, and suspicious cloud behavior.

The examples below are designed for training, portfolio demonstration, and investigation support in Microsoft enterprise environments using Microsoft Entra ID, Microsoft 365, Azure AD sign in logs, and audit data.

## Purpose

The purpose of these detection queries is to help analysts:

1. Identify suspicious authentication patterns
2. Detect password spraying and brute force activity
3. Investigate impossible travel events
4. Review privileged role assignment activity
5. Detect potential token theft indicators
6. Investigate data exfiltration activity in OneDrive and SharePoint
7. Support alert triage and incident response workflows

## Data Sources

These example queries are commonly used with the following Microsoft security data sources:

1. SigninLogs
2. AuditLogs
3. IdentityInfo
4. OfficeActivity
5. AADNonInteractiveUserSignInLogs
6. CloudAppEvents

## Password Spray Detection

This query looks for repeated failed sign in attempts across multiple accounts from the same IP address within a short timeframe. This pattern may indicate a password spraying attack.

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count(), TargetedUsers = dcount(UserPrincipalName) by IPAddress, bin(TimeGenerated, 15m)
| where FailedAttempts >= 15 and TargetedUsers >= 5
| order by FailedAttempts desc
