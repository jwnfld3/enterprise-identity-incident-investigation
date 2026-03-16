# Attack Evidence Logs

This directory contains log artifacts representing suspicious or malicious activity identified during identity security investigations.

These logs simulate authentication based attacks commonly investigated by Security Operations Center analysts.

---

# Attack Log Files

| Attack Evidence | Description |
|---|---|
| [Brute Force Login Log](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/evidence/attacks/brute-force-login-log.md) | Repeated authentication attempts against a single account using multiple password guesses. |
| [Credential Stuffing Log](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/evidence/attacks/credential-stuffing-log.md) | Authentication attempts using compromised username and password combinations obtained from external breaches. |
| [Malicious Mailbox Rule Log](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/evidence/attacks/malicious-mailbox-rule-log.md) | Suspicious mailbox rule creation that may indicate persistence or email interception after account compromise. |
| [Password Spray Log](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/evidence/attacks/password-spray-log.md) | Authentication attempts targeting multiple accounts using a small set of commonly used passwords. |
| [Phishing Login Attempt Log](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/evidence/attacks/phishing-login-attempt-log.md) | Authentication activity associated with credential phishing attempts. |
| [Suspicious IP Attack Log](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/evidence/attacks/suspicious-ip-attack-log.md) | Authentication attempts originating from suspicious or previously unseen IP addresses. |
| [Token Theft Log](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/evidence/attacks/token-theft-log.md) | Authentication activity indicating possible session token theft or session hijacking. |

---

# Investigation Context

These logs are used as supporting evidence for the investigation cases documented in the repository.

Security analysts use these artifacts to:

• analyze suspicious authentication activity  
• identify credential attack patterns  
• reconstruct attacker timelines  
• correlate events across systems  

---

# Navigation

[Return to Evidence Directory](https://github.com/jwnfld3/enterprise-identity-incident-investigation/tree/main/evidence)

[Return to Investigation Cases](https://github.com/jwnfld3/enterprise-identity-incident-investigation/tree/main/case-files)
