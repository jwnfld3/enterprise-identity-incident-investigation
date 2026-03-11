# Identity Compromise Response Playbook

This playbook outlines the investigation and remediation procedures for suspected user account compromise within Microsoft Entra ID.

---

## Detection

Identity compromise may be detected through:

Sign-in risk alerts  
Impossible travel alerts  
User reported suspicious activity  
Unusual login activity  

---

## Investigation Procedure

### Step 1 – Review Sign-In Logs

1. Open Microsoft Entra Admin Center
2. Navigate to Identity
3. Select Monitoring and Health
4. Open Sign-in Logs
5. Filter logs for the affected user

---

### Step 2 – Review Risk Alerts

1. Navigate to Identity Protection
2. Select Risky Sign-ins
3. Review alerts associated with the user

---

### Step 3 – Verify User Activity

1. Contact the user directly
2. Confirm whether the login activity was legitimate

---

## Containment Actions

Reset the user password  
Revoke active sessions  
Require Multi-Factor Authentication  
Block suspicious IP addresses  

---

## Post Incident Actions

Review login history  
Monitor account activity  
Provide user awareness training
