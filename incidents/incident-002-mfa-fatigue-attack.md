Evidence source: Microsoft Entra ID Sign-in Logs

Investigators reviewed authentication telemetry to analyze the pattern of login attempts associated with the affected user account.

Log analysis confirmed repeated authentication attempts originating from an unfamiliar IP address. Each login attempt triggered a Multi Factor Authentication push notification sent to the user’s registered device.

The repeated authentication attempts occurred within a short time interval, which is a behavior commonly associated with MFA fatigue attacks.

---

### Step 2 – Identify Suspicious Authentication Behavior

The authentication activity demonstrated characteristics consistent with a potential MFA fatigue attack.

Observed indicators included:

- Repeated MFA push notifications sent to the user
- Authentication attempts originating from an unfamiliar geographic location
- Login attempts from an IP address not previously associated with the user
- Multiple authentication failures followed by MFA challenges

Attackers sometimes attempt to overwhelm users with authentication prompts in the hope that the user will eventually approve the request.

---

### Step 3 – Confirm User Activity

Security investigators contacted the affected user to verify whether the authentication attempts were legitimate.

The user confirmed that they did not initiate the login attempts and had not attempted to access Microsoft 365 during the time the authentication prompts were received.

This confirmation indicated that the authentication attempts were unauthorized.

---

### Step 4 – Evaluate Security Controls

Conditional Access and Multi Factor Authentication policies were reviewed to confirm that the authentication attempts were unsuccessful.

Security controls successfully prevented the attacker from gaining access to the Microsoft 365 environment because the user did not approve any authentication prompts.

---

## Remediation

The following remediation actions were taken to secure the affected account.

- User password was reset
- Active authentication sessions were revoked
- Multi Factor Authentication settings were reviewed
- Security monitoring was increased for the affected account
- User was instructed to report any additional unexpected MFA prompts

These remediation actions ensured that the attempted authentication activity did not result in unauthorized account access.

---

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Attempted authentication using legitimate user credentials |
| Multi Factor Authentication Interception | T1621 | Attempts to bypass or manipulate multi factor authentication mechanisms |

---

## Lessons Learned

This investigation demonstrates how attackers may attempt to exploit user behavior by sending repeated authentication prompts in an attempt to gain approval.

Multi Factor Authentication remains an effective security control, but user awareness is critical. Users should be trained to recognize unexpected authentication prompts and immediately report suspicious activity.

Monitoring authentication logs and promptly investigating unusual login behavior helps organizations detect and respond to identity security threats before unauthorized access occurs.

---

## Documentation

The investigation techniques and remediation procedures documented in this incident report were developed through review of publicly available cybersecurity documentation and vendor guidance.

- **Microsoft Sentinel Documentation**  
  https://learn.microsoft.com/en-us/azure/sentinel/

- **Microsoft Entra ID Sign-in Logs Documentation**  
  https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

- **Kusto Query Language Documentation**  
  https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/

- **Microsoft Entra Conditional Access Documentation**  
  https://learn.microsoft.com/en-us/entra/identity/conditional-access/

- **Microsoft Defender Security Documentation**  
  https://learn.microsoft.com/en-us/defender/

- **MITRE ATT&CK Framework**  
  https://attack.mitre.org/
