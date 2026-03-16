# Enterprise Identity Incident Investigation

![Microsoft Entra ID](https://img.shields.io/badge/Microsoft-Entra%20ID-purple)
![Microsoft Sentinel](https://img.shields.io/badge/Microsoft-Sentinel-blue)
![Kusto Query Language](https://img.shields.io/badge/KQL-Log%20Analysis-green)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-black)
![Incident Response](https://img.shields.io/badge/SOC-Incident%20Response-orange)

This repository demonstrates enterprise identity security incident investigations using Microsoft Entra ID authentication logs, SOC investigation methodology, and structured incident response procedures.

The investigation scenarios documented in this repository simulate real world Security Operations Center workflows used to analyze authentication anomalies, identify indicators of compromise, and apply remediation actions within Microsoft cloud environments.

---

## SOC Investigation Dashboard

Total Investigations: **9** | Environment: **Microsoft Entra ID / Microsoft Sentinel** | Investigation Status: **Completed**

The following scenarios simulate identity related security incidents commonly investigated by Security Operations Center analysts. Each case demonstrates authentication log analysis, detection techniques, MITRE ATT&CK mapping, and incident response procedures within Microsoft cloud environments.

| Case ID | Incident Type | Severity | Status | Investigation |
|:------:|---------------|:--------:|:------:|--------------|
| CASE-001 | Suspicious Authentication Activity | High | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-001-suspicious-authentication.md) |
| CASE-002 | MFA Fatigue Attack | High | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-002-mfa-fatigue.md) |
| CASE-003 | Impossible Travel Login | Medium | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-003-impossible-travel.md) |
| CASE-004 | Disabled Account Authentication | Medium | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-004-disabled-account.md) |
| CASE-005 | Conditional Access Policy Block | Low | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-005-conditional-access.md) |
| CASE-006 | Password Spray Attack | High | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-006-password-spray.md) |
| CASE-007 | Data Exfiltration Activity | High | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-007-data-exfiltration.md) |
| CASE-008 | Identity Account Compromise | Critical | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-008-identity-compromise.md) |
| CASE-009 | Phishing Attack | High | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/incidents/case-009-phishing.md) |
---

# Incident Response Playbooks

| Playbook | Description | Playbook Link |
|---|---|---|
| Conditional Access Policy Block Remediation | Procedures for blocking suspicious authentication activity using Conditional Access policies | [View Playbook](playbooks/conditional-access-policy-block-remediation.md) |
| Data Exfiltration Investigation Remediation | Investigation and remediation procedures for suspected data exfiltration activity | [View Playbook](playbooks/data-exfiltration-investigation-remediation.md) |
| Identity Compromise Remediation | Response procedures for compromised user identities and unauthorized access | [View Playbook](playbooks/identity-compromise-remediation.md) |
| Impossible Travel Login Remediation | Investigation procedures for logins originating from geographically distant locations | [View Playbook](playbooks/impossible-travel-login-remediation.md) |
| MFA Fatigue Attack Remediation | Investigation and mitigation procedures for repeated MFA authentication prompts | [View Playbook](playbooks/mfa-fatigue-attack-incident-remediation.md) |
| Password Spray Attack Remediation | Investigation and containment procedures for password spray authentication attempts | [View Playbook](playbooks/password-spray-attack-remediation.md) |
| Phishing Attack Remediation | Investigation procedures for phishing related authentication attempts | [View Playbook](playbooks/phishing-attack-remediation.md) |

---

# Investigation Methodology

The investigation procedures documented in this repository follow a structured Security Operations Center workflow used to analyze identity security alerts within enterprise environments.

SOC analysts typically follow a consistent investigative process when responding to suspicious authentication activity.

Alert Detection  
Security alerts are generated by monitoring platforms such as Microsoft Entra ID Identity Protection or Microsoft Sentinel when abnormal authentication behavior is detected.

Log Analysis  
Authentication telemetry is analyzed using Microsoft Entra ID sign-in logs to identify suspicious login patterns, unusual locations, or abnormal authentication methods.

Threat Correlation  
Security events are correlated across authentication logs, directory audit logs, and security monitoring platforms to determine the scope of the incident.

Threat Identification  
Analysts evaluate whether the activity represents legitimate user behavior, administrative activity, or potential attacker activity.

Containment and Remediation  
Security controls such as Conditional Access policies, credential resets, and session revocation are implemented to prevent unauthorized access.

Documentation and Reporting  
All investigation findings are documented to support incident response records and future detection improvements.

---

# Detection Queries

Security analysts often use log queries to identify suspicious authentication behavior during investigations.

Example query identifying authentication failures:

```kql
SigninLogs
| where ResultType != 0
| summarize FailureCount = count() by IPAddress, UserPrincipalName
| where FailureCount > 10
| order by FailureCount desc

```
## Documentation Sources

The investigation procedures and remediation strategies documented in this repository were developed through review of publicly available cybersecurity research, vendor security documentation, and industry threat intelligence frameworks.

These resources were used to better understand authentication monitoring, identity threat detection, incident response procedures, and enterprise security controls within Microsoft cloud environments.

The following documentation sources were referenced during the investigation process.

- **Microsoft Sentinel Documentation**  
  https://learn.microsoft.com/en-us/azure/sentinel/

- **Microsoft Entra ID Sign-in Logs Documentation**  
  https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

- **Kusto Query Language Documentation**  
  https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/

- **Microsoft Entra Conditional Access Documentation**  
  https://learn.microsoft.com/en-us/entra/identity/conditional-access/

- **Microsoft Defender Security Documentation**  
  https://learn.microsoft.com/en-us/defender/

- **MITRE ATT&CK Framework**  
  https://attack.mitre.org/

  ---

  ## Analyst Learning Outcomes

The investigation scenarios documented in this repository provided practical insight into how identity related security incidents are analyzed and remediated within enterprise environments.

Through these investigations, several important security concepts became clearer.

Authentication telemetry provides valuable visibility into user activity across enterprise systems. By analyzing sign-in logs, analysts can detect abnormal login patterns such as impossible travel events, repeated authentication failures, and login attempts originating from unfamiliar locations.

Security monitoring platforms play a critical role in detecting potential threats. Tools such as Microsoft Sentinel and Microsoft Entra ID Identity Protection generate alerts when suspicious authentication behavior is detected, allowing analysts to quickly begin investigating potential incidents.

Correlation of multiple security events is essential for understanding the scope of an incident. Authentication logs, directory audit logs, and security alerts must be analyzed together to determine whether suspicious activity represents a single isolated event or part of a broader attack.

Identity security controls such as Conditional Access policies and multi-factor authentication significantly reduce the likelihood of successful credential abuse. In several investigation scenarios documented in this repository, Conditional Access policies successfully blocked suspicious authentication attempts before unauthorized access occurred.

Effective incident response requires both technical analysis and structured documentation. Maintaining clear investigation records, documenting indicators of compromise, and outlining remediation actions helps organizations improve detection capabilities and strengthen overall security posture.

These investigations demonstrate the importance of continuous monitoring, proactive threat detection, and structured incident response procedures in protecting enterprise identity systems.
