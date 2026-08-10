# Security Hardening Report: Active Directory Restructuring & Group Policy Implementation

**Date:** 08-10-2026  

**Environment:** Controlled lab environment — Windows Server domain controller (THM.local), simulating a small business AD environment.

---

## Scenario

As part of onboarding into a security administration role, I was tasked with reviewing and restructuring an existing Active Directory domain. The objective was to align the directory with the organization's current structure, apply least-privilege delegation practices, and implement baseline security policies (GPOs) across all workstations and servers.

---

## Investigation & Implementation

### Auditing the Existing OU Structure
Before making changes, I reviewed the current AD structure against the organizational chart to identify discrepancies. I discovered a department Organizational Unit (OU) that no longer matched the current business structure. Since deleting an OU is a destructive action, I temporarily disabled Active Directory's built-in accidental-deletion protection via the Object properties tab. This safeguard exists because OU deletion cascades to every user, group, and sub-OU beneath it. Once verified against the org chart, the stale OU was securely removed.

### Reconciling Users Against the Source of Truth
After removing the outdated OU, I cross-checked existing users in each department OU against the organizational chart. I provisioned new accounts and deprovisioned outdated ones to bring AD in line with the actual business structure, treating the org chart as the definitive source of truth rather than the existing (outdated) AD state.

### Implementing Least-Privilege Delegation
Rather than requiring Domain Administrator credentials to handle routine tasks, I delegated specific, limited control over the Sales OU to the IT support user account. I granted only password-reset rights rather than full administrative control. This follows the principle of least privilege—the IT support user can perform their job function without being granted broader access, significantly reducing the domain's overall attack surface if that account were ever compromised.

I validated the delegation by authenticating as the IT support user and forcing a password reset and mandatory change at next logon via PowerShell, ensuring the IT admin did not retain visibility into the user's new password.

### Reorganizing Computer Objects by Role
By default, all domain-joined machines land in a single generic `Computers` container, meaning workstations and servers receive identical Group Policy treatment. Because workstations and servers have fundamentally different security requirements, I created dedicated `Workstations` and `Servers` OUs. I migrated existing machines into the appropriate OUs based on their role to ensure targeted policy deployment.

### Designing and Deploying Group Policy Objects (GPOs)
With the OU structure corrected, I implemented two core security-hardening GPOs:

*   **Restrict Control Panel Access:** Configured under *User Configuration* to prevent non-IT users from accessing Control Panel and PC settings. I linked this GPO specifically to the Sales, Marketing, and Management OUs, deliberately excluding IT, as they require legitimate system-level access.
*   **Auto Lock Screen Policy:** Configured a 5-minute inactivity lockout under *Computer Configuration*. I linked this at the root domain level rather than to individual OUs, as this policy must apply universally across all workstations, servers, and domain controllers. Linking at the root allows child OUs to inherit the policy automatically.

I verified enforcement by logging in as a Marketing department user and confirming Control Panel access was denied, while confirming IT department accounts retained normal access.

---

## Commands & Tooling

**Reset a user's password under delegated (non-admin) privileges:**
```powershell
Set-ADAccountPassword -Identity "sophie" -Reset -NewPassword (Read-Host -AsSecureString -Prompt "Enter New Password") -Verbose
```

**Force password change at next logon:**
```powershell
Set-ADUser -Identity "sophie" -ChangePasswordAtLogon $true -Verbose
```

**Force immediate GPO sync on a target machine:**
```powershell
gpupdate /force
```

---

## Findings & Security Impact

*   **Administrative Drift Mitigation:** The existing AD structure contained a stale OU and several out-of-sync user accounts. This represents accumulated administrative drift that compounds access-control risk over time if left unaddressed.
*   **Exposure Reduction:** Prior to this hardening pass, all users had unrestricted Control Panel access, and no automatic screen-lock policy was enforced. Both represented avoidable exposure to opportunistic access.
*   **Blast Radius Containment:** Delegated administration allowed IT support to perform password resets without requiring broader domain privileges, effectively reducing the blast radius if that specific account were compromised.

---

## MITRE ATT&CK Mapping

*   **[M1026] Privileged Account Management (Mitigation)** — Delegation of limited administrative rights rather than broad privilege grants.
*   **[M1035] Limit Access to Resource Over Network (Mitigation)** — Control Panel restriction and OU-based policy segmentation.

---

## Analyst Notes

This exercise reinforced that Active Directory hardening is not a one-time setup; it requires ongoing reconciliation against organizational reality. Structural drift (stale OUs, outdated user records) directly weakens policy enforcement over time. 

It also highlighted why least-privilege delegation matters operationally, not just theoretically. Granting targeted password-reset rights instead of full Domain Admin access meant the support account carried meaningfully less risk while maintaining full operational capacity. In a production environment, I recommend periodic AD audits against HR records to catch this drift proactively.
