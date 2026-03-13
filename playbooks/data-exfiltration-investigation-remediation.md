# Data Exfiltration Investigation Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Data Exfiltration  
**Severity:** Critical  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Identify, contain, and remediate suspected data exfiltration involving Microsoft 365 cloud services such as SharePoint Online and OneDrive.

## Overview

This playbook is used when file activity suggests that a user account may be downloading, copying, syncing, or sharing data in a suspicious manner. The goal is to determine what data was accessed, whether the activity was authorized, whether the account may be compromised, and what actions are required to contain the threat.

## Who

This procedure is typically performed by:

1. Security Operations Center analysts
2. Incident responders
3. Microsoft 365 security administrators
4. Compliance administrators
5. Identity administrators

## What

This procedure is used to:

1. Identify suspicious file activity
2. Determine whether files were accessed, downloaded, synced, or shared
3. Confirm whether the user authorized the activity
4. Contain access if compromise is suspected
5. Preserve evidence and strengthen controls

## Where

This procedure is performed in:

1. Microsoft Purview portal
2. Microsoft 365 Compliance portal
3. Microsoft Entra admin center
4. SharePoint admin center

## When

Use this playbook when:

1. Large file downloads are detected
2. Unusual OneDrive or SharePoint access appears in audit logs
3. Sensitive data may have been exposed
4. A compromised user account is suspected
5. External sharing appears unauthorized

## Why

This is important because data exfiltration can lead to data loss, regulatory issues, privacy exposure, and business damage. Quick action helps protect files, accounts, and systems.

## Step 1: Identify the Affected User and Activity

### Purpose

This step identifies which user performed the suspicious activity and what file actions occurred.

### Instructions

1. Open a web browser.
2. Go to the Microsoft Purview portal.

```text
https://purview.microsoft.com
```

3. Sign in with an administrator account.
4. In the left navigation pane, click:

```text
Audit
```

5. Open:

```text
Audit Search
```

6. Set the date and time range covering the suspicious activity.
7. In the activities filter, search for file related actions such as:

```text
File downloaded
File accessed
File synced
File copied
Sharing action
```

8. In the users filter, enter the suspected user account.
9. Click:

```text
Search
```

10. Review the results for unusual file volume, repeated downloads, or abnormal timing.

### Explanation

This step identifies the suspicious file activity and ties it to a specific user account. It gives the analyst an initial picture of what happened and when.

## Step 2: Review SharePoint and OneDrive Activity

### Purpose

This step identifies where the activity occurred and what files were involved.

### Instructions

1. In the audit results, determine whether the activity occurred in:

```text
SharePoint Online
OneDrive
```

2. Review and document:

```text
File names
File paths
Timestamps
Number of files accessed
Download actions
Sync actions
Sharing actions
```

3. Look for suspicious patterns such as:

```text
Mass downloads
Large transfer volume
After hours access
Access from unusual locations
Repeated sync behavior
```

### Explanation

Attackers often access many files quickly after gaining access to an account. Reviewing the exact file activity helps determine whether the behavior looks normal or suspicious.

## Step 3: Review Sign In Activity

### Purpose

This step determines whether suspicious login activity happened before the file activity.

### Instructions

1. Open a new browser tab.
2. Go to the Microsoft Entra admin center.

```text
https://entra.microsoft.com
```

3. Sign in if prompted.
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

7. Filter for the affected user.
8. Review sign ins that occurred immediately before and during the suspicious file activity.
9. Document:

```text
IP addresses
Locations
Device details
Client application
Sign in result
```

10. Determine whether the file activity followed a suspicious sign in.

### Explanation

If a risky sign in happened immediately before a file download spike, that is a strong sign the account may have been compromised.

## Step 4: Confirm Whether the Activity Was Authorized

### Purpose

This step verifies whether the user actually performed the file actions.

### Instructions

1. Contact the user using an approved communication method.
2. Ask whether they intentionally:

```text
Accessed the files
Downloaded the files
Synced the files
Shared the files
```

3. Ask what device they were using.
4. Ask where they were located.
5. Document the user’s response.
6. If the user denies the activity, treat the event as a possible compromise.

### Explanation

This step helps distinguish normal business work from malicious activity performed through a stolen account.

## Step 5: Revoke Access Sessions

### Purpose

This step forces all active sessions to end so a possible attacker loses current access.

### Instructions

1. In the Microsoft Entra admin center, click:

```text
Users
```

2. Select the affected user account.
3. Locate the option for:

```text
Revoke sessions
```

4. Click:

```text
Revoke sessions
```

5. Confirm the action.

### Explanation

This invalidates active authentication tokens and forces the account to sign in again. It is a fast containment step when compromise is suspected.

## Step 6: Reset the User Password

### Purpose

This step prevents continued use of stolen credentials.

### Instructions

1. Stay inside the affected user account.
2. Click:

```text
Reset password
```

3. Generate a temporary password.
4. Enable the option requiring password change at next sign in.
5. Save the change according to internal policy.

### Explanation

If the attacker knows the current password, resetting it removes that access path.

## Step 7: Require MFA Re Registration

### Purpose

This step protects the account if an attacker may have interfered with authentication methods.

### Instructions

1. Open the affected user account.
2. Go to the section for:

```text
Authentication methods
```

3. Select:

```text
Require re register MFA
```

4. Confirm the action.

### Explanation

This forces the legitimate user to register authentication methods again, which helps if an attacker added or influenced MFA settings.

## Step 8: Review External Sharing

### Purpose

This step determines whether data was shared outside the organization.

### Instructions

1. Open the SharePoint admin center.
2. Review the affected SharePoint site or OneDrive location.
3. Check whether files were:

```text
Shared externally
Linked publicly
Granted anonymous access
```

4. Remove unauthorized sharing links.
5. Remove unauthorized external permissions.
6. Document the actions taken.

### Explanation

Data exfiltration does not always involve downloading files. It can also involve sharing them externally through links or permissions.

## Step 9: Restrict Further Access if Needed

### Purpose

This step blocks the account from signing in if the risk remains high.

### Instructions

1. Return to the Microsoft Entra admin center.
2. Open the affected user account.
3. Locate the control for:

```text
Block sign in
```

4. Enable the block if required by internal procedure.
5. Save the change.
6. Re enable the account only after the investigation confirms safe conditions.

### Explanation

This is a stronger containment action when there is high confidence of compromise or ongoing risk.

## Step 10: Review Conditional Access Policies

### Purpose

This step checks whether security controls were strong enough and whether gaps need correction.

### Instructions

1. In the Microsoft Entra admin center, click:

```text
Protection
```

2. Click:

```text
Conditional Access
```

3. Review policies affecting the user or the application involved.
4. Confirm that controls are in place for:

```text
Multi Factor Authentication
Location restrictions
Compliant devices
Blocking legacy authentication
```

5. Update policies if approved and necessary.

### Explanation

Strong Conditional Access controls reduce the chance that stolen credentials can be used successfully.

## Step 11: Review Data Loss Prevention and Sensitivity Controls

### Purpose

This step checks whether the organization’s data protection controls were applied properly.

### Instructions

1. Return to the Microsoft Purview portal.
2. Click:

```text
Data Loss Prevention
```

3. Review whether DLP policies covered the affected files or locations.
4. Determine whether:

```text
Sensitivity labels were applied
DLP alerts were generated
Policy gaps existed
```

5. Update or recommend updates to protection policies if approved.

### Explanation

If sensitive data was not protected by policy, this step helps identify control gaps that contributed to the incident.

## Step 12: Preserve Investigation Evidence

### Purpose

This step ensures the evidence is available for review, escalation, and reporting.

### Instructions

1. Export or securely document:

```text
Audit log entries
Sign in logs
File access history
Sharing settings
User verification notes
```

2. Save the evidence in the approved case file or repository.
3. Ensure timestamps and account details are preserved accurately.

### Explanation

Evidence preservation is important for incident reporting, legal review, internal escalation, and later lessons learned.

## Step 13: Continue Monitoring

### Purpose

This step confirms that the suspicious behavior has stopped.

### Instructions

1. Return to Audit Search and sign in logs.
2. Re run the same searches used earlier.
3. Watch for:

```text
Further mass downloads
New unauthorized shares
Repeated suspicious sign ins
More abnormal access patterns
```

4. Document whether the activity has stopped.

### Explanation

Attackers may try again after containment. Continued monitoring helps confirm the account and data are secure.

## Resolution

The suspected data exfiltration activity was investigated, the affected account was secured, active sessions were revoked, password and authentication controls were reset, sharing settings were reviewed, and policy protections were validated to reduce future risk.

### Documentation Sources

Microsoft 365 Audit Log Search  
https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-search

Microsoft Defender for Cloud Apps Investigation  
https://learn.microsoft.com/en-us/defender-cloud-apps/investigate-activities

Microsoft Data Loss Prevention Documentation  
https://learn.microsoft.com/en-us/microsoft-365/compliance/dlp-learn-about-dlp
