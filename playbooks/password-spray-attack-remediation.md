# Password Spray Attack Remediation

| Field | Value |
|------|------|
| Playbook Type | Credential Attack Investigation |
| Threat Category | Password Spray |
| Severity | High |
| Platform | Microsoft Entra ID |

---

## Objective

Investigate repeated login attempts across multiple accounts using a small set of passwords.

---

## Overview

Password spraying attempts to authenticate across many accounts using common passwords.

---

## Detection Reference

detections/password-spray-detection.md

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1110.003 | Password Spraying |

---

## Who

SOC analysts.

---

## What

Investigate login failures across multiple users.

---

## Where

Microsoft Sentinel and Microsoft Entra sign in logs.

---

## When

When repeated login failures originate from a single IP address.

---

## Why

Password spraying is commonly used to identify weak passwords.

---

# Step 1 Identify Source IP

Locate repeated login attempts from a single IP.

---

# Step 2 Review Targeted Accounts

Identify affected user accounts.

---

# Step 3 Block Malicious IP

Block the IP address if malicious.

---

# Step 4 Enforce Strong Authentication

Require MFA and reset passwords if necessary.

---

# Resolution

The attack source was identified and mitigation controls were applied.

---

# Documentation Sources

MITRE ATT&CK Password Spraying  
https://attack.mitre.org/techniques/T1110/003/
