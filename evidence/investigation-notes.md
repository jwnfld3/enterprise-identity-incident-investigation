# Investigation Notes

These notes document observations collected during the identity security investigation.

---

## Initial Alert

Microsoft Entra ID Identity Protection generated a suspicious sign-in alert for user jsmith@company.com.

The alert indicated authentication activity from an unfamiliar geographic location.

---

## Initial Observations

User normally signs in from Seattle, Washington.

Authentication attempts detected from Bucharest, Romania.

Device associated with login attempt was not registered in Microsoft Entra ID.

---

## Risk Assessment

Risk Level: High

The authentication attempts were determined to represent a potential unauthorized access attempt.

---

## Investigator Notes

User confirmed they did not attempt to sign in from the suspicious location.

Password reset and session revocation were implemented to secure the account.
