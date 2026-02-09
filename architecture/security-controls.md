# Security Controls & Mitigations

This document details the specific technical and administrative controls implemented to protect the FitTrack Pro environment. These controls were selected to address the risks identified during the STRIDE threat modeling process.

## 1. Network & Infrastructure Security
* **Transport Layer Security (TLS):** All data in transit between the client and Firebase/GCP is encrypted using TLS 1.2 or higher.
* **API Protection:** Firebase App Check is utilized to verify that incoming requests originate from the legitimate web application, mitigating unauthorized API access and bot traffic.
* **Environment Isolation:** Separate projects are used for development and production to prevent configuration errors from impacting live user data.

## 2. Data Protection & Encryption
* **Encryption at Rest:** All data stored in Firestore and Cloud Storage is automatically encrypted using AES-256.
* **Secrets Management:** Sensitive keys and service account credentials are stored in Google Secret Manager or as environment variables, never hardcoded in source code.
* **Data Minimization:** Only necessary recovery metrics and PII are collected to reduce the impact of a potential breach.

## 3. Identity & Access Management (IAM)
* **Least Privilege:** Roles are scoped to the minimum permissions required (e.g., Firestore Read-Only for support staff).
* **Multi-Factor Authentication (MFA):** Mandatory for all accounts with administrative access to the GCP Console.
* **Audit Logging:** Admin activity and permission changes are logged via Cloud Audit Logs for accountability.

## 4. Application-Level Controls
* **Firestore Security Rules:** Server-side validation ensures users can only read or write to documents where `request.auth.uid == resource.data.userId`.
* **Input Validation:** All data sent to Cloud Functions is sanitized to prevent injection attacks.
* **Session Management:** Handled via Firebase Authentication with secure, short-lived JWT tokens.

## Control Summary Table

| Control Category | Implementation | Mitigation Target |
| :--- | :--- | :--- |
| **Confidentiality** | Encryption at Rest/Transit | Information Disclosure |
| **Integrity** | Firestore Security Rules | Tampering / Unauthorized Edits |
| **Availability** | Billing Alerts & Rate Limiting | Denial of Service (DoS) |
