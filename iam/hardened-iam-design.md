# Hardened IAM Design (Least Privilege)

## Overview
This document outlines the redesigned IAM policy for the GCP/Firebase environment. These roles have been restricted to follow the Principle of Least Privilege (PoLP), ensuring that users and services only have the minimum permissions necessary to perform their functions.

## Hardened Role Definitions

| Role | Access Level | Permissions Included |
| :--- | :--- | :--- |
| **Admin** | IAM & Security Admin | Manage IAM policies, logs, and security settings. No access to database content. |
| **Developer** | App Engine/Functions Developer | Can deploy code to Cloud Functions. No access to production data. |
| **Support** | Firestore Read-Only | Read-only access to specific non-sensitive collections. No PII/PHI access. |

## Security Improvements & Risk Mitigation

### 1. Implementation of Least Privilege
* **Fix:** The Support role is now restricted to read-only access for non-sensitive data.
* **Impact:** This reduces the risk of internal data leaks of sensitive health metrics.

### 2. Separation of Duties
* **Fix:** Admins are restricted from viewing application data, and Developers cannot access production data.
* **Impact:** Prevents a single account compromise from leading to a total system breach.

### 3. Mandatory Security Controls
* **Fix:** Multi-Factor Authentication (MFA) is now required for all administrative roles.
* **Fix:** Strict password policies have been enforced across the organization.
* **Impact:** Adds a critical layer of defense against credential theft and unauthorized access.

## Risk Reduction Summary
This redesign ties directly into our threat model by closing the "Elevation of Privilege" gap. By restricting the Admin and Developer roles, we have ensured that even a compromised account has limited impact on the production environment.
