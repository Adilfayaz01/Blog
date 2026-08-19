+++
date = '2026-08-19T09:00:00+05:30'
draft = false
title = 'NCNICC-1:2025: The First NCA Cybersecurity Controls That Now Bind Private Companies'
tags = ["NCA", "NCNICC", "compliance", "KSA", "Saudi Arabia", "cybersecurity", "cloud security"]
+++

For years, if you ran a private company in Saudi Arabia, the National Cybersecurity Authority's (NCA) controls were something you admired from a distance. They applied to government entities and critical national infrastructure operators. If you weren't in those categories, you could read the frameworks, nod along, and carry on.

That era just ended.

In December 2025, the NCA published **NCNICC-1:2025**, the Non-Critical National Information Infrastructure Cybersecurity Controls. It took effect in January 2026. And for the first time, a binding NCA framework now applies directly to the general private sector. If you run a private company in the Kingdom, this is now your problem to solve, not someone else's.

Here is what it actually says, who it binds, and how to get defensible without a panic-buy of consultants.

## What NCNICC Actually Is

NCNICC is the NCA's framework for entities that are private, and that do not own, operate, or host critical national infrastructure. Think of it as the private-sector sibling of the Essential Cybersecurity Controls (ECC), scaled down and tuned for organizations that were previously outside formal scope.

It is the first framework of its kind: a mandatory, enforceable cybersecurity baseline for ordinary private businesses in Saudi Arabia.

## Do You Even Fall in Scope?

The most common question I get is "does this apply to me?" The answer depends entirely on your size, because NCNICC tiers the requirements by headcount and revenue.

| Entity type | Framework | Scope |
|---|---|---|
| Government entities & CNI operators | ECC-2:2024 | Mandatory, full (4 domains, ~110 controls) |
| Private, large (over 250 staff or over SAR 200M revenue) | NCNICC-1:2025 | Mandatory, full (~65 controls) |
| Private, SME (6 to 249 staff or SAR 3M to 200M) | NCNICC-1:2025 | Mandatory subset (~26 controls); rest recommended |
| Micro (under 6 staff, under SAR 3M) | NCNICC-1:2025 | Not mandatory, treat as best practice |
| Private entity serving government under contract | ECC cascaded | ECC controls for the relevant systems |

Two things stand out here.

First, the NCA may impose additional controls on specific high-risk sectors at its discretion, regardless of your tier. Your industry can pull you up a level even if your headcount would not.

Second, if you deliver services to a government body, ECC can flow down to you contractually even if you are firmly private. Signing a government contract can quietly drag a whole new set of controls onto your plate.

## What Is Actually Mandatory

Strip away the jargon and NCNICC's mandatory core is refreshingly practical. It is the same security hygiene you have known about for a decade, now with legal force.

**Governance.**
- A cybersecurity function that is independent of IT, not a box ticked by the IT manager in their spare time.
- Approved policies, a documented risk management methodology, and awareness training that actually happens.
- For large entities, cyber leadership roles filled by qualified Saudi nationals.

**The technical baseline.**
- Identity and access: least privilege, MFA for remote and privileged access, and periodic access reviews.
- Endpoints and networks: secure configuration, endpoint protection, network security, and mobile device controls.
- Email security aligned to the NCA's Haseen platform.
- Data classification and encryption, using national cryptographic standards where required.
- Tested backups and recovery.
- Vulnerability management and periodic penetration testing.
- Centralized logging, monitoring, and incident management with NCA notification when something significant happens.

**Third parties and cloud.**
- Security clauses in your contracts: confidentiality and incident notification.
- Vendor risk assessments for anyone who touches your data.
- For cloud users, the Cloud Cybersecurity Controls (CCC) continue to apply on top of NCNICC.

If you are a small or medium business, your mandatory slice is narrower but still real: MFA, endpoint security, email and phishing protection, patching, backups, and a named incident response plan. The "recommended" items are not optional forever. They are very likely the next mandatory set, so treat them as a roadmap rather than a maybe.

## How Compliance Gets Checked

This is not a self-certify-and-forget arrangement. NCNICC uses a layered assessment model:

- **Self-assessment** against the applicable control set.
- **Independent audits** by NCA-approved third parties.
- **Direct NCA inspections** when the authority decides to look.

It is a recurring review, not a one-time certification. And this is the part executives should care about: adverse findings affect your standing in regulated business relationships. If you are a supplier, a bank, or a healthcare contractor, a poor NCNICC posture can quietly cost you clients and contracts.

## A Roadmap to a Defensible Baseline

The good news is that NCNICC does not require a multi-year transformation. Most SMEs can reach a defensible baseline in two to three quarters if they sequence the work correctly.

1. **Confirm your category.** Headcount and revenue determine which control set binds you.
2. **Run a gap assessment** against the applicable set, not a generic checklist.
3. **Phase 1: governance basics.** Security ownership, baseline policies, a risk register.
4. **Phase 2: asset inventory.** Every device, cloud account, SaaS tool, and sensitive data location.
5. **Phase 3: MFA everywhere.** Email, cloud apps, and every admin account. This is the single highest-impact control, and it is cheap.
6. **Phase 4: tested backups** for your critical systems.
7. **Phase 5: a named incident response plan.** Someone specific owns it, and they know what to do.
8. **Phase 6: recurring awareness training** plus phishing simulations.
9. **Then formalize the rest.** Monitoring, third-party risk, and resilience become documented evidence rather than assumptions.

Notice how much of that is not expensive. MFA, patching, backups, a named incident owner, and a phishing-tested workforce cover an outsized share of the actual risk. NCNICC is a security program, not a shopping list.

## What Executives Should Take From This

If you are a leader at a private company in Saudi Arabia, three numbers should stay in your head: the tier that binds you, the roughly two to three quarters it takes to get defensible, and the fact that NCA inspections are real and recurring.

The companies that treat NCNICC as a genuine security uplift will sail through. The ones that treat it as a paperwork exercise will find out the hard way, at audit time, or worse, at incident time.

The controls were never really optional. Now they are mandatory.
