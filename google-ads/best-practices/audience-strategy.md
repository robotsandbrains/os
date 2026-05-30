---
title: Audience Strategy
version: v0.1
updated: 2026-05-31
status: draft
---

# Audience Strategy

## How audiences work in Google Ads in 2026

Forget the feature list. The underlying reality is this: in a Smart Bidding account, audiences are mostly **bid signals, not targeting gates.** They tell the model *who is more likely to convert and how much they're worth*, and the model factors that into the auction-time bid alongside the dozens of other signals it reads (see [[smart-bidding]]). They are an *input to the algorithm*, not a fence around your traffic — and conflating those two things is the single most expensive audience misunderstanding in the platform.

The distinction that governs everything:
- **Audience as input (signal):** "people on my customer list tend to convert and are worth more — bid accordingly." The campaign still reaches everyone eligible; the audience just shapes *how hard* it bids for different people. This is how audiences should work in most modern campaigns.
- **Audience as filter (hard inclusion/exclusion):** "only ever show to this audience" (or "never show to this audience"). This restricts *reach*, full stop. Sometimes correct, often catastrophic.

The model uses audience-membership data as one more probabilistic signal: membership in a high-converting list raises the predicted value of an auction, the bid rises, and you win more of the *right* impressions without locking out everyone else. That's the mechanism — probabilistic bidding, not binary gating.

Why practitioners get this wrong: they bring a pre-automation instinct that audiences are *targeting* — "I'll add my in-market and remarketing audiences to narrow this to good people." In a Smart Bidding world that instinct **over-restricts**: it converts a rich signal the model could have used to bid intelligently across the whole auction into a wall that starves the campaign of volume and, ironically, of the conversion data the model needs to learn. The default posture in 2026 is **feed signals, don't build walls** — give the model your best first-party and intent data as observation/signal, and let it bid, rather than pre-filtering the audience down yourself.

## Observation vs targeting

This is the most misunderstood setting in Google Ads, and getting it wrong silently destroys campaigns. There are two ways to attach an audience to a Search/Display campaign, and they do completely different things.

- **Observation ("monitor"):** adds the audience for *data and bid adjustment* **without restricting reach at all.** The campaign keeps serving to everyone eligible; you simply collect performance data for that audience and — under Smart Bidding — feed the model a signal it can bid on. Observation has essentially no downside: it can't shrink your reach, only inform your bidding. This is why it's the safe, default way to attach audiences.
- **Targeting ("target and bid"):** **restricts the campaign to serve *only* to that audience.** Reach collapses to the audience's size. This is a hard filter, not a signal.

**When targeting is appropriate:** rarely, and only when narrowing reach is the explicit intent — e.g. an RLSA-only campaign deliberately bidding on broad keywords *just* to past visitors, a remarketing campaign that should only reach prior audiences, or a tightly-scoped promotion to a known list. **When it actively destroys performance:** layering targeting onto a normal prospecting Search campaign. It strangles traffic, starves Smart Bidding of volume, and you'll watch impressions crater — usually misdiagnosed as "the campaign stopped working" when someone set audiences to *target* instead of *observe*.

**Default recommendation by campaign type:**
- **Search (prospecting):** **observation.** Add your best audiences as observation to inform bidding; never set them to target unless you specifically want an audience-only campaign.
- **Search (RLSA-only / remarketing):** targeting — that's the whole point of the campaign.
- **PMax:** the question doesn't apply in the same way — audience signals are *always* inputs, never hard filters (see PMax section).
- **Display / Demand Gen:** targeting is more normal here since these are audience-led formats — but still lead with the broadest sensible audience and let bidding optimise within it.

## Audience types and their value

An honest assessment of each, by signal value:

- **Customer Match — the highest-value signal you have.** First-party CRM data is truth: these people *actually* bought or converted. Nothing the platform builds from behavioural inference matches it. Use it for bid uplift on known converters, suppression of existing customers, and as the seed for similar/expanded audiences. If you do one thing in audience strategy, do this. See the dedicated section below.
- **Remarketing lists — high value, your second-best first-party asset.** Site/app visitors and converters you've collected. Powers RLSA on Search and remarketing across Display/Demand Gen/PMax signals. Segment by **recency** (recent visitors convert better) and **depth/intent** (cart-abandoners > category-browsers > homepage-bouncers). Keep lists large enough to stay eligible for serving.
- **Similar segments — largely deprecated as a standalone targeting product.** Google retired similar/lookalike audiences as manual targets; the lookalike function now lives *inside* the optimisation — you provide a first-party seed (Customer Match, remarketing) and the system expands from it automatically, especially in PMax and Demand Gen. The takeaway: stop looking for a "similar audiences" checkbox; *feed strong seed lists* and let expansion happen.
- **In-market audiences — useful as signal, dangerous as a tight target.** People actively researching a category. Strong as an *observation* signal that sharpens Smart Bidding; risky as a hard target because the inference is coarse and over-narrowing starves volume. In-market for Search = observe. In-market as a Display/Demand Gen audience = reasonable starting layer.
- **Affinity audiences — broad, upper-funnel, frequently not worth it for direct response.** Lifestyle/interest buckets built for awareness. Worth using for top-of-funnel reach plays and brand campaigns; mostly *not* worth using to "improve" a conversion campaign, where they add breadth without intent. Skip them on performance campaigns unless you have a specific upper-funnel reason.
- **Combined segments — useful when the combination encodes real intent.** Layering (e.g. in-market for X *and* a remarketing list *and not* existing customers) can build a genuinely meaningful audience for Display/Demand Gen prospecting. Valuable as observation signals or as targeting on audience-led formats; don't over-engineer combinations so narrow they can't serve.

## Customer Match

Customer Match is the single most **underused high-value capability** in Google Ads. It turns your CRM into a targeting and signalling asset, and most accounts either never set it up or upload one stale list and forget it.

**Set it up properly:**
- Upload clean, well-formatted first-party data (email, phone, address — more fields = higher match rate). Hash is handled on upload; the data stays first-party.
- Mind **match rates**: a poorly formatted or tiny list matches weakly and may not reach the minimum size to be usable. Bigger, cleaner lists match better and serve more reliably.
- Segment lists by what you'll *do* with them — all-customers, converters, high-value/LTV, recent-purchasers, lapsed — rather than one undifferentiated dump.

**The three use cases:**
1. **Bid uplift on known converters** — attach converter/high-value lists as signals so Smart Bidding bids harder for people who resemble your real customers.
2. **Suppression of existing customers** — exclude current customers from acquisition campaigns (or from offers meant only for new customers), so you stop paying to re-acquire people you already have. In ecomm and subscription especially, this is found money.
3. **Seed list for similar/expanded audiences** — your customer list is the highest-quality seed for the platform's lookalike expansion (now automatic inside PMax/Demand Gen). Good seed in, good expansion out.

**Freshness and maintenance:** Customer Match is only as good as the list behind it. Stale lists decay — people churn, emails die, intent ages. Automate list updates where possible (CRM/API/Google Ads Data Manager connection) so converter and suppression lists stay current, and refresh manually uploaded lists on a regular cadence. A maintained Customer Match programme compounds; a one-time upload rots.

## Audiences in Search

- **Observation on every Search campaign as a baseline.** Attach your meaningful audiences — Customer Match, remarketing/RLSA lists, relevant in-market — in **observation** mode across Search campaigns by default. It can't hurt reach, it builds data, and under Smart Bidding it feeds the model signal it will use to bid better. There's almost no reason *not* to.
- **RLSA strategy.** Remarketing Lists for Search Ads let you bid differently (or serve different ads/keywords) to people who've visited before. Two modes: as **observation** layered on normal Search (bid up returning users), or as a dedicated **targeting** RLSA campaign that bids on broader/more aggressive keywords *only* for past visitors — a classic way to safely buy head terms you couldn't afford to prospect on.
- **When to layer targeting on Search:** only for deliberate audience-only campaigns (RLSA-only, remarketing). For standard prospecting Search, never — keep it observation (see the observation-vs-targeting section).
- **How audience data feeds Smart Bidding:** every observed audience is another signal the model folds into its auction-time bid. The more good first-party signal you attach, the better it discriminates between a high-value and low-value impression.
- **Interaction with broad match:** this pairing is underrated. Broad match casts wide; audience signals (especially Customer Match and remarketing) give Smart Bidding the context to bid that wide net *intelligently* — leaning into queries from people who look like converters and easing off the rest. Broad + strong audience signals + Smart Bidding is a core modern Search pattern (see [[search]]); broad with no audience signal gives the model less to work with.

## Audiences in PMax

In PMax, audiences are **signals — inputs, not constraints** — and this is non-negotiable in how the system works. An **audience signal** does *not* restrict who PMax serves to; it tells the model "here's who's likely to convert, start here," accelerating learning before the model explores beyond it. Adding a signal is a head start, not a fence; removing one doesn't "open up" reach. Practitioners who expect PMax audience signals to behave like targeting are always confused by the results.

- **Customer Match is the highest-value PMax signal**, exactly as elsewhere — seed every eligible PMax campaign with your converter and high-value lists.
- **New PMax campaign:** give it strong signals *early* — Customer Match, best-converting remarketing lists, custom segments built from high-intent search/URL behaviour. This materially shortens the learning period by pointing the model at known-good intent from day one.
- **Established PMax campaign:** signals matter less over time as the campaign accumulates its own conversion history and effectively learns its own audience — but refreshed first-party lists still help, especially after seasonal shifts or a new product line.
- **With vs without signals:** with good signals, PMax learns faster and explores from a sensible starting point. Without any, it still runs but learns slowly and expensively, exploring blindly until conversions accumulate — on a low-volume account that blind phase burns real budget. Never launch signal-less PMax if you have any first-party data to give it. See [[pmax]].

## Audiences for prospecting vs retention

Audience logic is how you stop treating new and existing customers as the same person. The two have different value and should be bid and budgeted differently.

- **Separate acquisition from retention with suppression and lists.** Use Customer Match suppression to keep existing customers out of pure-acquisition campaigns (or out of new-customer offers), and use remarketing/customer lists to *target* retention and win-back where that's the goal. The mistake is one campaign indiscriminately paying the same to re-reach a loyal customer and to win a stranger.
- **The new-customer acquisition goal (PMax and Shopping).** PMax can optimise for *new* customers specifically — either bidding higher for new customers (value mode) or restricting to new customers only — by using your Customer Match lists to know who's already a customer. This is the cleanest built-in way to make the model chase incremental growth rather than re-buying existing demand. It requires well-maintained customer lists to work.
- **Value differentiation between new and returning.** Decide what a new customer is worth vs a repeat one and encode it — via the new-customer value bonus, value rules, or separate campaigns/targets. An account that values a first purchase and a tenth purchase identically is mis-allocating budget. See [[smart-bidding]] on feeding value.

## Lead gen considerations

- **Suppress converted leads.** Once someone has become a lead (or a customer), stop paying to convert them again — suppress your existing-leads and customers lists from acquisition campaigns. In long sales cycles this prevents wasting spend re-acquiring people already in the pipeline. See [[lead-gen]].
- **Use CRM lists to find lookalikes.** Upload your *qualified* leads and *closed-won* customers as Customer Match seeds so the system's expansion finds more people like your good leads — not just anyone likely to fill a form. Seed quality is everything: feed it closed deals, not raw form-fills.
- **RLSA for re-engagement.** Past site visitors who didn't convert are prime for re-engagement on Search — layer RLSA (observation to bid up, or a dedicated campaign) to recapture researchers who left.
- **In-market: limited for B2B, useful for B2C.** In-market segments are consumer-behaviour inferences — reasonable signal value for B2C lead gen (insurance, home services, education), but weak and coarse for niche B2B where the "market" is a handful of job titles in specific companies. For B2B, lean on first-party CRM lists and custom segments built from high-intent behaviour rather than off-the-shelf in-market audiences.

## Ecomm considerations

- **Cart and checkout abandoners are your highest-intent remarketing audience.** Segment them out (begin-checkout, add-to-cart, product-viewers) and treat them as a distinct high-value signal — they're closer to purchase than any inferred audience. See [[ecomm]].
- **Purchaser suppression vs retention targeting — decide per goal.** For one-time/considered purchases, *suppress* recent purchasers from acquisition so you're not paying to re-sell what they just bought. For consumables/replenishment and cross-sell, *target* purchasers deliberately at the right interval. The error is doing neither — letting the account silently re-market to fresh buyers with no plan.
- **Lifetime-value segmentation via Customer Match.** Build LTV tiers from your data (high-value/VIP, mid, one-and-done) and feed them as signals so Smart Bidding bids toward customers who resemble your *best* ones, not just any buyer. This is where value-based bidding and audiences reinforce each other (see [[smart-bidding]]).
- **The new-customer acquisition goal.** For ecomm with a healthy returning-customer base, use the new-customer goal/value bonus in PMax and Shopping so the model prices in the incremental value of a first-time buyer and doesn't just harvest cheap repeat purchases — the classic way PMax over-credits itself with existing demand. Requires current customer lists. See [[pmax]].

## Related
[[smart-bidding]], [[campaign-structure]], [[creative-strategy]], [[search]], [[pmax]], [[demand-gen]], [[lead-gen]], [[ecomm]].
