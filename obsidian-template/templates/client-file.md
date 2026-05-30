---
title: Client File Template
version: v0.1
updated: 2026-05-31
status: draft
---

# [CLIENT NAME]

> The primary context file. Claude reads this before every account-specific response. Keep it current — stale context produces bad advice.

## Basic details
- **Client name:** [CLIENT NAME]
- **Folder slug:** [client-name] <!-- kebab-case, matches clients/{client-name}/ -->
- **Website:** [https://example.com]
- **Account manager:** [PRACTITIONER NAME]
- **Engagement start:** [YYYY-MM-DD]
- **Status:** [active | paused | onboarding | offboarding]
- **Last updated:** [YYYY-MM-DD]

## Business model
- **Model:** [lead-gen | ecomm]  <!-- see [[lead-gen]] or [[ecomm]] for framing -->
- **Sector / industry:** [e.g. home services, B2B SaaS, fashion retail]
- **Product / service:** [what they sell, in one or two lines]
- **Average order value / deal size:** [AOV or typical deal value]
- **Sales cycle:** [instant purchase | days | weeks | months]
- **Margins / unit economics:** [if known — informs target CPA/ROAS]

## Account context
- **Platforms:** [Google Ads | Meta | Microsoft | other]
- **Account ID(s):** [stored locally only — never in the repo]
- **Monthly budget:** [MONTHLY BUDGET] across [number] campaigns
- **Primary KPIs:** [e.g. cost per qualified lead, ROAS, CAC, revenue]
- **Targets:** [e.g. tCPA $[X], tROAS [X]%]
- **Conversion tracking:** [what's tracked, enhanced conversions?, offline import?]
- **Current performance summary:** [1–3 lines: how the account is doing vs target right now]

## Campaign structure overview
Brief map of the live account so Claude understands the structure before advising:

- **[Campaign name / type]** — [goal, budget share, bid strategy, notes]
- **[Campaign name / type]** — [goal, budget share, bid strategy, notes]
- **[Campaign name / type]** — [goal, budget share, bid strategy, notes]

<!-- See [[campaign-structure]] for principles. Note any PMax/Search overlap, see [[pmax]]. -->

## Key business rules
Constraints Claude must respect in every recommendation:

- **Brand terms:** [protected brand keywords; defend or exclude?]
- **Excluded topics / negatives:** [topics, competitors, or themes to avoid]
- **Geo targeting:** [included / excluded locations]
- **Seasonal patterns:** [peak periods, slow periods, promo calendar]
- **Compliance / claims:** [regulated language, restrictions]
- **Do-not-touch:** [anything off-limits without sign-off]

## Stakeholders and communication
- **Primary contact:** [NAME, ROLE, email]
- **Decision maker:** [NAME, ROLE]
- **Other stakeholders:** [NAMES, ROLES]
- **Reporting cadence:** [weekly | fortnightly | monthly]
- **Preferred channel:** [email | Slack | call]
- **Tone / style preferences:** [e.g. concise and data-led, avoid jargon]

## Current priorities and open questions
- **Priority 1:** [the most important thing right now]
- **Priority 2:** [next]
- **Priority 3:** [next]
- **Open questions:** [unresolved items awaiting data or client input]
- **Active tests:** [what's being tested and the read date]

## Notes and history
Running log of meaningful changes, decisions, and events (most recent first):

- **[YYYY-MM-DD]** — [what changed or was decided, and why]
- **[YYYY-MM-DD]** — [what changed or was decided, and why]
- **[YYYY-MM-DD]** — [engagement start / baseline]

<!-- Link related notes: [[account-context]], meeting notes in meetings/ -->
