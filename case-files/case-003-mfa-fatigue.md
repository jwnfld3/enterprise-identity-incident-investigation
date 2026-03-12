# MFA Fatigue Attack Investigation Case File

**Case ID:** CASE-003  
**Incident Type:** Authentication Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365  
**Primary Detection Source:** Authentication Monitoring  
**MITRE ATT&CK Technique:** T1621 Multi-Factor Authentication Request Generation  
**Status:** Resolved  

---

# Incident Summary

Multiple MFA push notifications were generated for a targeted user account within a short timeframe. This activity suggested an MFA fatigue attack designed to trick the user into approving a malicious login attempt.

---

# Detection

Authentication monitoring revealed repeated MFA prompts for a single account.

Evidence source:

```
attacks/phishing-login-attempt-log.md
```

---

# Investigation Process

1. Reviewed MFA authentication events.
2. verified repeated login attempts.
3. confirmed login attempts originated from an external source.

---

# Containment and Remediation

Response procedure used:

```
playbooks/mfa-fatigue-attack-incident-remediation.md
```

Actions taken:

- revoked active sessions
- required password reset
- verified MFA settings
- monitored authentication activity

---

# Outcome

No unauthorized access was confirmed. Additional monitoring was implemented.

---

# Case Status

Resolved
