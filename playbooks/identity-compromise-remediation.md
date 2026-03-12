# Identity Compromise Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Identity Compromise  
**Severity:** Critical  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Investigate and remediate suspected user account compromise within Microsoft Entra ID and Microsoft 365.

## Overview

This playbook is used when a user account may have been compromised. Common signs include risky sign in alerts, impossible travel alerts, suspicious login behavior, or user reports of unusual activity. The goal is to confirm whether compromise occurred, contain access quickly, and restore secure access for the legitimate user.

## Who

This procedure is typically performed by:

1. Security Operations Center analysts
2. Incident responders
3. Identity administrators
4. Microsoft 365 administrators

## What

This procedure is used to:

1. Review suspicious sign in activity
2. Check risk alerts
3. Verify activity with the user
4. Reset access controls
5. Revoke active sessions
6. Monitor for continued compromise

## Where

This procedure is performed in:

1. Microsoft Entra admin center
2. Microsoft Entra Identity Protection
3. Microsoft Sentinel if available

## When

Use this playbook when:

1. Risk alerts indicate account compromise
2. The user reports suspicious sign ins
3. Unusual or high risk authentication is detected
4. Security monitoring shows abnormal access patterns

## Why

Identity compromise can lead to unauthorized access, data theft, lateral movement, and additional attacks. Fast response is important to limit damage and secure the account.

## Detection

Identity compromise may be detected through:

1. Sign in risk alerts
2. Impossible travel alerts
3. User reported suspicious activity
4. Unusual login activity
5. Suspicious IP based access
6. Abnormal cloud activity following authentication

## Step 1: Review Sign In Logs

### Purpose

This step identifies suspicious login events involving the affected account.

### Instructions

1. Open a web browser.
2. Go to the Microsoft Entra admin center.

```text
https://entra.microsoft.com
```

3. Sign in with an administrator account.
4. In the left navigation pane, click:

```text
Identity
```

5. Click:

```text
Monitoring & health
```

6. Click:

```text
Sign in logs
```

7. Filter the logs for the affected user.
8. Review recent sign ins.
9. Document:

```text
IP addresses
Locations
Result type
Device details
Client application
Time of sign in
```

### Explanation

This step gives the analyst direct visibility into how the account was used and whether the sign in pattern appears normal or suspicious.

## Step 2: Review Risk Alerts

### Purpose

This step checks whether Microsoft has already detected the sign in as risky.

### Instructions

1. In the Microsoft Entra admin center, click:

```text
Protection
```

2. Click:

```text
Identity Protection
```

3. Open:

```text
Risky sign ins
```

4. Search for the affected user.
5. Review the alert details.
6. Record:

```text
Risk level
Risk reason
Location
IP address
Sign in status
```

### Explanation

Microsoft may have already classified the sign in as risky based on threat intelligence, impossible travel, malware linked IPs, token misuse, or other signals.

## Step 3: Verify User Activity

### Purpose

This step determines whether the suspicious activity was performed by the real user.

### Instructions

1. Contact the user through an approved communication method.
2. Ask whether they performed the sign in.
3. Ask where they were located.
4. Ask which device they used.
5. Ask which applications they accessed.
6. Document the response.
7. If the user denies the activity, treat the event as probable compromise.

### Explanation

User verification is often one of the fastest ways to confirm whether the login was legitimate.

## Step 4: Reset the User Password

### Purpose

This step removes access if stolen credentials were used.

### Instructions

1. In the Microsoft Entra admin center, click:

```text
Users
```

2. Open the affected user account.
3. Click:

```text
Reset password
```

4. Generate a temporary password.
5. Require password change at next sign in.
6. Save the change.

### Explanation

A password reset removes one of the main ways an attacker can continue to access the account.

## Step 5: Revoke Active Sessions

### Purpose

This step ends all current authentication sessions.

### Instructions

1. Stay inside the affected user account.
2. Find the option for:

```text
Revoke sessions
```

3. Click:

```text
Revoke sessions
```

4. Confirm the action.

### Explanation

This forces reauthentication and invalidates active tokens that may still be in use by an attacker.

## Step 6: Require Multi Factor Authentication

### Purpose

This step strengthens the account against reused or stolen passwords.

### Instructions

1. Review whether Multi Factor Authentication is enabled for the account.
2. If needed, go to the policy area in Microsoft Entra.
3. Confirm that the user is included in an MFA requirement.
4. If necessary, require the user to re register MFA methods.

### Explanation

MFA adds an extra layer of protection and helps prevent attackers from signing in even if they know the password.

## Step 7: Block Suspicious IP Addresses if Applicable

### Purpose

This step prevents further sign in attempts from known malicious sources.

### Instructions

1. Review the suspicious IP addresses identified in sign in logs.
2. Determine whether they should be blocked through approved security controls.
3. If internal process allows, update Conditional Access or location based controls to block the IP or region.
4. Document the action taken.

### Explanation

Blocking a malicious source can reduce repeated attack attempts while the investigation continues.

## Step 8: Review Login History and Follow On Activity

### Purpose

This step determines whether the attacker did anything after signing in.

### Instructions

1. Return to the sign in logs.
2. Review login history before and after the suspicious event.
3. Look for unusual patterns such as:

```text
Repeated sign ins
Multiple locations
Unusual devices
Unexpected application access
```

4. Review cloud activity if available.
5. Document findings.

### Explanation

Compromise is not only about the initial login. This step checks whether the attacker used the account for anything else.

## Step 9: Monitor the Account

### Purpose

This step confirms that the compromise has been contained.

### Instructions

1. Continue reviewing sign in logs for the account.
2. Watch for repeated suspicious activity.
3. Confirm that new sign ins come only from expected locations and devices.
4. Record whether the account remains stable.

### Explanation

Monitoring confirms whether the actions taken were successful and whether the attacker tries again.

## Step 10: Provide User Awareness Guidance

### Purpose

This step helps prevent repeat compromise.

### Instructions

1. Explain to the user what suspicious activity was observed.
2. Remind the user not to approve unexpected MFA prompts.
3. Advise the user to report suspicious emails or login prompts quickly.
4. Document that awareness guidance was provided if required.

### Explanation

Users are part of the security process. Awareness reduces the likelihood of repeated phishing or MFA fatigue success.

## Resolution

The suspected identity compromise was investigated, suspicious sign in activity was reviewed, the user’s credentials and sessions were reset, account protections were strengthened, and the account was monitored to confirm secure access was restored.
