# Threat Model (STRIDE)

This analysis identifies potential threats to the application based on the architectural design and the data assets.

| Threat Category | Potential Attack | Mitigation Strategy |
| :--- | :--- | :--- |
| **S**poofing | Attacker pretends to be a valid user to access PHI. | Implementing Firebase Auth with multi-factor authentication (MFA). |
| **T**ampering | Unauthorized modification of recovery metrics in Firestore. | Firestore Security Rules that validate user UID before allowing 'write' operations. |
| **R**epudiation | A user denies making a specific payment or changing data. | Enabling GCP Cloud Logging to maintain an immutable audit trail of all API calls. |
| **I**nformation Disclosure | Sensitive PHI/PII leaked via insecure API responses. | Cloud Functions configured to return only necessary data fields; data encrypted at rest in Firestore. |
| **D**enial of Service | Flooding the Cloud Functions to crash the app or spike costs. | Implementing Firebase App Check and setting usage quotas/rate limiting on API endpoints. |
| **E**levation of Privilege | A standard user gains admin access to the GCP Console. | Strict Principle of Least Privilege (PoLP) using GCP IAM roles; no broad 'Editor' permissions. |

## Critical Attack Surface: The API Bridge
The most critical point of failure in this architecture is the link between **Firebase Hosting** and **Cloud Functions**. Because this is where authentication is verified, any logic flaw here could expose the entire **Firestore** database.

### Mitigation Summary
1. **Scope Reduction:** By using **Stripe**, we eliminate the "T" (Tampering) and "I" (Information Disclosure) risks associated with credit card data.
2. **Identity-First Security:** All data requests are challenged by Firebase Auth before the API executes any business logic.
3. **Environment Isolation:** The Squarespace marketing site has zero connectivity to the database, ensuring a breach of the CMS does not lead to a breach of PHI.
