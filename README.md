# Enterprise Identity Incident Investigation

This project documents a simulated enterprise identity security investigation involving suspicious authentication activity detected in Microsoft Entra ID.

The objective of the investigation was to analyze authentication logs, determine whether the activity represented a potential account compromise, and implement containment and remediation procedures.

---

## Technologies Used

Microsoft Entra ID  
Microsoft 365  
Windows 11  
Authentication Logs  
Identity Protection Alerts  

---

## Skills Demonstrated

Security incident investigation  
Authentication log analysis  
Identity security monitoring  
Account compromise response  
Security documentation  

---

## Security Incident Investigation Dashboard

This repository contains a collection of enterprise identity security
investigations designed to demonstrate detection engineering, threat
analysis, and structured incident response procedures.

The investigations simulate real-world identity-based attack scenarios
within enterprise Microsoft environments using Microsoft Entra ID,
Microsoft 365, and Microsoft Sentinel. Each case documents the
investigation process, identifies adversary techniques using the
MITRE ATT&CK framework, and outlines remediation actions used to
contain and resolve the security event.

## Security Incident Investigation Dashboard

| Case Identifier | Investigation | Severity | MITRE ATT&CK Technique | Status | Investigation Report |
|--------|---------------|----------|------------------------|--------|---------------------|
| CASE-001 | Password Spray Attack | High | T1110.003 Password Spraying | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-001-password-spray.md) |
| CASE-002 | Enterprise Identity Compromise | Critical | T1078 Valid Accounts | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md) |
| CASE-003 | MFA Fatigue Attack | High | T1621 Multi-Factor Authentication Request Generation | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-003-mfa-fatigue.md) |
| CASE-004 | Impossible Travel Authentication | Medium | T1078 Valid Accounts | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-004-impossible-travel.md) |
| CASE-005 | Phishing Authentication Attempt | High | T1566 Phishing | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-005-phishing-login.md) |
| CASE-006 | Authentication Token Theft | High | T1528 Steal Application Access Token | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-006-token-theft.md) |
| CASE-007 | Data Exfiltration Activity | Critical | T1041 Exfiltration Over Command and Control Channel | Resolved | [View Investigation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-007-data-exfiltration.md) |
## Investigation Scenario

A security alert was triggered indicating unusual authentication activity for a user account in Microsoft Entra ID.

The login attempt originated from a geographic location that differed from the user's normal sign in pattern.

The objective of the investigation was to determine whether the login activity represented legitimate user activity or a potential unauthorized access attempt.

---

## Investigation Workflow

1 Review authentication logs  
2 Analyze login location and device information  
3 Verify user activity  
4 Determine risk level  
5 Implement containment actions  
6 Document findings and lessons learned  

