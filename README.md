# Microsoft 365 Licensing Master Guide

A comprehensive, technically accurate reference for understanding Microsoft's licensing architecture — not memorizing SKU names.

**Last verified:** September 2026  
**Primary sources:** Microsoft Learn · Microsoft Product Terms · Official service descriptions

---

## Why this exists

Microsoft 365 licensing is one of the most confusing commercial software licensing systems in the industry. The terminology is inconsistent across documentation, product names change frequently, and the relationship between SKUs is rarely explained clearly.

This guide is structured around **understanding the architecture**, not listing features. After reading it, you should be able to look at any Microsoft 365 license, add-on, or suite and know exactly where it fits.

---

## What's covered

- The mental model: why E3/E5/E7 are bundles, not a ladder
- Every licensing vocabulary term you need (SKU, add-on, prerequisite, entitlement, etc.)
- All licensing families: Business, Enterprise, Frontline, Education, Government
- Office 365 vs Microsoft 365 — the actual difference
- Deep dives into every major product family:
  - Microsoft Entra (Free → P1 → P2 → Governance → Suite)
  - Microsoft Defender (for Office 365 / Endpoint / Identity / Cloud Apps / XDR)
  - Microsoft Purview (all capabilities, E3 vs E5 vs Purview Suite, legacy SKU history)
  - Microsoft Copilot, Security Copilot, and Agent 365
  - Microsoft Intune (Plan 1 / Plan 2 / Suite)
  - Enterprise Mobility + Security (EMS)
  - Windows Enterprise (E3/E5)
- Real-world personas and organization scenarios
- Mixed licensing: how different license tiers work in the same tenant
- "If I need X, what license do I need?" — full lookup table
- Common misconceptions corrected
- Master comparison matrix (Business, Enterprise, and Frontline plans)
- Decision trees and a final cheat sheet

---

## Files

| File | Contents |
|------|---------|
| [`00-index.md`](00-index.md) | Start here — navigation, quick-answer index, 10 test questions |
| [`01-mental-model-vocabulary.md`](01-mental-model-vocabulary.md) | Core licensing mental model + all vocabulary terms |
| [`02-licensing-families.md`](02-licensing-families.md) | Family overview + Office 365 vs Microsoft 365 |
| [`03-business-licensing.md`](03-business-licensing.md) | Business Basic / Standard / Premium (≤300 users) |
| [`04-enterprise-e-series.md`](04-enterprise-e-series.md) | E1, E3, E5, E7 — full capability breakdowns and comparison |
| [`05-frontline-licensing.md`](05-frontline-licensing.md) | F1, F3, Office 365 F3 — frontline worker plans |
| [`06-entra-licensing.md`](06-entra-licensing.md) | Microsoft Entra — all tiers and what each actually adds |
| [`07-defender-licensing.md`](07-defender-licensing.md) | Microsoft Defender — all products, P1/P2, Defender Suite |
| [`08-purview-licensing.md`](08-purview-licensing.md) | Microsoft Purview — capabilities, suite vs E5, legacy SKUs |
| [`09-copilot-agent-licensing.md`](09-copilot-agent-licensing.md) | M365 Copilot, Security Copilot, Agent 365 |
| [`10-intune-ems-windows.md`](10-intune-ems-windows.md) | Intune, EMS E3/E5, Windows Enterprise |
| [`11-scenarios-personas.md`](11-scenarios-personas.md) | 10 personas, 8 org scenarios, mixed licensing rules |
| [`12-decision-guide.md`](12-decision-guide.md) | Decision tree, lookup table, misconceptions, matrix, cheat sheet |

---

## Quick answers

| Question | File |
|---------|------|
| What does E7 actually add over E5? | [04 § E7](04-enterprise-e-series.md#microsoft-365-e7) |
| What's in E3 vs E5 vs E7? | [04 § Comparison](04-enterprise-e-series.md#e3-vs-e5-vs-e7) |
| Entra P1 vs P2 vs Governance vs Suite | [06](06-entra-licensing.md) |
| Defender for Endpoint P1 vs P2 | [07](07-defender-licensing.md) |
| What Purview is in E3 vs E5 | [08](08-purview-licensing.md) |
| What is Purview Suite? Does it equal E5 Compliance? | [08 § Legacy](08-purview-licensing.md#legacy-compliance-skus) |
| What is Agent 365? | [09](09-copilot-agent-licensing.md) |
| Intune Plan 1 vs Plan 2 vs Suite | [10](10-intune-ems-windows.md) |
| Can different users have different licenses in one tenant? | [11 § Mixed](11-scenarios-personas.md#mixed-licensing) |
| If I need X, what license? | [12 § Lookup](12-decision-guide.md#if-i-need-x-what-license) |
| Common misconceptions | [12 § Misconceptions](12-decision-guide.md#common-misconceptions) |

---

## Key things this guide gets right that most don't

**E7 is not a renamed E5.** E7 = E5 + Microsoft 365 Copilot + Entra Suite + Agent 365. It became generally available May 1, 2026.

**Copilot is not included in E5.** E5 includes Security Copilot (for security analysts, SCU-based capacity). Microsoft 365 Copilot (the productivity AI) is a separate add-on for E3/E5, and is included in E7.

**Purview Suite is not the same as E5 Compliance.** "Microsoft 365 E5 Compliance" is a legacy add-on name. The current add-on is "Microsoft Purview Suite." Same concept, evolved entitlements.

**Entra P2 ≠ Entra Suite.** P2 gives you risk-based identity and PIM. The Suite additionally gives you Private Access (replaces VPN), Internet Access (SWG), full ID Governance (lifecycle workflows), and Verified ID premium — entirely different product categories.

**Features in the admin portal ≠ licensed for use.** Microsoft provisions capabilities at the tenant level. A feature appearing in your admin center does not mean every user is entitled to use it.

**Intune changed in July 2026.** E3 users now get Remote Help and Advanced Analytics at no extra cost. E5 users now get Endpoint Privilege Management, Cloud PKI, and Enterprise App Management from the base E5 license.

---

## Sources

All content is derived from official Microsoft documentation:

- [Microsoft Learn — M365 plan options](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options)
- [Microsoft Learn — Entra licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing)
- [Microsoft Learn — Defender service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-defender-service-description)
- [Microsoft Learn — Purview service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)
- [Microsoft Learn — E3/E5/E7 Copilot feature comparison](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-license-feature-overview)
- [Microsoft Learn — Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
- [Microsoft TechCommunity — M365 E7 & Agent 365 GA](https://techcommunity.microsoft.com/blog/microsoft_365blog/microsoft-365-e7-and-agent-365-are-now-generally-available/4516295)
- [Microsoft Product Terms](https://www.microsoft.com/licensing/terms/en-US/product/changes/)
- [Microsoft Subscription Suites Licensing Guidance](https://www.microsoft.com/licensing/guidance/subscription-suites)

> Microsoft licensing changes frequently. Verify against current Microsoft documentation before making procurement decisions.
