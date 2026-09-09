# Microsoft 365 Licensing Master Guide

> **Goal:** Build a durable mental model of Microsoft's licensing architecture — not memorise SKU names.
> **Date checked:** September 2026 | **Primary source:** Microsoft Learn / Microsoft Product Terms

---

## How to read this guide

Microsoft licensing is a *stack*, not a single ladder. Each file in this guide covers one layer of that stack. Start with the mental model (file 01), then read the family that matters for your current question.

---

## Files in this guide

| # | File | What it answers |
|---|------|----------------|
| 01 | [Mental Model & Vocabulary](01-mental-model-vocabulary.md) | What *is* Microsoft licensing? Core concepts, vocabulary, the stack diagram |
| 02 | [Licensing Families](02-licensing-families.md) | Business / Enterprise / Frontline / Education / Gov; Office 365 vs Microsoft 365 |
| 03 | [Business Licensing](03-business-licensing.md) | Basic → Standard → Premium; 300-seat limit |
| 04 | [Enterprise E-Series](04-enterprise-e-series.md) | E1, E3, E5, E7 — what each actually contains |
| 05 | [Frontline Licensing](05-frontline-licensing.md) | F1, F3, Office 365 F3 |
| 06 | [Microsoft Entra](06-entra-licensing.md) | Free → P1 → P2 → Governance → Entra Suite |
| 07 | [Microsoft Defender](07-defender-licensing.md) | Defender for Office 365, Endpoint, Identity, Cloud Apps, XDR, Defender Suite |
| 08 | [Microsoft Purview](08-purview-licensing.md) | All Purview capabilities, E3 vs E5 vs Purview Suite; legacy SKU history |
| 09 | [Copilot & Agent 365](09-copilot-agent-licensing.md) | M365 Copilot, Security Copilot, Agent 365, prerequisites |
| 10 | [Intune, EMS & Windows](10-intune-ems-windows.md) | Intune Plan 1/2/Suite; EMS E3/E5; Windows Enterprise E3/E5 |
| 11 | [Scenarios & Personas](11-scenarios-personas.md) | 10 personas, 8 org scenarios, stacking examples |
| 12 | [Decision Guide](12-decision-guide.md) | Decision tree, misconceptions, master comparison matrix, cheat sheet |

---

## Quick-answer index

| I want to know about… | Go to… |
|----------------------|--------|
| What E7 adds over E5 | [04 § E7](04-enterprise-e-series.md#microsoft-365-e7) |
| E3 vs E5 vs E7 comparison table | [04 § Comparison](04-enterprise-e-series.md#e3-vs-e5-vs-e7) |
| Entra P1 vs P2 vs Governance vs Suite | [06](06-entra-licensing.md) |
| Defender for Endpoint P1 vs P2 | [07](07-defender-licensing.md) |
| What Purview is included in E3 vs E5 | [08](08-purview-licensing.md) |
| Purview Suite vs E5 Compliance (legacy) | [08 § Legacy](08-purview-licensing.md#legacy-compliance-skus) |
| What Agent 365 actually is | [09](09-copilot-agent-licensing.md) |
| Intune Plan 1 vs Plan 2 vs Suite | [10](10-intune-ems-windows.md) |
| Mixed licensing in one tenant | [11 § Mixed](11-scenarios-personas.md#mixed-licensing) |
| "If I need X, what license?" table | [12 § Lookup](12-decision-guide.md#if-i-need-x-what-license) |
| Common misconceptions corrected | [12 § Misconceptions](12-decision-guide.md#common-misconceptions) |
| Final cheat sheet | [12 § Cheat Sheet](12-decision-guide.md#cheat-sheet) |

---

## The 10 questions this guide lets you answer

1. We have 500 E3 users. We want Conditional Access, Defender for Endpoint P2, Insider Risk, eDiscovery Premium, and Copilot. What do we need?
2. We have Business Premium and want advanced Purview. Do we need E5?
3. What is the difference between E5, Purview Suite, Entra Suite, and Defender Suite?
4. If I buy E5, what separate add-ons might I still need?
5. What exactly changes E3 → E5 → E7?
6. Can different users in the same tenant have different licenses?
7. Does an E5 user automatically have every Purview feature?
8. What is the difference between Entra P1, P2, Governance, and Entra Suite?
9. What is the difference between Defender for Office 365 P1/P2 and Defender for Endpoint P1/P2?
10. What does Microsoft 365 E3 add over Office 365 E3?

> **Answers are in the files above.** Use the quick-answer index to navigate directly.

---

## Sources used (primary)

- [Microsoft Learn — M365 plan options](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options)
- [Microsoft Learn — Entra licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing)
- [Microsoft Learn — Defender service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-defender-service-description)
- [Microsoft Learn — Purview service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description)
- [Microsoft Learn — E3/E5/E7 Copilot feature comparison](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-license-feature-overview)
- [Microsoft Learn — Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
- [Microsoft TechCommunity — M365 E7 & Agent 365 GA](https://techcommunity.microsoft.com/blog/microsoft_365blog/microsoft-365-e7-and-agent-365-are-now-generally-available/4516295)
- [Microsoft Product Terms](https://www.microsoft.com/licensing/terms/en-US/product/changes/)
- [Microsoft Subscription Suites Licensing Guidance](https://www.microsoft.com/licensing/guidance/subscription-suites)
