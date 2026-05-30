---
title: Monthly Report Brief
version: v0.1
updated: 2026-05-31
status: draft
---

# Monthly Report Brief

## What this skill does

This skill generates the **written narrative** for a monthly client report — the *story around the data*, not the data itself. It takes your performance inputs and produces **client-ready prose** in four parts: a tight month-in-summary, a genuine explanation of what drove the results (the real *why*, not "performance improved"), what you changed and the reasoning behind it, and the priorities for the coming month. The point is to translate metrics into a narrative a client actually understands and trusts — turning "CPA fell 18%" into *why* it fell, what you did to make it happen, and what it means for next month. **It is not a slide-deck builder and not a dashboard** — it's a narrative generator that produces the words you drop into a report, an email, or your talking points. It writes only from the numbers and context you provide; it does not access the account.

## When to use it

- **Monthly client reporting cycle** — the written brief that accompanies the numbers.
- **When preparing for a monthly client call** — a narrative to talk from.
- **When a client asks for a written performance summary** — a fast, polished response.

## The prompt

> Paste the following into Claude Code with this repo loaded. Attach or paste the metrics when prompted. If a client vault is configured, Claude will read the relevant client file first — for the relationship, tone, business rules, KPIs, and history that make the narrative accurate and personal (see [[vault-structure]]).

```
You are writing the narrative brief for a monthly client report using the Robots & Brains OS.
Produce client-ready prose — the story around the data, not the data. No tables, no dashboards.

STEP 1 — Load context before you start.
- If a vault is configured, read this client's file at {VAULT_PATH}/clients/{client-name}/
  (client-file.md) for the relationship, KPIs, targets, business rules, and recent history.
- Read the relevant context file: [[lead-gen]] or [[ecomm]].
- Skim [[smart-bidding]] if performance movement needs a bidding/learning explanation.
If no vault is configured and I ask for a specific client, remind me to set the vault path
or paste the client context, then proceed with what I provide.

STEP 2 — Confirm inputs.
Ask me for, and wait until I provide:
1. Client name.
2. Reporting month (and account type: lead gen or ecomm).
3. Key metrics: spend, conversions, and CPA (lead gen) or ROAS / revenue (ecomm),
   each shown vs PRIOR MONTH and vs TARGET. Include anything else worth narrating
   (conv. rate, AOV, lead quality, new-customer share).
4. Significant changes made during the month (campaigns launched/paused, budget or
   target changes, restructures, creative/offer tests) — with rough dates.
5. External factors: seasonality, client-side changes (site, pricing, stock, promotions),
   market/competitive events, tracking changes.
6. TONE: "executive summary" (brief, outcome-led, minimal jargon) or
   "detailed analytical" (fuller reasoning, still plain-language). 
If inputs are missing, tell me what's missing and write the best honest brief you can —
don't invent numbers or causes.

STEP 3 — Write four sections (see this skill's output structure for length/tone):
1. MONTH IN SUMMARY — 2–3 sentences. The headline story: how the month went vs target
   and vs last month, in plain language.
2. WHAT DROVE PERFORMANCE — the real explanation. Connect results to actual causes
   (changes made, learning periods, seasonality, market, tracking). Never settle for
   "performance improved" — say WHY it moved. Be honest about bad months and uncertainty.
3. WHAT WE CHANGED AND WHY — the work done this month and the reasoning, framed around
   client outcomes (not platform jargon). Show the thinking, not just the activity.
4. PRIORITIES FOR NEXT MONTH — 3–5 concrete priorities, each with a one-line rationale.
   Include any decisions or inputs needed from the client.

STEP 4 — Style rules.
- Match the chosen tone consistently. Lead with outcomes, then explanation.
- Plain language a non-technical stakeholder understands; explain any unavoidable term.
- Honest, not spin — a weak month explained credibly builds more trust than gloss.
- Ground every claim in the data/context I gave you. Flag anything you couldn't verify.
```

## Example output structure

> The four-section narrative Claude should produce. Placeholders show format and the length/tone guidance for each section — no fabricated data.

```
# [Client Name] — Performance Brief: [Month YYYY]
Account type: [lead gen | ecomm]   |   Tone: [executive | detailed analytical]

## Month in Summary
[2–3 sentences. The headline outcome vs target and vs last month, in plain language.
This is the part a busy stakeholder reads first and maybe only — make it land.]

## What Drove Performance
[The real explanation of the numbers.
- Executive tone: 1 short paragraph — the main driver(s), simply put.
- Detailed analytical tone: 2–3 short paragraphs — primary and secondary drivers,
  how changes/learning/seasonality/market interacted, with honest notes on uncertainty.
Connect cause to effect. No "performance improved" without the WHY.]

## What We Changed and Why
[The month's work, framed around client outcomes and the reasoning behind each move.
- Executive tone: a few bullets or one short paragraph.
- Detailed analytical tone: bullets or short paragraphs grouped by theme.
Show the thinking — why each change was the right call — not just an activity log.]

## Priorities for Next Month
[3–5 concrete priorities, each with a one-line rationale tying it to the goal.]
- [Priority] — [why it matters / expected effect].
- [Priority] — [rationale].
- [Priority] — [rationale].

[Decisions / inputs needed from you: any client-side actions, approvals, or info required.]
```

## Related
Consumes the analysis from [[campaign-review]] and [[account-audit]]; draws context from [[lead-gen]] / [[ecomm]] and the client file in [[vault-structure]]. Pairs with [[client-email-draft]] for sending it.
