---
layout: project
title: "Designing the billing experience of a $50M ARR product"
description: "3,000+ brands could not see how much visitor quota they had left. When it ran out, their experiments stopped."
role: "Research, billing logic & UX"
date: 2026-08-21 10:00:00
year: 2024
tags: ["B2B SaaS", "Systems thinking", "UX"]
image: "/assets/uploads/vwo-billing-hero.png"
link: ""
order: 0
published: true
---

> ### When your visitor quota runs out, every experiment stops. No overage. No grace period.
> That is not a billing detail. It is the line between experiments running and going dark. And customers could not see that line.

<table><tbody><tr><td><strong>Product</strong></td><td>VWO by Wingify — A/B testing &amp; experimentation</td></tr><tr><td><strong>Scale</strong></td><td>3,000+ brands, 90+ countries, ~$50M ARR</td></tr><tr><td><strong>My role</strong></td><td>Competitive research, billing logic, state model, core screens</td></tr><tr><td><strong>Team</strong></td><td>1 PM, me, 1 design manager, 1 UI/UX, 1 QA, eng pod</td></tr><tr><td><strong>Status</strong></td><td>Shipped. Phase 2 in flight.</td></tr></tbody></table>

## The problem

The most important number in the product — how much quota is left — was three clicks deep, next to an unrelated activity timeline, shown as raw text.

![The old Accounts to Usage screen, showing quota as 17K of 10K visitors with no forecast](/assets/uploads/vwo-billing-before-usage.png)

**17K / 10K visitors.** Already over. No forecast, no warning, no way to see what ate it.

Our PM handed me a PRD and a document of every billing request support had received. Read as a list they look like feature requests. Read together they are one question, asked over and over:

<table class="data"><thead><tr><th>What the customer said</th><th>What they actually needed</th></tr></thead><tbody>
<tr><td>"My dashboard says I used 18,000 visitors. My test ran on 1.18 million. Which is right?"</td><td>Show me how you count.</td></tr>
<tr><td>"Two of our teams share one quota. One team used it all. The other can't run anything now."</td><td>Show me who spent it.</td></tr>
<tr><td>"I download four invoices every month just to find the newest one."</td><td>Give invoices a name I can read.</td></tr>
<tr><td>"Can we pick our own date range instead of emailing you for it?"</td><td>Stop making me ask a human.</td></tr>
</tbody></table>

Take the first one. Both numbers were right. VWO [counts a person once per billing cycle](https://help.wingify.com/hc/en-us/articles/58784135981465-Visitor-Counting-Logic-in-Wingify) even if they land in five different tests — so 1.18 million visits really were 18,000 billable people.

Sensible rule. It just appeared nowhere on screen. So the customer sees two numbers that don't match, assumes something is broken, and opens a ticket. Every row in that table is the same shape: the product knew the answer and never said it out loud.

That reframed it for me. I was not designing a settings page. I was designing the thing that makes usage-based pricing survivable for the person paying for it.

## Audience

-   **Experimentation lead** — needs warning before quota kills a live test.
-   **Account admin** — needs per-workspace breakdowns to allocate quota fairly.
-   **Finance** — needs readable invoices and the monthly cost, in one place.

Each one is a person who wrote one of those tickets.

## Constraints

**"Next renewal date" had six different correct answers.**

Three cycles run independently — contract term, quota cycle, billing cycle — and the billing month is anchored to the contract date, not the calendar.

<table class="data"><thead><tr><th>Case</th><th>Contract</th><th>Quota</th><th>Billing</th><th>What the screen must show</th></tr></thead><tbody>
<tr><td><strong>1</strong></td><td>12m</td><td>12m</td><td>12m</td><td>One date.</td></tr>
<tr><td><strong>2</strong></td><td>12m</td><td>6m</td><td>12m</td><td>Auto-pay changes the label.</td></tr>
<tr><td><strong>3</strong></td><td>12m</td><td>6m</td><td>3m</td><td>Renewal ≠ invoice ≠ quota reset.</td></tr>
<tr><td><strong>4</strong></td><td>Until cancelled</td><td>12m</td><td>12m</td><td>No end date exists.</td></tr>
<tr><td><strong>5</strong></td><td>Until cancelled</td><td>12m</td><td>1m</td><td>Twelve invoices per quota cycle.</td></tr>
<tr><td><strong>6</strong></td><td colspan="3">Organic self-serve signup</td><td>No contract to anchor to.</td></tr>
</tbody></table>

Design the screens first and half of them confidently show the wrong date. So I built the matrix before I drew anything.

## What I did

### Every state an account can be in

Not one status — four independent tracks running at once.

![The subscription status model: trial and premium branches, each with quota, renewal and payment tracks](/assets/uploads/vwo-billing-state-model.png)

Two details mattered more than they look:

**Auto-renewal has no grace period. Manual renewal does.** So "grace" means two different things, and the screen has to say which.

**We stopped calling expired trials "inactive."** Inactive sounds like something you switched off. *Disabled with zero quota* tells you what happened and what to do. One word, one fewer ticket.

![Loading framework: passive versus active loading, and lazy loading strategies](/assets/uploads/vwo-billing-loading-framework.png)

I split loading into **passive** (system-initiated, can be a skeleton) and **active** (user asked for it, must confirm something is happening). The invoices table got pagination out of this — finance needs to jump to one invoice, not scroll.

### From flow to final

![Exploration: the add-payment-method and edit-subscription flows, including cancel and downgrade paths](/assets/uploads/vwo-billing-explore.png)

Flows first — cancel, pause and downgrade paths, before any visual design.

![Billing profile iterations, from single profile to multiple card layouts](/assets/uploads/vwo-billing-iterate.png)

Iterating on billing profiles until multiple cards, products and addresses fit one readable layout.

![The final design set: product usage, subscription dashboard, invoices and billing](/assets/uploads/vwo-billing-final-screens.png)

The final set — product usage, subscription dashboard, invoices, billing.

![The shipped Subscription and Invoices hub, showing MTU consumed, next renewal and a daily usage graph](/assets/uploads/vwo-billing-hero.png)

Shipped. A product card now reads like a sentence: *17K / 2.01M, auto-renews Aug 1, 5 days left.*

I did not run the usability sessions — someone else did. My job was the synthesis: clustering raw observations into themes and separating real problems from one person's preference. The copy and the forecast visualisation both changed because of it.

## Outcomes

No numbers yet. So here is what actually changed.

<table class="data"><thead><tr><th>&nbsp;</th><th>Before</th><th>After</th></tr></thead><tbody>
<tr><td>Find your quota</td><td>3 clicks, buried</td><td>Own section in the nav</td></tr>
<tr><td>What it told you</td><td>"17K / 10K visitors"</td><td>Consumed, expiry, renewal, days left</td></tr>
<tr><td>Usage by workspace</td><td>Raise a ticket</td><td>Daily graph, 180-day range, export CSV</td></tr>
<tr><td>Latest invoice</td><td>Download several and check</td><td>Readable IDs and statuses</td></tr>
<tr><td>Quota running out</td><td>You find out when tests stop</td><td>A warning state, before it happens</td></tr>
<tr><td>Old Usage page</td><td>—</td><td>"Page has been moved →"</td></tr>
</tbody></table>

That last row is the proof it shipped.

**The honest gap.** The PRD bet on fewer billing tickets and lower churn. I do not have those figures, and I would rather leave the hole visible than claim a win I cannot back up.

## Three things I would carry forward

-   **Design the logic before the layout.** The matrix and the state map *were* the design.
-   **Read the raw input, not just the brief.** Every screen traces to a sentence a customer actually wrote.
-   **Deciding what not to ship is senior work.** The highest-impact ticket on a 29-story board was deleting two pages.

Thank you for reading my case study.
