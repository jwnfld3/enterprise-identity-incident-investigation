# Identity Compromise Investigation Case File

**Case ID:** CASE-002  
**Incident Type:** Account Compromise  
**Severity:** Critical  
**Platform:** Microsoft Entra ID / Microsoft 365  
**Primary Detection Source:** Microsoft Sentinel  
**MITRE ATT&CK Technique:** T1078 Valid Accounts  
**Status:** Resolved  

---

# Incident Summary

Suspicious authentication activity indicated that a user account may have been compromised. Successful authentication attempts were observed from an unfamiliar geographic location shortly after several failed login attempts.

---

# Detection

Authentication monitoring alerts triggered investigation.

Evidence source:

```
attacks/suspicious-ip-attack-log.md
```

Indicators included:

- successful login from unfamiliar IP
- abnormal login location
- authentication following repeated failures

---

# Investigation Process

1. Reviewed authentication logs.
2. Verified login locations.
3. analyzed device and application access activity.
4. correlated activity with known credential attacks.

---

# Containment and Remediation

Response procedure used:

```
playbooks/identity-compromise-remediation.md
```

Actions taken:

- password reset
- session revocation
- MFA verification
- monitoring for additional suspicious activity

---

# Outcome

The compromised account was secured and authentication monitoring was increased to detect further suspicious activity.

---

# Case Status

Resolved
