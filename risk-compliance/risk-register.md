# Security Risk Register

This register identifies and tracks security risks associated with the application. It provides a structured way to prioritize mitigation efforts based on the likelihood of occurrence and the business impact.

## Risk Rating Matrix
* **Critical:** High Likelihood + High Impact (Immediate Action Required)
* **High:** High Likelihood or High Impact (Priority Mitigation)
* **Medium:** Moderate Likelihood and Impact (Planned Mitigation)
* **Low:** Low Likelihood and Impact (Monitor/Accept)

## Current Risk Inventory

| Risk ID | Asset | Threat | Likelihood | Impact | Rating | Mitigation Strategy |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **RR-001** | User PII/PHI | Data Breach via SQLi or Injection | Medium | High | **High** | Input validation and Firestore Security Rules. |
| **RR-002** | Cloud Console | Admin Account Takeover (ATO) | Low | Critical | **High** | Hardened IAM and mandatory hardware MFA. |
| **RR-003** | API Service | Resource Exhaustion (DoS) | High | Medium | **High** | API Rate limiting and Billing Alerts. |
| **RR-004** | Backup Data | Unauthorized access to backups | Low | High | **Medium** | Encryption at rest and restricted access logs. |
| **RR-005** | Internal Team | Phishing/Social Engineering | High | Medium | **Medium** | Security Awareness Training and Phishing Sims. |

## Risk Treatment Plan
* **Mitigated:** Risks where technical controls (IAM, Logging, Detection) have been implemented to reduce the rating.
* **Transferred:** Risks like Payment Data handling which are moved to third parties (Stripe).
* **Accepted:** Low-level risks where the cost of mitigation exceeds the potential impact.

## Conclusion
This register is a living document. As new threats are identified in our STRIDE model or through incident reports, they are added here to ensure visibility and accountability.
