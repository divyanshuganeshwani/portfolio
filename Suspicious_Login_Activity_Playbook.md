# SOC Playbook — Suspicious Login Activity
**Author:** Divyanshu Ganeshwani  
**Date:** August 2025  
**Environment:** Personal lab & course lab exercises

## Objective
Provide a Tier-1 SOC process for investigating unusual login activity such as impossible travel, logins from new countries, or logins from anonymous/proxy IPs.

## Detection Sources
- Microsoft Sentinel (SigninLogs)
- Azure AD sign-in logs
- Defender for Cloud Apps / Conditional Access logs
- User reports

## Tier-1 Triage Steps
1. **Validate**: Confirm user identity and timestamp of the login.
2. **Collect**: IP address, geolocation, device type, user agent, MFA status, session ID.
3. **Baseline comparison**: Check historical sign-ins for the user to establish normal patterns.
4. **Quick containment**:
   - If confirmed suspicious: force password reset and revoke active sessions.
   - If uncertain: enable additional monitoring and notify user.
5. **Escalate**: If there is corroborating evidence (MFA failure, multiple risky IPs), escalate to SOC L2.
6. **Document**: Add full timeline and actions to incident ticket.
7. **Post-incident**: Recommend enforcing or tightening MFA, adding conditional access, and user awareness.

## Tools
- Microsoft Sentinel / SigninLogs
- ipinfo.io / MaxMind GeoIP
- Azure AD portal (revoke sessions, reset passwords)
- PowerShell / Microsoft Graph for bulk actions

## Deliverables
- Incident ticket and timeline
- Risk assessment for affected account
- Recommendations for policy changes (MFA, conditional access)
