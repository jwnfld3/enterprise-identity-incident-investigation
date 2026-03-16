# Incident Report: Suspicious Authentication Activity

## Case Metadata

Incident ID: IR-001  
Category: Identity Security Incident  
Severity: High  
Status: Resolved  

Detection Source: Microsoft Entra ID Sign-in Monitoring  
Reported By: Automated Security Alert  

Investigation Start Time: 2026-03-10 09:10 UTC  
Investigation End Time: 2026-03-10 10:05 UTC  

Affected User: jsmith@company.com  
Affected System: Microsoft 365  

---

## Incident Summary

Suspicious authentication attempts were detected targeting a user account within the Microsoft 365 environment.

Authentication attempts originated from a foreign IP address that had not previously been associated with the user. Multiple failed login attempts were recorded before Conditional Access policies blocked further attempts.

Security monitoring systems flagged the activity due to abnormal login patterns and geographic location anomalies.

---

## Detection

The incident was detected through Microsoft Entra ID sign-in monitoring alerts.

Indicators included:

- Multiple failed login attempts
- Authentication attempts from a foreign IP address
- Login attempts originating from an unusual geographic location

---

## Investigation

Security analysts followed a structured investigation process to determine whether the activity represented malicious behavior.

---

### Step 1 – Review Microsoft Entra ID Sign-in Logs

1. Open the Azure Portal  
   https://portal.azure.com

2. Navigate to **Microsoft Entra ID**

3. Select **Monitoring & Health**

4. Click **Sign-in Logs**

5. In the search filters:

   - Enter the affected user account
   - Adjust the time range to match the incident timeframe
   - Review the **Client IP Address**
   - Review the **Location**
   - Review the **Authentication Result**

6. Identify abnormal login indicators such as:

   - unfamiliar IP addresses
   - foreign geographic locations
   - repeated authentication failures
   - abnormal login times

---

### Step 2 – Investigate Security Alerts in Microsoft Sentinel

1. Open **Microsoft Sentinel** in the Azure Portal.

2. Select **Incidents**.

3. Locate the alert associated with the suspicious authentication activity.

4. Click the incident to view:

   - alert details
   - associated entities
   - triggered analytics rules
   - investigation graph

5. Review related alerts connected to the user account.

---

### Step 3 – Query Authentication Logs Using Kusto Query Language (KQL)

1. In **Microsoft Sentinel**, select **Logs**.

2. Run a query against authentication events.

Example query:

```kusto
SigninLogs
| where UserPrincipalName == "jsmith@company.com"
| project TimeGenerated, IPAddress, Location, AppDisplayName, ResultType
| order by TimeGenerated desc
```

3. Review results for:

   - login location anomalies
   - authentication failures
   - unusual application access

---

### Step 4 – Review Cloud Activity Logs

1. In **Microsoft Sentinel Logs**, query Microsoft 365 activity.

Example query:

```kusto
OfficeActivity
| where UserId == "jsmith@company.com"
| project TimeGenerated, Operation, ClientIP
| order by TimeGenerated desc
```

2. Identify abnormal actions such as:

   - mass file downloads
   - mailbox access
   - SharePoint document access
   - OneDrive activity

---

### Step 5 – Validate IP Address Reputation

Investigators validated suspicious IP addresses using threat intelligence sources.

- https://www.abuseipdb.com
- https://otx.alienvault.com
- https://www.microsoft.com/en-us/security/business/security-intelligence

Indicators reviewed include:

- malicious reputation score
- previous attack reports
- geographic origin
- known threat actor infrastructure

---

### Step 6 – Confirm User Activity

Security investigators contacted the affected user to verify whether the login activity was legitimate.

User confirmation helps determine whether authentication activity represents:

- legitimate user behavior
- compromised credentials
- automated attack activity

---

### Step 7 – Evaluate Security Controls

Security analysts reviewed identity protection controls including:

- Multi Factor Authentication
- Conditional Access Policies
- Account Lockout Policies
- Identity Protection Risk Alerts

This step determines whether existing security controls successfully prevented unauthorized access.

---

## Recommended Incident Structure

Each incident report in the repository should follow the same investigation structure.

Incident Summary  
Detection  
Timeline  
Investigation  
Indicators of Compromise  
Remediation  
MITRE ATT&CK Mapping  
Lessons Learned  
Documentation

Maintaining a consistent structure across all incidents makes the repository easier to read and mirrors real Security Operations Center documentation practices.

---

## Documentation

The investigation techniques and procedures documented in this repository were developed through review of publicly available cybersecurity documentation.

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
