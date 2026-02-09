# Incident Response Plan (IRP)

This document outlines the framework for responding to security incidents involving the application environment. The goal is to ensure a coordinated response that minimizes impact on user data (PII/PHI) and restores services quickly.

## 1. Roles and Responsibilities
* **Incident Commander:** Primary lead for the technical response and decision-making.
* **Security Analyst:** Responsible for investigating logs, performing forensics, and executing containment.
* **Communications Lead:** Manages internal stakeholder updates and external messaging if data breach notification is required.
* **Legal/Compliance:** Evaluates the impact on PHI/PII and ensures the response meets regulatory requirements.

## 2. Incident Severity Levels
| Severity | Definition | Example Scenario |
| :--- | :--- | :--- |
| **Level 1 (Critical)** | Total system outage or confirmed data breach involving PHI. | Massive database export; Ransomware. |
| **Level 2 (High)** | Targeted attack or partial service compromise. | Unauthorized Admin account created in GCP. |
| **Level 3 (Medium)** | Suspicious activity with no confirmed breach. | Multiple failed logins from a single IP. |
| **Level 4 (Low)** | Minor policy violation or non-critical system bug. | User misconfiguration or accidental data share. |

## 3. Escalation Paths
* **Detection:** Incident is identified via automated detection rules or user reports.
* **Triaging:** The Security Analyst verifies the threat and assigns a severity level.
* **Escalation:** If Level 1 or 2, the Incident Commander and Legal are notified immediately.
* **Notification:** External parties (users, regulators) are notified only after the threat is contained and the impact is confirmed.

## 4. Response Lifecycle
1. **Preparation:** Maintain logging, backups, and updated contact lists.
2. **Identification:** Confirm the incident through log analysis (Step 6/7).
3. **Containment:** Disable compromised accounts or rotate leaked API keys.
4. **Eradication:** Remove the root cause and patch vulnerabilities.
5. **Recovery:** Restore services from backups and monitor for recurrence.
6. **Lessons Learned:** Document the root cause and update defenses to prevent a repeat.
