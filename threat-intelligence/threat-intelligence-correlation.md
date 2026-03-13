# Threat Intelligence Correlation

## Overview

Threat intelligence correlation is the process of comparing known threat indicators against security logs in order to identify potential malicious activity within an environment.

Threat intelligence indicators may include:

- malicious IP addresses
- suspicious domains
- phishing URLs
- known malware file hashes

Security platforms such as Microsoft Sentinel ingest threat intelligence from internal and external sources. These indicators are then correlated with authentication logs, cloud activity logs, and other security telemetry to identify potential matches.

When a match occurs between a threat indicator and a log event, security alerts can be generated to notify analysts of possible malicious activity.

## Evidence Source

Threat intelligence correlation relies on combining multiple security data sources, including:

- Microsoft Entra ID Sign-in Logs
- Microsoft 365 Activity Logs
- Microsoft Sentinel Log Analytics data
- External threat intelligence feeds
- Known malicious IP and domain indicator lists

These sources provide the context necessary to identify suspicious activity associated with known attacker infrastructure.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Sentinel portal.
2. Navigated to **Microsoft Sentinel**.
3. Selected the appropriate **Log Analytics Workspace**.
4. Opened the **Logs** query editor.
5. Selected relevant log tables such as **SigninLogs** or **OfficeActivity**.
6. Queried threat intelligence tables such as **ThreatIntelIndicators**.
7. Correlated authentication or activity logs with known threat indicators.
8. Reviewed query results for matching indicators such as IP addresses or domains.
9. Investigated matching events to determine whether malicious activity occurred.
10. Documented findings and preserved investigation results.

## Example Correlation Query

The following query identifies authentication events originating from IP addresses that appear in threat intelligence indicator lists.

```kusto
SigninLogs
| join kind=inner ThreatIntelIndicators
on $left.IPAddress == $right.NetworkIP
| project TimeGenerated, UserPrincipalName, IPAddress, ThreatType
```

This query correlates login activity with known malicious IP addresses recorded in threat intelligence feeds.

## Investigation Use Cases

Threat intelligence correlation is commonly used to detect:

- credential attacks originating from known malicious IP addresses
- phishing campaigns associated with known domains
- command and control infrastructure communication
- compromised accounts accessing services from attacker infrastructure

Correlating threat intelligence with log activity helps security analysts quickly identify high confidence indicators of compromise.

## Documentation Sources

Microsoft Sentinel Threat Intelligence Overview  
https://learn.microsoft.com/en-us/azure/sentinel/understand-threat-intelligence

Microsoft Sentinel Threat Intelligence Integration  
https://learn.microsoft.com/en-us/azure/sentinel/threat-intelligence-integration

Use Threat Indicators in Microsoft Sentinel Analytics Rules  
https://learn.microsoft.com/en-us/azure/sentinel/use-threat-indicators-in-analytics-rules
