# Phishing Authentication Attempt Investigation

**Case ID:** CASE-005  
**Incident Type:** Credential Phishing  
**Severity:** High  
**Platform:** Microsoft 365  
**MITRE ATT&CK Technique:** T1566 Phishing  
**Status:** Resolved  

---

# Incident Summary

Users reported suspicious authentication prompts and login attempts following a phishing email campaign targeting enterprise users.

---

# Detection

Evidence source:

```
attacks/phishing-login-attempt-log.md
```

---

# Investigation Process

1. reviewed authentication logs
2. identified targeted accounts
3. correlated login attempts with phishing reports

---

# Containment and Remediation

Response procedure used:

```
playbooks/phishing-attack-remediation.md
```

Actions taken:

- password resets
- MFA enforcement
- user notification

---

# Outcome

User accounts were secured and phishing indicators were documented.

---

# Case Status

Resolved
