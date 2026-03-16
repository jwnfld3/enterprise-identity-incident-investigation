# Investigation Evidence Repository

This directory contains investigation artifacts and supporting evidence used during cybersecurity incident investigations documented in this repository.

The files stored in this directory represent the types of logs, authentication records, and cloud activity events that security analysts review when investigating identity based security incidents in enterprise environments.

These artifacts simulate evidence collected during a Security Operations Center investigation and support the analysis performed in the documented case files.

---

# Evidence Categories

The evidence directory is organized by log source and event type to reflect how security analysts categorize and review investigation data.

---

## Attacks

The **attacks** directory contains evidence related to suspicious or malicious activity identified during investigations.

Examples include:

• suspicious IP authentication attempts  
• credential attack indicators  
• abnormal login activity  

These logs help investigators identify attacker behavior and reconstruct incident timelines.

---

## Authentication

The **authentication** directory contains authentication and sign in logs used during identity security investigations.

These logs help analysts identify:

• failed authentication attempts  
• unusual login locations  
• abnormal login frequency  
• suspicious authentication sources  

Authentication logs are a primary source of evidence during identity compromise investigations.

---

## Cloud Activity

The **cloud** directory contains logs representing cloud service activity.

Examples include:

• SharePoint access logs  
• file download activity  
• abnormal cloud resource access  

These logs help investigators detect potential data access or data exfiltration events.

---

## Multi Factor Authentication

The **mfa** directory contains logs related to multi factor authentication activity.

Examples include:

• repeated MFA prompts  
• suspicious authentication approvals  
• abnormal MFA challenge patterns  

These events are often associated with MFA fatigue attacks or unauthorized login attempts.

---

## Security Policy

The **policy** directory contains logs related to security control enforcement such as conditional access policies.

Examples include:

• conditional access policy evaluation  
• authentication blocking events  
• security control enforcement activity  

These logs help investigators determine whether security controls were applied during suspicious authentication attempts.

---

# Additional Investigation Files

Additional files in this directory provide supporting evidence used during investigations.

## authentication-log-example.md

Example authentication logs used to demonstrate how login activity appears during investigations.

## mfa-authentication-log.md

Example MFA related authentication activity used during MFA investigation scenarios.

## investigation-notes.md

Working notes and observations collected during investigation analysis.

These notes help document investigative reasoning and event correlation during the incident review process.

---

# Purpose

The purpose of this directory is to demonstrate how security analysts organize and review evidence during cybersecurity investigations.

The structure reflects common evidence categories used during identity threat investigations including:

• authentication logs  
• cloud activity records  
• security policy enforcement logs  
• multi factor authentication events  

This repository simulates the investigation process used by Security Operations Center analysts when analyzing authentication based security incidents.

---

# Related Investigation Cases

The evidence stored in this directory supports the investigation scenarios documented in the case files directory.
