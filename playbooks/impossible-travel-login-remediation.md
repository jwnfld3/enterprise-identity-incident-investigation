# Impossible Travel Login Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Identity Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Investigate and remediate sign in events where a user appears to authenticate from two geographically distant locations within an unrealistic timeframe.

## Overview

This playbook is used when sign in data suggests that a user signed in from two locations that are too far apart to be legitimate within the time available. The goal is to determine whether one of the sign ins was malicious, confirm the user’s real activity, and secure the account if compromise is suspected.

## Who

This procedure is typically performed by:

1. Security Operations Center analysts
2. Identity administrators
3. Incident responders

## What

This procedure is used to:

1. Review impossible travel alerts or risky sign ins
2. Compare sign in events across locations
3. Verify the user’s actual activity
4. Reset access if compromise is suspected
5. Strengthen protections and monitor the account

## Where

This procedure is performed in:

1. Microsoft Entra admin center
2. Microsoft Entra Identity Protection
3. Sign in logs
4. Conditional Access policy area

## When

Use this playbook when:

1. An impossible travel alert is generated
2. Sign in logs show unrealistic geographic movement
3. Risky sign in alerts involve multiple distant locations
4. The user reports suspicious access

## Why

Impossible travel can indicate that one of the sign ins came from an attacker using stolen credentials or stolen session access. Quick review helps determine whether the sign in was legitimate or malicious.

## Step 1: Review the Risk Alert

### Purpose

This step identifies the alert and the affected account.

### Instructions

1. Open a web browser.
2. Go to the Microsoft Entra admin center.

```text
https://entra.microsoft.com
```

3. Sign in with an administrator account.
4. If available in your tenant, navigate to:

```text
Protection
Identity Protection
```

5. Open the relevant impossible travel alert or risky sign in event.
6. Record the affected user and timestamps.

### Explanation

The alert is the starting point for the investigation. It identifies which account is involved and the time window that must be reviewed.

## Step 2: Review Sign In Logs

### Purpose

This step compares the actual sign in events behind the alert.

### Instructions

1. In the Microsoft Entra admin center, click:

```text
Identity
```

2. Click:

```text
Monitoring & health
```

3. Click:

```text
Sign in logs
```

4. Filter for the affected user.
5. Review the sequence of successful sign ins.
6. Compare the following details across the sign ins:

```text
Timestamps
IP addresses
Locations
Device details
Client application
```

### Explanation

This step helps determine whether the sign ins really happened close together and whether the locations are truly inconsistent with normal travel.

## Step 3: Compare Known Activity

### Purpose

This step identifies which sign in is more likely to be legitimate.

### Instructions

1. Review the user’s usual sign in history if available.
2. Compare the suspicious sign ins to the user’s known patterns.
3. Identify which sign in appears consistent with:

```text
Normal device
Normal region
Normal application use
Expected business hours
```

4. Document the differences between the two sign ins.

### Explanation

One of the sign ins may match the user’s normal behavior while the other does not. This helps the analyst decide which event is more likely to be malicious.

## Step 4: Verify User Activity

### Purpose

This step confirms whether the user traveled or actually performed the sign in.

### Instructions

1. Contact the user using an approved communication method.
2. Ask whether they traveled during the time window.
3. Ask what device they used.
4. Ask where they were located.
5. Ask whether they signed in to the application involved.
6. Document the response.

### Explanation

If the user confirms they did not travel and did not perform the sign in, the suspicious event becomes much more likely to be malicious.

## Step 5: Reset the Password if Suspicious

### Purpose

This step removes access if compromise is suspected.

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

A password reset is a standard containment action when account compromise is suspected.

## Step 6: Revoke Sessions

### Purpose

This step invalidates active sessions and tokens.

### Instructions

1. Stay inside the affected user account.
2. Locate the option for:

```text
Revoke sessions
```

3. Click:

```text
Revoke sessions
```

4. Confirm the action.

### Explanation

Even after a password reset, active sessions may remain valid. Revoking sessions ensures the attacker is forced out.

## Step 7: Review MFA and Conditional Access

### Purpose

This step checks whether security controls are strong enough to prevent similar incidents.

### Instructions

1. In the Microsoft Entra admin center, click:

```text
Protection
```

2. Click:

```text
Conditional Access
```

3. Review policies affecting the user or sign in scenario.
4. Confirm that the environment enforces:

```text
Multi Factor Authentication
Risk based controls
Blocking legacy authentication
Location based restrictions where appropriate
```

5. Update protections if approved by internal process.

### Explanation

This step helps prevent future compromise by improving sign in controls.

## Step 8: Monitor the Account

### Purpose

This step confirms that suspicious sign ins do not continue.

### Instructions

1. Return to sign in logs.
2. Continue reviewing the account after remediation.
3. Confirm that future sign ins come only from expected locations and devices.
4. Record whether any repeated suspicious activity appears.

### Explanation

Monitoring is necessary because attackers may retry from another IP address or location.

## Resolution

The impossible travel event was investigated, the affected user’s activity was verified, suspicious access was contained as needed, and account protections were reviewed to reduce the risk of unauthorized access.

### Documentation Sources

Microsoft Identity Protection Risk Events  
https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-risks

Microsoft Impossible Travel Detection  
https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy
