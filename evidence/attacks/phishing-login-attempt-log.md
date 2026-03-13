# Phishing Login Authentication Log

## Overview

This log captures authentication activity associated with a phishing credential theft scenario.

Attackers often obtain user credentials through phishing emails and then attempt to authenticate to enterprise services.

## Evidence Source

Authentication events were collected from Microsoft Entra ID Sign-in Logs.

| Timestamp | Username | Source IP | Location | Result |
|-----------|----------|-----------|----------|--------|
| 2026-03-13 14:22 | jsmith@company.com | 202.44.12.19 | Singapore | Success |

## Click-by-Click Learning Process

1. Opened Microsoft Defender Portal.
2. Navigated to Threat Explorer.
3. Identified phishing email event.
4. Checked user interaction with the email.
5. Reviewed authentication activity.
6. Identified suspicious login event.
7. Documented login details.

## Related Case File

Case 005 Phishing Login Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-005-phishing-login.md

## Documentation Sources

Microsoft Defender for Office 365  
https://learn.microsoft.com/en-us/defender-office-365/
