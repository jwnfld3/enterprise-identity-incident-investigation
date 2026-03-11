# Conditional Access Policy Block Remediation

**Playbook Type:** Security Control Remediation  
**Threat Category:** Access Control Enforcement  
**Severity:** Medium  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Review and validate a Conditional Access block event, determine whether the block was expected, and ensure secure access is maintained.

---

## Step 1 – Review the Blocked Sign-In

1. Sign in to the **Microsoft Entra admin center**.
2. Select **Identity**.
3. Select **Monitoring & health**.
4. Click **Sign-in logs**.
5. Filter for the affected user.
6. Locate the sign-in event showing **Failure** or **Blocked**.
7. Open the event.

---

## Step 2 – Review Conditional Access Details

1. Inside the sign-in event, locate the **Conditional Access** tab or section.
2. Review:
   - policy name
   - grant controls
   - session controls
   - result
   - failure reason
3. Document which policy caused the block.

---

## Step 3 – Review Device and Location Details

1. In the same sign-in event, review:
   - device state
   - browser
   - operating system
   - IP address
   - geographic location
2. Determine whether the sign-in came from:
   - an unmanaged device
   - an untrusted location
   - a risky session

---

## Step 4 – Verify User Intent

1. Contact the affected user.
2. Confirm whether the user attempted the sign-in.
3. Confirm the device and location used.
4. Document whether the block was expected or suspicious.

---

## Step 5 – Review Device Compliance if Applicable

1. Open **Microsoft Intune admin center** if device compliance is part of the policy.
2. Search for the user’s device.
3. Review compliance status.
4. Confirm whether the device is:
   - enrolled
   - compliant
   - correctly assigned to policy

---

## Step 6 – Adjust Policy Only if Necessary

1. Return to **Microsoft Entra admin center**.
2. Navigate to **Protection**.
3. Click **Conditional Access**.
4. Open the blocking policy.
5. Review:
   - included users
   - excluded users
   - cloud apps
   - conditions
   - grant controls
6. Make changes only if the policy is blocking legitimate business activity incorrectly.
7. Save the updated policy if changes are approved.

---

## Step 7 – Retest Access

1. Ask the user to attempt sign-in again using a compliant device or approved method.
2. Confirm whether access is now successful.
3. Verify that the policy behaves as intended.

---

## Resolution

The blocked sign-in was reviewed, the policy behavior was validated, and secure access requirements were confirmed.
