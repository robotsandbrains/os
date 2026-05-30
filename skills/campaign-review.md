---
title: Campaign Review
version: v0.1
updated: 2026-05-31
status: draft
---

# Campaign Review

## What this skill does

This skill runs a fast, structured **campaign-level performance review** that surfaces three things: **what changed, why it likely changed, and what to do about it.** It compares a recent window against the prior equivalent window, reads the movement against the bidding strategy's health (learning status, target vs actual), budget pacing, and notable search-term shifts, and turns it into a **decision-ready summary** — not a data dump. It's built to be run **weekly or fortnightly** as a recurring optimisation habit, so a practitioner can stay on top of active campaigns in minutes and walk away with a clear, prioritised set of actions and watch-items. Like all skills here, Claude does not access the account directly — the practitioner pastes or attaches the metrics; the review is only as good as the data supplied.

## When to use it

- **Weekly campaign check-ins** — the routine optimisation sweep.
- **After a significant budget or target change** — confirm the change is behaving and learning is settling.
- **When a client asks "how are things going"** — a quick, honest read before you reply.
- **Before a client call** — to prepare clear, defensible talking points.

## The prompt

> Paste the following into Claude Code with this repo loaded. Attach or paste the metrics when prompted. If a client vault is configured, Claude will read the relevant client file first for context (targets, business rules, recent changes — see [[vault-structure]]).

```
You are running a recurring campaign performance review using the Robots & Brains OS.
Be fast and decision-led. Produce a tight summary, not a data dump.

STEP 1 — Load context before you start.
Read and apply:
- The relevant campaign-type file(s) for this campaign:
  [[search]], [[pmax]], and/or [[demand-gen]]
- [[smart-bidding]] (for learning status and target-vs-actual interpretation)
- The relevant context file: [[lead-gen]] or [[ecomm]]
Do not begin until you've read these.

STEP 2 — Confirm inputs.
Ask me for, and wait until I provide:
1. Campaign name and type (Search / PMax / Demand Gen / Shopping).
2. Account type: lead gen or ecomm.
3. Date range — default to LAST 14 DAYS vs the PRIOR 14 DAYS (recommend this;
   accept another comparison window if I specify one).
4. Key metrics for both periods: impressions, clicks, conversions, cost,
   and CPA (lead gen) or ROAS / conv. value (ecomm). Include CTR and conv. rate
   if available, the bid strategy + target, and the current learning status.
5. Optional but useful: notable search-terms changes, and any budget/target/creative
   changes I made in or just before the window (with dates).
If something's missing, tell me what, note which parts of the review are limited,
and proceed with what I give you. Account for seasonality/weekday effects in a
14-day comparison and don't over-read a single noisy day.

STEP 3 — Analyse.
Work through, briefly:
- PERFORMANCE TREND: is the campaign up / down / stable on its primary KPI
  (CPA or ROAS) and on volume? Quantify the change (%), and judge it against
  normal noise — flag only meaningful movement.
- LIKELY CAUSES: tie movement to probable drivers — a recent target/budget change,
  learning period, seasonality, auction/competition, conversion-tracking shifts,
  search-term mix, or creative. Distinguish signal from noise; say when a cause
  is uncertain rather than guessing confidently.
- BIDDING HEALTH: learning status (is it stuck or stable?), target vs actual CPA/ROAS,
  and whether any target whiplash or budget cap is distorting results
  (apply [[smart-bidding]]).
- BUDGET PACING: under- or over-pacing vs intended spend; budget-limited status.
- SEARCH TERMS / PLACEMENTS: any new wasteful or high-value terms worth acting on
  (negatives, or protecting a winner).

STEP 4 — Triage and output.
Flag each finding as either:
  [ACT NOW] — needs action this week, or
  [WATCH] — monitor, not yet actionable (note what would trigger action).
Then output in the exact three-section format from the "Example output structure"
section of this skill file: WHAT CHANGED → WHY → WHAT TO DO.
Critical constraint: respect learning periods — do NOT recommend touching a campaign
that's mid-learning unless something is genuinely broken; if so, say "hold and monitor"
and why. Cite the numbers. Don't invent data.
```

## Example output structure

> The structure Claude should produce. Placeholders show format only — no fabricated data.

```
# Campaign Review — [Campaign Name] ([type])
Account type: [lead gen | ecomm]   |   [last 14 days] vs [prior 14 days]   |   Date: [YYYY-MM-DD]

Verdict: [one line — e.g. "Stable and healthy" / "CPA up, action needed" / "In learning, hold"]

## 1. What Changed
- Primary KPI: [CPA/ROAS] [direction] [X%] ([period] vs [period]).
- Volume: conversions [direction] [X%]; cost [direction] [X%].
- Supporting: CTR / conv. rate / impressions [direction] [X%] — only the movements that matter.
- [Each notable change as a tight bullet. Quantified. No filler.]

## 2. Why
- [Likely cause of the main movement, tied to evidence — e.g. target change on [date],
  learning period, seasonality, search-term shift.]
- [Secondary driver, if any.]
- [State uncertainty honestly where the cause isn't clear.]

## 3. What To Do
[ACT NOW]
- [Specific action] — [one-line rationale]. Effort: [Low/Med/High].
- [Specific action] — [rationale].

[WATCH]
- [Item to monitor] — [what would trigger action and roughly when to recheck].
- [Item to monitor] — [trigger].

Notes for client call (optional):
- [1–2 plain-language talking points if this review is prepping a conversation.]
```

## Related
Knowledge in [[smart-bidding]], [[search]], [[pmax]], [[demand-gen]], [[creative-strategy]]; contexts [[lead-gen]] / [[ecomm]]. Pairs with [[account-audit]] (deeper, periodic) and feeds [[monthly-report-brief]] (reporting).
