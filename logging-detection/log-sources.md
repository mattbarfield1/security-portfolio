# Security Logging Sources

This document identifies the critical log sources required to monitor the application environment. These logs provide the visibility necessary for threat detection and forensic investigation.

## Log Source Inventory

| Log Source | Component | Data Captured | Security Relevance |
| :--- | :--- | :--- | :--- |
| **Authentication Logs** | Firebase Auth | Success/fail, MFA status, account changes. | Shows brute force and account takeover attempts. |
| **API Request Logs** | Cloud Functions | Headers, timestamps, source IP, status codes. | Identifies API probing and DoS attempts. |
| **IAM Audit Logs** | GCP Cloud Audit | Role changes, permission updates, policy edits. | Monitors for unauthorized privilege escalation. |
| **Payment Event Logs** | Stripe Webhooks | Charge status, refund requests, metadata. | Identifies financial fraud or payment tampering. |
| **Database Access Logs** | Firestore | Read/Write operations on PII/PHI collections. | Detects unauthorized data access or tampering. |

## Strategy & Relevance
* **Behavioral Insight:** These logs show exactly who is doing what within the system, allowing us to differentiate between normal user behavior and attacker activity.
* **Incident Support:** In the event of a breach, these logs provide the audit trail needed to determine the scope of the impact and the root cause.
* **Compliance:** Maintaining these logs ensures we meet standard security requirements for monitoring access to sensitive PII and health data.
