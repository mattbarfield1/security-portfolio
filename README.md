# FitTrack Pro Security Portfolio

**By Matthew Barfield** | [LinkedIn](https://www.linkedin.com/in/matthew-barfield-grc/) | mattbarfield1@gmail.com

[![ISC2 Certified in Cybersecurity](https://img.shields.io/badge/ISC2-Certified%20in%20Cybersecurity-blue)](https://www.isc2.org/Certifications/CC) [![NIST CSF](https://img.shields.io/badge/Framework-NIST%20CSF%20v2.0-green)](https://www.nist.gov/cyberframework) [![GRC Focus](https://img.shields.io/badge/Focus-Governance%20Risk%20Compliance-orange)]()

---
## About This Portfolio

This portfolio demonstrates end-to-end GRC capabilities through a fictional SaaS security program. The work showcases skills developed through 3+ years of fraud detection, incident investigation, and PCI-DSS compliance enforcement at Lifetime Fitness, combined with hands-on experience securing cloud applications. Each deliverable reflects real-world security operations translated into formal governance documentation.
**Key Focus Areas:** Risk assessment, compliance framework mapping (NIST CSF), incident response procedures, access control design, and security control documentation.

## Table of Contents
- [Fictional Company Overview](#fictional-company-overview)
- [Project Roadmap & Security Deliverables](#project-roadmap--security-deliverables)
- [Technical Skills Demonstrated](#technical-skills-demonstrated)
- [Connect With Me](#connect-with-me)

---

## Fictional Company Overview
FitTrack Pro is a web-based SaaS platform that allows users to track workouts, create programs, and subscribe to premium features. It serves individual users, with a focus on user privacy and secure payments.

- **Data Handled**: User PII (names, emails, fitness data like recovery metrics and goals), payment information (processed via Stripe, not stored locally), authentication credentials.
- **Technologies Used**: Google Cloud Platform (GCP) for hosting, Firebase/Firestore for authentication and database, Stripe for payments, web app built with modern frameworks (e.g., React for frontend, Node.js for API).
---

## Project Roadmap & Security Deliverables

This project is organized into modular phases, covering the full security lifecycle from identification to recovery.

### Phase 1: Planning & Architecture
* **Asset Inventory:** Defined the system boundaries and identified critical data assets. [View File](/architecture/asset-inventory.md)
* **Threat Modeling:** Conducted a STRIDE analysis to identify potential attack vectors. [View File](/threat-modeling/threat-model.md)

### Phase 2: Technical Hardening
* **Identity & Access Management:** Redesigned IAM roles to enforce the Principle of Least Privilege (PoLP). [View File](/iam/hardened-iam-design.md)
* **Infrastructure Security:** Documented the baseline security controls for the cloud environment. [View File](/architecture/security-controls.md)

### Phase 3: Detection & Response
* **Logging Strategy:** Identified critical log sources for monitoring and forensics. [View File](/logging-detection/log-sources.md)
* **Detection Logic:** Authored plain-English rules for alerting on suspicious behavior. [View File](/logging-detection/detection-rules.md)
* **Incident Response Plan:** Defined the SOP for handling and escalating security breaches. [View File](/incident-response/incident-response-plan.md)
* **Fictional Post-Mortem:** Analyzed a simulated API key leak and documented remediation. [View File](/incident-response/incident-report.md)

### Phase 4: GRC (Governance, Risk, & Compliance)
* **Risk Register:** Quantified business risks based on likelihood and impact. [View File](/risk-compliance/risk-register.md)
* **Framework Mapping:** Cross-referenced all project controls with the **NIST CSF v2.0**. [View File](/risk-compliance/control-mapping.md)
* **Vulnerability Assessment:** Evaluated existing architectural gaps and planned mitigations. [View File](/vulnerability-management/vulnerability-report.md)

---

## Technical Skills Demonstrated
* **Security Frameworks:** NIST CSF, HIPAA/PCI-DSS Compliance Alignment.
* **Cloud Security:** GCP/Firebase IAM Hardening, Secret Management, Cloud Logging.
* **Threat Intelligence:** STRIDE Threat Modeling, Custom Alert Logic (SIEM/EDR mindset).
* **Incident Management:** Root Cause Analysis (RCA), Containment Strategies.
---

## Connect With Me

I'm actively seeking GRC Analyst or Compliance Analyst opportunities where I can apply my incident investigation, risk assessment, and compliance experience.

📫 **Contact:** mattbarfield1@gmail.com  
💼 **LinkedIn:** [matthew-barfield-grc](https://www.linkedin.com/in/matthew-barfield-grc/)  
📄 **Resume:** [View My Resume](https://docs.google.com/document/d/11j7yx5Nkfmr7T-e7wQktyStoxdVbWzNh/edit?usp=sharing&ouid=103440986515006912895&rtpof=true&sd=true)

*Open to opportunities in: Governance, Risk & Compliance | Security Operations | Compliance Analysis | Risk Management*
