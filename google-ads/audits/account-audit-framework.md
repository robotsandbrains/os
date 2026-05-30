---
title: Account Audit Framework
version: v0.1
updated: 2026-05-31
status: draft
---

# Account Audit Framework

## What this framework is

This is the **methodology** behind the account audit — the structured thinking that the [[account-audit]] skill executes. The skill is the runnable procedure (the inputs, the 20 checks, the output format); **this file is the reasoning underneath it**: why those dimensions, why that order, what each check is really testing, and what separates a critical failure from a warning. Read this to understand *why* the audit is built the way it is; run the skill to *do* an audit.

The framework is a **diagnostic**, and that word is deliberate. A performance report describes *symptoms* — CPA is up, ROAS is down, volume fell. An audit diagnoses *root causes* — the reason CPA is up is that brand and non-brand share a campaign and the bidding is optimising on a polluted signal. The distinction matters because you can't fix a symptom; you can only fix a cause. The audit's entire job is to trace observed performance back to the structural, tracking, bidding, creative, and query-level decisions that produced it, and to rank those causes by how much they're costing and how hard they are to fix. It evaluates account *health* — the soundness of the foundations — not account *results*. A healthy account can have a bad month; an unhealthy account can post good numbers while quietly wasting half its budget. The audit finds the latter.

## The five dimensions and why they are ordered this way

The five dimensions run in a fixed sequence, and **the order is dependency, not preference**:

**Conversion Tracking → Campaign Structure → Bidding Strategy → Creative & Assets → Search Term Quality**

Each dimension depends on the ones before it, so auditing out of order produces wrong conclusions:

- **Tracking comes first because everything downstream optimises toward it.** Smart Bidding, structure decisions, creative testing, and your own judgement all rest on the conversion data being true. If tracking is broken, every other metric in the account is measuring the wrong thing — so you must establish whether the data is trustworthy *before* you interpret a single result. Diagnosing a "bidding problem" on top of broken tracking is diagnosing a reflection.
- **Structure comes before bidding because structure determines whether bidding *can* work.** Smart Bidding learns on pooled conversion volume at the campaign level (see [[campaign-structure]] and [[smart-bidding]]). A fragmented account starves the bidding of data no matter how well the strategy and targets are set. You cannot fairly assess a bid strategy sitting inside a structure that can't feed it — so structure is judged first.
- **Bidding comes before creative because the bid strategy and target define what "good creative" is even being asked to do**, and because a campaign in perpetual learning or target-whiplash will distort any creative read.
- **Creative comes before search terms because the assets shape which queries convert**, and you want to know whether under-performance is a creative problem before you start blaming the query mix.
- **Search term quality comes last because it's the finest-grained, most downstream layer** — query-level waste and cannibalisation only make sense to act on once the foundations above are sound. Cutting negatives on a campaign with broken tracking is rearranging deck chairs.

Audit top-down. A critical failure high in the stack often *explains* apparent problems lower down, so resolving the highest-level cause first prevents you from "fixing" symptoms that were never the real issue.

## Dimension A — Conversion Tracking

**The foundation. Failures here are weighted most heavily** because they invalidate everything else — corrupt conversion data doesn't just mislead you, it actively trains Smart Bidding toward the wrong outcome. A tracking failure is the only category that can make a "good-looking" account genuinely worthless.

The four checks, in their own internal hierarchy (integrity → dedup → value → signal):

1. **Primary conversion integrity.** Is the campaign optimising toward the *right outcome* — a qualified lead / purchase value — rather than a weak proxy (raw form fills, micro-events, page views counted as conversions)? *Critical* if the primary conversion is the wrong thing entirely (e.g. lead gen optimising to un-screened form fills with no OCI; see [[lead-gen]]). This is the single most consequential check in the audit.
2. **Deduplication and junk removal.** Are conversions double-counted (multiple tags, client+server events, no transaction ID) or inflated by junk/auto-tracked actions? *Critical* if inflation is material enough to mislead bidding and reporting; *Warning* for minor redundancy.
3. **Value data.** For ecomm: dynamic, accurate per-transaction values with transaction IDs (see [[ecomm]]). For lead gen: lead values / OCI feeding downstream quality back. *Critical* if value-based bidding is running on absent or static/placeholder values; *Warning* if values exist but are crude.
4. **Enhanced signals.** Enhanced conversions and Consent Mode configured, and a sensible (data-driven) attribution model. *Warning* in most cases (it degrades accuracy and recovery rather than breaking the account), rising toward *Critical* where measurement loss is severe enough to starve bidding.

What to look for: conversion actions list with categories/values/inclusion settings, suspiciously round or duplicated counts, value columns that are blank or uniform, attribution and enhanced-conversion status.

## Dimension B — Campaign Structure

Structure is audited as a **signal-consolidation** question, not an aesthetic one (see [[campaign-structure]]). The test is whether the account's boundaries feed or starve the bidding.

The four checks:

1. **Consolidation vs fragmentation.** Do campaigns clear the **~30 conversions / 30 days** learning threshold? This is the structural test: a long list of sub-threshold campaigns is fragmentation, and fragmentation starves Smart Bidding. *Critical* when most spend sits in campaigns too thin to learn; *Warning* for a few under-volume campaigns.
2. **Brand vs non-brand separation.** Is brand isolated and fenced out of PMax? This is **the one near-universal segmentation** — brand traffic is cheap and high-converting, and mixed in with non-brand it pollutes the conversion signal, inflates apparent performance, and hides true acquisition cost. *Critical* if brand and non-brand are blended (the data is corrupted); *Warning* if separated but brand is bleeding into PMax.
3. **Segmentation logic.** Are splits made for genuine management differences (margin/value tier, geo, budget, goal) rather than for category, match type, or device — the wrong reasons that just fragment data? *Warning* for needless segmentation; escalates to *Critical* when it's severe enough to starve learning.
4. **Budget health.** Are strategies chronically budget-capped (throttling the bidding), or are campaigns starved or running away? *Critical* for a budget cap materially distorting a target strategy; *Warning* for minor pacing issues.

What fragmentation looks like in data: many low-conversion campaigns, category-mirrored campaign names, separate broad/phrase/exact campaigns for the same theme, SKAG-era ad group sprawl, brand terms scattered across non-brand campaigns.

## Dimension C — Bidding Strategy

Bidding is audited *after* tracking and structure because it can only be fairly judged once you know the data is sound and the structure can feed it. See [[smart-bidding]].

The four checks:

1. **Strategy fits the goal.** Value-based bidding (Max Conv Value / tROAS) where value varies (ecomm, value lead gen); tCPA on a *qualified* outcome for lead gen; a deliberate reason for any Manual/Max-Conversions choice. *Critical* if the strategy is fundamentally mismatched to the objective (e.g. tROAS with no value data, or Manual on a campaign that should be automated and has the data for it).
2. **Target achievability.** Are targets derived from economics and sane relative to **trailing 30–60 day actuals**, or aspirational? A tROAS/tCPA set far tighter than the account has ever achieved starves delivery. *Critical* when an unachievable target is visibly throttling volume; *Warning* when targets are aggressive but delivery holds.
3. **Target whiplash / stuck learning.** Evidence of frequent target/budget changes or campaigns perpetually in learning. *Critical* when constant changes are preventing the account from ever stabilising; *Warning* for occasional over-management.
4. **Optimising to the correct conversion.** Does the strategy actually point at the right conversion action (ties directly to Dimension A, checks 1 and 3)? *Critical* if a sound strategy is aimed at the wrong/weak conversion — a good engine driving toward the wrong destination.

How to read target achievability: compare each campaign's target to its trailing actual CPA/ROAS and its impression-share-lost-to-rank/budget. **Target whiplash** shows up as a change history full of target edits, volatile day-to-day CPA/ROAS, and "learning" statuses that never clear — it's damaging because every change restarts learning, so the account lives in permanent instability and never reaches the performance the strategy could deliver.

## Dimension D — Creative and Assets

Creative is audited as an **asset-pool diversity and relevance** question (see [[creative-strategy]]). The system is a combinatorial tester; the audit asks whether it's been given enough distinct, relevant material to work with.

The four checks:

1. **RSA asset variety.** Do RSAs provide genuinely *distinct angles* (benefit, proof, offer, feature, brand) or fifteen rewordings of one idea? *Warning* in most cases (semantic repetition caps potential rather than breaking serving); escalates where coverage is so thin the ad can't compete.
2. **Pinning and Ad Strength handling.** Is pinning used sparingly (not locking every position and killing the combination engine), and is the account chasing "Excellent" with stuffed keyword-laden assets? Treat Ad Strength as a coverage signal, not a target. *Warning*.
3. **PMax asset coverage.** Do asset groups have **full format coverage** — all image ratios (1:1, 1.91:1, 4:5), video, multiple logos — and are they tightly themed to a landing page? Missing formats lock the campaign out of inventory (see [[pmax]]). *Critical* when missing assets materially cut reach or force auto-generated low-quality creative; *Warning* for partial gaps.
4. **Message match.** Does the ad-to-landing-page promise hold for key campaigns? *Warning* (it depresses conversion rate and Quality Score rather than breaking the account), escalating where mismatch is severe.

Assessing variety from an export: read the headline/description assets and group them by angle — a heavy clustering in one angle with empty angles elsewhere signals semantic repetition. **Auditing message match without the live page:** you won't always have the landing page, so audit what you *can* — does the final URL look intent-appropriate (specific product/service page vs generic homepage), does the ad's offer/claim have a plausible destination, and do asset performance ratings or low conversion rates on otherwise healthy campaigns hint at a post-click leak? Flag message match as a check to verify on the live page rather than asserting it from data alone.

## Dimension E — Search Term Quality

The finest-grained layer, audited last because query-level action only pays off once the foundations are sound. See [[search]].

The four checks:

1. **Negative coverage.** Are shared negative lists in place and obvious waste (jobs, DIY, free-seekers, irrelevant modifiers) excluded? *Warning* normally; *Critical* when the absence of negatives is driving large, visible wasted spend.
2. **n-gram waste.** Does n-gram analysis of the search terms report surface high-spend / zero-conversion themes? *Critical* when a single recurring n-gram is consuming meaningful budget with no return; *Warning* for smaller leaks.
3. **Match-type strategy fit.** Does the match-type mix fit the account — broad only where clean conversion data and Smart Bidding support it, more conservative phrase/exact on thin or high-CPA accounts (see [[lead-gen]])? *Warning* for a mismatch; *Critical* when wide-open broad on weak data is visibly hemorrhaging budget.
4. **Search/PMax cannibalisation.** Is exact-match Search protecting high-intent terms, and is brand kept out of PMax? *Warning* to *Critical* depending on how much value is leaking across the boundary.

**The n-gram method:** break the search terms report into unigrams and bigrams, aggregate cost and conversions by n-gram, and surface the words/pairs that consistently spend without converting — a single bad token ("free", "job", a wrong-fit modifier) often spans hundreds of wasteful queries, so you negate the *n-gram*, not each query. **Reading match-type strategy** from the report: high spend on loosely-related, non-converting queries signals broad running ahead of the data. **Identifying cannibalisation** from available data: look for brand queries appearing in PMax/non-brand campaigns, overlap between PMax and Search on high-intent terms, and the absence of exact-match coverage on terms you'd want to control — the channel-overlap picture (and a PMax channel-breakdown script) tells you where Search and PMax are competing for the same demand.

## Severity ratings

Every check is rated **Pass / Warning / Critical**. Clear definitions keep the audit consistent and the action list honest.

- **Pass** — the check meets best practice (or is a non-issue for this account). No action needed; note it so the report shows what's working.
- **Warning** — **suboptimal but not breaking.** Performance is being left on the table, but the account isn't actively corrupting data or blocking the bidding. Real, worth fixing, not urgent. (Most creative, enhanced-signal, and minor-segmentation findings.)
- **Critical** — **blocks performance, corrupts data, or cannot be safely ignored.** It meets at least one of: it *invalidates the conversion data* (and therefore the bidding and the reporting), it *starves or throttles* Smart Bidding (fragmentation, budget caps, unachievable targets), or it is *causing large, visible, ongoing waste*. Criticals are the headline of the audit and the front of the action list.

**How severity interacts with effort:** severity sets the *priority*; effort sets the *sequence within it*. The prioritised action list sorts by severity first (Criticals before Warnings) and by impact next — but effort is what surfaces the **quick wins**: a Critical that's also low-effort is the first thing to do, full stop. A Critical that's high-effort becomes a planned project; a low-effort Warning can be swept up cheaply alongside bigger work. Severity says *what matters*; effort says *what to do first within what matters*.

## Using the audit output

- **Prioritise the action list** by severity, then impact, then effort. Criticals lead; among them, do the high-impact / low-effort items first.
- **The quick-wins vs strategic-projects split.** **Quick wins** = high impact, low effort (add the missing negative list, fix the duplicate conversion, fence brand out of PMax) — do these immediately; they build momentum and credibility. **Strategic projects** = high impact, high effort (rebuild tracking with OCI, consolidate a fragmented account, restructure by performance tier) — these need planning, sequencing, and a learning-period budget, and should be scheduled deliberately, one change at a time (see [[campaign-structure]] on restructuring).
- **Presenting findings to a client.** Lead with the **executive summary** (plain-language health verdict + the headline opportunity), then the prioritised actions. Frame causes and money, not platform jargon — "your bidding is optimising on inflated data" beats a screenshot of tag settings. Be honest about Criticals; a credible problem named early builds trust. Set expectations that the big fixes carry a temporary learning dip.
- **When to re-audit.** Full audit on onboarding and then **quarterly**; an interim audit after any major restructure (once it has cleared learning and stabilised — don't re-audit mid-flux), after a significant tracking change, or when performance shifts in a way the routine [[campaign-review]] can't explain. Between audits, the lighter [[campaign-review]] skill handles ongoing optimisation.

## Related
Executed by the [[account-audit]] skill. Grounded in [[smart-bidding]], [[campaign-structure]], [[pmax]], [[search]], [[creative-strategy]]; contexts [[lead-gen]] / [[ecomm]]. Companion: [[pmax-audit-framework]]. Feeds [[campaign-review]] and [[monthly-report-brief]].
