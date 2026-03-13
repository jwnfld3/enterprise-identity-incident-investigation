# Incident Response Playbooks

The following playbooks document investigation and remediation procedures for identity-based security incidents simulated within this lab environment.

These procedures were developed through hands-on practice in a Microsoft security lab, step-by-step testing in Microsoft Sentinel and Microsoft Entra ID, and review of publicly available Microsoft and MITRE documentation.

---

## How I Learned the Investigation and Remediation Process

The workflow used in these playbooks was learned by building a repeatable lab process and following Microsoft security documentation step by step.

### Click-by-Click Learning Process

1. Signed in to the Microsoft Azure portal.

2. Opened **Microsoft Sentinel** from the Azure portal search bar.

3. Selected the lab workspace used for investigation practice.

4. Opened **Logs** inside Microsoft Sentinel.

5. Reviewed available log tables such as **SigninLogs** and other authentication-related records.

6. Copied sample and custom **Kusto Query Language (KQL)** queries into the query editor.

7. Ran queries to identify suspicious authentication activity such as repeated failures, unusual login locations, and excessive MFA prompts.

8. Compared the query results to the simulated incident scenario to determine what activity appeared suspicious.

9. Reviewed relevant **Microsoft Entra ID** sign-in activity and identity-related events to better understand the authentication behavior.

10. Mapped the observed activity to the appropriate **MITRE ATT&CK technique** so the incident could be categorized using a recognized industry framework.

11. Documented the investigation steps used to review the alert, validate the suspicious activity, and identify potential containment actions.

12. Created remediation playbooks based on the repeated workflow used in the lab so each incident type followed a structured response process.

This approach helped build familiarity with security investigation workflow, authentication log analysis, and documentation practices commonly used in Security Operations Center environments.

---

## Playbook Dashboard

| Playbook | Description | MITRE ATT&CK Technique | Playbook Link |
|:---------|:-------------|:----------------------|:--------------|
| Conditional Access Policy Block Remediation | Response procedures for blocking suspicious authentication activity using Conditional Access policies | Defense Evasion / Initial Access | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/conditional-access-policy-block-remediation.md) |
| Data Exfiltration Investigation Remediation | Investigation and remediation procedures for suspected data exfiltration activity | T1041 Exfiltration Over Command and Control Channel | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/data-exfiltration-investigation-remediation.md) |
| Identity Compromise Remediation | Response procedures for compromised user identities and unauthorized access | T1078 Valid Accounts | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/identity-compromise-remediation.md) |
| Impossible Travel Login Remediation | Investigation procedures for logins originating from geographically distant locations within a short timeframe | T1078 Valid Accounts | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/impossible-travel-login-remediation.md) |
| MFA Fatigue Attack Remediation | Investigation and mitigation procedures for repeated MFA authentication prompts | T1621 Multi Factor Authentication Request Generation | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/mfa-fatigue-attack-incident-remediation.md) |
| Password Spray Attack Remediation | Investigation and containment procedures for password spray authentication attempts | T1110.003 Password Spraying | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/password-spray-attack-remediation.md) |
| Phishing Attack Remediation | Investigation procedures for phishing-based authentication attempts targeting user credentials | T1566 Phishing | [View Playbook](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/phishing-attack-remediation.md) |

---

## Documentation Sources

The investigation procedures and response steps documented in this repository were learned through review of publicly available Microsoft security documentation and the MITRE ATT&CK framework.

### Primary Documentation Used

Microsoft Sentinel Documentation  
[Microsoft Sentinel Documentation](https://learn.microsoft.com/en-us/azure/sentinel/)

Microsoft Entra ID Sign-in Log Documentation  
[Microsoft Entra ID Sign-in Logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins)

Kusto Query Language Documentation  
[Kusto Query Language Documentation](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)

Microsoft Entra Conditional Access Documentation  
[Microsoft Entra Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/)

MITRE ATT&CK Enterprise Matrix  
[MITRE ATT&CK Enterprise Matrix](https://attack.mitre.org/matrices/enterprise/)

---

## Why These Sources Were Used

These references were used to learn:

- how Microsoft security logs are collected and reviewed
- how KQL is used to search and analyze authentication events
- how Microsoft Sentinel supports alert investigation and response workflows
- how Microsoft Entra ID records sign-in and identity-related activity
- how MITRE ATT&CK techniques help classify attacker behavior

This repository is intended as a hands-on learning project built in a controlled lab environment and does not represent production security operations experience.
