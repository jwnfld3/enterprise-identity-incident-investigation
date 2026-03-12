# Enterprise Identity Security Investigation Lab

![Microsoft Sentinel](https://img.shields.io/badge/Microsoft-Sentinel-blue)
![Microsoft Entra ID](https://img.shields.io/badge/Microsoft-Entra%20ID-purple)
![Microsoft 365](https://img.shields.io/badge/Microsoft-365-green)
![KQL](https://img.shields.io/badge/Kusto-Query%20Language-orange)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red)
![Security Operations](https://img.shields.io/badge/SOC-Investigation-black)

This repository demonstrates Security Operations Center investigation techniques used to detect, analyze, and respond to identity-based security threats in Microsoft Entra ID and Microsoft 365 environments.

The lab simulates enterprise authentication attacks and documents the full investigation lifecycle including detection engineering, authentication log analysis, threat intelligence correlation, incident response procedures, and SOC case documentation.

---

# Security Operations Investigation Workflow

Security incidents in this lab follow a structured investigation process used by Security Operations Centers.

```
Attack Activity
↓
Detection Alert
↓
Authentication Log Analysis
↓
Threat Intelligence Correlation
↓
Incident Confirmation
↓
Containment and Remediation
↓
Case Documentation
```

This workflow mirrors how enterprise security teams investigate identity-based attacks.

---

# Security Architecture Overview

```
Attacker
   │
   │ Authentication Attempts
   ▼
Microsoft Entra ID
   │
   │ Authentication Logs
   ▼
Microsoft Sentinel SIEM
   │
   │ Detection Queries (KQL)
   ▼
Security Alert
   │
   │ SOC Investigation
   ▼
Log Analysis + Threat Intelligence
   │
   │ Incident Confirmation
   ▼
Response Playbooks
   │
   ▼
Containment and Remediation
```

This architecture demonstrates how authentication activity is monitored, analyzed, and investigated within a Security Operations environment.

---

# Repository Structure

```
enterprise-identity-security-lab
│
├── README.md
├── SOC-Investigation-Workflow.md
│
├── attacks
│
├── detections
│
├── incidents
│
├── playbooks
│
├── threat-intelligence
│
└── case-files
```

Each directory represents a stage in the SOC investigation lifecycle.

---

# Attack Evidence

The **attacks** directory contains authentication logs and attack artifacts used during investigations.

These logs simulate evidence analysts review during incident response.

Example attack scenarios include:

- Password spray authentication attempts
- Suspicious IP login activity
- Phishing authentication attempts
- Token theft indicators
- Malicious mailbox rule creation
- Data exfiltration activity

Attack artifacts represent authentication events observed during simulated investigations.

---

# Detection Engineering

The **detections** directory contains detection logic and Microsoft Sentinel queries used to identify suspicious activity.

Detection examples include:

- Password spray detection
- Impossible travel authentication detection
- MFA fatigue detection
- Suspicious authentication patterns
- Data exfiltration detection

These detections demonstrate SIEM monitoring and security alert generation using Kusto Query Language.

---

# Incident Reports

The **incidents** directory contains formal incident reports documenting confirmed security events.

Reports include:

- Incident summary
- Investigation timeline
- Indicators of compromise
- Investigation findings
- Containment actions

These reports mirror the documentation practices used by enterprise Security Operations Centers.

---

# Incident Response Playbooks

The **playbooks** directory contains step-by-step incident response procedures used to contain and remediate attacks.

Response procedures include:

- Authentication log investigation
- Password spray containment
- Identity compromise response
- MFA fatigue remediation
- Conditional access enforcement
- Data exfiltration response

Each playbook describes the procedures analysts follow during incident response.

---

# Threat Intelligence Analysis

The **threat-intelligence** directory documents correlation between observed activity and external threat intelligence sources.

Threat intelligence platforms referenced include:

- Microsoft Security Intelligence
- Cybersecurity and Infrastructure Security Agency (CISA)
- MITRE ATT&CK Framework
- AbuseIPDB
- AlienVault Open Threat Exchange

Threat intelligence correlation helps analysts determine whether suspicious activity aligns with known attacker techniques.

---

# SOC Case Files

The **case-files** directory contains complete investigation documentation for simulated security incidents.

Each case file connects:

- detection logic
- attack evidence
- threat intelligence research
- incident reports
- response procedures

Case files represent the final investigation narrative produced by a Security Operations Center.

Example investigations include:

- Password spray attack investigation
- Identity compromise investigation
- MFA fatigue attack investigation
- Impossible travel authentication investigation
- Phishing login attempt investigation
- Token theft investigation
- Data exfiltration investigation

---

# Skills Demonstrated

This lab demonstrates practical Security Operations Center capabilities including:

- Authentication log analysis
- SIEM detection engineering
- Identity security monitoring
- Threat intelligence correlation
- Incident investigation
- Incident response procedures
- SOC case documentation

These capabilities align with responsibilities commonly required for SOC analyst and cybersecurity analyst roles.

---

# Technologies Used

Microsoft Entra ID  
Microsoft 365  
Microsoft Sentinel  
Kusto Query Language (KQL)  
MITRE ATT&CK Framework  

---

# Purpose of the Lab

This lab demonstrates how security analysts detect and respond to identity-based attacks within enterprise cloud environments.

The repository illustrates the full lifecycle of a SOC investigation including detection, analysis, containment, and documentation.

---

# Author

Enterprise Identity Security Investigation Lab  
Cybersecurity Portfolio Demonstration
