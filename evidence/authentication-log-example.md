# Authentication Log Example

The following example represents a simulated authentication log review performed during the investigation of suspicious login activity detected in Microsoft Entra ID.

These logs were analyzed to determine whether the authentication attempts represented legitimate user activity or a potential unauthorized access attempt.

---

## Authentication Log Entries

| Timestamp (UTC) | User | Application | Location | Device | Result |
|-----------------|------|------------|---------|--------|--------|
| 2026-03-10 14:02 | jsmith@company.com | Microsoft 365 | Seattle, WA, USA | Windows 11 | Success |
| 2026-03-10 14:05 | jsmith@company.com | SharePoint Online | Seattle, WA, USA | Windows 11 | Success |
| 2026-03-10 14:11 | jsmith@company.com | Microsoft 365 | Bucharest, Romania | Unknown Device | Failure |
| 2026-03-10 14:12 | jsmith@company.com | Microsoft 365 | Bucharest, Romania | Unknown Device | Failure |
| 2026-03-10 14:13 | jsmith@company.com | Microsoft 365 | Bucharest, Romania | Unknown Device | Blocked |

---

## Observations

Recent successful logins were observed from Seattle, Washington, which matches the user's normal login location.

Shortly afterward, multiple authentication attempts were detected from Bucharest, Romania using an unknown device.

The authentication attempts from Romania failed and were blocked by existing authentication policies.

---

## Investigation Notes

The login attempts originating from Romania were identified as anomalous because the user typically signs in from the United States.

Device information associated with the suspicious login attempts did not match any device previously registered to the user account.

Based on the log analysis and user verification, the login attempts were determined to represent a potential unauthorized access attempt.

---

## Security Controls Triggered

Multi-Factor Authentication challenge triggered

Conditional Access policy evaluation

Risk based authentication detection

---

## Conclusion

The authentication logs indicate that the suspicious login attempts were unsuccessful and blocked by existing security controls.

The user account was secured by resetting credentials and verifying Multi-Factor Authentication enrollment.
