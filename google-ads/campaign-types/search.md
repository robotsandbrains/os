---
title: Search Campaigns
version: v0.1
updated: 2026-05-31
status: draft
---

# Search Campaigns

## What Search campaigns are in 2025-2026

Search is still the account's demand-capture core — it puts you in front of people actively searching for what you sell, at the moment of intent. But the campaign type a practitioner manages in 2025-2026 bears little resemblance to the 2018 version, and managing it with 2018 instincts is the single most common reason accounts underperform.

The two changes that rewrote everything are **broad match** and **Smart Bidding**, and they only make sense together. In the old world, the keyword *was* the targeting: you bid on a keyword, you appeared for that keyword, you controlled the mapping query-to-bid by hand. In the modern world, **the keyword is a signal, not a target.** Broad match keywords tell the system the *kind* of intent you want; Smart Bidding then decides, auction by auction, which actual queries are worth bidding on and how much — using signals you can't see (see [[smart-bidding]]). You are no longer selecting queries. You are describing intent and supplying conversion data, and the system selects queries.

What practitioners have to *accept* before they can manage modern Search well:
- **You will not see or control every query you serve on.** You influence the query mix through keywords, negatives, and bid signals — you don't pick it.
- **Broad match without Smart Bidding is a money fire.** The two are a system. Broad on manual bidding is the worst of both worlds; broad with good conversion data and tROAS/tCPA is how modern Search scales.
- **Conversion data quality is now a Search lever**, not just a bidding lever. Garbage conversions → the model chases garbage queries. Search performance is downstream of measurement.
- **Less manual control, more system design.** Your job shifts from picking keywords and bids to building clean structure, feeding clean data, and policing query quality with negatives.

Practitioners who fight this — over-segmenting, hoarding exact match, manual-bidding broad — get fragmented data and worse results. Practitioners who design *for* the system win.

## Match types

Forget Google's definitions; here's the observed behaviour today.

- **Broad match** no longer means "any loosely related query." With Smart Bidding feeding it, broad uses the keyword plus user signals, query intent, landing pages, and account history to find converting queries you'd never have thought to add — and it's genuinely good at it *when the conversion data is clean and volume is sufficient*. Without Smart Bidding, broad is exactly the indiscriminate spend-everywhere disaster its reputation says. **Broad's behaviour is entirely contingent on the bidding strategy behind it.** Broad + tCPA/tROAS = a scaling engine. Broad + manual = avoid.
- **Phrase match** is the pragmatic middle and still very much alive in 2025. It honours meaning and sequence while allowing variation, giving you broad-like reach with more intent guardrails. **The case for phrase:** it's the default when you want Smart Bidding's query-finding but can't yet fully trust broad — newer accounts, thinner conversion data, higher-risk/high-CPA verticals, or where query control matters. Many accounts run a phrase-led core and test broad on top.
- **Exact match** still matches close variants (same meaning), so even "exact" isn't literal. It's worth the coverage trade-off for your **highest-intent, must-control terms** — brand, top converting commercial queries, terms where you want tight messaging and to guarantee Search wins over PMax (see the hierarchy below). You give up reach; you buy control and predictability.

The throughline: **match type strategy is now inseparable from bidding strategy.** You cannot choose a match type in isolation — broad assumes Smart Bidding and data density; exact assumes you want control over reach. Decide them together, not in separate meetings.

## Keyword strategy

Build keyword sets that work *with* Smart Bidding, which means **consolidation over coverage.** The old instinct — exhaustively map every variant, every long-tail, every misspelling into its own tightly-controlled keyword — actively harms a Smart Bidding account by fragmenting conversion signal across hundreds of low-volume keywords that never individually learn.

- **Fewer, broader keywords feeding richer data** beats thousands of granular ones. Let close variants and broad/phrase do the query-discovery work instead of pre-enumerating it. A modern ad group might run a handful of phrase/broad keywords, not 200 exacts.
- **Negatives are how you steer**, not more keywords. In a broad/phrase world you refine by *subtracting* bad queries, not by *adding* more keywords. See the negatives section.
- **Use the search terms report to refine, not to expand.** The old habit was mining search terms to harvest new keywords to add. The modern habit is mining them to (a) find negatives and (b) sanity-check that broad/phrase is finding the right intent. Harvesting a converting query into its own exact keyword is mostly unnecessary now — the system already serves on it — and often just fragments data. Add it as exact only when you specifically want to control it (tight messaging, ring-fence from PMax) or split it to a different bid target.
- **Add keywords vs let broad work:** add keywords when you're entering genuinely new intent territory the system isn't exploring, or when you need a controlled exact for messaging/hierarchy reasons. Otherwise, let broad + good signals find the queries. Default to trusting the system once data is clean and ample.

## Campaign and ad group structure

The modern argument is **consolidation: fewer, better-fed campaigns over many tightly-themed ones.** Smart Bidding optimises on conversion volume; every time you split a campaign you divide that volume, slow learning, and lengthen instability. SKAGs (single keyword ad groups) are dead — they're the archetypal over-segmentation mistake, fragmenting data for control you no longer need or get. See [[campaign-structure]].

- **Default to consolidated structure:** group by genuine theme or landing-page/offer, not by hair-splitting keyword variants. An ad group should map to one coherent message and destination, and contain enough keywords/traffic to matter.
- **Single ad group campaigns make sense** in specific cases: brand (you want it isolated and controlled), a single hero product/service, or when you deliberately want one clean bid target and signal pool. They're a tool, not a default.
- **Structure exists to serve signal volume and control**, in that priority order. Split campaigns only for reasons that *require* a campaign boundary: separate budgets you must ring-fence, different bid targets (tCPA/tROAS), geo/language splits, or brand vs non-brand separation. Don't split for tidiness.
- **Ad group themes in an RSA world:** the ad group's job is to keep keywords, the RSA's assets, and the landing page thematically aligned so relevance holds. You need *enough* theme tightness for the RSA to be relevant — not so much that you've recreated SKAGs. One theme, one message, one page, enough volume to learn.

## RSAs

Responsive Search Ads are the only standard Search ad format now, and they work by **combination**: you supply up to 15 headlines and 4 descriptions, and the system assembles and tests combinations per auction, learning which perform. Understanding the mechanics is what separates good RSAs from asset soup.

- **Pinning** forces an asset to a fixed position (or excludes it from others). Pinning everything turns an RSA back into a static ad and kills the model's ability to optimise — **the pinning trade-off is control vs optimisation.** Pin only what genuinely must always show or always lead (a legal disclaimer, a non-negotiable brand line, a price you must control). Pin sparingly; when you must pin, pin 2-3 assets to a position so the model still has choices.
- **Give the model genuine variety, not semantic repetition.** Fifteen headlines that all say "Best [Product] Online" teach the model nothing — it can only test rewordings of one idea. Provide distinct *angles*: benefit, proof/credibility, offer, objection-handling, feature, CTA, urgency. Variety is what makes the combination engine work. See [[creative-strategy]].
- **Ad Strength is a coverage/variety signal, not a performance target.** "Excellent" means you've supplied enough distinct assets and used keywords — it does **not** predict results, and chasing the label by stuffing repetitive assets is counterproductive. Use it as a checklist that you've given the model room to work; judge the ad on conversions.
- **Read and act on asset performance.** Asset ratings (Best / Good / Low / Pending) tell you which assets earn their place. Replace "Low" assets with new angles; keep "Best"; don't thrash assets while a campaign is learning. Treat it as a slow, deliberate testing loop, not a daily fiddle.

## Negative keywords

The modern role of negatives is **query quality control**, not keyword sculpting. In the old world negatives were used to route traffic between tightly-themed ad groups (sculpting). That's obsolete and, in a Smart Bidding account, harmful. Today negatives do one essential job: **keep low-quality, irrelevant, and wasteful queries out of a broad/phrase account.**

- **Shared negative lists vs campaign-level:** use **shared lists** for account-wide exclusions — competitor terms (where appropriate), irrelevant categories, profanity/junk, jobs/careers/DIY/free-seekers, and the universal waste themes. Use **campaign-level** negatives for campaign-specific needs and for managing the Search/PMax/brand boundary.
- **Identify negatives systematically, not anecdotally.** The professional method is **n-gram analysis**: break the search terms report into single words and word-pairs (unigrams/bigrams), aggregate spend and conversions by n-gram, and find the words that consistently cost money without converting. A single bad word ("free", "job", "DIY", a wrong-fit modifier) often appears across hundreds of wasteful queries — negate the n-gram, not each query one at a time. This is the highest-leverage routine maintenance task on a broad-match Search campaign.
- **Don't over-negative.** Every negative you add narrows the query space the model can explore, and an over-negated broad campaign loses the query-discovery that made broad worth running — you starve it back toward an expensive, narrow exact-match campaign with none of the upside. Negate clear waste and clear irrelevance; resist the urge to negate every query that didn't convert in a small sample. Trust the bidding model to value mediocre-but-relevant queries correctly. Cut junk, not breadth.

## Search and PMax

The hierarchy is the thing to internalise: **an exact-match keyword (and close variants) in a standard Search campaign always wins over PMax for that query.** Against phrase/broad keywords, Shopping, and everything else, **Ad Rank decides** — and PMax often wins those because it optimises across more signals. So PMax will quietly absorb your non-exact and brand demand unless you deliberately fence it. See [[pmax]].

How to make Search and PMax complement rather than cannibalise:
- **Protect what you want to own with exact match.** Your highest-intent commercial terms and brand belong in controlled exact-match Search so the hierarchy guarantees Search serves them — PMax can't take an exact-match query you hold.
- **Brand keyword handling.** Decide deliberately: run brand as an exact-match Search campaign *and* apply brand exclusions / brand lists to PMax, so PMax doesn't claim cheap brand conversions and flatter itself. Most accounts should keep brand in Search and fence it out of PMax. The alternative — letting PMax serve brand — inflates PMax's apparent performance and muddies measurement.
- **Let PMax run where it adds reach**, fence it where it just re-harvests. PMax earns its place finding incremental demand across inventory Search can't reach; it does *not* earn its place re-capturing brand and high-intent generics you already own in Search. Fence the latter (exact-match Search + exclusions), free the former.
- **Audit the overlap, don't assume it.** Use channel-breakdown and brand/non-brand splits to see what PMax is actually taking from Search before declaring either a winner (see [[pmax]]).

## Lead gen considerations

Search is usually the **foundation** of a lead-gen account because intent-matching is its core advantage — someone searching "emergency plumber near me" is closer to converting than any audience you could build. See [[lead-gen]].

- **Intent-matching is the whole point** — lean into high-commercial-intent queries and let match type and negatives keep the query mix tight to real buying intent.
- **Landing page alignment is non-negotiable.** Search sends high-intent traffic; if the landing page doesn't match the query's intent and offer, you pay premium CPCs to bounce them. Query → ad → page must be one continuous message.
- **Match type conservatism in high-CPA environments.** When clicks are expensive and conversions sparse, broad match's exploration costs real money before it learns. Lead with phrase (and exact for core terms), test broad deliberately on the campaigns with enough conversion volume to support it, and police with negatives aggressively. Don't run wide-open broad on a thin, high-CPA account.
- **Feed quality means conversion quality here:** with weak data, Smart Bidding optimises Search toward cheap form fills, not qualified leads — so offline conversion import matters for Search just as much as for PMax (see [[smart-bidding]]).
- **Search + PMax for lead gen:** Search owns the high-intent core; PMax (well-fenced, with OCI) extends reach. Keep brand and top commercial terms in controlled Search; let PMax expand carefully.

## Ecomm considerations

For ecomm, Shopping and PMax usually carry the product-level demand, and **Search plays a complementary, intent-and-brand role** rather than the lead. See [[ecomm]], [[shopping]], and [[pmax]].

- **The classic ecomm Search structure** is three buckets: **brand** (defend it cheaply, keep it out of PMax), **competitor** (conquesting, where margins and policy allow), and **high-intent non-brand generics** (category and product-type queries where text ads add value alongside Shopping). Don't try to out-Shopping Shopping with text ads on transactional product queries — let the feed-driven campaigns own those.
- **Search complements Shopping/PMax**, it doesn't duplicate them. Shopping/PMax show the product, price, and image for product queries; Search captures brand, research-y and comparison intent, and queries where a text ad with messaging (offers, USPs, store benefits) outperforms a product tile.
- **When to invest in Search vs shift to Shopping/PMax:** if product-level transactional demand is the bulk of the opportunity, weight budget to Shopping/PMax and keep Search lean (brand + competitor + select generics). Invest more in Search when you have strong brand demand to defend, meaningful competitor-conquesting opportunity, or research-stage queries where messaging matters. Let ROAS and the channel-overlap picture, not habit, decide the split.

## Related
[[smart-bidding]], [[campaign-structure]], [[creative-strategy]], [[audience-strategy]], [[pmax]], [[shopping]], [[quality-score]], [[lead-gen]], [[ecomm]].
