# Incident Report — Phishing Email Campaign
**Incident ID:** PH-2025-004  
**Reported by:** User reports + SIEM alert  
**Analyst:** Divyanshu Ganeshwani  
**Date:** October 2025  
**Environment:** Personal lab & course lab simulations (no production data)

## 1. Executive Summary
On October 2, 2025, a simulated phishing email campaign targeted multiple users in a course lab environment. Alerts were generated via Microsoft Sentinel detections and user reports. The campaign used a credential-harvesting page hosted on a free domain. Containment actions were executed in the lab environment; no real credentials were harmed (simulation only).

## 2. Incident Details
- **Category:** Phishing / Social Engineering  
- **Severity:** High (simulated credential harvesting)  
- **Detection Source:** Microsoft Sentinel KQL rule + user simulation  
- **Affected Entities:** 8 simulated users, 2 simulated clicks, 0 credential submissions (lab)

## 3. Timeline
| Time (UTC) | Event |
|------------|-------|
| 08:42 | Simulated user reported suspicious email |
| 08:50 | Sentinel alert triggered for matching IOC |
| 09:10 | URL analyzed in URLscan.io & VirusTotal (malicious) |
| 09:20 | Quarantined simulated messages and blocked domain in lab gateway |
| 09:35 | Added IOCs to SIEM watchlist and created incident ticket |
| 10:10 | Simulated credential resets executed for affected test accounts |
| 10:45 | Incident documented and closed (lab exercise) |

## 4. Investigation Findings
- **Phishing domain:** login-verify-microsoft[.]example (lab domain)  
- **Indicators:** malicious URL, hosted phishing page, originating test IP (lab)  
- **User impact:** Two simulated clicks; no credentials entered in lab simulation

## 5. Containment & Eradication
- Blocked phishing domain in lab email gateway and SIEM blocklists.
- Quarantined remaining phishing emails in lab mailboxes.
- Removed phishing page content from the demonstration hosting environment.
- Rotated lab test credentials for affected accounts.

## 6. Recovery & Lessons Learned
- Implemented an additional KQL detection to identify suspicious Microsoft-login keywords in URLs.
- Reinforced user awareness exercises in the lab training module.
- Recommended email authentication checks (SPF/DKIM/DMARC) be verified on any real deployments.

## 7. Attachments
- `Phishing_Email_Triage_Playbook.md`
- `Failed_Login_Detection_KQL_Query.kql`
- IOC list (example): `ioc_phishing_example.csv` 
