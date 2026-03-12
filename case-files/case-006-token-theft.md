# Authentication Token Theft Investigation

**Case ID:** CASE-006  
**Incident Type:** Session Hijacking  
**Severity:** High  
**Platform:** Microsoft 365  
**MITRE ATT&CK Technique:** T1528 Steal Application Access Token  
**Status:** Resolved  

---

# Incident Summary

Suspicious authentication sessions suggested possible token theft activity where attackers attempted to access resources without reauthenticating.

---

# Detection

Evidence source:

```
attacks/token-theft-log.md
```

---

# Investigation Process

1. reviewed session authentication logs
2. analyzed device identifiers
3. verified authentication token usage

---

# Containment and Remediation

Response procedure used:

```
playbooks/identity-compromise-remediation.md
```

Actions taken:

- revoked authentication tokens
- forced user sign-in
- reset credentials

---

# Outcome

Suspicious sessions were terminated and monitoring was increased.

---

# Case Status

Resolved
