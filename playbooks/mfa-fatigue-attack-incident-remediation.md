# MFA Fatigue Attack Remediation

## Objective

Stop repeated Multi-Factor Authentication prompts, secure the affected account, and prevent additional unauthorized authentication attempts.

---

## Step 1 – Review Sign-In Activity

1. Sign in to the **Microsoft Entra admin center**.
2. In the left navigation pane, select **Identity**.
3. Select **Monitoring & health**.
4. Click **Sign-in logs**.
5. In the **User** filter, select the affected account.
6. In the **Date** filter, choose the time range covering the reported incident.
7. Review the sign-in attempts for:
   - repeated authentication attempts
   - unfamiliar locations
   - unknown devices
   - repeated MFA challenges

---

## Step 2 – Review MFA Activity

1. In the sign-in logs, click one of the suspicious events.
2. Review the **Authentication Details** section.
3. Confirm that multiple MFA prompts were sent.
4. Document the timestamps and IP addresses associated with the prompts.

---

## Step 3 – Verify User Activity

1. Contact the affected user using an approved communication method.
2. Confirm whether the user initiated any sign-in attempts.
3. Confirm whether the user received unexpected MFA prompts.
4. Document the user’s response.

---

## Step 4 – Reset the User Password

1. In the left navigation pane, select **Identity**.
2. Select **Users**.
3. Open the affected user account.
4. Click **Reset password**.
5. Generate a temporary password.
6. Enable the option requiring the user to change the password at the next sign-in.
7. Save the new password securely according to internal procedures.

---

## Step 5 – Revoke Active Sessions

1. While still in the affected user account, locate the option to manage sign-in sessions.
2. Click **Revoke sessions**.
3. Confirm the action.

---

## Step 6 – Require MFA Re-Registration

1. Open the affected user account.
2. Navigate to **Authentication methods** if available in the tenant workflow.
3. Select the option to **Require re-register MFA**.
4. Confirm the action.

---

## Step 7 – Review Conditional Access Policies

1. In the left navigation pane, select **Protection**.
2. Click **Conditional Access**.
3. Review policies applying to the affected user or user group.
4. Confirm that:
   - MFA is required
   - legacy authentication is blocked
   - risky sign-ins are restricted
   - unfamiliar locations are controlled where appropriate
5. Update policies if necessary.

---

## Step 8 – Monitor for Recurrence

1. Return to **Sign-in logs**.
2. Continue monitoring the account for repeated attempts.
3. Confirm that no additional suspicious prompts occur after remediation.

---

## Resolution

The affected account was secured by resetting credentials, revoking sessions, requiring MFA re-registration, and reviewing Conditional Access protections.
