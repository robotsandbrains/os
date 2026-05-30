---
title: Creative Strategy
version: v0.1
updated: 2026-05-31
status: draft
---

# Creative Strategy

## How the creative system works in 2026

Stop thinking of an RSA or an asset group as "an ad." It isn't. In 2026, Google's creative system is a **combinatorial testing engine**, and what you build is a *pool of assets* the system assembles, serves, and tests at auction time. You don't write the ad anymore — you stock the inventory the system builds ads from. An RSA isn't a headline-and-description you wrote; it's up to 15 headlines and 4 descriptions the engine mixes into thousands of possible combinations and learns from. An asset group isn't a banner; it's a bundle of text, image, video, and logo assets the system recombines across six surfaces.

This mirrors the same shift that happened to bidding and targeting (see [[smart-bidding]] and [[audience-strategy]]): the practitioner moved from *operator* to *system designer*. Your job is no longer "write a good ad" — it's **"provide a diverse asset pool the system can optimise from."** The two demand opposite instincts. Writing one good ad rewards a single polished message. Stocking an asset pool rewards *coverage of distinct angles* — because the engine can only test the variety you give it. Fifteen polished headlines that all say the same thing is a worse asset pool than ten rougher headlines spanning ten genuinely different ideas. The engine doesn't need your single best line; it needs raw material it can match to different users, queries, and contexts.

What this means in practice:
- **Diversity beats polish.** Range of distinct angles is the asset of value, not the perfection of any one line.
- **You're feeding a tester, not publishing a finished piece.** Some combinations will be weak; that's fine — the system learns away from them.
- **Coverage is a strategy, not an afterthought.** Decide what angles must be present *before* you write (see Message architecture).
- **The system optimises assembly; you control the ingredients.** Your leverage is the quality and diversity of the pool, plus the few structural controls (pinning, asset choice) you still hold.

## RSA creative strategy

**How the combination engine works:** you supply up to 15 headlines and 4 descriptions; the system assembles them into ads (typically up to 3 headlines and 2 descriptions shown), tests combinations per auction, and learns which assets and combinations perform for which contexts. It favours your stronger assets over time but keeps exploring. You are not writing one ad — you're defining the combination space.

**What Ad Strength actually measures:** Ad Strength is a **coverage-and-variety diagnostic, not a performance predictor.** It rewards having enough headlines, enough distinct assets, keyword inclusion, and low redundancy. It says nothing reliable about whether the ad will *convert*. Chasing "Excellent" by stuffing the pool with near-duplicate keyword-laden headlines can make the meter green while making the ad worse. Use Ad Strength as a checklist — "have I given the engine enough distinct material to work with?" — and then ignore it and judge the ad on conversions. Green meter, bad ad is a real and common state.

**Write for genuine variety:** the discipline is providing headlines that differ in *kind*, not in wording:
- **Different angles** — benefit, proof, offer, feature, brand, objection-handling.
- **Different intent levels** — a headline that suits a researching user and one that suits a ready-to-buy user.
- **Different value propositions** — price, quality, speed, trust, selection — not five rewordings of "best value."
The failure mode is semantic repetition: "Affordable Plumbing Services," "Low-Cost Plumbing," "Cheap Plumber Near You," "Budget Plumbing Help" — that's one idea four times, and it teaches the engine nothing. Replace three of them with proof, speed, and guarantee angles.

**The pinning trade-off — control vs optimisation:** pinning fixes an asset to a position (or excludes it from others). Every pin removes combinations the engine could have tested, so pinning is *spending optimisation to buy control*. Pin only what genuinely must always show or always lead — a legal/compliance line, a non-negotiable brand mandate, a price you must control. When you must pin, **pin 2–3 assets to the same position** so the engine still has something to test there. Pinning everything turns the RSA back into a static ad and forfeits the whole point of the format.

**Read and act on asset ratings:** RSAs report per-asset ratings (Best / Good / Low / "Learning"/Pending). Use them as a slow testing loop: **replace "Low" assets** with new angles (don't just delete — substitute a different idea), keep "Best," and don't thrash assets while the campaign or ad is still learning. One deliberate swap, let it gather data, repeat. Beware: a "Low" asset that provides *necessary coverage* of an angle isn't always a failure (see Creative testing).

**The description's role:** descriptions expand and support the headline's promise — context, detail, proof, and CTA that don't fit a 30-character headline. Provide all 4, spanning different supporting angles (one benefit-led, one proof/credibility-led, one offer/CTA-led, one detail-led) so the engine can match a description to whichever headline combination it serves.

## Message architecture

Before writing a single headline, **build a message framework** — the set of angles the asset pool must cover. This is the highest-leverage creative habit, because it converts "think of headlines" (which produces semantic repetition) into "fill these angle slots" (which produces diversity by design). You write *to a map*, not off the top of your head.

The angles any well-rounded RSA or asset group should cover:
- **Unique value proposition** — the core reason to choose you over alternatives.
- **Specific benefits** — concrete outcomes the customer gets (not features — what the features *do for them*).
- **Social proof** — reviews, ratings, customer counts, recognisable clients, awards.
- **Urgency / offer** — the promotion, deadline, or reason to act now.
- **Brand** — who you are; trust and recognition signals.
- **Product / service specifics** — what exactly is on offer, key features, range.

**Map headlines to angles.** Tag each headline you write against the angle it serves, and look at the distribution. If 9 of 15 headlines are "specific benefits" and you have zero "social proof" and zero "urgency/offer," your coverage is lopsided and the engine can't test those angles — you've found the gap *before* launch, not after a month of mediocre data. The map tells you what you have and what's missing, turning creative from inspiration into a coverage exercise you can actually QA. Reuse the same framework across the RSA and the matching PMax asset group so the account speaks one coherent set of angles.

## Asset groups for PMax

Asset groups apply the same diversity principle as RSAs, but across **more formats and more inventory.** An asset group is a themed bundle — headlines, long headlines, descriptions, images (multiple ratios), logos, videos, and (for retail) a listing group — that PMax recombines across Search, Shopping, Display, YouTube, Discover, Gmail, and Maps. The combination engine is the same; the surface area is far larger. See [[pmax]].

- **Theme, landing page, and audience signal must align.** A good asset group is built around *one* coherent theme → one relevant landing page → seeded with the *audience signal* most likely to convert for that theme. Theme drift — generic assets, a generic page, no matched signal — gives the model nothing to anchor relevance on, and quality degrades across every surface. One asset group = one message = one destination = one intent.
- **Full asset coverage is an inventory unlock, not box-ticking.** Each missing format locks you out of placements. **No video** → PMax auto-generates a low-quality one (or you forfeit YouTube reach). **Missing image ratios** (1:1, 1.91:1, 4:5) and **missing logo formats** → you can't appear in the placements that need them. Supplying the full asset set is literally choosing how much inventory you're eligible for. Partial coverage is partial reach.
- **Write for asset groups the same way — diverse angles, mapped to the framework** — but across formats: text assets span the angle map; images and video carry the same angles visually (proof, product, offer, brand). Don't let the visual assets all say one thing while the text says another.
- **Ad Strength in PMax: same caveat, larger stakes.** It signals asset-group *coverage and variety* (do you have enough distinct assets, all formats present) — it does **not** predict performance and is not a KPI. "Excellent" means you've given the model room to work, nothing more. Judge the asset group on conversions and asset performance labels, not the meter.

## Video and display assets

**Video matters even if you think you're "just" running Search/Shopping.** The moment you run PMax — which most accounts do — video is the key to YouTube and a chunk of Display/Discover inventory. Without a video asset, PMax either auto-generates a poor one from your other assets or simply can't access that inventory. Treat video as table-stakes inventory access, not a premium add-on. The same applies to Demand Gen, which is video-and-image-led by nature (see [[demand-gen]]).

**Minimum viable video without a production budget:**
- Assemble simple videos from existing images, product shots, and text overlays using free/built-in tools (including Google's asset-library video creation) — a clean 10–30s clip with your offer, a few proof points, and a CTA beats no video and beats the auto-generated one.
- Provide a few durations/orientations where you can (a short bumper-length cut and a longer one; vertical for mobile-first surfaces).
- The bar is "relevant, on-brand, and clearly messaged," not "cinematic." Done-and-present outperforms perfect-and-absent.

**Display/image requirements and the quality bar:** supply the full ratio set (1:1, 1.91:1, 4:5) and proper logos. Images must be clean, uncluttered, correctly cropped, and free of excessive text overlay — low-quality or busy images drag serving quality and can look cheap across premium placements.

**Stock assets — acceptable vs harmful:** generic stock is *acceptable* as supporting/background imagery or to fill format coverage when you have nothing else, and it's better than leaving a format empty. It *hurts* when it becomes the hero image for a brand or product that should look distinctive — obvious stock erodes trust and undercuts differentiation, especially for ecomm where the actual product shot is the creative. Use real product/brand imagery wherever the asset is doing persuasive work; reserve stock for genuine coverage gaps.

## Creative testing

In an RSA/PMax world the system is *already* testing combinations continuously — so creative testing is no longer "ad A vs ad B" inside the ad. Your testing operates at two levels: the engine tests assets *within* the ad, and you test *changes to the asset pool* across time.

- **Read asset performance data at scale.** The per-asset Best/Good/Low ratings (RSA) and asset performance labels (PMax) are your primary read. At scale, look for patterns across the account: which *angles* consistently earn "Best" (proof? offer? speed?) and feed that learning back into every asset pool. The signal isn't one asset — it's which kinds of message win.
- **Campaign experiments for bigger creative bets.** When you want a clean read on a substantive creative change — a new message strategy, a different value-prop emphasis — use campaign experiments/drafts to split traffic, rather than eyeballing before/after. The in-ad ratings tell you which assets work; experiments tell you whether a *strategy* works.
- **Replace vs give it time.** Don't judge or swap assets mid-learning — you'll act on noise (see [[smart-bidding]] on learning). Once an asset has stable data and rates "Low," replace it with a *different angle* (not a reworded version of the same). Give new assets enough impressions to rate before deciding.
- **Low-performing vs necessary (coverage vs performance).** Critical distinction: an asset can rate "Low" yet be *necessary for coverage* — e.g. the only headline carrying a required disclaimer, or the lone asset covering an angle the engine still occasionally needs. Don't blindly cull every "Low" asset toward a monoculture of your one best message; that shrinks the combination space and can hurt overall. Cull "Low" assets that are *redundant*; keep "Low" assets that are the *only* coverage of something. Performance and coverage are two different jobs.

## Landing page alignment

**Creative doesn't end at the ad.** The message the user clicked must continue on the page they land on — ad-to-page **message match** is part of the creative system, and it drives both Quality Score (via landing page experience, see [[quality-score]]) and conversion rate. A brilliant ad pointed at a mismatched page wastes the click and the premium CPC you paid for it.

- **The effect:** strong message match lifts conversion rate (the user finds exactly what the ad promised) and supports Quality Score, which lowers CPCs — a compounding win. Weak match raises bounce, depresses conversions, and quietly taxes every click.
- **How to audit alignment:** click your own ads (or walk the query → ad → page path) and check three things — does the page headline echo the ad's promise/offer, is the product/service the same one the ad implied, and is the primary CTA the obvious next step for that intent? Mismatches between the ad's offer and the page's content are the flag.
- **Most common mismatch patterns:** ad promotes a specific product/offer but lands on a generic homepage; ad emphasises a price/discount the page doesn't surface; ad targets a specific intent (e.g. a service in a city) but lands on a national catch-all; ad's value prop (speed, free shipping, guarantee) is absent from the page.
- **Why fixing the page often beats writing new headlines.** When conversion rate is the bottleneck, improving landing page relevance and match frequently outperforms another round of headline writing — you're fixing where intent is *lost*, not where it's *captured*. Before iterating creative again, check whether the page is the actual leak.

## Lead gen considerations

- **Intent signalling in headlines.** Lead-gen creative should *qualify* as much as attract — headlines that signal who the service is for, the location served, and the nature of the offer pre-filter low-intent clicks (which you pay for) and lift lead quality, not just volume. A headline that says "Commercial HVAC — Melbourne, Licensed" attracts fewer but better clicks than "Get a Quote Today." See [[lead-gen]].
- **The offer is the primary creative lever.** In lead gen, *what you offer* (free quote, free audit, consultation, guide, finance) usually moves results more than wording. Test offers as creative, not just headlines — a stronger offer reframes the whole ad.
- **Form vs landing page.** Friction is a quality dial. Low-friction lead forms lift volume but often lower quality (and invite spam/bots); a qualified landing page with a real form raises friction and tends to raise lead quality. Match the friction to whether you're optimising for volume or qualified pipeline (see [[pmax]] on lead-form caution).
- **Creative × match type in high-CPA environments.** When clicks are expensive, creative that qualifies hard pairs with conservative match types (phrase/exact) and aggressive negatives (see [[search]]) to keep the query mix and the click mix tight to real buying intent. Loose creative + broad match + high CPCs is how lead-gen budgets evaporate.

## Ecomm considerations

- **Product-specific vs category-level creative.** Match creative altitude to campaign intent: product-specific creative (the exact item, its hero feature, its price) for high-intent product demand; category-level creative (range, USP, store benefits) for broader category and prospecting. Don't run generic store-level creative against specific product intent — it under-converts against the specificity the user wants. See [[ecomm]].
- **Promotional creative cadence.** Ecomm lives on offers — build a cadence for refreshing promotional assets (sales, seasonal, shipping offers) and *remove expired promos promptly* so the engine isn't serving a finished sale. Plan promo creative around the calendar rather than scrambling; stale offers in the pool are a silent conversion drag.
- **The Shopping/PMax asset relationship.** In feed-driven campaigns the product image, title, and price *are* the primary creative — your text/image/video assets supplement rather than replace them. Keep added assets consistent with the feed (same products, same offers) so the assembled ads are coherent. See [[shopping]] and [[pmax]].
- **Feed titles function as creative in Shopping.** This is the most underrated ecomm creative lever: in Shopping, the **product title is the headline.** It's what matches queries and what the user reads. Front-load the title with the attributes shoppers search (brand, product type, key specs, size/colour) rather than internal SKU naming — optimising titles is optimising creative, and it often moves Shopping performance more than any asset change. Treat the feed as a creative surface, not a data dump.

## Related
[[smart-bidding]], [[campaign-structure]], [[audience-strategy]], [[search]], [[pmax]], [[shopping]], [[demand-gen]], [[quality-score]], [[lead-gen]], [[ecomm]].
