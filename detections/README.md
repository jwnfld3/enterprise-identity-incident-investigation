# Detection Rules Library

This directory contains detection rules used to identify identity based security threats within Microsoft cloud environments.

The detection logic is written using Kusto Query Language (KQL) and is designed to identify authentication anomalies and suspicious activity within Microsoft Entra ID sign in logs.

## Detection Coverage

The following attack techniques are covered:

| Detection | Description |
|----------|-------------|
| Password Spray | Detects repeated login attempts across multiple accounts |
| Impossible Travel | Detects authentication attempts from distant geographic locations |
| MFA Fatigue | Detects repeated MFA push requests |
| Phishing Login | Detects authentication attempts following phishing activity |
| Token Theft | Detects suspicious authentication tokens |
| Data Exfiltration | Detects abnormal file access or downloads |

These detections simulate monitoring capabilities commonly implemented within Security Operations Centers using Microsoft Sentinel.
