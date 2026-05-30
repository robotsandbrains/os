---
title: Smart Bidding
version: v0.1
updated: 2026-05-31
status: draft
---

# Smart Bidding

## What Smart Bidding actually is

Smart Bidding is an auction-time machine learning system that sets a unique bid for every single auction, based on signals you cannot see and cannot fully audit. That last part is the part most practitioners never fully internalise. When someone searches, the model evaluates dozens of contextual signals in real time — device, time of day, day of week, location, browser, language, OS, the specific query, audience membership, remarketing-list presence, historical site behaviour, and a long tail of cross-signal combinations — and decides what this particular click is worth to you. You don't set bids anymore. You set a *goal*, and you control the *inputs*.

This is the mental shift: your job is no longer "what should I bid on this keyword." It's "am I giving the model a clean goal and clean data to optimise toward." The bid is the model's output, not yours. The signals that matter most are the ones tied to commercial intent and the ones derived from your own first-party data — query intent, audience signals, and conversion history carry far more weight than the cosmetic levers practitioners used to obsess over. Once you accept that the model out-computes you at the auction level, campaign management becomes about feeding it well: clean conversions, sensible structure, enough volume, and a goal that matches the business. See [[campaign-structure]] for how structure becomes a signal-consolidation exercise rather than a control exercise.

## The bidding hierarchy

There are really only two questions: **are you optimising for conversions or for value?** and **do you have an efficiency constraint or not?** That gives you the matrix.

- **Maximise Conversions** — spend the budget to get the most conversions, no efficiency target. Use it when conversions are roughly equal in value (most lead gen), and when you're early and want volume to build conversion history. The risk: with an uncapped budget it will chase volume at any CPA. Only run it on a controlled budget.
- **Maximise Conversions + Target CPA** — same, but with an efficiency guardrail. This is the default mature lead-gen strategy. Use it once you have stable conversion volume and a defensible CPA target.
- **Maximise Conversion Value** — spend the budget to get the most total value, no efficiency target. Use it when conversions differ in value (ecomm, value-based lead gen) and you're feeding real values back. Same uncapped-efficiency caveat as Max Conversions.
- **Maximise Conversion Value + Target ROAS** — the default mature ecomm strategy. Use it when you have meaningful value data and enough conversion volume to support a target.
- **Manual CPC (and Enhanced CPC):** Manual still makes sense in exactly three cases: (1) brand campaigns where you want tight, cheap control and the model has little to optimise; (2) tiny-volume accounts that will never feed a Smart Bidding model enough data to learn; (3) diagnostic periods where you deliberately want a flat baseline. Outside those, manual is leaving money on the table. eCPC is a deprecated halfway house — don't build a strategy on it.

**Decision framework:**
1. Do conversions vary in value? No → conversion-based (Max Conv / tCPA). Yes → value-based (Max Conv Value / tROAS).
2. Do you have ~15+ conversions in the last 30 days at the optimisation level? No → start with the uncapped variant on a controlled budget to build history. Yes → add the target.
3. Is the account too small to ever generate that volume, or is it pure brand defence? → Manual CPC is legitimate.

## Target setting

Set targets from your economics, not your ambitions. The single most common way practitioners kneecap a campaign is setting an aspirational target the account has never historically hit, then wondering why delivery collapses. The model can only buy auctions that clear your target; set tCPA far below your real CPA and it simply stops bidding on most of the auction landscape, volume craters, and the campaign starves.

**Calculate a starting target from first principles.** For lead gen: take your average order value (or deal value) × close rate × the margin or CPA-to-revenue ratio the business can tolerate. If a closed deal is worth $4,000, you close 20% of qualified leads, and you'll spend up to 25% of gross profit on acquisition, work backwards to the lead CPA that math supports — don't pluck a round number. For ecomm: tROAS = 1 ÷ (the margin fraction you're willing to spend on ads). Want to spend at most 25% of revenue → tROAS = 400%.

**The practical rule:** start your target at or slightly *looser* than the account's trailing 30–60 day actual, let it stabilise, then tighten in 10–15% steps with a week-plus between moves. Every target change is a re-learning event. Tightening a tROAS from 300% to 500% in one move is not "being ambitious," it's resetting the campaign. Targets and volume are linked: the tighter the target, the less volume clears it, the slower the model learns — which is why aggressive targets on thin accounts are doubly punishing.

## The learning period

Learning is the window where the model is recalibrating and delivery is unstable — wider CPA swings, volatile volume, unreliable daily numbers. It's triggered by anything that materially changes what the model is optimising: a new strategy, a target change beyond ~15–20%, a big budget change, structural changes that move conversion volume, or a conversion-action change.

Google's official line is "about 7 days." The real-world range is **1 to 3 weeks**, and it's gated by *conversions, not days*. A campaign needs roughly 2–3 weeks *and* enough conversions (rule of thumb: ~30+ during the window) to genuinely exit. A high-volume account can stabilise in a week; a low-volume lead-gen campaign can technically show "eligible" while still behaving like it's learning for a month.

**During learning, don't touch it.** No target tweaks, no budget swings, no structural surgery, no new conversion actions. Stacking changes restarts the clock and you never get a clean read. **How to tell it genuinely exited:** status shows eligible/optimising *and* daily CPA/ROAS has settled into a stable band over 5–7 days *and* volume is steady. If the status cleared but numbers are still swinging wildly, it's stuck — usually a sign of too little conversion volume to optimise on, which is a data problem (see below), not a patience problem.

## Signals and data quality

Smart Bidding is exactly as good as the conversion data feeding it. Garbage in, confident garbage out — the model will optimise hard toward whatever you told it to value, including the wrong thing. This is where most "the algorithm doesn't work" complaints actually originate.

- **Enhanced conversions** — hash-and-match first-party data to recover conversions lost to browser and consent restrictions. With privacy-driven measurement loss, this is no longer optional; it materially improves the data the model learns from.
- **Consent Mode v2** — required for EEA delivery, and conversion modelling fills the consent-driven gaps. Implement it properly or you're feeding the model a biased, partial picture.
- **Offline conversion imports (OCI)** — the single highest-leverage move in lead gen. Import the downstream outcome (qualified lead, opportunity, closed deal) so the model optimises for revenue, not for form fills. See [[lead-gen]].
- **Micro vs macro conversions** — optimise toward the macro conversion (purchase, qualified lead) whenever you have the volume to support it, because that's what the business actually wants. Use a micro-conversion (add-to-cart, begin-checkout, newsletter signup) as the optimisation target *only* when macro volume is too thin to learn on — and treat it as scaffolding to be removed once volume builds, not a permanent target.

## Common mistakes

1. **Target whiplash.** Changing tCPA/tROAS every few days chasing daily noise. Every change restarts learning; the campaign never stabilises and you blame the strategy.
2. **Optimising for the wrong conversion.** Counting every form fill as a conversion when half are junk. The model dutifully finds you more junk. Without OCI, lead-gen Smart Bidding optimises for *quantity of submissions*, not *quality of leads*.
3. **Aspirational targets on thin data.** Setting a target the account has never hit, on a campaign with 5 conversions a week. Delivery collapses, and it's read as the algorithm failing rather than starvation.
4. **Budget caps throttling the strategy.** A target strategy that's constantly budget-limited can't bid into the auctions it wants; you get a distorted, capped picture and worse efficiency than the uncapped math implies.
5. **Over-segmentation starving learning.** Splitting one healthy campaign into eight tightly-themed ones, so no single one gets enough conversions to learn. Consolidation feeds the model; fragmentation blinds it. See [[campaign-structure]].

## Lead gen considerations

Lead gen breaks Smart Bidding in a specific way: the conversion you can easily track (the form fill) is not the outcome you care about (the qualified, closeable lead), and those two things are often *negatively* correlated — the easiest forms to fill attract the lowest-intent traffic. Optimise naively for form fills and the model will reliably find you more cheap, low-quality submissions.

The fix is to feed downstream truth back via **offline conversion import**: pass the lead's real outcome — MQL, SQL, opportunity, closed-won — back to Google, ideally with a value attached, so the model optimises for leads that actually progress. **Value-based bidding for leads** (Max Conversion Value / tROAS using lead-stage values) is the mature endpoint: assign a value to each lead stage and let the model chase pipeline, not paperwork. The constraint is volume and lag — long sales cycles mean the model learns slowly, so many lead-gen accounts run tCPA on a *qualified*-lead conversion as a pragmatic middle ground. See [[lead-gen]] for the full treatment.

## Ecomm considerations

Ecomm has cleaner native data — real revenue per transaction flows back automatically — so value-based bidding works out of the box. The traps are subtler.

- **ROAS vs profit.** tROAS optimises for *revenue*, and revenue is not profit. The model will happily pour budget into high-revenue, low-margin products and discount-driven sales. If margins vary across the catalogue, a flat tROAS misallocates spend toward your worst products.
- **The case for POAS.** Feed *profit* (or margin-adjusted values) back instead of raw revenue, via conversion value rules or feed-level margin data, so the model optimises profit-on-ad-spend. This is the single biggest ecomm Smart Bidding upgrade for any catalogue with uneven margins.
- **Feed quality is a bidding input.** In Shopping and PMax, the product feed *is* the targeting and a major signal source. A thin, stale, or poorly-attributed feed degrades Smart Bidding the same way bad conversion data does — titles, types, attributes, and availability all feed the model. See [[shopping]] and [[pmax]].
- **Shopping/PMax signal interaction.** PMax pools conversion signals across Search, Shopping, Display, and more; consolidating value data into fewer, well-fed campaigns generally beats fragmenting it. Mind cannibalisation between Search and PMax, and let the value signal — not channel silos — drive allocation. See [[ecomm]] and [[pmax]].

## Related
[[campaign-structure]], [[audience-strategy]], [[creative-strategy]], [[search]], [[pmax]], [[shopping]], [[lead-gen]], [[ecomm]], [[quality-score]].
