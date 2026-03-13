# Privileged Role Assignment Activity Log

## Overview

This log documents a privileged role assignment event detected within Microsoft Entra ID.

Attackers who compromise user accounts may attempt to escalate privileges by assigning administrative roles. Monitoring role assignment events helps security teams detect unauthorized privilege escalation attempts.

These events were collected as evidence during the investigation of suspicious administrative activity.

## Evidence Source

Role assignment events were collected from Microsoft Entra ID audit logs.

| Timestamp (UTC) | Actor | Operation | Role Assigned | Target Account |
|-----------------|-------|-----------|---------------|---------------|
| 2026-03-15 12:11 | awalker@company.com | Add member to role | Global Administrator | tempadmin@company.com |

This activity shows a privileged role assignment that may require investigation to confirm legitimacy.

## Click-by-Click Learning Process

1. Signed in to the Microsoft Entra Admin Center.
2. Navigated to Identity.
3. Selected Roles and Administrators.
4. Opened Audit Logs.
5. Filtered results for role assignment events.
6. Identified the account performing the role assignment.
7. Reviewed the role granted during the operation.
8. Verified the target account receiving privileges.
9. Determined whether the assignment was authorized.
10. Documented the activity and preserved the log as evidence.

## Related Case File

Case 002 Identity Compromise Investigation  
https://github.com/jwnfld3/enterprise-identity-incident-investigation/blob/main/case-files/case-002-identity-compromise.md

## Documentation Sources

Microsoft Entra ID Role Management  
https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/

Microsoft Entra Audit Logs  
https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs
