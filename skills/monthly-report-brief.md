---
title: Monthly Report Brief
version: v0.1
updated: 2026-05-31
status: draft
---

# Monthly Report Brief

## What it does
Turns a month of account data into a clear client-facing report brief — performance narrative, what changed, what's next — ready to drop into a deck or email.

## When to use it
- Monthly (or end-of-period) client reporting cycle.
- Preparing for a performance review or QBR.
- When you need to translate metrics into a story a non-technical client understands.

## The prompt
Skeleton of the prompt Claude runs:
- Role and goal framing (act as the account manager writing for the client).
- Required inputs (this period vs last period data, goals, actions taken, context/events).
- Narrative instructions: lead with outcomes, explain drivers, avoid jargon.
- Tone and length guidance for the audience.
- Output format instructions (point to the structure below).

## Example output structure
- **Headline** — the one-sentence story of the month.
- **Performance vs goals** — key metrics, period-over-period, plain language.
- **What we did** — actions taken and why.
- **What it means** — interpretation and drivers.
- **Next month's plan** — priorities and tests.
- **Asks / decisions needed** — anything required from the client.

## Related
Consumes outputs of [[campaign-review]] and [[account-audit]]; pairs with [[client-email-draft]].
