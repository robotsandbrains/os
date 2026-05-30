---
title: Campaign Structure
version: v0.1
updated: 2026-05-31
status: draft
---

# Campaign Structure

## Why structure matters more than ever

Structure matters more than ever — but for the opposite reason it used to. In 2015, structure was a **control** mechanism: tightly-themed ad groups let you set precise bids, write precise ads, and route precise queries to precise destinations. You manually managed the mapping of query → bid → ad, and granularity gave you that control.

You don't set bids anymore. Smart Bidding does, at auction time, using signals you can't see (see [[smart-bidding]]). So structure's old job is gone — and its new job is **signal consolidation.** Campaign and ad group boundaries now determine one thing above all: *whether Smart Bidding has enough conversion data, pooled in one place, to learn well.* The model learns at the campaign level. Every boundary you draw divides the conversion signal on either side of it. Draw too many, and you hand the model a dozen data-starved fragments instead of one well-fed campaign that could actually optimise.

This is why the 2015 playbook **actively hurts** in 2025. Themed-ad-groups-for-relevance, SKAGs, splitting by match type, mirroring every category into its own campaign — all of it fragments the exact resource Smart Bidding depends on. The instinct that used to be "good account hygiene" is now self-sabotage. The shift to internalise: **from themed ad groups for relevance, to consolidated campaigns for volume.** Relevance is now carried by RSAs, broad match, and landing-page alignment; volume is carried by structure. Get the volume question right first.

## The consolidation principle

**Fewer, better-fed campaigns outperform many fragmented ones.** This is not a stylistic preference — it's a direct consequence of how Smart Bidding works. The model needs conversion volume to learn, it learns per campaign, and learning quality degrades as volume thins. Concentrate conversions and the model optimises confidently; scatter them and it never exits the unstable, exploratory phase on any single campaign.

**What consolidation means in practice:**
- Combine campaigns that share a goal, a bid target, and a budget priority into one, rather than running parallel near-duplicates.
- Let broad/phrase match and RSAs do the query-and-message work *inside* a consolidated campaign, instead of pre-splitting intent into many campaigns.
- Pool conversion signal so each campaign clears a meaningful volume threshold.

**The threshold that should govern structure decisions:** roughly **~30+ conversions per campaign per 30 days** as a working minimum for Smart Bidding to learn well — more is better, and value-based bidding wants more still. Use this as your structural test: *if splitting a campaign would push either resulting half below that threshold, don't split it.* Structure decisions should be made in units of conversions, not tidiness.

**When consolidation goes too far:** consolidation is the default, not an absolute. Some segmentation is genuinely warranted when a boundary lets you *manage something differently* (next section) — different margins you must bid differently, different budgets you must protect, materially different goals. The failure mode at the extreme is one giant campaign mixing brand and non-brand, high-margin and clearance, prospecting and remarketing, all under one blunt target — that under-segmentation is as real a mistake as over-segmentation. Consolidate until further consolidation would force genuinely different things to share a single goal and budget. Then stop.

## How to segment when you must

The governing rule, and the only test you need: **only create a new campaign if you would manage it differently.** If two would-be campaigns share a goal, a target, and a budget priority, they're one campaign. If they don't, they're two. Everything below is that rule applied.

**Right reasons to segment** — these reflect genuine management differences:
- **Margin / value tier** — products or services with materially different profitability you want to bid differently (a high-margin line at an aggressive target vs a thin-margin line at a conservative one).
- **Geography** — markets you'll budget, target, or measure separately (different countries, regions with different economics or languages).
- **Budget priority** — spend you must ring-fence (a brand-funded line, a strategic push you won't let the rest of the account cannibalise).
- **Audience / goal** — genuinely different objectives (new-customer acquisition vs total revenue; prospecting vs retention) that need different targets or measurement.

**Wrong reasons to segment** — these fragment signal for control you no longer get or need:
- **Keyword themes** — themes belong in ad groups (or are handled by broad + RSAs), not separate campaigns.
- **Match types** — splitting broad/phrase/exact into separate campaigns is a legacy reflex that scatters data; mix match types within a campaign and steer with negatives.
- **Device, ad scheduling, audiences as segmentation** — these are bid signals and settings the model already uses; they are not reasons to create campaigns.

**Segment by performance tier, not by category.** The most common structural error is mirroring the catalogue or service menu — one campaign per category because that's how the business is organised. The model doesn't need that; it reads keywords, feeds, and pages. Segment instead by **how the economics differ**: best-sellers / high-margin, mid-tier, clearance/low-performer — each at the target its economics justify. This puts budget where the return is and gives the model a clean goal per tier, which is what it actually rewards (see [[pmax]] for the same principle applied to asset groups).

## Budget and bidding architecture

Campaign boundaries *are* your budget boundaries — budget is set and spent at the campaign level, so structure directly determines where money can flow. This is the mechanism behind the consolidation argument: **split one healthy campaign into five and you've created five budgets, five learning processes, and five thinner conversion pools** — each now bidding with less data and constrained by a smaller slice of budget. The whole frequently performs worse than the consolidated original, and takes longer to stabilise after every change.

- **Structure and bidding are one decision.** A Smart Bidding strategy is only as good as the conversion volume in its campaign. Designing structure without thinking about the resulting per-campaign volume is designing the bidding to fail. Always ask: after this split, does each campaign still clear the volume threshold?
- **Shared budgets** help when several consolidated campaigns serve one goal and you want the system to allocate across them fluidly rather than manually babysitting individual caps. They *obscure* when you need to know exactly what a campaign spends (reporting, client ring-fencing) or when one campaign quietly eats a shared pool the others needed. Use shared budgets to reduce micro-management among like-goaled campaigns; avoid them where accountability or protection matters.
- **Portfolio bid strategies** pool several campaigns under one target so they learn on combined volume — genuinely useful when you have several small-but-related campaigns that individually fall below the learning threshold, letting them share a signal pool. They're worth the added complexity *only* when that pooling solves a real volume problem; otherwise standard campaign-level strategies are simpler and clearer. Don't reach for portfolios as a default — reach for them to rescue under-volume campaigns you can't otherwise consolidate.

## Ad group structure in an RSA world

**SKAGs are dead.** Single keyword ad groups were the purest expression of the control era — one keyword, one ad group, total mapping control. In a world of close variants, broad match, and RSAs, that control is illusory (close variants mean a SKAG serves many queries anyway) and the cost is severe: maximum fragmentation of conversion signal across hundreds of tiny ad groups that never learn. Don't build them; unwind them where you find them.

So what do ad group themes mean now, when RSAs and broad match deliberately blur keyword-to-query matching? An ad group is no longer a query-control unit — it's a **relevance-and-message unit.** Its job is to keep keywords, the RSA's assets, and the landing page thematically coherent so the ad stays relevant to the queries the system serves on. You need *enough* theme tightness for one RSA to be genuinely relevant to the whole ad group — and no more.

- **Group keywords by shared intent and shared message**, into ad groups big enough to carry meaningful traffic. A handful of broad/phrase keywords around one theme, one RSA, one page.
- **The landing page is the primary organising principle.** If two keyword sets should send traffic to the same page with the same message, they belong in the same ad group. If they need different pages or different messages, split them. Organise ad groups around destinations and messages, not around keyword variants. See [[creative-strategy]] for what goes inside the RSA.

## Account-level architecture

Zoom out from individual campaigns to how they relate as an ecosystem — Search, PMax, and Shopping competing in the same auctions for overlapping demand. Structure isn't just within-campaign; it's the boundaries *between* campaign types, and the main risk is **signal cannibalisation across campaigns.**

- **Mind the matching hierarchy.** Exact-match keywords in Search always win their queries; against everything else Ad Rank decides, and PMax frequently wins. So PMax will absorb non-exact and brand demand from Search unless you fence it (see [[pmax]] and [[search]]). Account architecture is largely the deliberate management of these overlaps.
- **The brand vs non-brand split still matters** — arguably more than any other single split. Brand traffic is cheap, high-converting, and would flatter any campaign it lands in; mixing it with non-brand pollutes your data, inflates Smart Bidding's apparent performance, and hides the true cost of acquisition. Keep brand in its own (usually exact-match) Search campaign and fence it out of PMax with brand exclusions. This is the one segmentation almost every account should make regardless of the consolidation default — because brand and non-brand are genuinely *managed differently* (different targets, different expectations, different reporting).
- **Auditing an existing structure for fragmentation:** list every campaign with its trailing-30-day conversions; flag any below the learning threshold and ask why it's separate. Look for near-duplicate campaigns that could merge, category-mirrored campaigns that should be performance-tiered, match-type or device splits that should collapse, and SKAG-era ad group sprawl. Map the Search/PMax/Shopping overlap and check brand isn't bleeding into PMax. The fragmentation usually announces itself as a long list of low-conversion campaigns. See [[account-audit-framework]].

## Structural anti-patterns

Five patterns you'll inherit or be tempted to build — name them, kill them:

1. **SKAGs / over-themed ad groups.** Hundreds of single- or few-keyword ad groups, each starved of data. *Why it hurts:* maximum signal fragmentation for control close variants already negate. *Instead:* consolidate into intent-and-page-themed ad groups with enough volume to learn.
2. **Category-mirrored campaigns.** One campaign per product category or service line because that's the org chart. *Why it hurts:* splits budget and signal along lines the model doesn't need, and bids unlike-economics products at one blunt target. *Instead:* segment by performance/margin tier; let feeds and keywords handle category.
3. **Match-type-split campaigns.** Separate broad, phrase, and exact campaigns for the same theme. *Why it hurts:* legacy reflex that scatters conversion data three ways and complicates negatives. *Instead:* mix match types within a consolidated campaign and steer with negatives.
4. **Brand and non-brand mixed together.** Cheap brand conversions inflate a campaign that's really carrying non-brand. *Why it hurts:* corrupts Smart Bidding signal and hides true CPA/ROAS. *Instead:* isolate brand in its own campaign and exclude it from PMax.
5. **Over-segmentation by setting (device / geo / schedule / audience).** Spinning up campaigns to "control" things the model already uses as signals. *Why it hurts:* multiplies starved campaigns for control you don't actually gain. *Instead:* leave these as bid signals and settings inside consolidated campaigns; only split geo when economics or budgets genuinely differ.

## Restructuring an existing account

Consolidation is usually the right call on an inherited account — but a restructure is a series of learning-period resets, so do it deliberately, not in one weekend slash-and-merge.

- **Phased approach.** Don't rebuild everything at once. Sequence it: (1) audit and map current structure and per-campaign volume; (2) fix the highest-leverage, lowest-risk consolidation first (collapse obvious duplicates, merge starved campaigns, kill SKAGs); (3) let each change settle and stabilise before the next; (4) tackle the bigger structural merges once you trust the pattern. Change one structural thing at a time so you can attribute the result.
- **Preserve history where it counts.** Build new consolidated campaigns thoughtfully rather than deleting everything — moving high-converting keywords and proven assets into the new structure, and being aware that new campaigns start learning fresh. Stagger so the account isn't *all* in learning simultaneously.
- **What to watch during and after.** Expect a dip and volatility while merged campaigns re-learn — that's the learning period (see [[smart-bidding]]), not failure. Watch total account-level conversions, CPA/ROAS, and impression share, not just the new campaign's self-reported numbers. Hold your nerve through learning; don't pile on changes mid-flux. Judge the restructure on stabilised post-learning performance against the pre-restructure baseline.
- **Making the case to a stakeholder attached to the old structure.** Clients and colleagues are often emotionally invested in the granular structure they built. Don't argue aesthetics — argue mechanism and money: explain that Smart Bidding learns on pooled conversion volume, that the current fragmentation starves it, and that consolidation feeds it. Frame it as *giving the automation the data it needs to spend their budget better*, set the expectation of a temporary learning dip up front, and agree the success metric (stabilised account-level CPA/ROAS) before you start so the inevitable mid-learning wobble doesn't derail the plan. See [[account-audit]] and [[campaign-review]] for the supporting analysis.

## Related
[[smart-bidding]], [[search]], [[pmax]], [[shopping]], [[creative-strategy]], [[audience-strategy]], [[account-audit-framework]], [[lead-gen]], [[ecomm]].
