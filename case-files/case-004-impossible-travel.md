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

### Click by Click Learning Process

1. Sign in to the Microsoft Entra Admin Center.
2. Navigate to Identity Protection.
3. Select Risky Sign-ins.
4. Locate the alert associated with the user account.
5. Review the locations associated with the sign-ins.
6. Compare timestamps of each authentication event.
7. Determine whether physical travel between locations was possible.
8. Review device and browser information.
9. Identify the IP addresses associated with each login.
10. Document investigation findings.

---

# Outcome

Investigation determined the activity was suspicious but no confirmed compromise occurred.

---

# Case Status

Resolved

### Documentation Sources

Microsoft Impossible Travel Detection  
https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy

Microsoft Entra Identity Protection Risk Events  
https://learn.microsoft.com/en-us/entra/id-protection/
