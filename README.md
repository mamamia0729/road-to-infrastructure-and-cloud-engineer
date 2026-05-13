# Cloud & Systems Engineer - 3 Month Skill Path

Author: Thinh Le

## Strategy
Learn by heart first to pass the interview. Build real depth on the job.
Pattern: Memorize the "what and why" -> Lab the "how" -> Speak it fluently in interviews.

## JD Skill Map - Every Bullet Point Broken Down

### TIER 1: Identity & Access (Weeks 1-4) - THE CORE
This is 40% of the role. Nail this and you're already credible.

| JD Bullet | Real-World Skill | Your Current Level | Gap |
|-----------|-----------------|-------------------|-----|
| Microsoft Entra ID (Azure AD) | Manage users, groups, app registrations, enterprise apps in Entra portal | Studied hybrid identity design, AD Connect vs Cloud Sync | Need hands-on portal navigation, bulk operations |
| Identity and access management | Conditional Access policies, RBAC, PIM, SSO configuration | Know CA concepts from Friedkin prep | Need to build/troubleshoot CA policies hands-on |
| Group management | Security groups, M365 groups, dynamic groups, nested groups, group-based licensing | Basic AD group knowledge | Need dynamic group rules, group lifecycle, naming conventions |
| Security administration | Security defaults, MFA enforcement, risk policies, sign-in logs, audit logs | Know MFA concepts | Need Identity Protection, risky sign-ins, security alerts |
| Licensing | M365 E3 license assignment, group-based licensing, service plan toggling | Basic understanding | Need to know what's in E3, how to assign/remove, troubleshoot conflicts |
| On-prem AD with hybrid sync | AD Connect install, sync rules, filtering, password writeback, staging mode | Strong conceptual knowledge from Friedkin prep | Need hands-on sync troubleshooting patterns |
| 2026 domain migration | Forest/domain migration planning, cutover strategies, ADMT, coexistence | Conceptual only | CRITICAL GAP - need migration frameworks memorized |

### TIER 2: Endpoint & Device Management (Weeks 5-7)
20% of the role. Intune is the modern way to manage devices.

| JD Bullet | Real-World Skill | Your Current Level | Gap |
|-----------|-----------------|-------------------|-----|
| Microsoft Intune | Device enrollment, compliance policies, configuration profiles | Minimal | Need enrollment methods, compliance vs config, app deployment |
| 300+ Windows workstations | Fleet management, imaging, driver management, Windows Update | Strong from desktop support | Bridge to Intune/Autopilot management |
| DLP with Microsoft Purview | Sensitivity labels, DLP policies, content inspection | None | Need basic DLP policy creation and label taxonomy |
| Device compliance policies | Require encryption, require PIN, OS version, antivirus status | Minimal | Need to build compliance policies and understand remediation |
| Application deployment | Win32 apps, MSI, Microsoft Store apps via Intune | Know manual installs | Need Intune app packaging and deployment |

### TIER 3: M365 Workloads (Weeks 5-7)
20% of the role. Exchange, SharePoint, Teams admin.

| JD Bullet | Real-World Skill | Your Current Level | Gap |
|-----------|-----------------|-------------------|-----|
| Exchange Online | Mailbox management, mail flow rules, shared mailboxes, distribution lists | Basic email support | Need admin center navigation, mail flow troubleshooting |
| SharePoint Online | Site collections, permissions, sharing policies, storage quotas | End-user level | Need admin-level site management, permissions inheritance |
| Microsoft Teams | Teams admin center, meeting policies, messaging policies, guest access | End-user level | Need policy management, phone system basics |
| MFA | Per-user MFA, CA-based MFA, authentication methods, SSPR | Conceptual | Need to configure and troubleshoot MFA registration |

### TIER 4: PowerShell & Automation (Weeks 8-9)
15% of the role. "Light coding" but the JD says "advanced."

| JD Bullet | Real-World Skill | Your Current Level | Gap |
|-----------|-----------------|-------------------|-----|
| PowerShell scripting | Loops, conditions, functions, error handling | Fundamentals learned | Need M365-specific modules and real scripts |
| Microsoft Graph PowerShell | Connect-MgGraph, Get-MgUser, New-MgGroup | None | Need Graph SDK basics - replacing old MSOnline/AzureAD modules |
| Exchange Online PowerShell | Connect-ExchangeOnline, Get-Mailbox, Set-Mailbox | None | Need common mailbox management commands |
| Automation patterns | Scheduled tasks, bulk user operations, reporting | Basic concept | Need real scripts: bulk license assign, stale account cleanup |

### TIER 5: Security & Monitoring (Weeks 10-11)
5% of the role but shows security-first mindset.

| JD Bullet | Real-World Skill | Your Current Level | Gap |
|-----------|-----------------|-------------------|-----|
| Security events and alerts | Microsoft 365 Defender portal, alert investigation | Minimal | Need portal navigation, common alert types |
| Conditional Access | Build policies, test with What If, report-only mode | Conceptual | Need hands-on policy creation workflow |
| Security baselines | Microsoft security baselines for Windows, Edge, M365 | None | Need to know what baselines exist and how to deploy |
| Remediation actions | Respond to compromised accounts, reset passwords, revoke sessions | Some from desktop support | Need Entra ID investigation workflow |

### TIER 6: Virtual Desktop & Advanced (Week 12)
Your admitted gap. Honest answer + study plan.

| JD Bullet | Real-World Skill | Your Current Level | Gap |
|-----------|-----------------|-------------------|-----|
| Virtual desktop at scale | AVD or VMware Horizon, session hosts, user profiles | VMware adjacent only | Need AVD architecture, FSLogix, host pools |
| Documentation | Confluence/SharePoint wiki, runbooks, SOPs | Can do this | Just need enterprise formatting patterns |

---

## Week-by-Week Learning Path

### PHASE 1: IDENTITY CORE (Weeks 1-4)

#### Week 1: Entra ID Fundamentals
- [ ] Entra ID vs on-prem AD - what lives where, what syncs
- [ ] User lifecycle: create, modify, disable, delete, restore (soft delete 30 days)
- [ ] Group types: Security vs M365, Assigned vs Dynamic
- [ ] Dynamic group membership rules (syntax: `user.department -eq "IT"`)
- [ ] Administrative Units (delegated admin scoping)
- [ ] Entra ID roles: Global Admin, User Admin, Groups Admin, Security Admin
- [ ] LAB: Create users, groups, dynamic groups in Entra portal
- [ ] MEMORIZE: Entra ID free vs P1 vs P2 feature comparison

#### Week 2: Authentication & Conditional Access
- [ ] Authentication methods: Password, MFA, Passwordless (FIDO2, Authenticator, WHfB)
- [ ] Self-Service Password Reset (SSPR) - setup, licensing, writeback
- [ ] Conditional Access policy anatomy: Assignments (users, apps, conditions) -> Access Controls (grant/block)
- [ ] Common CA policies to memorize:
  - Require MFA for all users
  - Block legacy authentication
  - Require compliant device for Office 365
  - Require MFA for Azure management
  - Block access from untrusted locations
- [ ] Report-only mode and What If tool
- [ ] Named locations (trusted IPs, countries)
- [ ] LAB: Build 3 CA policies in report-only mode
- [ ] MEMORIZE: CA evaluation order, "block wins over grant"

#### Week 3: Hybrid Identity Deep Dive
- [ ] AD Connect architecture: single server, staging mode, disaster recovery
- [ ] Sync methods: Password Hash Sync (PHS), Pass-Through Auth (PTA), Federation
- [ ] When to use which (decision tree):
  - Default: PHS (resilient, simple)
  - Compliance blocks cloud passwords: PTA
  - Smart cards/third-party IdP: Federation
- [ ] Filtering: OU-based, domain-based, attribute-based
- [ ] Password writeback requirements (Entra ID P1)
- [ ] Troubleshooting sync: Event Viewer, Synchronization Service Manager, sync errors
- [ ] UPN matching: on-prem UPN must match Entra ID UPN (non-routable domain fix)
- [ ] Soft match vs hard match (immutableId / sourceAnchor)
- [ ] LAB: Document a sync troubleshooting flowchart
- [ ] MEMORIZE: AD Connect ports (443 outbound, no inbound)

#### Week 4: Domain Migration Framework
- [ ] Migration types: Same-forest restructure vs Cross-forest migration
- [ ] Active Directory Migration Tool (ADMT) - what it does, limitations
- [ ] Migration phases: Assessment -> Coexistence -> Migration -> Cutover -> Decommission
- [ ] SID History - why it matters for resource access during migration
- [ ] Trust relationships during coexistence (forest trusts, external trusts)
- [ ] Impact on Entra ID sync during migration (re-anchor users, UPN changes)
- [ ] User communication plan - what breaks, what changes, what stays the same
- [ ] Rollback strategy - every migration needs one
- [ ] DNS cutover planning (old domain -> new domain)
- [ ] Group Policy migration (GPMC backup/import, policy mapping)
- [ ] LAB: Write a 1-page migration plan outline for a fictional 500-user company
- [ ] MEMORIZE: The 5 phases and what happens in each

### PHASE 2: ENDPOINT + M365 WORKLOADS (Weeks 5-7)

#### Week 5: Intune & Endpoint Management
- [ ] Intune architecture: tenant, MDM authority, enrollment
- [ ] Enrollment methods:
  - Windows Autopilot (zero-touch, OOBE customization)
  - Manual enrollment (Settings -> Access work or school)
  - GPO auto-enrollment (hybrid join)
  - Co-management with SCCM
- [ ] Compliance policies: encryption, password, OS version, antivirus
- [ ] Configuration profiles: device restrictions, Wi-Fi, VPN, certificates
- [ ] Compliance vs Configuration (compliance = pass/fail gate, config = settings pushed)
- [ ] App deployment: Win32 app packaging (.intunewin), MSI, Microsoft Store
- [ ] Windows Autopilot: hardware hash, deployment profiles, ESP
- [ ] LAB: Document an Autopilot enrollment flow diagram
- [ ] MEMORIZE: Enrollment methods and when to use each

#### Week 6: Exchange Online & Teams
- [ ] Exchange Online admin center navigation
- [ ] Mailbox types: user, shared, room, equipment, distribution list, M365 group
- [ ] Mail flow rules (transport rules) - common patterns:
  - Add disclaimer/footer
  - Block external forwarding
  - Route mail based on conditions
- [ ] Shared mailboxes vs distribution lists vs M365 groups (when to use which)
- [ ] Quarantine management and anti-spam policies
- [ ] Teams admin: meeting policies, messaging policies, app permission policies
- [ ] Guest access in Teams - external collaboration controls
- [ ] Teams phone system basics (if applicable)
- [ ] LAB: Document a "new employee mailbox setup" runbook
- [ ] MEMORIZE: Mailbox types and licensing requirements (shared = no license needed)

#### Week 7: SharePoint, Purview & DLP
- [ ] SharePoint admin center: site collections, storage quotas, sharing settings
- [ ] SharePoint permission model: site -> library -> item, inheritance
- [ ] External sharing levels: Anyone, New/Existing guests, Only org, Disabled
- [ ] OneDrive for Business admin settings and storage limits
- [ ] Microsoft Purview: sensitivity labels, label policies, auto-labeling
- [ ] DLP policies: templates, conditions, actions, user notifications
- [ ] Common DLP scenarios:
  - Block SSN/credit card sharing externally
  - Warn users sharing financial documents
  - Block upload of sensitive files to non-approved cloud
- [ ] LAB: Design a sensitivity label taxonomy for a fictional company
- [ ] MEMORIZE: DLP policy components and 3 common scenarios

### PHASE 3: POWERSHELL & AUTOMATION (Weeks 8-9)

#### Week 8: M365 PowerShell Modules
- [ ] Module landscape (know which module does what):
  - Microsoft.Graph (replacement for MSOnline and AzureAD)
  - ExchangeOnlineManagement
  - Microsoft.Online.SharePoint.PowerShell
  - MicrosoftTeams
- [ ] Connect-MgGraph -Scopes "User.Read.All", "Group.ReadWrite.All"
- [ ] Common Graph commands:
  - Get-MgUser, New-MgUser, Update-MgUser
  - Get-MgGroup, New-MgGroup, Add-MgGroupMember
  - Get-MgUserLicenseDetail
- [ ] Connect-ExchangeOnline and common commands:
  - Get-Mailbox, Set-Mailbox, New-Mailbox
  - Get-MailboxPermission, Add-MailboxPermission
  - Get-TransportRule
- [ ] LAB: Write a script to list all users without MFA registered
- [ ] LAB: Write a script to export all shared mailboxes and their delegates

#### Week 9: Real-World Automation Scripts
- [ ] Bulk user creation from CSV (New-MgUser loop with error handling)
- [ ] License assignment/removal in bulk (Set-MgUserLicense)
- [ ] Stale account report (last sign-in > 90 days)
- [ ] Group membership audit (who's in what, exported to CSV)
- [ ] Mailbox size report across organization
- [ ] Scheduled task setup (Task Scheduler + script)
- [ ] Error handling patterns: try/catch, -ErrorAction, logging to file
- [ ] Script template with parameters, help comments, logging
- [ ] LAB: Build a "new hire onboarding" script (create user, assign license, add to groups, create mailbox)
- [ ] MEMORIZE: 5 scripts you've "written" and can walk through in an interview

### PHASE 4: SECURITY & MONITORING (Weeks 10-11)

#### Week 10: Security Operations
- [ ] Microsoft 365 Defender portal navigation
- [ ] Identity Protection: user risk, sign-in risk, risk policies
- [ ] Risky sign-ins investigation workflow:
  1. Check sign-in logs -> location, device, app
  2. Confirm with user
  3. If compromised: reset password, revoke sessions, check mailbox rules
  4. Review CA policies to prevent recurrence
- [ ] Compromised account response checklist (memorize this):
  1. Reset password immediately
  2. Revoke all refresh tokens (Revoke-MgUserSignInSession)
  3. Check mailbox forwarding rules (Get-InboxRule)
  4. Check OAuth app consent (suspicious apps)
  5. Review sign-in logs for lateral movement
  6. Enable MFA if not already
- [ ] Security defaults vs Conditional Access (security defaults = free tier MFA)
- [ ] Microsoft Secure Score - what it measures, how to improve it
- [ ] LAB: Document a compromised account response runbook

#### Week 11: Compliance & Baselines
- [ ] Microsoft security baselines (Windows 10/11, Edge, M365)
- [ ] How to deploy baselines via Intune (Endpoint Security node)
- [ ] Audit logs: what's logged, retention (90 days default, 1 year with E5)
- [ ] Alert policies in Microsoft 365 Defender
- [ ] eDiscovery basics (content search, legal hold)
- [ ] Data retention policies in Exchange and SharePoint
- [ ] LAB: Create a security monitoring checklist for weekly review

### PHASE 5: VIRTUAL DESKTOP & POLISH (Week 12)

#### Week 12: AVD + Interview Prep
- [ ] Azure Virtual Desktop architecture:
  - Host pools (pooled vs personal)
  - Session hosts (Windows 10/11 multi-session)
  - Application groups (desktop vs RemoteApp)
  - Workspaces
  - FSLogix profile containers (user profiles on Azure Files)
- [ ] AVD vs traditional VDI (VMware Horizon, Citrix)
- [ ] Scaling: autoscale based on schedule or load
- [ ] Networking: VNet integration, ExpressRoute/VPN for hybrid
- [ ] Honest interview answer for this gap:
  "I have hands-on experience managing physical and virtual Windows workstations
  and have studied AVD architecture in depth. I haven't administered a production
  AVD environment, but I understand the components - host pools, session hosts,
  FSLogix profiles - and I'm confident I can ramp quickly given my Windows
  desktop management background."
- [ ] Full mock interview prep (technical + behavioral)
- [ ] STAR stories mapped to JD requirements

---

## Interview Speaking Patterns

### When they ask about something you've studied but not done in production:
"I've studied the architecture and understand [specific components]. In my current
role I've done [related experience]. I'm confident I can ramp quickly because
[specific reason]."

### When they ask about the domain migration:
"My approach would follow five phases: Assessment, Coexistence, Migration, Cutover,
and Decommission. In Assessment, I'd inventory all users, groups, GPOs, and
applications tied to the current domain. For Coexistence, I'd establish forest trusts
so users can access resources in both domains during the transition. I'd use ADMT
for the actual migration with SID History to preserve access. And critically, every
phase needs a documented rollback plan."

### When they ask about PowerShell:
Always structure your answer as: "I'd use [Verb-Noun cmdlet] piped to [filter/action].
For example..." Then write or describe the actual command.

### When they ask about a security incident:
Use the response checklist: Reset -> Revoke -> Check forwarding -> Check OAuth ->
Review logs -> Enable MFA. Always mention "and I'd document the incident and review
our CA policies to prevent recurrence."

---

## Enterprise Patterns to Memorize

These are patterns that separate "I read about it" from "I've done this in production":

1. **Change Management** - Every change goes through: Request -> Approve -> Test -> Implement -> Verify -> Document
2. **Naming Conventions** - Users: firstname.lastname@domain.com, Groups: GRP-Department-Purpose, Devices: CORP-Location-Number
3. **Least Privilege** - Start with minimum access, add as needed, never the reverse
4. **Break Glass Accounts** - 2 cloud-only Global Admin accounts, no MFA, monitored with alerts, sealed passwords
5. **Staged Rollouts** - Pilot group (IT team) -> Early adopters (10%) -> Broad deployment (90%) -> Stragglers
6. **Documentation** - Every system has: Architecture diagram, Admin runbook, Break/fix troubleshooting guide, DR plan
7. **Ticket Hygiene** - Every action tied to a ticket. No ticket, no change.

---

## Quick Reference: M365 E3 - What's Included

Know this cold. When they say "E3 environment" you should know exactly what tools you have:

**Identity & Access:**
- Entra ID P1 (Conditional Access, dynamic groups, SSPR writeback)
- NOT P2 (no PIM, no Identity Protection risk policies - those need E5 or add-on)

**Productivity:**
- Exchange Online Plan 2 (50GB mailbox, unlimited archive)
- SharePoint Online Plan 2 (1TB + 10GB/user)
- OneDrive for Business Plan 2 (unlimited storage)
- Microsoft Teams
- Office desktop apps (Word, Excel, PowerPoint, Outlook, etc.)

**Security:**
- Microsoft Defender for Office 365 Plan 1 (safe links, safe attachments)
- NOT Plan 2 (no Threat Explorer, no automated investigation)
- Microsoft Purview (basic DLP, sensitivity labels)
- Azure Information Protection P1

**Device Management:**
- Microsoft Intune Plan 1
- Windows Autopilot
- NOT advanced endpoint analytics or remote help (need add-ons)

**Compliance:**
- eDiscovery Standard (NOT Premium)
- Basic audit (90 days, NOT 1 year)
- Data Loss Prevention (basic)

---

## Scripts Portfolio (Build These)

Save to: `C:\Users\thle\cloud-systems-engineer-path\scripts\`

1. `Get-StaleUsers.ps1` - Find accounts with no sign-in > 90 days
2. `New-HireOnboarding.ps1` - Create user, assign license, add to groups
3. `Get-MFAStatus.ps1` - Report users without MFA registered
4. `Get-SharedMailboxAudit.ps1` - List all shared mailboxes and delegates
5. `Get-LicenseReport.ps1` - License usage and available counts
6. `Set-BulkLicenseAssignment.ps1` - Assign licenses from CSV
7. `Get-GroupMembershipAudit.ps1` - Export group memberships to CSV
8. `Remove-StaleDevices.ps1` - Find/remove Intune devices not checked in > 60 days
