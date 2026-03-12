# Data Exfiltration Investigation Case File

**Case ID:** CASE-007  
**Incident Type:** Data Exfiltration  
**Severity:** Critical  
**Platform:** Microsoft 365 / SharePoint / OneDrive  
**MITRE ATT&CK Technique:** T1041 Exfiltration Over Command and Control Channel  
**Status:** Resolved  

---

# Incident Summary

Abnormal cloud activity suggested large file transfers originating from a user account shortly after suspicious authentication activity.

---

# Detection

Detection reference:

```
detections/data-exfiltration-detection.md
```

Evidence source:

```
attacks/malicious-mailbox-rule-log.md
```

---

# Investigation Process

1. reviewed file access logs
2. analyzed cloud storage activity
3. verified authentication history

---

# Containment and Remediation

Response procedure used:

```
playbooks/data-exfiltration-response-playbook.md
```

Actions taken:

- revoked account sessions
- reviewed file access permissions
- monitored cloud storage activity

---

# Outcome

Suspicious activity was contained and access was restricted.

---

# Case Status

Resolved
