# Impossible Travel Login Remediation

| Field | Value |
|------|------|
| Playbook Type | Authentication Investigation |
| Threat Category | Suspicious Login |
| Severity | Medium |
| Platform | Microsoft Entra ID |

---

## Objective

Investigate authentication attempts that occur from geographically distant locations within an unrealistic timeframe.

---

## Overview

Impossible travel alerts occur when a user signs in from two locations too far apart to travel between within the observed timeframe.

---

## Detection Reference

detections/impossible-travel-detection.md

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1078 | Valid Accounts |

---

## Who

SOC analysts and identity administrators.

---

## What

Review authentication logs and confirm whether login attempts were legitimate.

---

## Where

Microsoft Entra sign in logs.

---

## When

When an impossible travel alert appears.

---

## Why

Impossible travel may indicate stolen credentials.

---

# Step 1 Review Authentication Logs

1. Open Microsoft Entra admin center  
2. Navigate to Sign in logs  
3. Filter for the user  

---

# Step 2 Review Login Locations

Review geographic location of authentication attempts.

---

# Step 3 Verify User Intent

Contact the user and confirm whether both login locations were legitimate.

---

# Step 4 Secure the Account if Necessary

Reset credentials and enable MFA.

---

# Resolution

Login behavior was reviewed and the account secured if necessary.

---

# Documentation Sources

Microsoft Entra Risky Sign in Investigation  
https://learn.microsoft.com/en-us/entra/id-protection/
