# Threat Intelligence Correlation Procedure

**Process Type:** Threat Investigation  
**Threat Category:** Identity Attack  
**Severity:** High  
**Platform:** Microsoft Entra ID / Microsoft 365 / Microsoft Sentinel

---

## Overview

Threat intelligence correlation is the process of taking suspicious activity found in enterprise logs and comparing that activity against trusted threat intelligence sources. This helps determine whether the activity is likely normal, suspicious, or malicious.

This procedure explains how a Security Operations Center analyst can review authentication activity, extract indicators of compromise, compare those indicators against open source intelligence platforms, map the activity to MITRE ATT&CK techniques, and document investigation results.

---

## Who

This procedure is performed by:

1. Security Operations Center analysts
2. Security engineers
3. Incident responders
4. Identity security administrators
5. Threat intelligence analysts

---

## What

This procedure is used to:

1. Review suspicious login activity
2. Identify malicious IP addresses
3. Recognize password spraying behavior
4. Detect MFA fatigue activity
5. Investigate token theft indicators
6. Compare suspicious activity against open source threat intelligence
7. Determine whether the activity matches known attacker techniques

---

## Where

This procedure is performed in the following platforms:

1. Microsoft Azure Portal
2. Microsoft Sentinel
3. Microsoft Entra Admin Center
4. AbuseIPDB
5. AlienVault Open Threat Exchange
6. MITRE ATT&CK
7. CISA threat advisories
8. Microsoft Security Intelligence resources

---

## When

This procedure should be performed when any of the following occurs:

1. A suspicious sign in alert is generated
2. Multiple failed authentication attempts are observed
3. Login attempts appear from unfamiliar locations
4. MFA prompts are repeatedly triggered
5. Unusual cloud activity follows sign in activity
6. A possible account compromise is suspected

---

## Why

This procedure is important because it helps security teams:

1. Determine whether suspicious activity is part of a known attack pattern
2. Confirm whether an external IP address has been associated with malicious behavior
3. Understand attacker tactics and techniques
4. Improve investigation accuracy
5. Make better containment and remediation decisions

---

## Prerequisites

Before beginning this procedure, confirm that the following are available:

1. Access to the Azure portal
2. Access to Microsoft Sentinel
3. Access to Microsoft Entra sign in logs
4. Access to internet based threat intelligence resources
5. A suspicious IP address, user account, or authentication event to investigate

---

## Step 1: Sign in to the Azure Portal

### Purpose

This step opens the cloud security environment where authentication activity can be reviewed.

### Instructions

1. Open a web browser.
2. Navigate to the Azure portal.

```text
https://portal.azure.com
```

3. Enter administrator or analyst credentials.
4. Complete multi factor authentication if prompted.
5. Wait for the Azure portal home page to load.

### Explanation

The Azure portal is the main access point for Microsoft cloud security tools. Authentication logs, Microsoft Sentinel, and Microsoft Entra security data can all be accessed from this location.

---

## Step 2: Open Microsoft Sentinel

### Purpose

This step opens the SIEM platform used to review authentication logs and run investigation queries.

### Instructions

1. In the Azure portal search bar, type:

```text
Microsoft Sentinel
```

2. Select:

```text
Microsoft Sentinel
```

3. Choose the correct Sentinel workspace.
4. Wait for the workspace overview page to load.

### Explanation

Microsoft Sentinel stores and analyzes security telemetry. This is where log queries are used to find suspicious authentication behavior, cloud activity, and attacker patterns.

---

## Step 3: Open the Logs Query Window

### Purpose

This step opens the workspace where authentication events can be searched and filtered.

### Instructions

1. In the left navigation pane of Microsoft Sentinel, click:

```text
Logs
```

2. Wait for the Log Analytics query editor to open.
3. Confirm that the correct workspace is selected.

### Explanation

The Logs page is used to search tables such as `SigninLogs`, `AuditLogs`, `OfficeActivity`, and other Microsoft security data sources.

---

## Step 4: Review Sign In Logs for Suspicious Activity

### Purpose

This step identifies authentication events that may indicate malicious behavior.

### Instructions

1. In the query editor, enter the following query:

```kusto
SigninLogs
| order by TimeGenerated desc
```

2. Click:

```text
Run
```

3. Review recent sign in events.
4. Look for the following fields:

```text
UserPrincipalName
IPAddress
Location
ResultType
AppDisplayName
DeviceDetail
TimeGenerated
```

### Explanation

This query displays recent sign in activity. It is useful for getting a general view of who signed in, where the sign in came from, and whether the authentication attempt was successful or failed.

---

## Step 5: Identify Failed Authentication Attempts

### Purpose

This step narrows the investigation to failed login attempts, which are often associated with credential attacks.

### Instructions

1. In the query editor, replace the previous query with:

```kusto
SigninLogs
| where ResultType != 0
| order by TimeGenerated desc
```

2. Click:

```text
Run
```

3. Review failed authentication events.
4. Look for repeated failures from the same IP address.
5. Look for multiple accounts being targeted.

### Explanation

`ResultType != 0` filters the logs to only failed sign ins. This helps isolate patterns commonly seen in brute force attempts and password spray activity.

---

## Step 6: Identify Suspicious IP Addresses

### Purpose

This step identifies external IP addresses generating suspicious login activity.

### Instructions

1. In the query editor, enter:

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by IPAddress
| order by FailedAttempts desc
```

2. Click:

```text
Run
```

3. Review the IP addresses with the highest number of failed attempts.
4. Copy the suspicious IP address to a text file or investigation notes.

### Explanation

This query counts failed sign ins by IP address. IP addresses with unusually high failure counts may indicate automated attack activity or credential guessing behavior.

---

## Step 7: Identify Password Spray Behavior

### Purpose

This step checks whether one IP address is attempting logins against multiple user accounts.

### Instructions

1. In the query editor, enter:

```kusto
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count(), TargetedUsers = dcount(UserPrincipalName) by IPAddress, bin(TimeGenerated, 15m)
| where FailedAttempts >= 15 and TargetedUsers >= 5
| order by FailedAttempts desc
```

2. Click:

```text
Run
```

3. Review results showing one IP address targeting multiple users.
4. Record the suspicious IP address and number of targeted accounts.

### Explanation

Password spraying usually involves a small number of passwords being tried across many accounts. This query helps find that pattern by counting failures and unique user targets in short time windows.

---

## Step 8: Review Geographic Login Patterns

### Purpose

This step determines whether the sign in activity comes from unusual or distant locations.

### Instructions

1. In the query editor, enter:

```kusto
SigninLogs
| project TimeGenerated, UserPrincipalName, IPAddress, Location, ResultType
| order by TimeGenerated desc
```

2. Click:

```text
Run
```

3. Review the `Location` field for suspicious regions.
4. Compare locations against the organization’s normal login patterns.
5. Note any unfamiliar countries or impossible travel patterns.

### Explanation

Attackers often authenticate from hosting providers, anonymized networks, or foreign countries that do not match normal employee login behavior.

---

## Step 9: Check the Suspicious IP in AbuseIPDB

### Purpose

This step determines whether the IP address has been reported for malicious activity by other security teams.

### Instructions

1. Open a new browser tab.
2. Navigate to:

```text
https://www.abuseipdb.com
```

3. Paste the suspicious IP address into the search field.
4. Click:

```text
Check
```

5. Review the abuse confidence score.
6. Review abuse categories and reported activity.
7. Record findings in investigation notes.

### Explanation

AbuseIPDB is used to see whether the IP has already been observed performing attacks such as brute force activity, credential stuffing, scanning, or malware communication.

---

## Step 10: Check the Suspicious IP in AlienVault OTX

### Purpose

This step checks whether the IP has been associated with threat indicators shared by the security community.

### Instructions

1. Open a new browser tab.
2. Navigate to:

```text
https://otx.alienvault.com
```

3. Paste the suspicious IP address into the search field.
4. Press Enter.
5. Review pulse results, indicator details, and related threat information.
6. Record relevant findings.

### Explanation

AlienVault OTX provides community shared threat intelligence. If the IP appears in known pulses or indicator collections, that increases confidence that the activity is malicious.

---

## Step 11: Review MITRE ATT&CK for Technique Mapping

### Purpose

This step maps observed activity to known attacker techniques.

### Instructions

1. Open a new browser tab.
2. Navigate to:

```text
https://attack.mitre.org
```

3. In the search bar, search for:

```text
T1110.003
```

4. Review the password spraying technique page.
5. Search for:

```text
T1528
```

6. Review the token theft technique page.
7. Search for:

```text
T1566
```

8. Review the phishing technique page.
9. Search for:

```text
T1078
```

10. Review the valid accounts technique page.
11. Document which techniques match the observed activity.

### Explanation

MITRE ATT&CK helps analysts describe behavior using a common framework. This improves reporting, incident communication, and understanding of attacker methods.

---

## Step 12: Review CISA for Known Threat Activity

### Purpose

This step determines whether the observed behavior aligns with known public advisories and current attack trends.

### Instructions

1. Open a new browser tab.
2. Navigate to:

```text
https://www.cisa.gov
```

3. Search for terms such as:

```text
password spraying
MFA fatigue
credential attacks
identity attacks
```

4. Review advisories, alerts, and guidance related to the activity.
5. Record any matching patterns or recommendations.

### Explanation

CISA publishes guidance on active threats and common attack methods. Matching internal activity to public advisories can strengthen investigation conclusions.

---

## Step 13: Review Microsoft Security Intelligence Information

### Purpose

This step checks whether Microsoft has published intelligence relevant to the observed attack pattern.

### Instructions

1. Open a new browser tab.
2. Search for Microsoft security intelligence resources related to the observed activity.
3. Review Microsoft guidance on identity attacks, MFA fatigue, password spraying, and malicious infrastructure.
4. Document findings that support the investigation.

### Explanation

Microsoft has broad visibility into cloud based identity attacks. Their guidance often helps validate whether the pattern matches known attack behavior in Microsoft environments.

---

## Step 14: Review MFA Authentication Activity

### Purpose

This step identifies repeated MFA prompts that may indicate MFA fatigue.

### Instructions

1. Return to Microsoft Sentinel.
2. In the query editor, enter:

```kusto
SigninLogs
| where AuthenticationRequirement == "multiFactorAuthentication"
| order by TimeGenerated desc
```

3. Click:

```text
Run
```

4. Review repeated authentication attempts for the same user.
5. Note any high volume of prompts in a short period.
6. Record the user account, IP address, and time range.

### Explanation

Repeated MFA prompts may indicate that an attacker already has the correct password and is attempting to pressure the user into approving the sign in.

---

## Step 15: Review Token Theft Indicators

### Purpose

This step identifies authentication patterns that may indicate session abuse or token theft.

### Instructions

1. In the query editor, enter:

```kusto
AADNonInteractiveUserSignInLogs
| project TimeGenerated, UserPrincipalName, IPAddress, AppDisplayName, Location, ResultType
| order by TimeGenerated desc
```

2. Click:

```text
Run
```

3. Review non interactive sign in activity.
4. Look for unfamiliar locations or applications.
5. Compare this activity against suspicious sign ins from previous steps.

### Explanation

Non interactive sign ins can show activity where access occurs without a user typing a password. When paired with suspicious cloud activity, this may suggest token theft or session hijacking.

---

## Step 16: Review Cloud Activity for Follow On Behavior

### Purpose

This step determines whether suspicious authentication was followed by suspicious cloud actions.

### Instructions

1. In the query editor, enter:

```kusto
OfficeActivity
| order by TimeGenerated desc
```

2. Click:

```text
Run
```

3. Review cloud events related to file access, file downloads, or administrative actions.
4. Look for activity shortly after suspicious authentication events.
5. Record abnormal actions such as mass downloads or unusual access patterns.

### Explanation

Attackers often move from account access to data access. Reviewing cloud activity helps determine whether the suspicious sign in led to actual use of the compromised account.

---

## Step 17: Determine Whether the Activity Is Malicious

### Purpose

This step combines the collected evidence into an investigation conclusion.

### Instructions

1. Review the following collected evidence:

```text
Suspicious IP reputation
Failed authentication counts
Number of targeted user accounts
MFA prompt activity
Cloud activity
MITRE ATT&CK mapping
Threat intelligence findings
```

2. Compare all findings together.
3. Determine whether the activity is:

```text
Benign
Suspicious
Malicious
```

4. Record the decision and supporting evidence.

### Explanation

A single failed login is usually not enough to confirm an attack. Correlation means combining multiple indicators until the activity can be confidently categorized.

---

## Step 18: Document Correlation Results

### Purpose

This step creates the written investigation record.

### Instructions

1. Open the case notes or investigation document.
2. Record the following:

```text
Date and time of investigation
Affected account names
Suspicious IP addresses
Observed login patterns
Threat intelligence results
MITRE ATT&CK techniques
Cloud activity findings
Investigation conclusion
```

3. Save the document.

### Explanation

Good documentation ensures the investigation can be reviewed later, handed off to another analyst, or used in incident reports.

---

## Step 19: Initiate Defensive Actions

### Purpose

This step begins containment and hardening actions if malicious activity is confirmed.

### Instructions

1. Notify the security team of confirmed malicious activity.
2. Open Microsoft Entra Admin Center.
3. Review whether the suspicious account requires a password reset.
4. Revoke active sessions if account compromise is suspected.
5. Evaluate whether Conditional Access should block the source location.
6. Ensure multi factor authentication is enabled for affected accounts.
7. Open the relevant response playbook and begin incident remediation.

### Explanation

Threat intelligence correlation is not only for research. It directly supports containment and response decisions.

---

## Step 20: Continue Monitoring

### Purpose

This step confirms that the suspicious activity has stopped and no additional compromise is occurring.

### Instructions

1. Return to Microsoft Sentinel.
2. Re run the sign in queries used earlier.
3. Review whether the suspicious IP activity continues.
4. Review whether any new user accounts are targeted.
5. Continue monitoring for follow on behavior.

### Explanation

Monitoring after containment is important because attackers may retry with different IP addresses, different accounts, or different methods.

---

## MITRE ATT&CK Mapping

The following techniques may apply during threat intelligence correlation:

| Technique | Description |
|----------|-------------|
| T1110.003 | Password spraying across multiple accounts |
| T1078 | Use of valid accounts for unauthorized access |
| T1528 | Theft or abuse of application access tokens |
| T1566 | Phishing used to obtain credentials |

---

## Defensive Recommendations

Recommended security controls include:

1. Enforce multi factor authentication for all users
2. Restrict risky logins with Conditional Access
3. Configure alerts for password spray patterns
4. Block malicious IP addresses
5. Enable Microsoft Entra Identity Protection
6. Review sign in activity regularly
7. Investigate abnormal cloud activity quickly

---

## Conclusion

Threat intelligence correlation helps security teams determine whether suspicious activity is part of a known attack pattern. By reviewing sign in logs, identifying indicators of compromise, checking public intelligence sources, mapping activity to MITRE ATT&CK, and documenting findings, analysts can make accurate and defensible incident decisions.

This process is essential for detecting identity attacks, confirming malicious infrastructure, and supporting timely incident response in Microsoft enterprise environments.
