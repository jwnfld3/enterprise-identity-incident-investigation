# Incident Response Playbooks

This directory contains remediation and response procedures for security incidents identified during the investigation scenarios documented in this repository.

These playbooks represent the actions security analysts and incident response teams may take after detecting suspicious activity or confirming a security incident.

Each playbook provides structured remediation guidance designed to contain threats, secure affected accounts or systems, and restore a secure operating environment.

---

# Purpose

The purpose of these playbooks is to demonstrate how security teams respond to common identity-based security incidents within enterprise environments.

The procedures focus on:

• incident containment  
• account security remediation  
• policy enforcement  
• investigation follow-up actions  
• threat mitigation  

These playbooks simulate response procedures commonly used by Security Operations Centers and incident response teams when handling authentication attacks and identity compromise events.

---

# Incident Response Playbooks

| Playbook | Description |
|---|---|
| [Conditional Access Policy Block Remediation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/conditional-access-policy-block-remediation.md) | Response actions when a conditional access policy blocks suspicious authentication activity. |
| [Data Exfiltration Investigation Remediation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/data-exfiltration-investigation-remediation.md) | Containment and remediation procedures when suspicious data access or exfiltration activity is detected. |
| [Identity Compromise Remediation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/identity-compromise-remediation.md) | Steps to secure compromised user accounts and investigate unauthorized authentication activity. |
| [Impossible Travel Login Remediation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/impossible-travel-login-remediation.md) | Investigation and response procedures for authentication events occurring from geographically impossible locations. |
| [MFA Fatigue Attack Incident Remediation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/mfa-fatigue-attack-incident-remediation.md) | Response procedures for repeated MFA prompt attacks targeting user accounts. |
| [Password Spray Attack Remediation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/password-spray-attack-remediation.md) | Containment and mitigation actions for password spray credential attacks. |
| [Phishing Attack Remediation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/playbooks/phishing-attack-remediation.md) | Steps to respond to credential phishing incidents and secure affected accounts. |

---

# Incident Response Workflow

Security investigations typically transition into remediation using the following workflow:

1. Detection  
   Suspicious activity is identified through security alerts or log analysis.

2. Investigation  
   Analysts review authentication logs and related evidence to confirm malicious activity.

3. Containment  
   Immediate actions are taken to prevent further unauthorized access.

4. Remediation  
   Security controls are applied to eliminate vulnerabilities and secure affected accounts or systems.

5. Documentation  
   The incident and remediation steps are documented for audit and learning purposes.

---

# Related Investigation Documentation

## Navigation

- [Return to Investigation Case Files](https://github.com/jwnfld3/enterprise-identity-incident-investigation/tree/main/case-files)
- [Return to Evidence Repository](https://github.com/jwnfld3/enterprise-identity-incident-investigation/tree/main/evidence)
