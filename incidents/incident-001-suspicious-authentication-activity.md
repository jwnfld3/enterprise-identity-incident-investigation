Evidence file: Entra ID Sign-in Logs

Investigators analyzed authentication telemetry including login timestamps, IP addresses, and geographic location data.

Log analysis confirmed that multiple authentication attempts originated from an unfamiliar IP address associated with a foreign geographic region. The login attempts failed due to incorrect credentials and Conditional Access restrictions.

### Step 2 – Identify Indicators of Suspicious Activity

The authentication attempts demonstrated several characteristics commonly associated with credential abuse attempts.

Observed indicators included:

- Multiple authentication failures targeting a single user account
- Login attempts originating from an unfamiliar geographic location
- Authentication attempts from an IP address not previously associated with the user

These indicators suggested a potential attempt to access the account using stolen or guessed credentials.

### Step 3 – Review Conditional Access Policy Results

Conditional Access policy logs confirmed that the authentication attempts were blocked by existing security controls.

The policy enforced multi-factor authentication and restricted access from unfamiliar locations, preventing the suspicious login attempts from successfully accessing the Microsoft 365 environment.

### Step 4 – Confirm Scope of Activity

Investigators reviewed authentication activity for additional user accounts to determine whether the activity represented a broader attack.

No additional suspicious login attempts were identified for other users, suggesting that the activity was isolated to the affected account.

---

## Remediation

The following remediation actions were taken to ensure the security of the affected account.

- User password was reset
- Active authentication sessions were revoked
- Conditional Access policies were reviewed
- User notified of suspicious login attempts
- Security monitoring continued for additional authentication anomalies

These remediation steps ensured that the attempted access did not result in unauthorized account compromise.

---

## MITRE ATT&CK Mapping

| Technique | ID | Description |
|---|---|---|
| Valid Accounts | T1078 | Attempted authentication using legitimate user credentials |
| Brute Force | T1110 | Multiple failed authentication attempts targeting a user account |

---

## Lessons Learned

This investigation highlights the importance of monitoring authentication activity within enterprise identity platforms.

Authentication telemetry provides valuable insight into potential credential abuse attempts, particularly when login attempts originate from unfamiliar locations or IP addresses.

Conditional Access policies play a critical role in preventing unauthorized access by enforcing additional authentication requirements and restricting suspicious login activity.

Continuous monitoring and investigation of authentication anomalies are essential components of effective identity security operations.
