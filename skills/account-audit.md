---
title: Account Audit
version: v0.1
updated: 2026-05-31
status: draft
---

# Account Audit

## What it does
A structured, full-account Google Ads audit that surfaces structural, tracking, bidding, creative, and budget issues, then prioritises them into an action plan.

## When to use it
- Onboarding a new client or inheriting an account.
- Quarterly health check or before a strategy reset.
- When performance has drifted and you need a systematic diagnosis (not a spot check).

## The prompt
Skeleton of the prompt Claude runs:
- Role and goal framing (act as a senior paid media auditor).
- Required inputs (account export, conversion setup, business context, goals).
- Audit dimensions to cover: tracking & measurement, account structure, bidding, keywords/targeting, creative/assets, budgets, audiences, policy.
- Scoring/prioritisation instructions (impact × effort).
- Output format instructions (point to the structure below).

## Example output structure
- **Executive summary** — overall health score and top 3 findings.
- **Findings by dimension** — issue, evidence, severity, recommendation per area.
- **Prioritised action plan** — ranked fixes with impact/effort.
- **Quick wins vs strategic projects** — split by horizon.
- **Open questions** — what needs client input or more data.

## Related
Draws on [[account-audit-framework]], [[smart-bidding]], [[campaign-structure]]; pairs with [[campaign-review]].
