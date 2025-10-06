# SOC Playbook — Phishing Email Triage
**Author:** Divyanshu Ganeshwani  
**Date:** Jul 2025 – Sep 2025  
**Environment:** Personal lab & course lab exercises (non-production)

## Objective
Provide a standardized Tier-1 SOC process for identifying, analyzing, containing, and remediating phishing email incidents.

## Scope
Applies to inbound email alerts from Microsoft Defender for Office 365, email gateway alerts, or user-reported suspicious emails in a monitored environment.

## Detection Sources
- Microsoft Defender for Office 365
- Microsoft Sentinel (KQL detections)
- User-reported suspicious email (SOC ticket)

## Triage Steps (Tier-1)
1. **Initial Validation**
   - Confirm alert timestamp and affected mailbox.
   - Check if alert is duplicate or correlates with other alerts.
2. **Evidence Collection**
   - Retrieve full email headers, raw message, URLs, and attachments.
   - Export message to evidence repository.
3. **Quick Analysis**
   - Check sender domain reputation (VirusTotal, Whois, passive DNS).
   - Inspect URLs (URLscan.io) and attachments (Any.run, VirusTotal).
   - Search for known IOCs (hash, domain, IP) in threat intel sources.
4. **Severity Classification**
   - Low: suspicious domain, single recipient, no payload.
   - Medium: malicious URL detected, multiple recipients.
   - High: credential harvesting page, mass distribution, confirmed credential submission.
5. **Containment Actions**
   - Quarantine the email across affected inboxes.
   - Block sender domain in email gateway and update blocklists.
   - Add indicators to SIEM/EDR watchlists.
6. **Eradication**
   - Remove malicious email copies, remove links from messages if feasible.
   - Reset compromised credentials if credential submission is suspected.
7. **Recovery**
   - Restore affected accounts from clean state.
   - Ensure backups/integrity of critical data.
8. **Documentation**
   - Update incident ticket with timeline, IOCs, and actions taken.
   - Save evidence artifacts (headers, screenshots, IOC lists).
9. **Post-Incident Review**
   - Recommend prevention controls (SPF/DKIM/DMARC, email filtering rules).
   - Plan targeted user awareness for recipients.

## Roles & Responsibilities
- **SOC L1 Analyst:** Validate alert, collect evidence, perform initial triage, quarantine emails, escalate as needed.
- **SOC L2 Analyst:** Deep analysis, confirm compromises, coordinate containment on endpoints.
- **Incident Manager:** Oversee incident lifecycle, sign-off on containment and closure, coordinate communications.

## Tools & References
- Microsoft Sentinel (SIEM) / Log Analytics
- Microsoft Defender for Office 365
- VirusTotal, URLscan.io, Any.run
- MITRE ATT&CK (T1566 – Phishing)

## Deliverables
- Incident ticket with artifacts
- IOCs (domains, URLs, hashes, IPs) CSV
- Post-incident lessons learned
