# Identity Compromise Incident Report

**Incident Type:** Identity Compromise  
**Severity:** Critical  
**Platform:** Microsoft Entra ID / Microsoft 365  
**MITRE ATT&CK Techniques:** T1078 Valid Accounts, T1110.003 Password Spraying, T1528 Steal Application Access Token  

---

# Incident Overview

An identity compromise incident was identified after suspicious authentication activity was detected within the Microsoft Entra ID environment. Security monitoring systems flagged abnormal login behavior involving multiple failed authentication attempts followed by a successful login from an unfamiliar IP address.

Initial investigation indicated that an attacker likely obtained valid user credentials and attempted to gain access to enterprise cloud services including Microsoft 365.

---

# Detection

The incident was detected through authentication monitoring and SIEM analysis within Microsoft Sentinel.

Security alerts identified:

- Repeated failed login attempts
- Authentication attempts from unfamiliar geographic locations
- Successful authentication following multiple failed attempts
- Suspicious cloud activity shortly after login

These indicators suggested a possible credential based attack.

---

# Timeline of Events

| Time | Event |
|-----|------|
| 08:12 | Multiple failed login attempts detected |
| 08:14 | Authentication attempts from external IP address |
| 08:16 | Successful login recorded |
| 08:17 | Suspicious cloud activity initiated |
| 08:18 | Security alert generated in SIEM |
| 08:25 | SOC analyst begins investigation |
| 08:35 | Incident confirmed as identity compromise |
| 08:40 | Incident response procedures initiated |

---

# Indicators of Compromise

The following indicators were identified during the investigation.

**Suspicious IP Address**

185.220.101.17

**Abnormal Login Location**

Login attempts originated from a geographic location inconsistent with the user's normal login patterns.

**Authentication Pattern**

- Multiple failed login attempts
- Successful authentication after repeated failures
- Authentication originating from unfamiliar infrastructure

**Suspicious User Activity**

Shortly after successful authentication, the account initiated cloud activity including file access and mailbox interactions.

---

# Investigation Steps

Security analysts performed the following actions during the investigation.

1. Reviewed Microsoft Entra ID sign-in logs.
2. Identified abnormal authentication patterns.
3. Verified login locations and IP reputation.
4. Reviewed user activity within Microsoft 365 services.
5. Cross referenced the suspicious IP address with threat intelligence databases.
6. Confirmed the activity was inconsistent with normal user behavior.

Threat intelligence sources indicated the IP address had previously been associated with credential attack activity.

---

# MITRE ATT&CK Mapping

The incident behavior aligns with the following adversary techniques.

| Technique | Description |
|----------|-------------|
| T1078 | Use of valid accounts to gain unauthorized access |
| T1110.003 | Password spraying attack targeting multiple accounts |
| T1528 | Theft or abuse of authentication tokens |

These techniques are commonly used in identity based attacks targeting cloud services.

---

# Containment Actions

After confirming the compromise, the following containment actions were executed.

1. The affected user account password was reset.
2. All active authentication sessions were revoked.
3. The suspicious IP address was blocked through Conditional Access policies.
4. Multi factor authentication was enforced for the affected account.
5. The user's mailbox and cloud storage activity were reviewed for unauthorized access.

These actions prevented further unauthorized access to enterprise systems.

---

# Recovery Actions

Following containment, additional recovery actions were implemented.

- The affected user was notified of the incident.
- The user was instructed to update all credentials.
- Authentication logs were monitored for continued suspicious activity.
- Identity protection policies were reviewed and strengthened.

No additional malicious activity was observed after remediation actions were completed.

---

# Defensive Improvements

To reduce the likelihood of similar incidents occurring in the future, the following security controls were recommended.

- Enforce multi factor authentication for all users
- Implement Conditional Access policies for risky locations
- Configure automated alerts for abnormal authentication behavior
- Monitor authentication logs for credential attack patterns
- Implement identity protection risk detection policies

---

# Lessons Learned

This incident highlights the importance of continuous authentication monitoring and rapid incident response. Credential based attacks remain one of the most common methods used by attackers to gain unauthorized access to cloud environments.

Early detection of suspicious login patterns allowed the security team to contain the compromise before significant damage occurred.

---

# Conclusion

The investigation confirmed that the suspicious authentication activity was the result of an identity compromise involving valid user credentials. Rapid response actions including password reset, session revocation, and conditional access enforcement successfully contained the incident.

Ongoing monitoring and improved identity security controls are recommended to strengthen the organization's security posture against credential based attacks.
