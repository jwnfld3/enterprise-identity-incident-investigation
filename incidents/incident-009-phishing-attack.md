# Incident Report: Phishing Attack Investigation

**Incident ID:** IR-2025-001  
**Incident Type:** Credential Phishing Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365  
**Detection Source:** Authentication Log Analysis and Security Alert  

---

# Incident Summary

A phishing attack targeting employee credentials was identified after suspicious authentication activity was detected within Microsoft Entra ID sign-in logs. Investigation revealed that a user had interacted with a malicious email containing a fraudulent login page designed to capture Microsoft 365 credentials.

The attacker attempted to use the compromised credentials to authenticate from an external IP address shortly after the phishing email was opened. Security monitoring systems flagged abnormal login behavior originating from a geographic region not previously associated with the affected user.

Immediate containment actions were taken to prevent unauthorized access to enterprise resources.

---

# Incident Timeline

| Time | Event |
|-----|------|
| 09:12 | Phishing email delivered to user inbox |
| 09:15 | User opened phishing email |
| 09:17 | User entered credentials into fraudulent login page |
| 09:20 | External authentication attempt detected |
| 09:22 | Security alert triggered for suspicious login |
| 09:25 | SOC analyst initiated investigation |
| 09:30 | User account sessions revoked |
| 09:33 | Password reset enforced |
| 09:35 | Malicious IP address blocked |

---

# Detection Method

The incident was detected through monitoring of authentication logs in Microsoft Sentinel. The following indicators triggered investigation:

- Successful login attempt from an unfamiliar geographic location
- Authentication originating from an IP address not previously associated with the user
- Login activity occurring shortly after interaction with a suspicious email

Security alerts identified abnormal authentication behavior and triggered SOC investigation procedures.

---

# Investigation Process

The investigation involved several steps to determine whether credentials had been compromised.

### Step 1: Review Authentication Logs

SOC analysts reviewed Microsoft Entra ID sign-in logs to identify unusual login patterns.

Observed indicators included:

- Login from an unfamiliar IP address
- Authentication originating from a foreign geographic location
- Login occurring shortly after the phishing email interaction

---

### Step 2: Examine User Activity

The affected user account was analyzed for unusual activity including:

- mailbox access
- file downloads
- SharePoint access
- OneDrive activity

No evidence of data access or exfiltration was identified.

---

### Step 3: Analyze Source IP Address

The source IP address was investigated using threat intelligence platforms including:

- AbuseIPDB
- AlienVault Open Threat Exchange
- Microsoft Security Intelligence

The IP address had previously been reported for credential harvesting activity.

---

### Step 4: Review Email Message

The phishing email contained a malicious link directing the user to a fake Microsoft login page designed to harvest credentials.

Indicators included:

- Domain impersonation
- misleading sender information
- embedded login page designed to mimic Microsoft authentication portals

---

# Indicators of Compromise (IOCs)

The following indicators were identified during the investigation:

| Indicator Type | Value |
|---------------|------|
| Malicious IP Address | 185.220.xxx.xxx |
| Attack Technique | Credential Phishing |
| Target Platform | Microsoft 365 |
| Suspicious Login Location | Foreign Region |
| Phishing Domain | login-security-check.example |

---

# MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1566 | Phishing |
| T1078 | Valid Accounts |
| T1110 | Credential Access Attempts |

Mapping attack activity to MITRE ATT&CK helps security teams understand adversary techniques and improve defensive strategies.

---

# Containment Actions

The following containment actions were executed to mitigate the incident:

1. The affected user account password was reset.
2. All active authentication sessions were revoked.
3. The malicious IP address was blocked using Conditional Access policies.
4. The phishing email was removed from affected mailboxes.
5. Multi-factor authentication enforcement was confirmed.

---

# Recovery Actions

To restore secure access and prevent further compromise:

- The user account was reauthenticated with a new password.
- MFA verification was completed.
- Security policies were reviewed to ensure proper protection.

---

# Defensive Improvements

Following the investigation, the following security measures were recommended:

- Expand phishing awareness training for employees.
- Implement stricter Conditional Access policies.
- Monitor authentication logs for suspicious activity.
- Enable automated alerts for risky sign-in events.
- Improve email filtering rules to block phishing attempts.

---

# Lessons Learned

Phishing attacks remain one of the most common techniques used by attackers to obtain user credentials. Early detection through authentication monitoring and threat intelligence correlation allowed the security team to quickly contain the threat before sensitive data was accessed.

Continued user education and identity security controls are essential to preventing similar incidents.

---

# Conclusion

The phishing attack successfully captured user credentials but was detected quickly through abnormal authentication monitoring. Security controls prevented further compromise, and remediation actions restored secure account access.

Ongoing monitoring and defensive improvements will reduce the likelihood of similar attacks targeting enterprise identity systems in the future.
