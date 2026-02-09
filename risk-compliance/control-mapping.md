# Security Control Mapping (NIST CSF)

This document maps the security controls implemented in this project to the NIST Cybersecurity Framework (CSF) v2.0. This ensures our security posture aligns with industry-recognized best practices.

## NIST CSF Mapping Table

| Function | Category | Control Implementation | Evidence (File Link) |
| :--- | :--- | :--- | :--- |
| **IDENTIFY** | Asset Management | Maintained a full inventory of data and systems. | `/architecture/asset-inventory.md` |
| **IDENTIFY** | Risk Assessment | Conducted STRIDE threat modeling and risk registration. | `/threat-modeling/threat-model.md` |
| **PROTECT** | Identity Management | Implemented Least Privilege and MFA for all roles. | `/iam/hardened-iam-design.md` |
| **PROTECT** | Data Security | Enforced AES-256 encryption at rest and TLS in transit. | `/architecture/security-controls.md` |
| **DETECT** | Monitoring | Configured logs for Auth, API, and IAM activity. | `/logging-detection/log-sources.md` |
| **DETECT** | Detection | Created logic for brute force and geo-impossible logins. | `/logging-detection/detection-rules.md` |
| **RESPOND** | Response Planning | Defined roles and severity levels for incidents. | `/incident-response/incident-response-plan.md` |
| **RECOVER** | Recovery Planning | Established root cause analysis and backup restoration. | `/incident-response/incident-report.md` |

## Framework Alignment Summary
By mapping our internal controls to the NIST CSF, we demonstrate that this security program is not just a collection of tools, but a structured approach to managing risk. 

* **Governance:** All controls are documented and reviewed against the Risk Register.
* **Traceability:** Every technical setting in the GCP console can be traced back to a specific framework requirement.
* **Continuous Improvement:** Post-incident activities (Step 9) feed directly back into the "Identify" and "Protect" functions.
