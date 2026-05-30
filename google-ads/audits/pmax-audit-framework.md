---
title: PMax Audit Framework
version: v0.1
updated: 2026-05-31
status: draft
---

# PMax Audit Framework

## What this framework is

This is a **structured diagnostic for evaluating the health of a Performance Max campaign** — the methodology a practitioner works through to decide whether a PMax campaign is *working, wasting, or broken*. It is the PMax-specific companion to the broader [[account-audit-framework]], and it exists because **PMax needs its own framework.** PMax is opaque *by design*: no placement-level control, no full search-term report, no native channel breakdown, conversions pooled across six surfaces and self-reported in the campaign's favour. A standard account audit — built around query data, structure, and visible levers — sails straight past the failure modes that actually matter in PMax, because the campaign hides them. This framework is built around that opacity: it tells you where to look *given* that Google won't just show you.

**What this framework can tell you:** whether the inputs are sound (assets, signals, tracking, settings), whether the reported performance is *trustworthy*, and — through scripts/API and segmentation analysis — roughly how PMax is actually spending and whether it's growing the business or recycling existing demand.

**What it cannot tell you:** PMax does not expose a clean per-inventory breakdown natively, full query-level data, or placement-level transparency. You work with what Google exposes — the Insights tab (search *categories*, not terms), asset performance labels, the new-customer reporting, and what you can extract via the **channel-breakdown script or the Google Ads API**. Treat every conclusion as "best available read," not ground truth, and verify against account-level totals rather than PMax's own numbers. See [[pmax]] for the campaign-type detail this framework audits against.

## The PMax audit dimensions

Six dimensions, run in this order — and as with the account framework, **the order is dependency, not preference:**

**Asset & Creative Quality → Audience Signals → Conversion Tracking & Goals → Campaign Structure & Settings → Performance Diagnosis → Search/PMax Interaction**

- **Assets come first because PMax is creative-led.** Within the inputs you control, the asset pool is the single biggest determinant of where PMax can serve and how well — missing formats literally lock the campaign out of inventory. It's the most common and most fixable failure, so you check it first.
- **Signals come second** because, after creative, audience signals are the main lever you feed the model — they shape how fast and how well it learns.
- **Conversion tracking & goals comes third — but it gates everything in Performance Diagnosis.** You verify creative and signals as *inputs* first, but you must confirm the conversion data is trustworthy **before you believe a single performance number.** A PMax campaign optimising toward the wrong conversion performs *confidently in the wrong direction* — so tracking is audited before any performance judgement is allowed.
- **Structure & settings (fourth)** covers the controls that fence and shape PMax — checked before performance because a missing brand exclusion or wrong URL-expansion setting *explains* performance distortions.
- **Performance Diagnosis (fifth)** can only happen honestly once the four input dimensions above are verified — otherwise you're diagnosing a number you haven't earned the right to trust.
- **Search/PMax Interaction (last)** is the account-level overlap question — the finest-grained, most downstream layer, only worth resolving once the campaign itself is sound.

## Dimension A — Asset and Creative Quality

PMax is creative-led; the asset pool decides inventory eligibility and serving quality (see [[creative-strategy]] and [[pmax]]). What to check:

1. **Full asset coverage.** All image ratios (1:1, 1.91:1, 4:5), **video**, multiple logo formats, the full complement of headlines/long headlines/descriptions. Each missing format removes inventory the campaign can appear on — coverage *is* reach.
2. **Asset group theming vs landing page alignment.** Each asset group tightly themed to one coherent message and a *relevant* landing page, not a generic catch-all pointed at the homepage. Theme drift gives the model nothing to anchor relevance on.
3. **Ad Strength as a coverage diagnostic, not a performance score.** Read it as "have I supplied enough distinct assets and formats," never as a prediction of results. Don't let "Excellent" reassure you and don't chase it with stuffed assets.
4. **Asset performance ratings — what Low/Good/Best actually mean.** They're *relative* labels for how an asset contributes to served combinations, not absolute quality verdicts. "Best" earns its place; **"Low"** means under-contributing — but distinguish a *redundant* Low asset (replace it with a new angle) from one providing *necessary coverage* of a format or angle (keep it). Many "Learning"/unrated assets just mean insufficient data yet.

**Critical failures here:** **no video** (forfeits YouTube and forces auto-generated low-quality creative); a **single asset group covering a large/varied catalogue** (no thematic relevance, no tier control); **Ad Strength Poor with missing formats** (the campaign is locked out of inventory). These are Critical because they cap what the campaign can *physically* do before any optimisation question arises.

## Dimension B — Audience Signals

Signals are inputs that accelerate learning, not constraints (see [[audience-strategy]] and [[pmax]]). What to check:

1. **Customer Match present and fresh.** Are converter / high-value lists uploaded and *maintained* (auto-updated or recently refreshed), or stale or absent? Customer Match is the highest-value signal; a missing or rotting list is a real miss.
2. **Signal quality — converters vs generic interests.** Are the audience signals built from *actual converters and first-party data*, or are they generic in-market/affinity buckets that give the model a weak starting point? Signal *quality* drives how useful the head-start is.
3. **New vs established signal approach.** A *new* campaign should be seeded with strong signals early to shorten learning; an *established* campaign relies more on its own accumulated conversion history, with refreshed lists still helping after seasonal shifts. Check the approach fits the campaign's maturity.
4. **What no-signals costs.** A signal-less PMax still runs but learns slowly and expensively, exploring blindly until conversions accumulate — on low-volume accounts that burns real budget. *No signals where first-party data exists* is a clear finding.

**Assessing signal quality from the inputs available:** look at what's attached to each asset group — are there Customer Match lists (and are they recent), are custom segments built from high-intent search/URL behaviour, or is it just off-the-shelf interest audiences? Strong, fresh, first-party signals = Pass; generic-only = Warning; none-despite-available-data = Warning toward Critical on a young or thin campaign.

## Dimension C — Conversion Tracking and Goals

**Weighted most heavily**, and for a sharper reason than in the general audit: PMax is opaque, so you can't eyeball *which* serving caused a conversion — which means you are even more dependent on the conversion data being true. A PMax campaign optimising toward the wrong thing will **perform confidently in the wrong direction**, and the opacity hides it. Verify this before trusting any performance number. What to check:

1. **Primary conversion is the right outcome.** Purchase value for ecomm; a *qualified* lead / OCI-fed outcome for lead gen — **not raw form fills.** Lead-gen PMax optimising to un-screened form fills with no OCI is the archetypal PMax money-waster (see [[lead-gen]]): it will flood you with cheap junk and report a great CPA.
2. **Conversion values present and dynamic (ecomm).** Real per-transaction values (ideally margin/profit-aware), not static or placeholder values — value-based bidding is only as good as the values fed (see [[ecomm]] and [[smart-bidding]]).
3. **No junk or duplicate conversions inflating apparent performance.** Deduplication (transaction IDs), no double-counted or auto-tracked junk actions puffing up the numbers. In PMax, inflated conversions are especially dangerous because you can't see where they came from.
4. **Enhanced conversions configured** (plus Consent Mode), so the data feeding the model is as complete as possible.

**Critical** whenever the campaign is optimising toward the wrong or junk conversion, or running value-based bidding on absent/placeholder values, or — for lead gen — running without OCI. This dimension can invalidate every number in Dimension E, which is exactly why it's verified first.

## Dimension D — Campaign Structure and Settings

The controls PMax *does* give you — mostly about fencing and shaping (see [[pmax]]). What to check:

1. **Brand exclusions in place.** Brand-exclusion list / brand restrictions applied so PMax isn't claiming cheap brand conversions and flattering its own performance. (Verified again from the interaction angle in Dimension F.)
2. **URL expansion settings appropriate.** Final URL expansion **off** (or restricted with URL exclusions) when destination/message control matters; on only when you trust it to find relevant deep pages. Unmanaged URL expansion sends traffic and auto-generated headlines anywhere on the site.
3. **Account-level negative keywords applied** for brand control, irrelevant terms, and known junk (now available for PMax — use them).
4. **Location and ad scheduling** set correctly (PMax respects these), and target-location settings (presence vs presence-or-interest) appropriate.
5. **Budget adequacy vs the learning threshold.** Enough budget and conversion volume (~30+ conv/30 days as the working floor) for the campaign to learn; not so starved it never stabilises (see [[campaign-structure]]).
6. **Feed-only vs full-asset choice justified.** For ecomm/lead gen, is the asset configuration deliberate — feed-only/asset-light where tighter control and efficiency are wanted, full-asset only where the broader inventory spread is intended?

**Settings that matter vs settings that don't:** the ones above (especially brand exclusions, URL expansion, negatives, budget) materially change outcomes. Don't waste the audit on cosmetic settings PMax overrides or that have negligible effect — focus on the fences and the feed/asset decision.

## Dimension E — Performance Diagnosis

Now — and only now that tracking is verified — judge performance, honestly, *around* the opacity. The governing question: **is PMax creating/growing demand, or harvesting demand the account already had and re-attributing it to itself?**

- **Channel breakdown (script or API).** PMax doesn't natively show the Search/Shopping/Display/YouTube spend-and-conversion split — pull it with the community **channel-breakdown script** or the Google Ads API. This is often the single most revealing diagnostic: a PMax that's quietly 70% cheap Display/remarketing is a completely different campaign from one serving on Shopping and Search, even at the same reported ROAS.
- **Separate brand from non-brand contribution.** Use the Insights search-category data, brand-exclusion testing, and the channel/term signals available to estimate how much of the "performance" is just brand demand you already owned. Great PMax numbers that are mostly brand are not growth.
- **New vs returning customer share.** Use the new-customer reporting (requires maintained Customer Match) to see whether PMax is acquiring new customers or recycling existing ones. For ecomm especially, this separates real growth from cheap repeat-purchase harvesting.
- **Creating vs harvesting demand.** Triangulate the above: heavy remarketing/Display lean + mostly brand + low new-customer share = harvesting and re-attributing. Genuine Shopping/Search serving + non-brand + new customers = creating value.
- **The incrementality question without a formal holdout.** A true geo/holdout lift test is the gold standard, but when you can't run one, approximate: compare **account-level** conversions/revenue and new-customer volume before vs after PMax launched (did the *total* move, or did PMax's numbers just appear while Search's fell?), watch brand-search and total-conversion trends, and treat PMax's self-reported ROAS with suspicion until account-level totals corroborate it. The mantra: **judge PMax by what the account did, not by what PMax says it did.**

## Dimension F — Search/PMax Interaction

The account-level overlap, audited last (see [[search]] and [[pmax]]). The hierarchy to verify: **exact-match keywords in a Search campaign always win their query**; against everything else Ad Rank decides, and PMax often wins. What to check:

1. **Exact-match Search is protecting high-intent terms.** Confirm your highest-intent commercial terms exist as exact-match in Search so the hierarchy guarantees Search — not PMax — serves them. Gaps here mean PMax can absorb demand you meant to control.
2. **Brand exclusion verification.** Confirm brand is genuinely fenced out of PMax (brand list/exclusions actually applied and working), cross-checking against Dimension D — and look for brand queries surfacing in PMax's insights as evidence of a leak.
3. **Identifying cannibalisation from available data.** Look for brand/high-intent terms appearing in PMax search-category insights, a drop in Search impression share or conversions coinciding with PMax ramp, and channel-breakdown evidence of PMax serving on Search inventory for terms Search should own.
4. **Healthy vs absorbing.** *Healthy:* PMax adds incremental reach across inventory Search can't touch, while exact-match Search and brand exclusions keep PMax off the demand you already own. *Absorbing:* PMax is eating brand and high-intent generic spend that Search would have captured more cheaply, inflating PMax's apparent performance at the account's expense.

## Severity ratings for PMax

Same **Pass / Warning / Critical** scale as the account framework, applied in the PMax context:

- **Pass** — meets best practice for PMax; note what's working.
- **Warning** — suboptimal but not breaking: generic-only signals, partial asset gaps, URL expansion left on without disaster, mild cannibalisation. Worth fixing, not urgent.
- **Critical** — blocks performance, corrupts data, or causes large hidden waste. **PMax-specific Criticals:** **no brand exclusions** (PMax claims and inflates on brand); **wrong/junk primary conversion** (especially **OCI missing for lead-gen PMax** — optimising to cheap form fills); **no video / missing formats blocking inventory**; **value-based bidding on absent/placeholder values**; **a single asset group spanning a large catalogue**; **budget/volume so thin the campaign can't learn**. These share the theme that PMax's opacity lets them do damage *invisibly* — which is why they rank Critical even when the reported numbers look fine.

**How PMax severity interacts with the broader account audit:** this framework drills into a campaign type the [[account-audit-framework]] only touches at a high level. Roll PMax Criticals up into the account-level prioritised action list — a PMax conversion-tracking or brand-exclusion failure *is* an account Critical. Run this framework whenever PMax carries meaningful spend; use the account framework for the whole-account view and this one for the PMax deep-dive.

## What to do with the findings

- **Prioritise in dependency order:** **tracking first, then assets, then signals, then settings**, with Search/PMax interaction addressed once the campaign itself is sound. Fixing assets while the campaign optimises toward a junk conversion is wasted effort — correct what the model *aims at* before you improve what it *serves*.
- **Sequence within that:** Criticals before Warnings; among Criticals, high-impact / low-effort first (apply a brand exclusion, switch the primary conversion, upload a Customer Match list) before the heavy lifts (rebuild tracking with OCI, re-segment asset groups by performance tier, add full video coverage).
- **Presenting findings to a client who doesn't get the opacity.** Explain *why* PMax is a black box in plain terms — "Google runs it as one automated campaign across all its platforms and deliberately limits what it shows us, so our job is to control the inputs and verify the outputs it does give." Frame findings as inputs-and-verification ("we're feeding it the wrong goal" / "its great results are mostly your existing brand traffic") rather than knobs you failed to turn. Manage the expectation that improvements run through a learning period.
- **Pause and rebuild vs fix in place.** **Fix in place** when the foundations are sound and the issues are additive — missing exclusions, signals to add, a conversion to switch, assets to complete. **Pause and rebuild** when foundations are fundamentally wrong in ways that have trained the model badly: the campaign has been optimising to the wrong conversion for a long time, structure is unsalvageable (one asset group for everything, no usable tiering), or it's been harvesting brand/existing demand while reporting fake success. Weigh the rebuild against the learning-period reset it triggers (see [[smart-bidding]]) — sometimes a clean rebuild with correct inputs beats nursing a campaign that learned the wrong lessons.

## Related
Companion to [[account-audit-framework]]; executed in spirit by the [[account-audit]] skill. Grounded in [[pmax]], [[smart-bidding]], [[creative-strategy]], [[audience-strategy]], [[search]], [[campaign-structure]]; contexts [[lead-gen]] / [[ecomm]].
