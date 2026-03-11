# Password Spray Attack Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Identity Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365
## Objective

Identify and contain a password spray attack targeting multiple accounts and reduce the likelihood of successful unauthorized access.

---

## Step 1 – Review Sign-In Logs

1. Sign in to the **Microsoft Entra admin center**.
2. Select **Identity**.
3. Select **Monitoring & health**.
4. Click **Sign-in logs**.
5. Set the time range to the suspected attack window.
6. Review failed sign-ins for:
   - repeated failures
   - multiple user accounts
   - the same IP address
   - similar authentication patterns

---

## Step 2 – Identify Affected Accounts

1. Document all usernames associated with the repeated failures.
2. Identify whether any accounts show:
   - lockouts
   - risky sign-ins
   - unusual MFA challenges
3. Create a list of targeted accounts.

---

## Step 3 – Identify the Source IP Address

1. Open several suspicious sign-in events.
2. Compare the source IP addresses.
3. Confirm whether the same IP is targeting multiple accounts.
4. Document the source IP and location.

---

## Step 4 – Review Risk Signals

1. Navigate to **Identity Protection** if available in the tenant.
2. Review:
   - risky sign-ins
   - risky users
   - sign-in risk levels
3. Document any related alerts.

---

## Step 5 – Block the Malicious Source if Applicable

1. Navigate to **Protection**.
2. Click **Conditional Access**.
3. Review location-based policy options.
4. Add the malicious IP or location to the appropriate blocked location policy if approved by internal process.
5. Save the policy.

---

## Step 6 – Reset Targeted Accounts if Needed

1. Navigate to **Identity**.
2. Select **Users**.
3. Open each affected user account requiring remediation.
4. Click **Reset password**.
5. Require password change at next sign-in.
6. Record completion for each user.

---

## Step 7 – Revoke Sessions for Affected Users

1. For each affected user, open the account page.
2. Select the option to **Revoke sessions**.
3. Confirm the action.

---

## Step 8 – Verify MFA Coverage

1. Review whether targeted accounts are protected by MFA.
2. For accounts not adequately protected, update security settings or group assignment as approved.
3. Require MFA enrollment or re-registration where appropriate.

---

## Step 9 – Continue Monitoring

1. Return to **Sign-in logs**.
2. Monitor for additional attempts from the same IP or against the same users.
3. Confirm the attack pattern has stopped.

---

## Resolution

The password spray activity was identified, targeted accounts were protected, suspicious source activity was addressed, and monitoring was increased.
