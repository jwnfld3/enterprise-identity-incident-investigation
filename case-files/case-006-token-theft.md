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

### Click by Click Learning Process

1. Access the Microsoft Entra Admin Center.
2. Navigate to Sign-in Logs.
3. Identify authentication events associated with the user account.
4. Review session details and authentication tokens.
5. Identify unusual session persistence or access patterns.
6. Compare device information across authentication events.
7. Look for authentication activity from new devices.
8. Review application access logs.
9. Identify unusual resource access patterns.
10. Document investigation findings.

---

# Outcome

Suspicious sessions were terminated and monitoring was increased.

---

# Case Status

Resolved

### Documentation Sources

Microsoft Entra Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/

Microsoft OAuth Token Security Guidance  
https://learn.microsoft.com/en-us/security/
