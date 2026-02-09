# System Architecture & Security Design

## Component Overview
* **Squarespace (Marketing Site):** This is the external entry point. It contains no user data and simply links users to the secure web application.
* **Firebase Hosting (Web App):** This hosts the actual application interface where users interact with their recovery data.
* **Firebase Cloud Functions (API):** The backend logic layer. It acts as the secure gatekeeper, ensuring only authenticated requests reach the database.
* **Firestore (Database):** Centralized storage for sensitive user information, including PII and PHI (weight and recovery metrics).

## Security Design Decisions
* **Outsourced Payment Processing:** We use **Stripe** to handle all transactions. By doing this, sensitive credit card data never touches our environment, which significantly reduces our PCI-DSS compliance scope and risk.
* **Defined Security Boundaries:** The **GCP/Firebase Environment** shown in the diagram is our primary security boundary. We use Firebase Authentication and IAM roles to ensure that only authorized users and services can access internal data.
* **Data Privacy (PHI):** Because we handle sensitive health metrics like weight and recovery stats, we treat this data as PHI. The architecture is designed to isolate this sensitive data from the public-facing marketing site.

## Security Labels Map
* **Authentication:** Handled at the connection between the Web App and Cloud Functions.
* **PII/PHI Storage:** Located securely within the Firestore Database.
* **Payment Flow:** Data is securely handed off from our API directly to Stripe's infrastructure.
