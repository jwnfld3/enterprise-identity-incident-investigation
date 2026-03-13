# MFA Fatigue Attack Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Identity Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Stop repeated Multi Factor Authentication prompts, secure the affected account, and prevent additional unauthorized authentication attempts.

---

## Overview

An MFA fatigue attack occurs when an attacker repeatedly attempts to sign in with a user's correct password and triggers multiple authentication prompts. The attacker hopes the user becomes confused, distracted, or frustrated and eventually approves one of the requests.

This procedure explains how to review the sign in activity, confirm whether the prompts were legitimate, secure the account, and reduce the chance of additional unauthorized attempts.

---

## Step 1: Review Sign In Activity

### Purpose

This step helps identify whether the account is experiencing repeated sign in attempts that match MFA fatigue behavior.

### Instructions

1. Open a web browser.
2. Go to the Microsoft Entra admin center.

```text
https://entra.microsoft.com
```

3. Sign in with an administrator account.
4. In the left navigation pane, click **Identity**.
5. Click **Monitoring & health**.
6. Click **Sign in logs**.
7. In the filter area, select the **User** filter.
8. Choose the affected user account.
9. In the **Date** filter, select the time range covering the reported incident.
10. Review the sign in attempts.

### What to Look For

1. Repeated authentication attempts in a short time
2. Unfamiliar locations
3. Unknown devices
4. Multiple MFA challenges
5. Sign in attempts the user does not recognize

### Explanation

This step helps determine whether the sign in activity looks normal or suspicious. MFA fatigue attacks often create repeated authentication events that stand out in the sign in logs.

---

## Step 2: Review MFA Activity

### Purpose

This step confirms whether repeated MFA prompts were actually sent to the user.

### Instructions

1. In the sign in logs, click one of the suspicious sign in events.
2. Open the event details page.
3. Locate the **Authentication Details** section.
4. Review whether MFA was required.
5. Confirm whether multiple MFA prompts were generated.
6. Record the timestamps of the prompts.
7. Record the IP addresses associated with the prompts.

### Explanation

The Authentication Details section helps confirm whether the sign in attempts triggered repeated MFA requests. This is one of the strongest indicators of an MFA fatigue attack.

---

## Step 3: Verify User Activity

### Purpose

This step confirms whether the sign in attempts were legitimate or unauthorized.

### Instructions

1. Contact the affected user using an approved method such as phone, Teams, or internal ticketing.
2. Ask whether the user attempted to sign in during the reported time.
3. Ask whether the user received unexpected MFA prompts.
4. Ask whether the user approved any prompt.
5. Document the user's response in the incident notes.

### Explanation

User confirmation is important because repeated MFA prompts might occasionally be caused by legitimate issues such as application reauthentication. The user's response helps determine whether the activity is suspicious.

---

## Step 4: Reset the User Password

### Purpose

This step prevents the attacker from continuing to use the compromised password.

### Instructions

1. In the left navigation pane, click **Identity**.
2. Click **Users**.
3. Search for the affected user account.
4. Open the user account.
5. Click **Reset password**.
6. Generate a temporary password.
7. Enable the option requiring the user to change the password at the next sign in.
8. Save the password according to internal security procedures.

### Explanation

If the attacker knows the user's password, resetting it removes the attacker's ability to keep triggering MFA prompts using that password.

---

## Step 5: Revoke Active Sessions

### Purpose

This step forces existing sign in sessions to end.

### Instructions

1. Stay on the affected user account page.
2. Locate the option related to sign in session management.
3. Click **Revoke sessions**.
4. Confirm the action.

### Explanation

If the attacker already gained access, they may have active sessions or cached authentication tokens. Revoking sessions forces reauthentication and helps cut off unauthorized access.

---

## Step 6: Require MFA Re Registration

### Purpose

This step ensures the user reconfigures their MFA methods if compromise is suspected.

### Instructions

1. Open the affected user account.
2. Navigate to **Authentication methods** if it is available in the tenant workflow.
3. Select the option to require MFA re registration.
4. Confirm the action.

### Explanation

If an attacker altered authentication methods or if the user's MFA setup is no longer trusted, re registration ensures the account is secured with verified MFA settings.

---

## Step 7: Review Conditional Access Policies

### Purpose

This step confirms that protective access controls are in place.

### Instructions

1. In the left navigation pane, click **Protection**.
2. Click **Conditional Access**.
3. Review the policies that apply to the affected user or user group.
4. Confirm that MFA is required.
5. Confirm that legacy authentication is blocked.
6. Confirm that risky sign ins are restricted if your environment supports it.
7. Confirm that unfamiliar locations are controlled where appropriate.
8. Update the policies if needed and according to internal approval processes.

### Explanation

Conditional Access policies add extra security controls that can make MFA fatigue attacks less effective, especially when suspicious locations or risky sign ins are involved.

---

## Step 8: Monitor for Recurrence

### Purpose

This step confirms that the suspicious behavior has stopped.

### Instructions

1. Return to **Sign in logs**.
2. Continue monitoring the affected account.
3. Look for any new repeated sign in attempts.
4. Confirm that no additional suspicious MFA prompts occur after remediation.
5. Document the outcome.

### Explanation

Monitoring after remediation helps verify that the attacker no longer has access and that the account remains secure.

---

## Resolution

The affected account was secured by reviewing suspicious sign in activity, confirming repeated MFA prompts, resetting the password, revoking active sessions, requiring MFA re registration, and reviewing Conditional Access protections.

### Documentation Sources

Microsoft MFA Security Guidance  
https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks

Microsoft MFA Number Matching  
https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-mfa-number-match
