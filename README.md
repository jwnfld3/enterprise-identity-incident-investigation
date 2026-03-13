# Enterprise Identity Security Incident Investigation

## Project Overview

This repository contains a collection of enterprise identity security investigations designed to simulate real-world attack scenarios within Microsoft cloud environments.

The project demonstrates threat detection, authentication log analysis, and structured incident response procedures using Microsoft Entra ID, Microsoft 365, and Microsoft Sentinel.

Each investigation documents the analysis process, maps adversary behavior to the MITRE ATT&CK framework, and outlines remediation actions used to contain and resolve the security event.

---

# Security and Infrastructure Technologies

| Category | Technologies |
|:----------|:-------------|
| Identity Security | Microsoft Entra ID, Identity and Access Management |
| Security Monitoring | Microsoft Sentinel, Microsoft Defender |
| Cloud Platform | Microsoft 365 Security |
| Query and Log Analysis | Kusto Query Language (KQL) |
| Infrastructure | Active Directory, Windows Server Administration |

---

# Security Incident Investigation Dashboard

## Investigation Summary

| Metric | Value |
|:------|------:|
| Total Cases | 7 |
| Critical Severity Incidents | 2 |
| High Severity Incidents | 3 |
| Medium Severity Incidents | 1 |
| Resolved Investigations | 7 |
| Open Investigations | 0 |

---

## Detection Coverage

These investigations simulate identity-based attack scenarios mapped to the MITRE ATT&CK framework.

Initial Access  
Credential Access  
Defense Evasion  
Persistence  
Exfiltration  

---

## Security Investigation Cases

| Case Identifier | Investigation | Severity | MITRE ATT&CK Technique | Status | Investigation Report |
|:---------------|:--------------|:---------|:----------------------|:------|:---------------------|
| CASE-001 | Password Spray Attack | High | T1110.003 Password Spraying | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-001-password-spray.md) |
| CASE-002 | Enterprise Identity Compromise | Critical | T1078 Valid Accounts | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md) |
| CASE-003 | MFA Fatigue Attack | High | T1621 Multi Factor Authentication Request Generation | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-003-mfa-fatigue.md) |
| CASE-004 | Impossible Travel Authentication | Medium | T1078 Valid Accounts | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-004-impossible-travel.md) |
| CASE-005 | Phishing Authentication Attempt | High | T1566 Phishing | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-005-phishing-login.md) |
| CASE-006 | Authentication Token Theft | High | T1528 Steal Application Access Token | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-006-token-theft.md) |
| CASE-007 | Data Exfiltration Activity | Critical | T1041 Exfiltration Over Command and Control Channel | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-007-data-exfiltration.md) |

---

# Detection Engineering

Example detection logic used to identify identity-based threats within Microsoft Sentinel.

## Password Spray Detection

MITRE ATT&CK Technique  
T1110.003 Password Spraying

```kql
SecurityEvent
| where EventID == 4625
| summarize FailureCount = count() by Account, IpAddress, bin(TimeGenerated, 10m)
| where FailureCount > 10
