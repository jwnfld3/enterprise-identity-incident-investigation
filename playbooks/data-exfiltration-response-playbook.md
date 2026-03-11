# Data Exfiltration Investigation Remediation

**Playbook Type:** Incident Response  
**Threat Category:** Data Exfiltration  
**Severity:** Critical  
**Platform:** Microsoft Entra ID / Microsoft 365

## Objective

Identify, contain, and remediate suspected data exfiltration involving Microsoft 365 cloud services such as SharePoint Online and OneDrive.

---

## Step 1 – Identify the Affected User and Activity

1. Sign in to the **Microsoft Purview portal** or **Microsoft 365 Compliance portal**.
2. In the left navigation pane, select **Audit**.
3. Open **Audit Search**.
4. Set the date and time range covering the suspicious activity.
5. In the **Activities** filter, search for events related to:
   - file downloaded
   - file accessed
   - file synced
   - file copied
   - sharing action.
6. In the **Users** filter, enter the suspected user account.
7. Run the search.
8. Review the results for unusual file volume, repeated download activity, or abnormal timing.

---

## Step 2 – Review SharePoint and OneDrive Activity

1. In the audit results, identify whether the activity occurred in:
   - **SharePoint Online**
   - **OneDrive**
2. Document:
   - file names
   - file paths
   - timestamps
   - number of files accessed
   - download or sync actions.
3. Look for:
   - mass downloads
   - large file transfer volume
   - unusual access outside business hours
   - downloads from unfamiliar locations.

---

## Step 3 – Review Sign-In Activity

1. Sign in to the **Microsoft Entra admin center**.
2. Navigate to **Identity**.
3. Select **Monitoring & health**.
4. Click **Sign-in logs**.
5. Filter by the affected user.
6. Review the sign-ins occurring immediately before and during the suspicious data activity.
7. Document:
   - IP addresses
   - locations
   - device details
   - client application
   - sign-in status.
8. Determine whether the data activity followed a suspicious or risky sign-in.

---

## Step 4 – Confirm Whether the Activity Was Authorized

1. Contact the user using an approved communication method.
2. Confirm whether the user intentionally:
   - accessed the files
   - downloaded the files
   - synced the files
   - shared the files.
3. Document the user’s response.
4. If the user denies the activity, treat the event as a potential compromise.

---

## Step 5 – Revoke Access Sessions

1. In the **Microsoft Entra admin center**, go to **Users**.
2. Select the affected user account.
3. Locate the sign-in or session management controls.
4. Click **Revoke sessions**.
5. Confirm the action.

This invalidates active authentication tokens and forces reauthentication.

---

## Step 6 – Reset the User Password

1. While still in the affected user account, click **Reset password**.
2. Generate a temporary password.
3. Enable the option requiring the user to change the password at next sign-in.
4. Save the change according to internal procedures.

---

## Step 7 – Require MFA Re-Registration

1. Open the affected user account.
2. Navigate to **Authentication methods** if available in your tenant workflow.
3. Select **Require re-register MFA**.
4. Confirm the action.

---

## Step 8 – Review External Sharing

1. Go to the **SharePoint admin center**.
2. Review the affected SharePoint site or OneDrive location.
3. Check whether files were:
   - shared externally
   - linked publicly
   - granted anonymous access.
4. Remove unauthorized sharing links or external permissions.
5. Document the changes made.

---

## Step 9 – Restrict Further Access if Needed

1. In the **Microsoft Entra admin center**, evaluate whether the account should be temporarily blocked.
2. If required by internal procedure, set the user account to **Block sign-in**.
3. Confirm the action.
4. Re-enable the account only after the investigation confirms safe access conditions.

---

## Step 10 – Review Conditional Access Policies

1. Navigate to **Protection**.
2. Select **Conditional Access**.
3. Review policies affecting the user or workload.
4. Confirm that policies enforce:
   - Multi-Factor Authentication
   - location restrictions where appropriate
   - compliant device requirements
   - blocked legacy authentication.
5. Update policies if needed and approved.

---

## Step 11 – Review Data Loss Prevention and Sensitivity Controls

1. Open the **Microsoft Purview portal**.
2. Navigate to **Data Loss Prevention**.
3. Review whether relevant DLP policies were in place for the affected data.
4. Determine whether:
   - sensitive labels were applied
   - DLP alerts were generated
   - policy gaps contributed to the exposure.
5. Update protection policies if approved.

---

## Step 12 – Preserve Investigation Evidence

1. Export or securely document:
   - audit log entries
   - sign-in log details
   - file access history
   - sharing settings
   - user verification notes.
2. Store the evidence in the appropriate investigation repository or case file.

---

## Step 13 – Continue Monitoring

1. Return to **Audit Search** and **Sign-in Logs**.
2. Continue monitoring the user and related resources for additional suspicious activity.
3. Confirm that:
   - no further mass downloads occur
   - no new unauthorized shares appear
   - no repeated suspicious sign-ins are detected.

---

## Resolution

The suspected data exfiltration activity was investigated, the affected account was secured, active sessions were revoked, unauthorized access paths were reviewed, and additional policy controls were validated to reduce the risk of future data loss.
