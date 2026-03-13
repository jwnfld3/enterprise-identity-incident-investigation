# Token Theft Authentication Log

## Overview

This log documents suspicious authentication sessions potentially associated with stolen authentication tokens.

Token theft allows attackers to maintain session access without repeatedly authenticating.

## Evidence Source

Session activity was obtained from Microsoft Entra ID authentication logs.

| Timestamp | Username | IP Address | Application | Result |
|-----------|----------|------------|-------------|--------|
| 2026-03-14 10:05 | awalker@company.com | 173.88.44.19 | Microsoft Teams | Success |

## Click-by-Click Learning Process

1. Opened Microsoft Entra Admin Center.
2. Navigated to Sign-in Logs.
3. Identified active authentication sessions.
4. Reviewed device information.
5. Reviewed IP address information.
6. Identified abnormal session activity.
7. Documented authentication session data.

## Related Case File

Case 006 Token Theft Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-006-token-theft.md

## Documentation Sources

Microsoft Entra Identity Protection  
https://learn.microsoft.com/en-us/entra/id-protection/
