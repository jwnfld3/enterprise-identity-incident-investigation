# Phishing Attack Remediation

| Field | Value |
|------|------|
| Playbook Type | Social Engineering Investigation |
| Threat Category | Phishing |
| Severity | High |
| Platform | Microsoft 365 |

---

## Objective

Investigate phishing activity targeting user credentials.

---

## Overview

Phishing attacks attempt to trick users into providing credentials through malicious emails or login pages.

---

## Detection Reference

detections/phishing-login-detection.md

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1566 | Phishing |

---

## Who

SOC analysts and security administrators.

---

## What

Investigate suspicious authentication events following phishing alerts.

---

## Where

Microsoft Defender and Microsoft Entra logs.

---

## When

When phishing alerts or suspicious login attempts occur.

---

## Why

Phishing is one of the most common methods attackers use to steal credentials.

---

# Step 1 Review Email Alert

Analyze the suspicious email.

---

# Step 2 Review Authentication Logs

Check whether the user attempted login after interacting with the email.

---

# Step 3 Verify User Intent

Confirm whether the user entered credentials.

---

# Step 4 Secure the Account

Reset password and revoke sessions.

---

# Resolution

Phishing activity was investigated and the affected account was secured.

---

# Documentation Sources

Microsoft Defender Phishing Investigation  
https://learn.microsoft.com/en-us/microsoft-365/security/
