---
title: Campaign Review
version: v0.1
updated: 2026-05-31
status: draft
---

# Campaign Review

## What it does
A focused review of one or more live campaigns against their goal — diagnosing performance, spotting wasted spend, and producing concrete optimisation actions.

## When to use it
- Recurring weekly/fortnightly optimisation cadence.
- A single campaign is under- or over-performing and needs a deep look.
- Before making a budget or bid-target change you want to justify.

## The prompt
Skeleton of the prompt Claude runs:
- Role and goal framing (act as the practitioner optimising this campaign).
- Required inputs (campaign export, goal/KPIs, date range, recent changes).
- Review checklist: pacing vs budget, bid strategy health, search terms/placements, asset performance, audience signals, conversion trends.
- Constraints (respect learning periods, flag don't-touch items).
- Output format instructions (point to the structure below).

## Example output structure
- **Snapshot** — campaign goal, current performance vs target.
- **What's working** — keep/scale items.
- **What's not** — issues with evidence.
- **Recommended actions** — specific changes, ranked, with rationale.
- **Watch list** — items to monitor, not yet act on.

## Related
Builds on [[smart-bidding]], [[creative-strategy]], campaign-type files; feeds [[monthly-report-brief]].
