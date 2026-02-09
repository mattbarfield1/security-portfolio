# Asset Inventory

| Asset Name | Asset Type | Data Sensitivity | Business Impact if Compromised |
| :--- | :--- | :--- | :--- |
| **User PII** (Email, Name) | Data | Confidential | High: Identity theft risk and loss of user trust. |
| **User PHI** (Weight, Recovery) | Data | Confidential | High: Severe reputational damage and privacy violation. |
| **Firebase Auth Database** | Service | Confidential | Critical: Mass account takeover and total system breach. |
| **Cloud Functions (API)** | System | Internal | High: Attacker could manipulate logic or intercept data. |
| **GCP IAM Roles** | System | Internal | Critical: Unauthorized control of cloud infrastructure. |
| **Security Logs** | Data | Internal | Medium: Loss of visibility into ongoing attacks. |

### Asset Significance
* **User PII/PHI:** These represent our primary legal liability and the core data we are tasked with protecting. We treat recovery metrics as PHI due to their sensitive nature.
* **Firebase Auth:** This is the gatekeeper; a compromise here bypasses all other frontend security layers.
* **Cloud Functions:** This acts as the secure bridge for all data moving between the user and the database.
* **GCP IAM:** Defines the administrative permissions for our entire cloud presence.
* **Security Logs:** Essential for detecting breaches, monitoring system health, and performing forensic investigations.
