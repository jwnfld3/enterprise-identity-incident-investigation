# OneDrive Data Exfiltration Log

This log represents file synchronization activity investigated for potential data exfiltration.

Attackers sometimes attempt to download large amounts of data from cloud storage services after gaining access to an account.

---

## File Sync Activity

| Timestamp (UTC) | User | Application | Data Transferred | Result |
|-----------------|------|-------------|------------------|--------|
| 2026-03-22 14:02 | jsmith@company.com | OneDrive | 25 MB | Success |
| 2026-03-22 14:05 | jsmith@company.com | OneDrive | 340 MB | Success |
| 2026-03-22 14:07 | jsmith@company.com | OneDrive | 1.2 GB | Success |

---

## Observations

File synchronization volume increased significantly compared to the user's normal activity baseline.

Large data transfers occurred shortly after a suspicious login alert.

---

## Security Controls Triggered

Unusual file activity alert

Security monitoring alert

Data exfiltration investigation initiated
