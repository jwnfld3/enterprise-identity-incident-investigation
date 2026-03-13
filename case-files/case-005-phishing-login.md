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

### Click by Click Learning Process

1. Access the Microsoft Defender Portal.
2. Navigate to Email and Collaboration.
3. Open Threat Explorer.
4. Search for the suspicious email.
5. Review sender domain and email headers.
6. Identify malicious links or attachments.
7. Determine whether the user clicked the phishing link.
8. Cross reference authentication activity within sign-in logs.
9. Identify successful login attempts following the phishing event.
10. Document investigation results.

---

# Outcome

User accounts were secured and phishing indicators were documented.

---

# Case Status

Resolved

### Documentation Sources

Microsoft Defender Phishing Investigation Guide  
https://learn.microsoft.com/en-us/defender-office-365/anti-phishing

Microsoft Security Operations Documentation  
https://learn.microsoft.com/en-us/security/operations/
