# Initial IAM Design (Insecure)

## Overview
This document outlines the initial administrative roles for the GCP/Firebase environment. These roles are intentionally designed with overly broad permissions to highlight common security misconfigurations and the risks associated with excessive privilege.

## Role Definitions & Access Levels

| Role | Access Level | Permissions Included |
| :--- | :--- | :--- |
| **Admin** | Full Project Owner | Full access to all GCP resources, billing, and IAM settings. |
| **Developer** | Project Editor | Can view, create, and delete any resource, including production databases and functions. |
| **Support** | Project Viewer | Can view all data across the entire project, including sensitive PII/PHI in Firestore. |

## Security Flaws & Risks Identified

### 1. Lack of Least Privilege
* **Risk:** The "Developer" and "Support" roles have access far beyond what is required for their daily tasks.
* **Impact:** A support agent can view sensitive medical recovery metrics (PHI) that they have no business reason to see, leading to a massive privacy violation.

### 2. Excessive "Owner" Roles
* **Risk:** Multiple accounts with "Owner" permissions increases the attack surface.
* **Impact:** If one admin account is compromised via phishing, the attacker has total control to delete the infrastructure or ransom the database.

### 3. Broad Data Access
* **Risk:** No separation exists between development and production data.
* **Impact:** A developer could accidentally run a delete script against the production Firestore database instead of a test environment.

### 4. Missing Security Guardrails
* **Risk:** These roles currently have no requirement for Multi-Factor Authentication (MFA).
* **Impact:** Weak or reused passwords on any of these accounts could lead to an immediate account takeover.
