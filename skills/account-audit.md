---
title: Account Audit
version: v0.1
updated: 2026-05-31
status: draft
---

# Account Audit

## What this skill does

This skill runs a structured **20-point audit** of a Google Ads account across the five dimensions that actually determine performance: conversion tracking, campaign structure, bidding strategy, creative and assets, and search-term quality. Claude works through each check against the best-practice knowledge in this repo, rates it **Pass / Warning / Critical**, and produces a **prioritised action list** with a severity rating and an estimated effort for every issue found — followed by a one-paragraph, client-ready executive summary. It is a diagnostic that turns a pile of account data into a ranked, defensible plan of what to fix and in what order. **It does not access the account directly** — Claude has no live connection to Google Ads. The practitioner provides the inputs (CSV/sheet exports or pasted data), and the audit is only as good as the data supplied. Treat the output as an expert second opinion to validate against the live account, not as automated account access.

## When to use it

- **Onboarding a new client account** — establish a baseline and a fix-list in week one.
- **Monthly or quarterly account health checks** — a repeatable hygiene sweep.
- **When performance has declined unexpectedly** — systematic diagnosis instead of guessing.
- **Before a major campaign launch or restructure** — confirm the foundations are sound first.
- **As a standalone deliverable for a prospect** — a credible, structured audit that demonstrates expertise and wins trust.

## The prompt

> Paste the following into Claude Code with this repo loaded. Attach or paste the requested exports when prompted. If a client vault is configured, Claude will also read the relevant client file first (see [[vault-structure]]).

```
You are running a structured Google Ads account audit using the Robots & Brains OS.

STEP 1 — Load context before you start.
Read these knowledge files and apply them as the standard you audit against:
- [[account-audit-framework]] (the audit methodology)
- [[smart-bidding]]
- [[campaign-structure]]
- [[pmax]]
- [[search]]
- [[creative-strategy]]
Then read the relevant context file for this account:
- If lead gen: [[lead-gen]]
- If ecomm: [[ecomm]]
Do not begin the audit until you have read these.

STEP 2 — Confirm inputs.
Ask me for, and wait until I provide:
1. Account type: lead gen or ecomm.
2. Campaign performance export — last 90 days (campaign-level: campaign name, type, status, cost, conversions, conv. value, CPA/ROAS, impr. share, budget, bid strategy + target).
3. Search terms report (last 90 days, with cost and conversions).
4. Conversion actions list (action name, category, count, value, include-in-"Conversions" setting, attribution model).
If any input is missing, tell me what's missing, note which checks you cannot fully complete, and proceed with what I provide (mark unverifiable checks clearly).

STEP 3 — Work through 20 checks across 5 dimensions.
Rate each check Pass / Warning / Critical, state the evidence from my data, and give a specific recommended action.

A. CONVERSION TRACKING (the foundation — weight failures here heavily)
1. Primary conversion is the right outcome (qualified lead / purchase value), not a weak proxy.
2. No duplicate, double-counted, or junk conversion actions inflating the data.
3. Conversion values present and dynamic (ecomm) / lead values or OCI in place (lead gen).
4. Enhanced conversions + Consent Mode configured; attribution model sensible (data-driven).

B. CAMPAIGN STRUCTURE
5. Consolidation vs fragmentation — campaigns meet the ~30+ conv/30-day learning threshold.
6. Brand vs non-brand are split, and brand is fenced out of PMax.
7. Segmentation is by performance/margin tier or genuine management difference, not by category/match-type/device.
8. Budgets are not chronically capping strategies; no starved or runaway campaigns.

C. BIDDING STRATEGY
9. Bid strategy matches the goal (value-based for ecomm/value lead gen; tCPA on qualified outcome for lead gen).
10. Targets are derived from economics and achievable vs trailing actuals — not aspirational.
11. No target whiplash / campaigns stuck in perpetual learning.
12. Strategy is optimising to the correct conversion (ties back to checks 1 and 3).

D. CREATIVE AND ASSETS
13. RSAs have genuine asset variety (distinct angles), not semantic repetition.
14. Pinning used sparingly; Ad Strength treated as coverage not a target.
15. PMax asset groups have full format coverage (image ratios, video, logos) and are tightly themed.
16. Ad-to-landing-page message match holds for key campaigns.

E. SEARCH TERM QUALITY
17. Negative keyword coverage — shared lists present; obvious waste excluded.
18. n-gram analysis of the search terms report surfaces no high-spend / zero-conversion themes.
19. Match-type strategy fits the account (broad only where data + Smart Bidding support it).
20. Search/PMax overlap and cannibalisation — exact-match Search protects high-intent terms; brand not bleeding into PMax.

STEP 4 — Output.
Produce the report in the exact format in the "Example output structure" section of this skill file:
- A summary scoreboard (counts of Pass/Warning/Critical).
- The 20 checks grouped by dimension, each with rating, evidence, and recommendation.
- A prioritised action table sorted by severity then impact, with effort estimates.
- A one-paragraph client-facing executive summary at the very end.
Be specific and evidence-led — cite the numbers from my data. Do not invent data; if you can't verify a check, say so.
```

## Example output structure

> The structure Claude should produce. Placeholders show format only — no fabricated data.

```
# Account Audit — [Account / Client Name]
Account type: [lead gen | ecomm]   |   Data period: [last 90 days]   |   Date: [YYYY-MM-DD]

## Scoreboard
Pass: [n]   |   Warning: [n]   |   Critical: [n]
Headline risks: [one line naming the 1–3 most serious findings]

## Dimension A — Conversion Tracking
| # | Check | Rating | Evidence | Recommendation |
|---|-------|--------|----------|----------------|
| 1 | Primary conversion is the right outcome | [Pass/Warning/Critical] | [what the data shows] | [specific action] |
| 2 | No duplicate / junk conversions | … | … | … |
| 3 | Conversion values / OCI in place | … | … | … |
| 4 | Enhanced conversions + consent + attribution | … | … | … |

## Dimension B — Campaign Structure
| # | Check | Rating | Evidence | Recommendation |
| 5–8 … |

## Dimension C — Bidding Strategy
| 9–12 … |

## Dimension D — Creative and Assets
| 13–16 … |

## Dimension E — Search Term Quality
| 17–20 … |

## Prioritised Action List
(Sorted by severity, then estimated impact. Effort = Low / Medium / High.)

| Priority | Issue | Severity | Est. impact | Effort | Recommended action |
|----------|-------|----------|-------------|--------|--------------------|
| 1 | [issue] | Critical | [High/Med/Low] | [Low/Med/High] | [action] |
| 2 | [issue] | Critical | … | … | … |
| 3 | [issue] | Warning | … | … | … |
| … | | | | | |

### Quick wins (high impact, low effort)
- [bullet] …

### Strategic projects (high impact, high effort)
- [bullet] …

### Open questions / data needed to finish the audit
- [bullet — anything that couldn't be verified from the supplied data] …

## Executive Summary
[One paragraph, plain language, client-facing. Overall account health in a sentence,
the most important finding(s), the headline opportunity, and the single most urgent
next action. Written so a non-technical stakeholder understands it and can decide.]
```

## Related
Methodology in [[account-audit-framework]]; knowledge in [[smart-bidding]], [[campaign-structure]], [[pmax]], [[search]], [[creative-strategy]]; contexts [[lead-gen]] / [[ecomm]]. Pairs with [[campaign-review]] for ongoing optimisation and [[monthly-report-brief]] for reporting.
