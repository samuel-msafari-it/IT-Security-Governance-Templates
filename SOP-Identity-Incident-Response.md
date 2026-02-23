# SOP: Identity Incident Response Foundations (Microsoft Entra ID)
**Version:** 1.0
**Classification:** Internal Security
**Owner:** IT Security & Governance

## 1. Overview
This Standard Operating Procedure (SOP) outlines the foundational steps for responding to a compromised identity within Microsoft Entra ID. The goal is to minimize organizational risk, isolate the threat, and restore secure operations with zero data loss.

---

## Phase 1: Identify (Detection & Triage)
*Goal: Confirm the breach and determine the scope of impact.*

- [ ] **Immediate Lockdown:** If compromise is suspected, disable the user account and clear all active sessions immediately.
- [ ] **Log Analysis:** Review the following logs for the past 7-14 days:
    - **Microsoft Entra ID:** Sign-in logs and Audit logs.
    - **Endpoint Logs:** Windows Security logs and XDR/EDR alerts.
    - **Network Logs:** Firewall and VPN connectivity logs.
- [ ] **Correlate Indicators of Compromise (IoCs):**
    - [ ] Identify the IP address(es) used by the attacker.
    - [ ] Search for other identities utilizing the same IP or endpoint baseline.
    - [ ] Check for atypical travel or unusual geolocation logins.
- [ ] **Scope Definition:** Document all systems and identities touched by the compromised account.

---

## Phase 2: Contain (Isolation)
*Goal: Stop the spread of the compromise to downstream systems.*

- [ ] **System Lockdown:**
    - [ ] Reset the Microsoft Entra ID password.
    - [ ] Lock down non-federated systems (CRMs, Sales tools, Private Messaging).
    - [ ] Revoke VPN and remote connectivity certificates.
- [ ] **Correlated Event Audit:**
    - [ ] Check for unauthorized local software installations on endpoints.
    - [ ] Audit for privilege escalation attempts using the compromised account.
- [ ] **E-Discovery Investigation:**
    - [ ] Execute an E-Discovery case to review emails sent during the compromise period.
   
---

## Phase 3: Remove the Threat (Remediation)
*Goal: Eliminate attacker persistence and harden the identity.*

- [ ] **Credential Rotation:** Perform a forced password reset across all identified impacted accounts.
- [ ] **MFA Hardening:**
    - [ ] **Disable SMS/Voice MFA:** Transition the user to Microsoft Authenticator or FIDO2 keys.
    - [ ] **Verify SIM Integrity:** Confirm no unauthorized SIM swaps have occurred with the provider.
- [ ] **KQL Validation:** Re-run Kusto queries to ensure no new unauthorized entries exist in the logs since remediation began.

---

## Phase 4: Recover (Restoration & Monitoring)
*Goal: Safely return the user to productivity under heightened observation.*

- [ ] **Temporary Sentinel Rules:**
    - [ ] Deploy custom Analytics Rules in Microsoft Sentinel to monitor the impacted account.
    - [ ] Set a calendar reminder (14 days) to decommission temporary monitoring.
- [ ] **Identity Re-enablement:**
    - [ ] Validate MFA status and re-enable the account.
    - [ ] Perform a "Live Test" login with the user to verify access.

---

## Phase 5: Follow-up (Post-Mortem & Hardening)
*Goal: Improve security posture to prevent recurrence.*

### **Security Posture Improvements Checklist:**
- [ ] **Credentials:** Implement Password Hash Sync and block legacy authentication.
- [ ] **Attack Surface:** Configure Conditional Access policies to restrict login by location and device compliance.
- [ ] **Automation:** - [ ] Enable **Entra Identity Protection** (User/Sign-in risk policies).
    - [ ] Configure automated password resets for "High Risk" signals.
- [ ] **Privileged Access:** Move all administrative roles to **Entra PIM** (Just-In-Time access).
- [ ] **Education:** Assign mandatory phishing and identity compromise training to the impacted user.

---

## **Core Privileged Roles to Protect (MFA Mandatory):**
* Ensure these roles are excluded from any MFA exceptions:
* Global Administrator | Security Administrator | Helpdesk Administrator | User Administrator | Conditional Access Administrator

---
**Disclaimer:** This is a foundational document. Organizational-specific integrations (VPNs, custom apps) must be added to this framework as needed.
