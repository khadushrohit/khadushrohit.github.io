---
layout: project
title: "Redesigning the billing experience for a $50M ARR product"
description: "How I helped 3,000+ brands see their usage before it cost them their experiments."
role: "Product Designer — research, design & testing"
date: 2026-08-21 10:00:00
year: 2026
tags: ["B2B SaaS", "Research", "UX"]
image: "/assets/uploads/vwo-billing-hero.png"
link: ""
order: 0
published: true
---
### How I helped 3,000+ brands see their usage before it cost them their experiments.

| | |
| --- | --- |
| **Role** | **Product Designer** — owned research, design, and testing end to end |
| **Design Manager** | Rohit Bind — direction, design critique, stakeholder alignment |
| **Product** | VWO by Wingify — enterprise A/B testing & experimentation |
| **Scale** | 3,000+ brands · 90+ countries · 600,000+ experiments · ~$50M ARR |
| **Team** | 1 PM · me (Product Designer) · 1 Design Manager · 1 UI/UX · 1 QA · eng pod · 3 stakeholders |
| **Status** | All phases are shipped now |
| **My focus** | Subscription Overview · per-product pages · MTU usage graph · invoice & billing flows · the billing-logic system underneath it all |

![The redesigned Subscription and Invoices hub, showing MTU consumed, next renewal, and a daily workspace usage graph](/assets/uploads/vwo-billing-hero.png){: loading="lazy" decoding="async"}

## 1. The Problem

One screen was quietly costing a market leader its trust.

VWO runs on a visitor quota called **MTU**. The rule underneath it is brutal: **when MTU runs out, every test stops and unused quota expires.** No overage, no grace. For these customers, usage isn't a billing detail — it's the line between experiments running and going dark.

They couldn't see that line.

![The old Accounts to Usage screen, showing quota as a raw 17K of 10K visitors with no forecast](/assets/uploads/vwo-billing-before-usage.png){: loading="lazy" decoding="async"}

**BEFORE (old "Accounts → Usage"):** quota shown as raw **"17K / 10K visitors"** — already over, no forecast, no alert — with shared-quota confusion shoved into a banner. Buried three clicks deep, tangled with an activity timeline.

![The old account usage panel sitting next to an unrelated activity timeline](/assets/uploads/vwo-billing-before-invoices.png){: loading="lazy" decoding="async"}

The old Usage and Billing pages were an afterthought: billing showed only web testing, split across two cycles, with no per-workspace or per-campaign breakdown. The on-screen MTU number routinely disagreed with reality — because VWO counts a unique visitor only once per cycle no matter how many campaigns they touch, logic that's correct but invisible. When the math looked wrong, the only fix was a support ticket.

The evidence was specific and damning:

- One enterprise account's dashboard said **18,000 visitors**. The real number was **1.18 million** — a **6,400% gap** only support could explain.
- Visitor overlap inflated consumption by **200%+** with zero on-screen reason.
- A **20-workspace** account couldn't pull its own **Jan–Jul** usage. Another had **two teams sharing one quota** — one drained it, the other got locked out, blind.
- Three accounts at once sat in grace-period limbo, unsure if they'd even failed a payment.
- Finance couldn't download invoices, couldn't tell which was latest, couldn't find their monthly cost.

This wasn't an edge case. VWO holds **4.4/5 across ~1,000 G2 reviews** — and the single most repeated complaint is *this exact thing:* quota confusion, the hard stop, opaque pricing. **When a market leader's #1 gripe is "I can't see what I'm paying for," that's not a UI bug. It's churn, loading.**

Three layers of one problem:

- **Functional:** "I can't see my usage, invoices, or true cost."
- **Operational:** every blind spot became a deflectable support ticket.
- **Strategic:** opacity in a usage-based product is a churn precursor.

**The mandate:** kill the opacity. Build a self-serve hub where customers answer their own questions and catch quota exhaustion *before* it kills their tests.

## 2. The Users

### Three people share one account — and each one was flying blind differently.

VWO's users are **CRO leaders, product managers, marketers, and UX professionals** at mid-market and enterprise eCommerce, SaaS, and media companies — teams of 5–20 running experiments off a shared quota. The subscription dashboard serves three of them, and the ticket data made it clear they have *opposing* needs.

**Persona 1 — Maya, the Experimentation Lead (CRO / Growth)**
*Owns the program.* Runs dozens of tests across workspaces. Her nightmare is quota silently running out mid-test and killing live experiments.

- **Wants:** "Show me what's left, what's eating it, and warn me before it's gone."
- **Job to be done:** protect running experiments from a surprise hard stop.

**Persona 2 — Devang, the Account Admin (Product / Ops owner)**
*Owns the contract and the workspaces.* Manages sub-accounts and reconciles which team spent what.

- **Wants:** per-workspace, per-campaign breakdowns for any date range, exportable.
- **Job to be done:** allocate and defend quota fairly across teams.

**Persona 3 — Priya, Finance / Procurement**
*Owns the money.* Doesn't log in to experiment — logs in to reconcile.

- **Wants:** downloadable invoices with readable IDs, clear statuses, and the monthly cost in one place.
- **Job to be done:** close the books without emailing support.

These aren't invented archetypes. Each maps to a real support ticket and a real account — and to VWO's documented buyer base of CRO managers, PMs, and growth leaders.

## 3. The Team

#### No unicorns. I designed it; my manager steered it.

- **Product Manager:** Mayank — PRD, prioritisation
- **Product Designer (me):** competitive research, the billing-logic system, all core screens, and the usability testing
- **Design Manager:** Rohit Bind — design direction, critique, and stakeholder alignment
- **Engineers:** Anand & team
- **QA:** Shubhra
- **Stakeholders:** 3

I drove the work day to day — research, the date-logic matrix, the screens, and the user testing. Rohit Bind, as Design Manager, set direction, ran critique, and kept the work aligned with stakeholders and the wider design system.

## 4. The Constraint

### "Next renewal date" had six different correct answers.

That was the whole problem in four words. The date a customer sees depends on the combination of **Contract Term × Order Frequency × Billing Frequency × Auto-pay** — and VWO's billing month is anchored to the contract date, so cycles never line up. Design the screens first, and half of them confidently show the wrong date.

Stacked on top: shared MTU across products, complimentary plans, pay-as-you-go, extensions, grace periods, trials. Three data sources that disagreed — **Salesforce, 2Checkout, Data360.** Eight product states from *normal* to *exhausted* to *empty.* And a backlog too big for one release.

## 5. The Work

### I ran it like research, not decoration — teardown, logic, design, test, ship.

**Stage 1 — I tore down how 20+ products solve this.** Before sketching anything, I built a competitive research wall: how Spotify, Disney+, Shopify, ExpressVPN and Coda handle subscription and cancellation; how Mixpanel and Amplitude visualise usage; how Deel, Fiverr and Contra do invoices and payment methods; how Jasper, Squarespace, GitHub, Glide and Intercom handle upgrades and trials. I dissected enterprise procurement separately — Zoom and Zoho end to end, plus the hard truths (Salesforce: no self-service; Amazon: quote-only; Atlassian: trial-led; HubSpot: unified cart). I organised every teardown under the four pillars we'd own: **Subscription Info, Subscription Management, Usage Statistics, Billing & Invoices** — grounding the design in proven patterns (Jakob's Law) instead of invention.

**Stage 2 — I designed the logic before the layout.** The date-scenario matrix defined what each screen shows for every contract, billing and auto-pay combination, and I designed the **MTU quota status system** (Default → Warning → Exhausted) up front, so state was a foundation, not a bolt-on.

**Stage 3 — I designed the core surfaces.** The Subscription main page (product cards reading "Testing Visitor Quota 17K / 2.01M · billing auto-renews Aug 1 · 5 days left"), per-product detail pages with a **daily-consumption graph** and editable billing cycle, the add-ons and inactive-subscription tables, and the invoices table with full status, download, and pagination. Every number on screen traced back to a real account state.

**Stage 4 — I tested it, internally and externally.** I ran usability sessions on a dedicated FigJam board with **separate internal and external tracks**, capturing neutral observations and quotes live, then clustered findings into concrete iteration themes: **forecast bars, filter behaviour, export placement, contract-date copy, hover states, insights sampling, and table/filter usability.** The copy and the forecast visualisation both changed because of what testing surfaced — not opinion.

**Stage 5 — I phased the ship.** With Mayank I ran every story through impact/effort. Decommissioning the old confusing pages was critical-impact, low-effort — so it shipped first.

## 6. The Impact

### From "email support to read your own bill" to self-serve, in one screen.

**Before:** quota at "17K / 10K," over-limit, buried, shared-quota note as an apology banner.

**After:** a dedicated **Subscription & Invoices** hub — per-product MTU consumed and total, expiry, next renewal, billing frequency, add-ons, clean cards.

**Proof it shipped:** the old Usage page now reads *"Page has been moved → Go to Subscription & Invoices."*

**Shipped & live (Phase 1 & 1.5):** My Subscription page, per-product pages, the MTU usage graph, the invoice list — plus retiring the old pages, consistent graph colours across products and workspaces, the 180-day range, exact-date-on-hover, and corrected combined-quota CSVs.

**In flight (Phase 2):** subscription timeline, transaction history, billing profiles, in-app Salesforce invoices, monthly-to-annual switch, usage forecasting.

**The bet:** fewer billing and quota tickets · higher dashboard adoption · lower churn · higher NPS — on a $50M revenue base where opacity was the #1 complaint.

### What I'd carry forward

- **Design the logic before the layout.** In a system this conditional, the matrix *was* the design.
- **Real tickets beat invented personas.** Every screen traced to a sentence a customer wrote.
- **Deciding what *not* to ship first is senior work.** Phasing kept the dashboard usable instead of overwhelming.
