# Impossible Travel Authentication Investigation Case File

**Case ID:** CASE-004  
**Incident Type:** Suspicious Authentication  
**Severity:** Medium  
**Platform:** Microsoft Entra ID  
**MITRE ATT&CK Technique:** T1078 Valid Accounts  
**Status:** Resolved  

---

# Incident Summary

Authentication logs revealed two successful login attempts for the same account from geographically distant locations within a short time period. The time between logins made legitimate travel impossible.

---

# Detection

Detection reference:

```
detections/impossible-travel-detection.md
```

---

# Investigation Process

1. reviewed login timestamps
2. verified geographic login locations
3. analyzed authentication device information

---

# Containment and Remediation

Response procedure used:

```
playbooks/impossible-travel-login-remediation.md
```

Actions taken:

- session revocation
- password reset
- MFA verification

---

# Outcome

Investigation determined the activity was suspicious but no confirmed compromise occurred.

---

# Case Status

Resolved
