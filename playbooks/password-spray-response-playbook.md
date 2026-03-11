# Password Spray Attack Response Playbook

This playbook describes the investigation process for password spray attacks targeting enterprise accounts.

---

## Detection

Password spray attacks may be detected through:

Multiple failed logins across several accounts  
Repeated login attempts from a single IP address  
Account lockout alerts  

---

## Investigation Procedure

### Step 1 – Review Authentication Logs

1. Open Microsoft Entra Admin Center
2. Navigate to Sign-in Logs
3. Identify multiple failed login attempts

---

### Step 2 – Identify Targeted Accounts

Review which accounts were targeted.

---

### Step 3 – Identify Source IP Address

Determine whether login attempts originated from the same source.

---

## Containment Actions

Block malicious IP address  
Reset targeted user passwords  
Enable Multi-Factor Authentication  

---

## Post Incident Actions

Review password policy  
Increase login monitoring
