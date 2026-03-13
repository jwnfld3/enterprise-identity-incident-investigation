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

### Click by Click Learning Process

1. Access the Microsoft Entra Admin Center.
2. Navigate to Identity.
3. Select Users.
4. Locate the suspected user account.
5. Open the user profile.
6. Review the Sign-in activity section.
7. Identify sign-ins from unusual geographic locations or unknown devices.
8. Check authentication methods used during the login attempt.
9. Verify whether the user reported suspicious activity.
10. Document findings and determine if the account was compromised.

---

# Outcome

The compromised account was secured and authentication monitoring was increased to detect further suspicious activity.

---

# Case Status

Resolved

### Documentation Sources

Microsoft Entra Risky Sign-ins Documentation  
https://learn.microsoft.com/en-us/entra/id-protection/

Microsoft Security Incident Response Guidance  
https://learn.microsoft.com/en-us/security/operations/
