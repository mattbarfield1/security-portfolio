# Incident Report: Unauthorized API Usage (Key Leak)

## Executive Summary
On February 8, 2026, the security team identified an anomaly in cloud billing and API latency. It was determined that a Firebase API key was leaked via a public GitHub repository, allowing an external actor to make unauthorized requests to our Cloud Functions, resulting in a 400% spike in compute costs over a 12-hour period.

## Incident Overview
* **Incident Type:** API Key Compromise / Resource Exhaustion
* **Detection Method:** Automated Cloud Billing Alert (Cost Threshold Exceeded)
* **Impact:** High (Financial/Service Availability)
* **Status:** Resolved

## Timeline (All times in UTC)
* **02:15:** Developer accidentally pushes a hardcoded API key to a public personal repository.
* **02:22:** Automated bot scrapes the key and begins making unauthorized requests to the `/processData` endpoint.
* **08:30:** Cloud Billing alert triggers for a $500 cost threshold.
* **09:15:** Security Analyst identifies the source of the traffic as an unauthorized external IP using a valid API key.
* **09:45:** **Containment:** The compromised API key is revoked in the GCP Console.
* **10:00:** **Recovery:** A new, restricted API key is generated and deployed to the production environment using Environment Variables.

## Root Cause Analysis (RCA)
The root cause was a failure to follow secure coding practices. A developer included sensitive credentials in the source code rather than using a dedicated secrets management tool or environment variables. The lack of a `.gitignore` file in the developer's personal repo allowed the secret to be indexed by public scrapers.

## Remediation & Prevention
1.  **Immediate Fix:** Revoked the compromised key and rotated all active service account credentials.
2.  **Secret Scanning:** Implemented GitHub Secret Scanning to automatically block any commits containing API keys or tokens.
3.  **App Check:** Enabled **Firebase App Check** to ensure that only requests originating from our verified Web App can reach our Cloud Functions.
4.  **Training:** Conducted a mandatory security awareness session on managing secrets and using environment variables.

## Impact Assessment
* **Data Privacy:** No PII or PHI was accessed during this incident; the attacker only targeted the compute resource for token/resource consumption.
* **Financial:** Total unauthorized compute cost: $1,240.00.
