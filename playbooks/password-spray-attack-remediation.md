# Password Spray Attack Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Identity Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Identify and contain a password spray attack targeting multiple accounts and reduce the likelihood of successful unauthorized access.

---

## Overview

A password spray attack occurs when an attacker attempts a small number of common passwords across many accounts. Instead of trying many passwords against one user, the attacker spreads the attempts across multiple users to avoid lockouts.

This procedure explains how to identify the attack, locate the affected accounts, review the attack source, protect targeted users, and continue monitoring for additional attempts.

---

## Step 1: Review Sign In Logs

### Purpose

This step helps identify whether failed authentication activity is consistent with a password spray attack.

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
7. Set the time range to the suspected attack window.
8. Review failed sign ins.

### What to Look For

1. Repeated failures
2. Multiple user accounts being targeted
3. The same IP address appearing repeatedly
4. Similar authentication patterns across several users

### Explanation

Password spraying usually creates repeated authentication failures against many accounts. The same source often appears across multiple sign in attempts.

---

## Step 2: Identify Affected Accounts

### Purpose

This step creates a list of users targeted during the attack.

### Instructions

1. Review the suspicious sign in events.
2. Document all usernames associated with the repeated failures.
3. Check whether any accounts show lockouts.
4. Check whether any accounts show risky sign ins.
5. Check whether any accounts show unusual MFA challenges.
6. Create a complete list of targeted accounts.

### Explanation

A clear list of targeted users helps analysts understand the scope of the attack and determine which accounts need immediate protection.

---

## Step 3: Identify the Source IP Address

### Purpose

This step identifies whether one source is targeting multiple accounts.

### Instructions

1. Open several suspicious sign in events.
2. Compare the source IP addresses.
3. Confirm whether the same IP address appears across multiple targeted accounts.
4. Record the IP address.
5. Record the reported location of the IP address.

### Explanation

Password spray attacks are often launched from one or a small number of IP addresses. Identifying the source helps with correlation, blocking, and documentation.

---

## Step 4: Review Risk Signals

### Purpose

This step checks whether Microsoft has already identified related risk indicators.

### Instructions

1. In the left navigation pane, open **Identity Protection** if it is available in the tenant.
2. Review **Risky sign ins**.
3. Review **Risky users**.
4. Review sign in risk levels.
5. Record any related alerts or risk findings.

### Explanation

Risk signals can strengthen the investigation by showing that Microsoft has already detected suspicious behavior associated with the accounts or the sign in activity.

---

## Step 5: Block the Malicious Source if Applicable

### Purpose

This step reduces the chance of repeated attack attempts from the same source.

### Instructions

1. In the left navigation pane, click **Protection**.
2. Click **Conditional Access**.
3. Review location based policy options.
4. Add the malicious IP address or location to the appropriate blocked location policy if approved by internal process.
5. Save the policy.

### Explanation

If the source IP is confirmed to be malicious, blocking it through access controls helps reduce additional password spray attempts.

---

## Step 6: Reset Targeted Accounts if Needed

### Purpose

This step protects accounts that may have been exposed or are considered at higher risk.

### Instructions

1. In the left navigation pane, click **Identity**.
2. Click **Users**.
3. Open each affected user account that requires remediation.
4. Click **Reset password**.
5. Generate a temporary password.
6. Require a password change at the next sign in.
7. Record completion for each user.

### Explanation

Resetting passwords reduces the chance that a guessed or weak password can be used successfully by the attacker.

---

## Step 7: Revoke Sessions for Affected Users

### Purpose

This step terminates any active sessions that may already exist.

### Instructions

1. Open each affected user account.
2. Locate the option to manage sign in sessions.
3. Click **Revoke sessions**.
4. Confirm the action.
5. Repeat for each affected user as needed.

### Explanation

If a sign in was successful, the attacker may already have an active session. Revoking sessions forces reauthentication and helps contain the incident.

---

## Step 8: Verify MFA Coverage

### Purpose

This step confirms that targeted users have appropriate MFA protection.

### Instructions

1. Review whether each targeted account is protected by MFA.
2. For accounts that are not adequately protected, update security settings or group assignment as approved.
3. Require MFA enrollment where appropriate.
4. Require MFA re registration if compromise is suspected.

### Explanation

Password spray attacks are much less likely to succeed when strong MFA coverage is in place.

---

## Step 9: Continue Monitoring

### Purpose

This step confirms that the attack has stopped.

### Instructions

1. Return to **Sign in logs**.
2. Monitor for additional attempts from the same IP address.
3. Monitor for repeated attempts against the same user accounts.
4. Confirm that the pattern of attack has stopped.
5. Document the monitoring results.

### Explanation

Attackers may retry the same technique after initial failures. Continued monitoring helps ensure the remediation was effective.

---

## Resolution

The password spray activity was identified through sign in log review, targeted accounts were documented, suspicious source activity was reviewed, appropriate account protections were applied, and monitoring was increased to confirm the attack stopped.
