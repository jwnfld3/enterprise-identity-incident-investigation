# Conditional Access Policy Block Remediation

**Playbook Type:** Security Control Remediation  
**Threat Category:** Access Control Enforcement  
**Severity:** Medium  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Review and validate a Conditional Access block event, determine whether the block was expected, and ensure secure access is maintained.

## Overview

This playbook is used when a user reports that sign in was blocked by a Conditional Access policy or when a security analyst notices a blocked sign in event in Microsoft Entra ID. The goal is to identify which policy caused the block, determine whether the block was correct, and verify that legitimate users can still access resources securely.

## Who

This procedure is typically performed by:

1. Security Operations Center analysts
2. Identity administrators
3. Microsoft 365 administrators
4. Help desk staff with identity support responsibilities

## What

This procedure is used to:

1. Review a blocked sign in event
2. Identify the Conditional Access policy that caused the block
3. Confirm whether the sign in was legitimate or suspicious
4. Check whether device compliance contributed to the block
5. Correct policy issues if legitimate business access was blocked incorrectly

## Where

This procedure is performed in:

1. Microsoft Entra admin center
2. Microsoft Intune admin center if device compliance is involved

## When

Use this playbook when:

1. A user reports that access was blocked
2. Sign in logs show a Conditional Access block
3. A policy appears to be preventing legitimate access
4. Security staff need to confirm that a block was working as intended

## Why

This is important because Conditional Access is a key security control. If the policy is working correctly, it prevents risky or unauthorized access. If the policy is misconfigured, it can interrupt legitimate business activity.

## Step 1: Review the Blocked Sign In

### Purpose

This step identifies the exact sign in event that was blocked and confirms the affected user.

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

7. Use the filters at the top of the page.
8. In the user filter, enter the affected user account.
9. Review the sign in results.
10. Locate the sign in event showing a failed or blocked result.
11. Click the event to open the details.

### Explanation

This step is important because the sign in event contains the full story of what happened. It shows the user, the application, the device, the location, and whether Conditional Access caused the block.

## Step 2: Review Conditional Access Details

### Purpose

This step identifies the exact policy that blocked access.

### Instructions

1. Inside the sign in event, find the section labeled:

```text
Conditional Access
```

2. Click the Conditional Access details.
3. Review the following information:

```text
Policy name
Result
Grant controls
Session controls
Failure reason
```

4. Record the name of the policy that caused the block.
5. Record whether the result shows success, failure, or report only evaluation.

### Explanation

This step tells the analyst exactly which policy was involved. Without this step, it is not possible to know whether the block came from a location rule, a device rule, an application rule, or another access condition.

## Step 3: Review Device and Location Details

### Purpose

This step helps determine why the policy was triggered.

### Instructions

1. Stay inside the same sign in event.
2. Review the device information.
3. Review the location information.
4. Document the following details:

```text
Device state
Browser
Operating system
IP address
Geographic location
Client application
```

5. Determine whether the sign in came from:

```text
An unmanaged device
An unknown device
An untrusted location
A risky session
A blocked client application
```

### Explanation

Conditional Access often blocks access because the device is not compliant, the login came from an unusual location, or the user did not meet a required control such as Multi Factor Authentication.

## Step 4: Verify User Intent

### Purpose

This step confirms whether the user actually attempted the sign in.

### Instructions

1. Contact the affected user using an approved communication method.
2. Ask the user whether they attempted the sign in.
3. Ask what device they used.
4. Ask where they were located during the sign in.
5. Ask which application they were trying to access.
6. Document the user’s responses.
7. Determine whether the blocked sign in was expected or suspicious.

### Explanation

This step helps separate legitimate access issues from possible malicious activity. If the user confirms the sign in, the issue may be a policy configuration problem. If the user denies the sign in, the event may indicate a security incident.

## Step 5: Review Device Compliance if Applicable

### Purpose

This step determines whether device compliance status caused the block.

### Instructions

1. Open a new browser tab.
2. Go to the Microsoft Intune admin center.

```text
https://intune.microsoft.com
```

3. Sign in with an administrator account if prompted.
4. Search for the user’s device.
5. Open the device record.
6. Review the compliance status.
7. Confirm whether the device is:

```text
Enrolled
Compliant
Correctly assigned to policy
```

8. Document the compliance findings.

### Explanation

Some Conditional Access policies require a compliant device before access is allowed. If the device is not enrolled or not compliant, the policy may correctly block access.

## Step 6: Adjust Policy Only if Necessary

### Purpose

This step corrects the policy only when legitimate business activity is being blocked incorrectly.

### Instructions

1. Return to the Microsoft Entra admin center.
2. In the left navigation pane, click:

```text
Protection
```

3. Click:

```text
Conditional Access
```

4. Click:

```text
Policies
```

5. Select the blocking policy identified earlier.
6. Review the following sections:

```text
Users
Target resources
Conditions
Grant controls
Session controls
Exclusions
```

7. Determine whether the policy configuration matches intended business and security requirements.
8. Make changes only if approved by internal process.
9. Save the updated policy if a change is necessary.

### Explanation

Policies should not be changed casually. If the block is protecting the environment correctly, the policy should remain in place. This step is only for correcting misconfiguration, not weakening security.

## Step 7: Retest Access

### Purpose

This step confirms whether the user can now sign in under correct and secure conditions.

### Instructions

1. Ask the user to attempt sign in again.
2. Ensure the user is using an approved method such as:

```text
Compliant device
Trusted location
Required Multi Factor Authentication
Supported client application
```

3. Return to the sign in logs.
4. Refresh the logs after the new attempt appears.
5. Confirm whether access was successful.
6. Confirm whether the policy behaved as intended.

### Explanation

Retesting proves whether the issue was resolved. It also confirms whether the Conditional Access policy is enforcing the correct security requirement without blocking legitimate work.

## Resolution

The blocked sign in was reviewed, the responsible Conditional Access policy was identified, the user’s sign in attempt was verified, and policy behavior was confirmed or corrected as needed to maintain secure access.
