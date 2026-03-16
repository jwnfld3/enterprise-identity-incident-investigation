# Security Investigation Case Files

This directory contains documented cybersecurity investigation cases that simulate real world Security Operations Center (SOC) incident investigations.

Each case file represents a structured investigation scenario focused on identity based threats, authentication anomalies, and suspicious activity detected within enterprise identity environments.

The investigations demonstrate how security analysts review authentication activity, analyze security alerts, reconstruct incident timelines, and recommend remediation actions based on available evidence.

The environment used for these investigations focuses on identity security monitoring using Microsoft Entra ID authentication logs and Microsoft Sentinel security analytics.

---

# Investigation Objectives

The purpose of these case investigations is to demonstrate practical security analysis skills including:

• Security alert triage  
• Authentication log analysis  
• Threat detection investigation  
• Incident timeline reconstruction  
• Security event correlation  
• MITRE ATT&CK technique mapping  
• Incident response documentation  

Each investigation follows a structured analysis methodology designed to mirror real Security Operations Center workflows.

---

# Investigation Case Files

| Case ID | Investigation Title | Description |
|------|------|------|
| Case 001 | Password Spray Investigation | Analysis of repeated authentication failures targeting multiple user accounts |
| Case 002 | Identity Compromise Investigation | Investigation of suspicious authentication activity indicating potential account compromise |
| Case 003 | MFA Fatigue Attack Investigation | Analysis of repeated multi factor authentication prompts used to bypass identity protection |
| Case 004 | Impossible Travel Investigation | Detection of authentication events originating from geographically impossible locations |
| Case 005 | Phishing Login Investigation | Investigation of authentication activity associated with credential phishing |
| Case 006 | Token Theft Investigation | Analysis of suspicious authentication tokens potentially used for session hijacking |
| Case 007 | Data Exfiltration Investigation | Investigation of abnormal activity suggesting unauthorized data access or transfer |

---

# Investigation Methodology

Each case investigation follows a consistent investigation process used in many Security Operations Centers.

1. Alert Identification  
   Identification of suspicious activity or security alert.

2. Log Analysis  
   Examination of authentication logs and related security events.

3. Event Correlation  
   Correlation of multiple events across systems to identify patterns of malicious activity.

4. Timeline Reconstruction  
   Creation of a timeline describing the sequence of events during the incident.

5. Impact Assessment  
   Determination of affected users, systems, and potential data exposure.

6. Remediation Recommendations  
   Documentation of containment and mitigation actions.

---

# Technologies Referenced

The investigation scenarios reference identity monitoring and security analytics platforms including:

• Microsoft Entra ID  
• Microsoft Sentinel  
• Authentication and sign in log analysis  
• Security investigation workflows  

These platforms are commonly used in enterprise environments for identity threat detection and security monitoring.

---

# Learning Focus

These case investigations were created as part of a hands on cybersecurity learning process focused on developing practical incident investigation skills.

The goal of this project is to demonstrate how security analysts approach authentication based threats and document investigation findings using structured analysis techniques.

---

# Repository Navigation

Return to the main project documentation:

[Enterprise Identity Incident Investigation](../README.md)
