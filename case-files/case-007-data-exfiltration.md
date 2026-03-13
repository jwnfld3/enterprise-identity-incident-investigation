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

### Click by Click Learning Process

1. Sign in to the Microsoft Entra Admin Center.
2. Navigate to Identity.
3. Select Monitoring.
4. Open Sign-in Logs.
5. Filter results for Failed Sign-in attempts.
6. Sort by IP address to identify repeated login attempts.
7. Review accounts targeted from the same IP address.
8. Identify patterns of repeated password attempts across multiple accounts.
9. Confirm whether the behavior matches password spray attack patterns.
10. Document the source IP address and impacted accounts.

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

### Documentation Sources

Microsoft Password Spray Investigation Guide  
https://learn.microsoft.com/en-us/security/operations/incident-response-playbook-password-spray

Microsoft Entra Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/

MITRE ATT&CK Password Spraying  
https://attack.mitre.org/techniques/T1110/003/
