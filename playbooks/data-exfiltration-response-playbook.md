# Data Exfiltration Investigation Playbook

This playbook outlines the investigation procedures for suspected data exfiltration from cloud services.

---

## Detection

Possible indicators include:

Large file downloads  
Unusual OneDrive synchronization  
Mass SharePoint file access  

---

## Investigation Procedure

### Step 1 – Review File Activity Logs

1. Open Microsoft 365 Compliance Center
2. Navigate to Audit Logs
3. Search for file download activity

---

### Step 2 – Identify Abnormal Activity

Look for unusual spikes in downloads.

---

### Step 3 – Verify User Intent

Contact the user to confirm activity.

---

## Containment Actions

Suspend account access if compromise suspected  
Block suspicious IP addresses  
Revoke authentication sessions  

---

## Post Incident Actions

Review Data Loss Prevention policies  
Increase monitoring for cloud activity
