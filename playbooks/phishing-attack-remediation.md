# Phishing Attack Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Identity Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Investigate a suspected phishing attack, determine whether the user account was exposed, remove malicious email related changes, and secure the environment against additional compromise.

---

## Overview

A phishing attack attempts to trick a user into revealing credentials, approving access, or interacting with malicious content. In Microsoft 365 environments, phishing incidents can lead to account compromise, suspicious sign in activity, mailbox rule abuse, and unauthorized email forwarding.

This playbook explains how to review the suspicious message, examine account activity, inspect mailbox rules, contain the incident, and complete follow up actions.

---

## Detection

Phishing incidents may be detected through:

1. User reports
2. Suspicious login alerts
3. Email security alerts
4. Defender alerts
5. Reports of unexpected MFA prompts
6. Unusual mailbox behavior

---

## Investigation Procedure

## Step 1: Review the Suspicious Email Message

### Purpose

This step determines whether the email contains signs of phishing and helps identify the scope of the threat.

### Instructions

1. Open a web browser.
2. Go to the Microsoft 365 Defender portal.

```text
https://security.microsoft.com
```

3. Sign in with an authorized administrator or security analyst account.
4. In the left navigation pane, open **Email & collaboration** if visible in your tenant.
5. Open **Explorer** or **Threat Explorer**.
6. Search for the suspicious email using known details such as:
   1. Sender address
   2. Recipient address
   3. Subject line
   4. Message time
7. Open the suspicious email record.
8. Review the sender domain.
9. Review whether the sender appears spoofed or misleading.
10. Review any embedded links.
11. Review any attachments.
12. Document the findings.

### Explanation

This step helps determine whether the message was likely malicious and whether it was delivered to one user or multiple users.

---

## Step 2: Review Authentication Activity

### Purpose

This step checks whether the phishing message led to suspicious sign in activity.

### Instructions

1. Open the Microsoft Entra admin center.

```text
https://entra.microsoft.com
```

2. Sign in with an administrator account.
3. In the left navigation pane, click **Identity**.
4. Click **Monitoring & health**.
5. Click **Sign in logs**.
6. Search for the affected user account.
7. Set the time range to cover the reported phishing incident.
8. Review sign in attempts for:
   1. Unfamiliar locations
   2. Unfamiliar IP addresses
   3. Unknown devices
   4. Successful sign ins after suspicious email delivery
9. Document suspicious results.

### Explanation

If the user entered credentials into a phishing page, suspicious authentication activity may appear soon after the message was received.

---

## Step 3: Review Mailbox Rules

### Purpose

This step identifies whether the attacker created malicious rules to hide messages or forward mail externally.

### Instructions

1. Open the Microsoft 365 admin center or Exchange admin center depending on administrative workflow.
2. Locate the affected mailbox.
3. Open mailbox settings or mailbox management options.
4. Review inbox rules.
5. Look for suspicious rules such as:
   1. Automatic forwarding to external addresses
   2. Rules that delete incoming messages
   3. Rules that move messages to hidden folders
   4. Rules based on finance, invoices, password resets, or security alerts
6. Remove any malicious or unauthorized rules.
7. Document what was found and removed.

### Explanation

Attackers often create mailbox rules after compromise to maintain visibility or hide evidence from the user.

---

## Containment Actions

## Step 4: Reset User Credentials

### Purpose

This step removes the attacker's ability to continue using stolen credentials.

### Instructions

1. In Microsoft Entra admin center, click **Identity**.
2. Click **Users**.
3. Search for the affected user.
4. Open the user account.
5. Click **Reset password**.
6. Generate a temporary password.
7. Require the user to change the password at the next sign in.
8. Record the action according to internal procedure.

### Explanation

If the phishing attack captured the user's password, resetting the password is one of the most important containment steps.

---

## Step 5: Revoke Active Sessions

### Purpose

This step ends any current sessions that may already be active.

### Instructions

1. Open the affected user account.
2. Locate the session management area.
3. Click **Revoke sessions**.
4. Confirm the action.

### Explanation

If the attacker already signed in, they may have active sessions or tokens. Revoking sessions forces fresh authentication.

---

## Step 6: Remove Malicious Mailbox Rules

### Purpose

This step removes attacker persistence and hidden email manipulation.

### Instructions

1. Return to the mailbox settings or Exchange administrative interface.
2. Review all mailbox rules one more time.
3. Remove any malicious or suspicious rules.
4. Save the mailbox configuration.

### Explanation

Removing malicious mailbox rules prevents continued forwarding, hiding, or deletion of messages.

---

## Step 7: Block Malicious Sender Domains

### Purpose

This step reduces the chance of additional phishing messages from the same source.

### Instructions

1. Open the Microsoft 365 Defender portal.
2. Locate the area for email protection policy management based on tenant configuration.
3. Add the malicious sender or domain to the appropriate blocked list if approved by internal policy.
4. Save the changes.

### Explanation

Blocking malicious senders helps reduce repeat phishing attempts against other users in the organization.

---

## Post Incident Actions

## Step 8: User Phishing Awareness Follow Up

### Purpose

This step reduces future risk by helping the user recognize phishing attempts.

### Instructions

1. Notify the affected user of the confirmed or suspected phishing incident.
2. Explain what indicators made the message suspicious.
3. Reinforce how to report suspicious emails in the future.
4. Document completion of the user follow up if required by policy.

### Explanation

User awareness is an important part of reducing repeat phishing success.

---

## Step 9: Review Email Filtering Rules

### Purpose

This step helps strengthen the organization's overall protection.

### Instructions

1. Review email filtering and anti phishing policies in Microsoft 365 Defender.
2. Check whether similar messages were delivered to other users.
3. Update rules, policies, or indicators as approved by internal security process.
4. Document any protective changes.

### Explanation

A phishing incident involving one user may indicate that other users were also targeted. Reviewing filtering rules helps improve protection across the organization.

---

## Resolution

The phishing attack was investigated by reviewing the suspicious email, examining sign in activity, checking mailbox rules, resetting credentials, revoking sessions, removing unauthorized mailbox changes, blocking malicious senders, and completing post incident awareness and filtering review.
