# 11 — Real-World Scenarios & Personas

> Back to [Index](00-index.md)

---

## Part A: Mixed Licensing in One Tenant {#mixed-licensing}

### Can Different Users Have Different Licenses?

**Yes — absolutely.** This is one of the most important practical concepts in Microsoft licensing.

Within a single Microsoft 365 tenant, you can have:
```
User A → Microsoft 365 E5
User B → Microsoft 365 E3
User C → Microsoft 365 F3
User D → Microsoft 365 Business Premium   ← This is unusual but possible
User E → Microsoft 365 E3 + Purview Suite add-on
User F → Microsoft 365 E5 + Microsoft 365 Copilot add-on
```

### Rules for Mixed Licensing

**User-level assignment:** Each license is assigned to individual users (or groups). A user can be assigned multiple licenses simultaneously (base + add-on). When a user has both E3 and Purview Suite, they get both sets of capabilities.

**Shared workloads:** SharePoint sites, Exchange mailboxes, and Teams channels are shared — they are accessed by users with different license levels. Here's how it works:

| Resource | Licensing implication |
|---------|----------------------|
| SharePoint site | DLP/sensitivity label protections apply based on the accessing user's license AND the policy scope. If a site is subject to E5-licensed DLP, all members/owners must have qualifying Purview licenses. |
| Exchange mailbox | Each user's mailbox is governed by that user's license. An E3 user's mailbox is not protected by Defender for Office 365 P2 unless they have a P2 license. |
| Teams channel | Defender for Office 365 applies to users with qualifying licenses. An E3 user in a shared Team is protected by EOP baseline, not MDO P2. |
| Device | Defender for Endpoint licensing follows the device owner/primary user. If a shared device has E5-licensed users, only those users' sessions are covered by MDE P2. |

### Practical Implication — Who Needs Which License?

| Scenario | Who needs the license |
|---------|----------------------|
| DLP policy protecting a SharePoint site | All users with owner/member access to that site |
| Defender for Office 365 protecting email | All users whose mailboxes receive email |
| Intune MDM managing a device | The user assigned to (or primarily using) that device |
| Audit Premium — 1-year retention | The user whose activities you want retained for 1 year |
| Insider Risk Management monitoring a user | That specific user |
| Conditional Access policy applied to everyone | All users the policy applies to (they all need Entra P1) |
| PIM managing admin role activation | The admins being managed through PIM |
| eDiscovery Premium reviewing a custodian's content | The custodian (user whose content is held) |

### Mixed Licensing Gotchas

> ⚠️ **Gotcha 1:** If you enable Defender for Identity at the tenant level for all users, you need DFI licenses for ALL users who benefit from the protection — not just the admins who configured it.

> ⚠️ **Gotcha 2:** An E5 user sharing a Teams meeting with an E3 user does not "grant" the E3 user E5 benefits. Each user's experience is governed by their own license.

> ⚠️ **Gotcha 3:** If a compliance administrator with E5 creates an Insider Risk Management policy that monitors all users, every user being monitored needs Purview Suite or E5 licenses — not just the admin who created the policy.

> ⚠️ **Gotcha 4:** Business Premium users cannot be in the same "Business" pool as Enterprise users. However, a tenant can have both Business and Enterprise licenses assigned to different users (the 300-seat Business cap applies to Business licenses, not the entire tenant).

---

## Part B: 10 Real-World Personas

### Persona 1 — Small Business Employee (Non-Technical)

**Description:** Works for a 50-person accounting firm. Uses email, Excel for invoices, Teams for internal calls, and occasionally edits Word documents.

**Requirements:** Email, desktop Office, Teams, OneDrive, basic collaboration

**Recommended license:** **Microsoft 365 Business Standard**

**Why:** Desktop Office apps + Exchange Plan 1 + Teams + SharePoint. No security/compliance requirements beyond basics.

**What they don't need:** Intune, Conditional Access, advanced compliance, endpoint security

**If the firm grows security-aware:** Upgrade to **Business Premium** for Intune + Defender for Business + Entra P1

---

### Persona 2 — Small Business IT Admin (Security-Aware)

**Description:** IT manager at a 150-person law firm. Manages devices, enforces password policies, concerned about phishing attacks, needs to manage employee data on offboarding.

**Requirements:** Device management, Conditional Access, endpoint protection, basic compliance

**Recommended license:** **Microsoft 365 Business Premium** (for themselves and all users)

**Why:** Entra P1 for Conditional Access, Intune for device management, Defender for Business for endpoint security, Defender for O365 P1 for email protection

**What they might add:** Purview Suite for Business Premium if they need eDiscovery for legal matters (common for law firms)

**Limitation:** 300-seat cap; if firm exceeds 300, must move to Enterprise

---

### Persona 3 — Enterprise Knowledge Worker (Standard)

**Description:** Marketing manager at a 2,000-person manufacturing company. Creates presentations, collaborates on documents, uses Teams, travels and works from personal devices occasionally.

**Requirements:** Full productivity, managed device or BYOD, basic security, corporate email

**Recommended license:** **Microsoft 365 E3**

**Why:** Full desktop Office, Exchange Plan 2, Intune for device compliance, Entra P1 for Conditional Access on BYOD, Defender for Endpoint P1 for prevention

**What they don't need:** EDR, advanced Purview, Security Copilot (not a sensitive role)

---

### Persona 4 — Enterprise Software Developer

**Description:** Backend developer at a 5,000-person tech company. Has access to source code, production credentials, Azure resources. Frequently uses VSCode, GitHub, and cloud CLIs.

**Requirements:** Code access, privileged resource access management, device security

**Recommended license:** **Microsoft 365 E3** + **Entra ID P2** (or full E5 if org is on E5)

**Why:** Developer needs PIM for Azure resource access (just-in-time elevation), Identity Protection to detect if their account is compromised, Conditional Access for code access. The core productivity is E3; the identity elevation is P2.

**What they don't need:** Advanced Purview (unless working with regulated data)

**Alternative path:** If the organization is standardizing on E5, developers get P2 included

---

### Persona 5 — Enterprise Privileged Administrator

**Description:** Global Administrator / Azure subscription owner at a 10,000-person enterprise. Has tenant-wide admin rights.

**Requirements:** Least-privilege management, just-in-time activation, audit trail for privileged actions

**Recommended license:** **Microsoft 365 E5** (or minimum **Entra ID P2** + base license)

**Why:** PIM is non-negotiable for privileged admins. Entra P2 provides PIM, Identity Protection (alert if admin account is compromised), and Access Reviews (periodically validate who still needs admin rights).

**Why this matters:** A Global Admin with permanent rights who has a compromised account = full tenant takeover. PIM means the admin has the *eligibility* to become Global Admin, not permanent rights. The window of vulnerability is minutes, not forever.

---

### Persona 6 — Frontline Store Associate

**Description:** Retail cashier and stock clerk at a 2,000-person retail chain. Uses shared tablets to check inventory, communicate with managers via Teams, and access shift schedules.

**Requirements:** Teams, basic communication, shift management (Shifts app in Teams), shared device management

**Recommended license:** **Microsoft 365 F1** (if no email needed) or **Microsoft 365 F3** (if kiosk email needed)

**Why:** F1 gives Teams, SharePoint (read), and Intune for shared device management. F3 adds kiosk email and Office web apps.

**What they don't need:** Desktop Office, full mailbox, advanced security

**Device management approach:** Intune in shared device mode (multiple users, one device) — available with F3/Intune Plan 1

---

### Persona 7 — Compliance Officer

**Description:** Data Protection Officer (DPO) at a 500-person financial services firm regulated by GDPR, MiFID II, and FCA. Responsible for eDiscovery, data subject requests, retention policies, and regulatory reporting.

**Requirements:** eDiscovery Premium, Audit Premium, Insider Risk Management, retention/records management, sensitivity labels + auto-labeling, DLP, data connectors

**Recommended license:** **Microsoft 365 E5** (simplest path for full advanced Purview)

**Alternative:** **Microsoft 365 E3 + Purview Suite** (if all users don't need E5 security features)

**Why E5 makes sense here:** The compliance officer needs the full suite. E5 gives everything they need without purchasing separate add-ons.

**What they also need:** Appropriate Purview roles assigned in the portal (Compliance Administrator, eDiscovery Manager)

**Who else needs E5/Purview Suite?** All users whose data the compliance officer manages — not just the DPO. Every mailbox subject to retention policies, every user being monitored for insider risk, every custodian in eDiscovery matters.

---

### Persona 8 — SOC Analyst (Security Operations)

**Description:** Tier 2 SOC analyst at a 3,000-person enterprise. Investigates security alerts, hunts for threats, responds to incidents, manages Defender alerts.

**Requirements:** Defender XDR (full), Defender for Endpoint P2 (EDR), Defender for Identity, Defender for Cloud Apps, Advanced Hunting, Security Copilot

**Recommended license:** **Microsoft 365 E5** (or **Microsoft Defender Suite** add-on if on E3)

**Why:** Full Defender ecosystem is required for effective SOC work. EDR is non-negotiable (you can't investigate what you can't see). Security Copilot (included in E5) dramatically improves analyst efficiency.

**What they need beyond the license:** Appropriate Defender portal roles (Security Reader, Security Operator, Security Administrator). Defender XDR access is via the portal, not a separate license.

**Who also needs E5 licensing?** All users being protected by Defender XDR. If only the analyst has E5 and users are on E3, the analyst can see E3-level data but not E5-level signals for those E3 users.

---

### Persona 9 — Executive / Copilot-Heavy User

**Description:** VP of Sales at a 1,000-person company. Constantly preparing decks, summarizing meeting notes, drafting executive emails. Wants Copilot to accelerate everything.

**Requirements:** Microsoft 365 Copilot, full productivity apps, Teams

**Recommended license:** **Microsoft 365 E3 + Microsoft 365 Copilot** (or E7 if upgrading the org)

**Data security consideration:** Executives often have access to highly sensitive data. Before enabling Copilot for executives, the organization should implement sensitivity labels and DLP. If the org hasn't done this, **Purview Suite** should be added before Copilot.

**Why:** Copilot can surface any data the user can access. An overprivileged executive with Copilot who can access all SharePoint sites is a data exposure risk. Purview labeling + DLP + SharePoint Advanced Management controls what Copilot can reference.

---

### Persona 10 — Security Architect

**Description:** Enterprise Security Architect at a 5,000-person company. Designs the overall security strategy, evaluates new Microsoft capabilities, responsible for identity, endpoint, cloud, and compliance posture.

**Requirements:** Full visibility across the security estate, advanced identity (PIM, Identity Protection), full Defender XDR, compliance oversight

**Recommended license:** **Microsoft 365 E5** (for themselves)

**What they design for the organization:**
- Knowledge workers: E3 → consider E5 or Defender Suite add-on based on risk profile
- Compliance-heavy users: E3 + Purview Suite or E5
- Frontline: F3 + F5 Security if needed
- Admins: E5 minimum for PIM

**The architect's own license:** E5 (or E7 if deploying agent governance). They need visibility across all security surfaces to do their job.

---

## Part C: Organization Scenarios

### Scenario A — 50-Person Company (Basic Needs)

**Industry:** Professional services
**Needs:** Office apps, email, Teams, basic security
**Budget:** Cost-conscious

| Users | License | Reason |
|-------|---------|--------|
| All 50 | **Microsoft 365 Business Standard** | Desktop Office + Exchange + Teams + SharePoint |

**Missing:** No Intune, no Conditional Access, no endpoint security
**What to add if security becomes a concern:** Upgrade to Business Premium

---

### Scenario B — 200-Person Company (Security-Aware SMB)

**Industry:** Healthcare/Legal (handles sensitive data)
**Needs:** Device management, Conditional Access, endpoint security, basic compliance

| Users | License |
|-------|---------|
| All 200 | **Microsoft 365 Business Premium** |

**Additionally consider:** **Purview Suite for Business Premium** for eDiscovery (HIPAA/litigation holds) and sensitivity labeling automation

**Result:** Full SMB security posture with advanced compliance available as add-on

---

### Scenario C — 500-Person Enterprise (Full Enterprise)

**Industry:** Financial services
**Needs:** Enterprise productivity, advanced identity, Defender for Endpoint P2, DLP, eDiscovery, compliance

| User group | License |
|-----------|---------|
| 450 knowledge workers | **Microsoft 365 E5** |
| 50 SOC/IT admins | **Microsoft 365 E5** (same; they need full Defender) |

**Why E5?** At this scale, buying E3 + Defender Suite + Purview Suite per user is often more expensive than E5 and adds SKU complexity. E5 unifies security + compliance + productivity.

---

### Scenario D — Regulated Enterprise (Compliance-Heavy)

**Industry:** Legal/Financial (eDiscovery, strict retention, insider risk monitoring)
**Needs:** Audit Premium, eDiscovery Premium, Insider Risk Management, Communication Compliance, records management

| User group | License |
|-----------|---------|
| All 1,000 employees | **Microsoft 365 E3 + Purview Suite** |
| 20 compliance/legal staff | **Microsoft 365 E5** (they additionally need advanced identity, Defender visibility) |

**Why not E5 for everyone?** The organization's primary need is compliance, not security. E3 + Purview Suite delivers full advanced Purview without paying for Defender for Endpoint P2 and other E5 security features that the compliance team doesn't need.

---

### Scenario E — Security-Focused Enterprise (XDR Priority)

**Industry:** Technology (high-value IP, sophisticated threat actors)
**Needs:** Full Defender XDR, Identity Protection, EDR, CASB, Defender for Identity

| User group | License |
|-----------|---------|
| All 2,000 employees | **Microsoft 365 E3 + Microsoft Defender Suite** |

**Why not E5?** The primary need is security (XDR coverage). E5 also includes advanced Purview, which this org doesn't need yet. E3 + Defender Suite costs less than E5 while providing equivalent security posture. Add Purview Suite later if compliance needs emerge.

---

### Scenario F — Copilot-Heavy Organization (AI Priority)

**Industry:** Professional services (law firm, consulting)
**Needs:** Microsoft 365 Copilot for all knowledge workers, data governance to support safe Copilot deployment

| User group | License |
|-----------|---------|
| 300 partners/consultants | **Microsoft 365 E7** |
| 100 support staff | **Microsoft 365 E3 + Microsoft 365 Copilot add-on** |

**Why E7 for top-tier workers?** Copilot is included (no add-on cost), Entra Suite provides Private Access (replacing VPN for sensitive client systems), Agent 365 enables AI agent governance as the firm builds custom agents. The math may favor E7 over E5 + Copilot when Copilot is deployed widely.

**Data governance note:** Before rolling out Copilot, the firm implements sensitivity labels (auto-labeling via E7's Purview), DLP policies, and SharePoint permissions cleanup.

---

### Scenario G — Frontline Organization

**Industry:** Retail with 5,000 store associates + 200 corporate staff

| User group | License |
|-----------|---------|
| 5,000 store associates | **Microsoft 365 F3** |
| 200 corporate HQ staff | **Microsoft 365 E3** |
| 20 corporate security team | **Microsoft 365 E3 + Defender Suite** |
| 5 compliance officers | **Microsoft 365 E3 + Purview Suite** |

**Key considerations:**
- F3 for frontline gives them Teams (Shifts, Walkie Talkie, messaging), kiosk email, Intune for device management, and basic security
- Corporate staff on E3 get full productivity + managed devices + baseline security
- Security team gets advanced Defender capabilities via add-on (not everyone needs E5)
- Compliance officers get advanced Purview via add-on (not everyone needs E5)

---

### Scenario H — E3 + Modular Add-ons (Flexibility Over Simplicity)

**Why an organization chooses E3 + add-ons instead of E5 or E7:**

**Organization:** 1,000-person manufacturing company
- 700 workers need productivity + standard security
- 200 need advanced compliance (work with regulated data)
- 100 need advanced security (IT + SOC)
- 50 want Copilot (executives + knowledge workers)

| User group | Users | License |
|-----------|-------|---------|
| Standard workers | 700 | M365 E3 |
| Compliance-heavy | 200 | M365 E3 + Purview Suite |
| Security-heavy | 100 | M365 E3 + Defender Suite |
| Copilot users | 50 | M365 E3 + Microsoft 365 Copilot |

**vs. Full E5 for everyone:**
- E5 for all 1,000 = every user gets full security + compliance + Power BI Pro + Phone System
- Modular approach = each user gets what they need
- Cost: Modular is usually cheaper if most users genuinely don't need E5 features
- Complexity: Modular requires more SKU management
- Risk: If a worker moves roles, license reassignment is needed

**The modular approach works when:**
- User populations have clearly different needs
- <50% of users need full E5 capabilities
- IT has capacity to manage multiple SKUs
- Organization wants to avoid paying for unused features

---

## Sources

- [Microsoft Learn — Mixed licensing in M365](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options#changing-or-mixing-plans)
- [Microsoft Learn — Purview: who needs a license](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description#which-users-need-a-license)
- [Microsoft Learn — Defender: who needs a license (MDO)](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-defender-service-description)
- [Microsoft Learn — Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
