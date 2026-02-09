# Detection Logic & Alerting Rules

This document defines the logic used to identify suspicious activity across the application environment. These rules are designed to trigger alerts for high-risk behaviors identified in the STRIDE threat model.

## 1. Authentication: Brute Force / Credential Stuffing
* **Rule:** Multiple failed login attempts (5+) for a single account within a 60-second window.
* **Logic:** Filter `auth_logs` where `status == 'FAIL'` and `source_ip` is identical.
* **False Positive Potential:** Users forgetting passwords or automated testing scripts in dev environments.
* **Security Significance:** High probability of an automated account takeover attempt.

## 2. IAM: Privilege Escalation Attempt
* **Rule:** An existing IAM user attempts to call `SetIamPolicy` or modify their own role permissions.
* **Logic:** Monitor `cloud_audit_logs` for `methodName: "SetIamPolicy"` where the actor is not a known Security Admin.
* **False Positive Potential:** Authorized testing of IAM configurations by the security team.
* **Security Significance:** Critical; indicates an attacker is attempting to gain "Owner" level access to the cloud environment.

## 3. Database: Unauthorized PHI Export
* **Rule:** Mass read operation (>100 records) on the 'User_Health_Metrics' collection within 5 minutes.
* **Logic:** Aggregate `firestore_access_logs` by `userId` and count `document_read` events.
* **False Positive Potential:** Administrative data backup or authorized medical research reporting.
* **Security Significance:** Potential data exfiltration or a "scraped" database breach.

## 4. API: Geographically Impossible Access
* **Rule:** Two successful logins for the same user ID from IP addresses located in different countries within 1 hour.
* **Logic:** Compare `geographic_location` metadata in consecutive `auth_success` logs for a single UID.
* **False Positive Potential:** Users switching between a local network and a VPN.
* **Security Significance:** Strong indicator of compromised credentials being used by a remote attacker.
