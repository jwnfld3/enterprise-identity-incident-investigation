# Identity Compromise Remediation

| Field | Value |
|------|------|
| Playbook Type | Identity Security Investigation |
| Threat Category | Account Compromise |
| Severity | High |
| Platform | Microsoft Entra ID / Microsoft 365 |

---

## Objective

Investigate suspected identity compromise, determine whether unauthorized access occurred, and secure the affected account.

---

## Overview

This playbook is used when authentication logs indicate that a user account may have been compromised.

Compromised credentials allow attackers to access resources using legitimate authentication methods.

---

## Detection Reference

Possible detections include:

- detections/token-theft-detection.md
- detections/phishing-login-detection.md
- detections/impossible-travel-detection.md

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1078 | Valid Accounts |
| T1556 | Modify Authentication Process |

---

## Who

1. SOC analysts  
2. Identity administrators  
3. Microsoft 365 administrators  

---

## What

Investigate login activity and determine whether the account has been compromised.

---

## Where

1. Microsoft Entra admin center  
2. Microsoft Sentinel  

---

## When

Use when suspicious login behavior or alerts indicate possible credential compromise.

---

## Why

Compromised identities allow attackers to access corporate resources.

---

# Step 1 Review Sign in Logs

1. Open Microsoft Entra admin center  
2. Navigate to Identity  
3. Select Monitoring & health  
4. Click Sign in logs  
5. Filter results for the affected user

---

# Step 2 Review Location and Device

1. Review login locations  
2. Review IP addresses  
3. Review device information

---

# Step 3 Verify User Intent

1. Contact the user  
2. Confirm whether the login attempt was legitimate  

---

# Step 4 Secure the Account

1. Reset the password  
2. Revoke active sessions  
3. Require multi factor authentication  

---

# Resolution

The compromised account was secured and access was restored to the legitimate user.

---

# Documentation Sources

Microsoft Entra Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/
