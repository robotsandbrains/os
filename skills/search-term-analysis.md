---
title: Search Term Analysis
version: v0.1
updated: 2026-05-31
status: draft
---

# Search Term Analysis

## What this skill does

This skill runs a **structured search term analysis** across Search and PMax campaigns that goes well beyond the naive "flag high spend, low conversions" sweep. It applies a **conversion-lag offset** so terms that simply haven't had time to convert yet aren't cut prematurely, judges every term against the **client's actual CPA or ROAS target** (not an arbitrary spend threshold), identifies **converting terms worth promoting** to exact-match keywords, handles **PMax search terms** correctly (they can't be excluded individually — only account- or campaign-level negatives apply), and outputs **ready-to-import negative keyword lists** separated by account level and campaign level. The result is a precise, defensible set of actions: what to cut now, what to watch and when to recheck it, what to scale, and how to handle the PMax black box. Like every skill here, **it does not access the account directly** — the practitioner provides the search term export, and the analysis is only as good as that data.

## When to use it

- **Weekly or fortnightly search-term hygiene sweep** — the routine query-quality maintenance task.
- **After launching a new broad match campaign** — broad needs early, careful negative shaping (see [[search]]).
- **When CPA has risen unexpectedly** and poor search-term quality is a likely cause.
- **As part of a full account audit** — alongside the [[account-audit]] skill (Dimension E: search term quality).
- **When onboarding a new client** — to establish a negative keyword baseline from day one.

## The prompt

> Paste the following into Claude Code with this repo loaded. Attach or paste the search term export when prompted. If a client vault is configured, Claude will read the relevant client file first for targets and business rules (see [[vault-structure]]).

```
You are running a structured search term analysis using the Robots & Brains OS.
Be precise and target-led. Do not cut terms prematurely — respect conversion lag.

STEP 1 — Load context before you start.
Read and apply:
- [[smart-bidding]] — for conversion lag and why premature cuts starve learning.
- [[search]] — for match-type strategy and negative keyword principles (incl. n-gram thinking).
- [[campaign-structure]] — for the Search/PMax matching hierarchy (exact-match Search wins).
- The relevant context file: [[lead-gen]] or [[ecomm]].
If a vault is configured, read this client's file for the live target and any business rules
(protected brand terms, competitor policy, excluded topics). Do not begin until you've read these.

STEP 2 — Confirm inputs.
Ask me for, and wait until I provide:
1. Account type: lead gen or ecomm.
2. The client's current target: CPA target (lead gen) or ROAS target (ecomm).
3. The search term report export — last 30 days MINIMUM — with columns:
   search term, impressions, clicks, cost, conversions, conv. value, campaign name, campaign type.
4. Average conversion lag for this account (typical days between click and conversion).
   If unknown, DEFAULT to 7 days for ecomm, 14 days for lead gen — and say which you used.
If any input is missing, tell me what's missing, note which parts of the analysis are limited,
and proceed with what I provide. Respect any business rules from the vault (never recommend
negating a protected brand term, etc.). Assume "today" is the export's end date unless I say otherwise.

STEP 3 — Analyse. Sort every NON-PMax term into one of four categories:

A. IRRELEVANT — clearly off-topic / no commercial or conversion intent (wrong product,
   job-seekers, DIY, free-seekers, wrong geography, etc.). Exclude immediately regardless of spend.

B. EXPENSIVE, NO CONVERSIONS, INSIDE THE LAG WINDOW — spend above the cut threshold (see below)
   but the term's clicks are recent enough that conversions may still land (within the conversion-lag
   window from today). DO NOT cut. Flag for monitoring and give a lag-adjusted review date
   (click date + lag, or simply today + remaining lag).

C. EXPENSIVE, NO CONVERSIONS, OUTSIDE THE LAG WINDOW — spend above the cut threshold AND old enough
   that lag no longer explains the zero. Recommend excluding. State the spend threshold used —
   derive it from the target (e.g. cut threshold ≈ 1× to 1.5× the CPA target with zero conversions
   for lead gen; for ecomm, cost clearly exceeding what target ROAS would justify with zero value).
   Make the threshold explicit so I can adjust it.

D. CONVERTING, WORTH PROMOTING — terms converting AT OR BELOW the CPA target (or AT OR ABOVE the
   ROAS target) with meaningful volume that are NOT already exact-match keywords. Recommend adding
   as EXACT MATCH to the appropriate Search campaign so the hierarchy protects them from PMax.

For terms that are borderline (some spend, 1 conversion, near target) — judge against the target and
note the call rather than forcing a category. Don't over-negate: cut clear waste, not breadth (see [[search]]).

For PMax SEARCH TERMS specifically:
- Handle them SEPARATELY. They CANNOT be excluded individually — only account-level or
  campaign-level negatives apply to PMax.
- GROUP PMax terms by THEME (e.g. brand, competitor, irrelevant-category, high-intent-generic).
- Flag themes worth acting on, and recommend ACCOUNT-LEVEL or campaign-level negatives only where
  a whole theme is clearly wasteful (e.g. a junk category, or brand that should be fenced out of PMax).

STEP 4 — Output exactly four sections, in the format in this skill's "Example output structure":
1. TERMS TO EXCLUDE NOW — as an importable negative keyword list, split into ACCOUNT-LEVEL and
   CAMPAIGN-LEVEL, one keyword per line with match type noted.
2. TERMS TO MONITOR — table with the term, spend, why held, and the lag-adjusted review date.
3. TERMS TO PROMOTE — table with the term, performance vs target, recommended match type, and
   the suggested campaign/ad group to add it to.
4. PMAX TERMS SUMMARY — themes flagged, with any recommended account-/campaign-level negatives.
Cite the numbers behind each decision. State the cut threshold and conversion lag you used. Do not invent data.
```

## Example output structure

> The structure Claude should produce. Placeholders show format only — no fabricated data.

```
# Search Term Analysis — [Account / Client Name]
Account type: [lead gen | ecomm]   |   Target: [CPA $X | ROAS X%]
Data period: [last N days, ending YYYY-MM-DD]   |   Conversion lag used: [N days]
Cut threshold used: [e.g. "≥ $X spend with 0 conversions, outside lag window"]

## 1. Terms to Exclude Now
(Importable negative keyword lists. One keyword per line. Match type in brackets.)

### Account-level negatives
[negative keyword one] (phrase)
[negative keyword two] (exact)
[negative keyword three] (phrase)

### Campaign-level negatives — [Campaign Name]
[negative keyword] (exact)
[negative keyword] (phrase)

### Campaign-level negatives — [Other Campaign Name]
[negative keyword] (phrase)

> Reasoning summary: [n] terms excluded — [x] irrelevant (Category A),
> [y] expensive-no-conversion outside lag (Category C). Total spend recovered: [$].

## 2. Terms to Monitor
(Category B — expensive, no conversions yet, still inside the lag window. Do NOT cut.)

| Search term | Campaign | Cost | Clicks | Last seen | Review on |
|-------------|----------|------|--------|-----------|-----------|
| [term] | [campaign] | [$] | [n] | [date] | [date + lag] |
| [term] | [campaign] | [$] | [n] | [date] | [date + lag] |

## 3. Terms to Promote
(Category D — converting at/within target, not yet exact-match keywords.)

| Search term | Conversions | CPA / ROAS | vs target | Recommended match | Add to campaign / ad group |
|-------------|-------------|------------|-----------|-------------------|----------------------------|
| [term] | [n] | [$ / %] | [✓ below/above target] | Exact | [campaign > ad group] |
| [term] | [n] | [$ / %] | [✓] | Exact | [campaign > ad group] |

## 4. PMax Terms Summary
(PMax terms cannot be excluded individually — themes only.)

| Theme | Example terms | Spend | Conversions | Recommendation |
|-------|---------------|-------|-------------|----------------|
| [e.g. Brand] | [terms] | [$] | [n] | [fence out of PMax via brand exclusion / account negative] |
| [e.g. Irrelevant category] | [terms] | [$] | [n] | [add account-level negative] |
| [e.g. High-intent generic] | [terms] | [$] | [n] | [healthy — no action] |

> Recommended account-level negatives from PMax themes:
> [keyword] (phrase)
> [keyword] (phrase)

## Notes
- Cut threshold and lag are explicit above — adjust and re-run if your economics differ.
- [Any term that couldn't be categorised from the supplied data, and why.]
```

## Related
Knowledge in [[search]], [[smart-bidding]], [[campaign-structure]], [[pmax]]; contexts [[lead-gen]] / [[ecomm]]. Pairs with [[campaign-review]] (routine optimisation) and feeds [[account-audit]] (Dimension E). PMax handling aligns with [[pmax-audit-framework]].
