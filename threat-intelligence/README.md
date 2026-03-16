# Threat Intelligence and Detection Queries

This directory contains threat intelligence analysis and security detection queries used to support the investigation scenarios documented in this repository.

The files in this directory demonstrate how security analysts correlate threat intelligence with authentication logs and security alerts to identify suspicious activity and potential security incidents.

These resources simulate the analytical processes used by Security Operations Center analysts when identifying indicators of compromise and building detection logic within security monitoring platforms.

---

# Purpose

The purpose of this directory is to demonstrate how threat intelligence and detection queries support security investigations.

Security analysts commonly use threat intelligence and security analytics queries to:

• identify malicious IP addresses  
• detect abnormal authentication behavior  
• correlate known attacker techniques  
• investigate suspicious activity across systems  
• build detection rules for security monitoring platforms  

These processes help organizations detect and respond to identity based threats within enterprise environments.

---

# Threat Intelligence Resources

| Resource | Description |
|---|---|
| [Microsoft Sentinel KQL Detection Queries](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/threat-intelligence/sentinel-kql-detection-queries.md) | Example Kusto Query Language detection queries used in Microsoft Sentinel to identify suspicious authentication activity and identity based threats. |
| [Threat Intelligence Correlation](https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/threat-intelligence/threat-intelligence-correlation.md) | Demonstrates how threat intelligence indicators such as malicious IP addresses can be correlated with authentication logs during security investigations. |

---

# Detection Workflow

Threat intelligence and detection queries are typically used during the early stages of a security investigation.

The general workflow includes:

1. Alert Detection  
   Security monitoring systems identify suspicious activity using detection rules.

2. Threat Intelligence Correlation  
   Indicators such as IP addresses or domains are compared against known threat intelligence sources.

3. Log Analysis  
   Analysts review authentication logs and related activity to identify abnormal patterns.

4. Investigation  
   Analysts determine whether the activity represents malicious behavior.

5. Response  
   Security teams implement remediation procedures if a threat is confirmed.

---

# Technologies Referenced

These detection examples reference security monitoring and analysis tools commonly used in enterprise environments.

• Microsoft Sentinel  
• Kusto Query Language (KQL)  
• Microsoft Entra ID authentication logs  
• Threat intelligence correlation techniques  

---

# Navigation

## Return to Investigation Case Files
[Investigation Case Files](https://github.com/jwnfld3/enterprise-identity-incident-investigation/tree/main/case-files)

## Return to Evidence Repository
[Evidence Repository](https://github.com/jwnfld3/enterprise-identity-incident-investigation/tree/main/evidence)

## Return to Playbooks
[Incident Response Playbooks](https://github.com/jwnfld3/enterprise-identity-incident-investigation/tree/main/playbooks)
