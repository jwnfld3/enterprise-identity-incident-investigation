## Investigation Methodology and Learning Process

The investigation procedures and response playbooks in this repository were developed through hands-on practice in a controlled lab environment while studying Microsoft security documentation and the MITRE ATT&CK framework.

The goal of this project was to learn how Security Operations Center (SOC) analysts investigate identity-based alerts using Microsoft Sentinel and Microsoft Entra ID authentication logs.

---

## Understanding MITRE ATT&CK Techniques

The MITRE ATT&CK framework is a publicly available knowledge base that documents attacker tactics and techniques observed in real-world cyber incidents.

Security teams use ATT&CK techniques to classify suspicious behavior and understand where an attacker may be in the attack lifecycle.

Examples referenced in this project include:

| Technique | Description |
|-----------|-------------|
| T1110.003 Password Spraying | Attackers attempt a small set of passwords across many accounts to avoid account lockouts. |
| T1078 Valid Accounts | Attackers use compromised credentials to authenticate legitimately. |
| T1621 Multi-Factor Authentication Request Generation | Attackers repeatedly trigger MFA prompts hoping the user approves one. |
| T1041 Exfiltration Over Command and Control Channel | Attackers transfer sensitive data outside the environment. |

Mapping investigation scenarios to ATT&CK techniques helps analysts understand attacker behavior and improves detection coverage.

---

## Why Kusto Query Language (KQL) Is Used

Microsoft Sentinel and Azure Log Analytics use **Kusto Query Language (KQL)** to analyze security telemetry.

KQL allows analysts to:

• search authentication logs  
• identify suspicious login patterns  
• correlate events across users and IP addresses  
• investigate alerts and develop detection logic  

Security analysts rely on KQL to investigate identity-based security events and perform threat hunting within Microsoft cloud environments.

---

## How the Investigation Workflow Was Learned

The investigation workflow used in this project was learned by studying Microsoft Sentinel documentation and practicing log analysis inside a simulated lab environment.

### Click-by-Click Investigation Workflow

1. Signed in to the **Microsoft Azure Portal**.
2. Searched for **Microsoft Sentinel** in the Azure portal search bar.
3. Opened the Sentinel workspace used for the lab environment.
4. Selected **Logs** from the Sentinel navigation menu.
5. Reviewed available log tables including:

   - `SigninLogs`  
   - `SecurityEvent`  
   - `AuditLogs`

6. Entered KQL queries into the Sentinel query editor.
7. Selected **Run** to execute the query.
8. Reviewed authentication activity returned by the query results.
9. Identified suspicious patterns such as:

   - repeated login failures  
   - authentication attempts from unusual geographic locations  
   - repeated MFA prompts  

10. Compared the results with the simulated attack scenario.
11. Mapped the observed activity to the appropriate **MITRE ATT&CK technique**.
12. Documented the investigation process and remediation steps as structured incident response playbooks.

This process helped build familiarity with the workflow used by SOC analysts when investigating authentication-related alerts.

---

# Incident Response Playbooks

The following playbooks document investigation and remediation procedures for identity-based security incidents simulated within this lab environment.

| Playbook | Description | Playbook Link |
|:---------|:-------------|:--------------|
| Conditional Access Policy Block Remediation | Procedures for blocking suspicious authentication activity using Conditional Access policies | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/conditional-access-policy-block-remediation.md) |
| Data Exfiltration Investigation Remediation | Investigation and remediation procedures for suspected data exfiltration activity | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/data-exfiltration-investigation-remediation.md) |
| Identity Compromise Remediation | Response procedures for compromised user identities and unauthorized access | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/identity-compromise-remediation.md) |
| Impossible Travel Login Remediation | Investigation procedures for logins originating from geographically distant locations within a short timeframe | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/impossible-travel-login-remediation.md) |
| MFA Fatigue Attack Remediation | Investigation and mitigation procedures for repeated MFA authentication prompts | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/mfa-fatigue-attack-incident-remediation.md) |
| Password Spray Attack Remediation | Investigation and containment procedures for password spray authentication attempts | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/password-spray-attack-remediation.md) |
| Phishing Attack Remediation | Investigation procedures for phishing-based authentication attempts targeting user credentials | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/phishing-attack-remediation.md) |

---

## Documentation Sources

The investigation techniques and remediation procedures documented in this repository were developed through review of publicly available cybersecurity documentation and vendor guidance.

### Microsoft Security Documentation

Microsoft Sentinel Documentation  
https://learn.microsoft.com/en-us/azure/sentinel/

Microsoft Entra ID Sign-in Log Documentation  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

Kusto Query Language Documentation  
https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/

Microsoft Entra Conditional Access Documentation  
https://learn.microsoft.com/en-us/entra/identity/conditional-access/

### MITRE ATT&CK Framework

MITRE ATT&CK Enterprise Matrix  
https://attack.mitre.org/matrices/enterprise/

These sources were used to understand how security analysts investigate authentication activity, analyze identity security alerts, and develop structured incident response procedures.

---

## Project Transparency

All investigations and remediation procedures documented in this repository were performed in a simulated lab environment for educational purposes.

The project demonstrates investigation methodology, authentication log analysis, and documentation practices commonly used within Security Operations Center environments.
