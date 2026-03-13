# MFA Fatigue Attack Remediation

| Field | Value |
|------|------|
| Playbook Type | Authentication Attack Investigation |
| Threat Category | MFA Abuse |
| Severity | High |
| Platform | Microsoft Entra ID |

---

## Objective

Investigate repeated MFA prompts that may indicate an MFA fatigue attack.

---

## Overview

Attackers sometimes repeatedly trigger MFA prompts hoping the user will approve one.

---

## Detection Reference

detections/mfa-fatigue-detection.md

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1621 | Multi Factor Authentication Request Generation |

---

## Who

SOC analysts and identity administrators.

---

## What

Investigate repeated MFA prompts.

---

## Where

Microsoft Entra sign in logs.

---

## When

When multiple MFA prompts are generated in a short period.

---

## Why

MFA fatigue attacks attempt to trick users into approving unauthorized authentication.

---

# Step 1 Review Sign in Logs

Review authentication events requiring MFA.

---

# Step 2 Identify Prompt Patterns

Look for repeated MFA prompts within a short timeframe.

---

# Step 3 Verify User Intent

Confirm whether the user attempted the sign in.

---

# Step 4 Secure the Account

Reset password and revoke sessions.

---

# Resolution

Repeated MFA prompts were investigated and the account secured.

---

# Documentation Sources

Microsoft MFA Security Guidance  
https://learn.microsoft.com/en-us/entra/identity/authentication/
