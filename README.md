"I investigated a P1 (Priority 1) security incident involving an executive account takeover at Cloudora, a B2B HR software company. The investigation began with an 'impossible travel' alert for the CEO and evolved into a full-scale response involving credential harvesting, MFA persistence, and Business Email Compromise (BEC) staging."

## Tools & Technologies Used

- KQL (Kusto Query Language): Primary tool for hunting and data analysis.
- Azure Data Explorer / Microsoft Sentinel: Used for log ingestion and SIEM simulation.
- MITRE ATT&CK Framework: Used to map attacker techniques for industry-standard reporting.
- NIST Incident Response Lifecycle: Followed for Detection, Containment, Eradication, and Recovery.

## The Investigation Process

- Detection: Verified the 'Impossible Travel' alert (Lagos vs. London) using KQL.
- Analysis: Baselined the CEO's account and identified a three-night Password Spray attack (T1110.003) as the initial access vector.
- Persistence Discovery: Found two backdoors in the Audit Logs: an unauthorized MFA device (Pixel 6) and a malicious inbox rule ("RSS subscriptions") designed for invoice fraud.
- Scoping: Identified a second victim, Priya, through infrastructure-based hunting.
- Containment & Eradication: Executed a "Golden Order" containment sequence: Revoke Sessions → Reset Credentials → Remove MFA → Delete Rules → Block IPs → Verify.

## Key Findings (The Three Tiers)

- Confirmed Compromised: Daniel Reev (CEO), Priya.
- Targeted but Not Breached: 24 accounts hit by the password spray.
- Investigated and Cleared: Omar Farro (False positive/Legitimate business travel).
