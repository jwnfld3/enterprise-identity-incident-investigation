# Incident Report: MFA Fatigue Attack

## Case Metadata

Incident ID: IR-002  
Category: Identity Security Incident  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Entra ID Sign-in Monitoring  
Reported By: User Security Alert  

Investigation Start Time: 2026-03-12 09:40 UTC  
Investigation End Time: 2026-03-12 10:20 UTC  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

A suspected Multi Factor Authentication (MFA) fatigue attack was identified targeting a Microsoft 365 user account.

The user reported receiving multiple unexpected authentication prompts on their mobile device within a short time period. Security monitoring confirmed repeated login attempts originating from a foreign IP address.

MFA prompts were repeatedly sent to the user in an attempt to trick the user into approving the authentication request.

---

## Detection

The incident was detected through a combination of user reporting and automated authentication monitoring.

Indicators included:

- Multiple MFA push notifications sent within a short time period  
- Login attempts originating from an unfamiliar geographic location  
- Repeated authentication failures followed by MFA challenges  

---

## Investigation

Security analysts performed a structured investigation to determine whether the repeated MFA prompts were the result of a malicious authentication attempt.

---

### Step 1 – Review Microsoft Entra ID Sign-in Logs

Evidence Source: Microsoft Entra ID Sign-in Logs

1. Open the Azure Portal  
https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign-in Logs**

5. In the filters panel:

- Enter the affected user account `jsmith@company.com`
- Adjust the **Time Range** to the incident timeframe
- Review the **Client IP Address**
- Review the **Location**
- Review the **Authentication Requirement**

6. Investigators observed:

- repeated authentication attempts  
- authentication originating from a foreign IP address  
- multiple MFA challenges triggered  

These indicators suggested automated authentication attempts targeting the user account.

---

### Step 2 – Review Conditional Access Evaluation

1. Within the **Sign-in Logs** entry, select the suspicious authentication attempt.

2. Open the **Conditional Access** tab.

3. Review policy evaluation results including:

- MFA requirement enforcement  
- device compliance status  
- sign-in risk level  

The evaluation confirmed that MFA was correctly required for the authentication attempt.

---

### Step 3 – Query Authentication Logs Using KQL

1. In **Microsoft Sentinel**, select **Logs**.

2. Run the following query to identify repeated authentication attempts.

```kql
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| summarize AttemptCount = count() by IPAddress, Location, bin(TimeGenerated, 10m)
| order by AttemptCount desc
```

Query results confirmed multiple authentication attempts originating from the same external IP address within a short timeframe.

This pattern is consistent with MFA fatigue attack behavior.

---

### Step 4 – Validate IP Address Reputation

Investigators analyzed the source IP address using threat intelligence platforms.

Sources reviewed included:

- https://www.abuseipdb.com
- https://otx.alienvault.com
- https://www.microsoft.com/en-us/security/business/security-intelligence

The IP address had previously been associated with suspicious authentication activity.

---

### Step 5 – Confirm User Activity

Security investigators contacted the affected user to verify whether the authentication prompts were legitimate.

The user confirmed:

- they did not initiate any login attempts
- they did not approve any MFA prompts
- the prompts were unexpected

This confirmation verified that the authentication attempts were unauthorized.

---

### Step 6 – Evaluate Security Controls

Security analysts verified that identity protection controls were functioning correctly.

Controls reviewed included:

- Multi Factor Authentication enforcement
- Conditional Access policies
- account sign-in risk monitoring
- identity protection alerts

Because the user did not approve any MFA requests, the attacker was unable to gain access to the account.

---

### Step 7 – Determine Incident Impact

Investigators confirmed that:

- no successful login occurred
- no cloud resources were accessed
- no mailbox or file activity occurred

The attack attempt was unsuccessful due to MFA enforcement and user awareness.

---

## Conclusion

The investigation determined that the repeated authentication prompts were part of a Multi Factor Authentication fatigue attack targeting the user account.

The attacker attempted to trigger repeated MFA challenges in an effort to trick the user into approving an authentication request. However, the user did not approve any prompts and promptly reported the suspicious activity.

Because MFA was properly enforced and the user did not authorize the login attempt, the attacker was unable to gain access to the Microsoft 365 environment. The security controls in place effectively prevented unauthorized account access.

Continued monitoring and user awareness remain critical components of defending against identity-based attacks.

---

## Documentation

The investigation techniques and remediation procedures documented in this report were developed through review of publicly available cybersecurity documentation and vendor guidance.

- **Microsoft Sentinel Documentation**  
https://learn.microsoft.com/en-us/azure/sentinel/

- **Microsoft Entra ID Sign-in Logs Documentation**  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins

- **Kusto Query Language Documentation**  
https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/

- **Microsoft Entra Conditional Access Documentation**  
https://learn.microsoft.com/en-us/entra/identity/conditional-access/

- **Microsoft Defender Security Documentation**  
https://learn.microsoft.com/en-us/defender/

- **MITRE ATT&CK Framework**  
https://attack.mitre.org/
