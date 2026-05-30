---
title: Performance Max
version: v0.1
updated: 2026-05-31
status: draft
---

# Performance Max

## What PMax actually is

Performance Max is a single campaign type that serves across *all* Google inventory — Search, Shopping, Display, YouTube, Discover, Gmail, and Maps — from one campaign, driven by Smart Bidding and a set of asset groups (plus, for retail, a Merchant Center feed). You give it a goal, assets, and signals; it decides channel, placement, audience, and bid per auction. There is no channel-level bid control and no placement-level control. That is the trade: total automation in exchange for handing over the levers.

The part Google's marketing doesn't explain is the **matching hierarchy**, and it governs everything about how PMax behaves alongside the rest of your account. The order that matters:

- **Exact-match keywords in a Search campaign always win.** If a query exactly matches an eligible exact-match keyword (or close variant) in a standard Search campaign, that Search campaign serves — PMax does not take the query. This is your single most important lever for controlling cannibalisation.
- **Against everything else** — phrase/broad keywords, Shopping, Display — **Ad Rank decides**, and PMax's Ad Rank is frequently higher because it's optimising at auction-time across more signals. In practice this means PMax will quietly absorb non-exact Search demand, including a lot of brand and high-intent generic traffic, unless you fence it.
- **Within retail**, PMax outranks Standard Shopping for the same product by default — if both are eligible, PMax serves.

Why it matters: most "PMax is crushing it" reports are partly PMax harvesting demand that your Search and Shopping campaigns would have captured anyway, re-attributed to PMax. You cannot evaluate PMax in isolation. You evaluate it against what the *account* did, and you control the overlap deliberately — primarily by protecting exact-match Search and by managing brand traffic (see Search themes and Optimisation levers below, and [[search]]).

## When to use PMax (and when not to)

Most practitioners run PMax by default. That's a mistake. PMax is a demand-harvesting and demand-blending machine that works brilliantly when there's a strong signal to optimise toward and enough conversion volume to learn on — and burns money quietly when there isn't.

**Use PMax when:**
- You have **clean, high-volume conversion data** — roughly 30+ conversions/month minimum at the account/campaign level, ideally more. PMax is Smart Bidding with the targeting hidden; it needs the same data density (see [[smart-bidding]]).
- You're **ecommerce with a healthy Merchant Center feed** — this is PMax's strongest, most defensible use case.
- You have **first-party audience data** (customer lists) to seed signals.
- You want incremental reach *beyond* what Search/Shopping already capture, and you've set up the measurement to prove incrementality rather than assume it.

**Hold off when:**
- The account is **low-volume** — PMax will spend across six surfaces and learn on none of them. Run Search first, build conversion history, then layer PMax.
- **Conversion tracking is weak or counts junk** — PMax amplifies whatever you tell it to value, with less visibility to catch it. Fix tracking first.
- **Lead gen without offline conversion import** — see the lead-gen section; this is the most common way PMax wastes budget.
- You **can't tolerate the black box** — regulated accounts, strict brand-safety needs, or accounts that require placement transparency.

**Minimum viable setup:** clean macro-conversion tracking, a sensible Smart Bidding target derived from economics (not aspiration), at least one well-built asset group with full asset coverage, one or more audience signals, brand handling decided up front, and — for retail — a clean feed. Anything less and you're paying PMax to learn on your money.

## Campaign structure

**Feed-only vs full-asset.** For retail, you can run PMax with *only* a Merchant Center feed and no other assets ("feed-only"), which forces serving almost entirely into Shopping-style and remarketing inventory, behaving much like a smarter Shopping campaign. Or you add text, image, and video assets ("full-asset") to unlock the full inventory spread (YouTube, Display, Discover, Gmail). Feed-only is tighter, more predictable, and usually more efficient on direct response; full-asset reaches further but spends into upper-funnel inventory that's harder to attribute. Default ecomm to feed-only or asset-light unless you have a deliberate reason to chase the broader inventory (see Ecomm below).

**Single vs multiple campaigns.** Default to **fewer, better-fed campaigns.** PMax consolidates signals; splitting into many campaigns fragments conversion data and starves each one's learning — the same over-segmentation failure as in [[campaign-structure]]. Only split into separate campaigns when you have a genuine reason that *requires* a campaign boundary:

- **Different ROAS/CPA targets** — e.g. a high-margin tier you'll bid harder for vs a clearance tier.
- **Different budgets you must ring-fence** — e.g. a brand-funded product line.
- **Materially different goals** — e.g. new-customer acquisition vs total revenue.

**Segment by performance tier, not category.** The most common structural mistake is splitting PMax campaigns by product *category* (shoes / bags / accessories) because that's how the catalogue is organised. PMax doesn't need that — it reads the feed. Segment instead by **performance tier and margin**: best-sellers / high-margin, mid-tier, and low-performers/clearance, each with its own tROAS. This puts your budget where the economics are and lets you bid each tier to its real value, which is the thing PMax actually rewards. Use listing-group/asset-group structure within a campaign for finer control before you reach for more campaigns.

## Asset groups

An asset group is PMax's creative unit: a themed bundle of headlines, descriptions, images, logos, videos, and (for retail) a listing group, pointed at a final URL set. **A good asset group is tightly themed and matches its landing page.** Theme drift — generic assets pointing at a generic page — gives the model nothing to anchor relevance on, and serving quality suffers across every surface.

What actually matters:
- **Landing-page relevance is the spine.** Build the asset group around a specific offer/audience/landing page, not "the whole business." One asset group = one coherent message → one relevant destination.
- **Full asset coverage** unlocks inventory. Missing video means PMax auto-generates a low-quality one; missing image sizes (1:1, 1.91:1, 4:5) and missing logo formats lock you out of placements. Supply the full set or you're choosing which inventory you can't appear on.
- **Headlines and descriptions are messaging, not character-count filling.** Provide genuinely distinct angles — benefit, proof, offer, objection-handling — not fifteen rewordings of the same line. The model tests combinations; give it real variety to test. Pin sparingly and only for non-negotiables.
- **Ad Strength is a signal, not a target.** "Excellent" tells you coverage and variety are present; it does **not** predict performance and is not a KPI. Don't degrade good creative to chase a label, and don't assume "Excellent" means the asset group works. Judge it on conversions and asset performance ratings, not the strength meter. See [[creative-strategy]].

## Audience signals

Audience signals are **inputs, not constraints.** This is the single most misunderstood feature in PMax. A signal does *not* restrict who PMax shows to — it tells the model "here's who's likely to convert, start here," and the model uses it to accelerate learning, then expands beyond it. Adding a signal does not wall off your audience; removing one does not "open it up." They're a head start, not a fence.

- **Customer Match is the highest-value signal**, full stop. Your converter and high-value-customer lists are first-party truth; nothing else seeds the model as well. Upload them and use them on every campaign that can.
- **New campaign:** give it strong signals early — customer lists, your best converting audiences, relevant custom segments built from high-intent search/URL behaviour. This shortens the learning period materially.
- **Established campaign:** signals matter less as the campaign accumulates its own conversion history and effectively learns its own audience — but refreshed first-party lists still help, especially after seasonal shifts.
- **No signals:** PMax still runs — it just learns more slowly and more expensively, exploring blindly until conversions accumulate. On a low-volume account that exploration phase can burn real budget before it finds intent. Never launch a PMax campaign with zero signals if you have any first-party data to give it. See [[audience-strategy]].

## Search themes

Search themes let you tell PMax which queries you believe are relevant — supplemental search signals you add to an asset group. They **help** when PMax isn't yet surfacing for valuable queries you know convert and you want to nudge it (a launch, a new product line, a known-good theme the model hasn't found). They're **redundant** once PMax has enough data to find that demand itself, which it usually does.

The critical interaction: **search themes respect the same matching hierarchy** — exact-match keywords in a Search campaign still win over a PMax search theme. But against phrase/broad and brand traffic, a search theme can pull queries into PMax that you'd rather keep in a controlled Search campaign. Two rules to avoid self-inflicted cannibalisation: (1) don't add search themes for terms you're actively running and want to control in Search; (2) handle brand explicitly — either exclude brand from PMax via brand exclusions / the brand-exclusion list, or knowingly let PMax serve brand and account for it in reporting. Don't let search themes quietly siphon brand and high-intent generics out of campaigns you built to own them. See [[search]].

## Optimisation levers

PMax hides most controls, but the ones it gives you are high-leverage — use them.

- **Brand exclusions** — exclude your own brand terms (and competitor/irrelevant brands) so PMax doesn't claim cheap brand conversions and flatter its own numbers. Combine with the account brand list. This is usually the first thing to configure.
- **Account-level negative keywords** are now available for PMax — use them for brand control, irrelevant terms, and known junk.
- **Location, language, ad scheduling** — real settings, set them correctly; PMax respects them.
- **URL expansion / final URL expansion** — when on, PMax can send traffic to *any* page on your site it thinks is relevant and generate matching headlines. Turn it **off** (or restrict it) when you need control over destinations and messaging; leave it on only when you trust it to find relevant deep pages. Add URL exclusions for pages that should never receive traffic (careers, support, out-of-stock).
- **Asset rotation — add vs replace.** Read asset performance ratings (Best / Good / Low). **Replace** "Low" assets; don't just pile on more. **Add** when coverage is incomplete (missing video/sizes) or you have a genuinely new angle to test. Refresh creative on a cadence to fight fatigue, especially on the YouTube/Display side. Don't thrash a campaign in learning — change assets deliberately, not daily.

## Insights and reporting

PMax's reporting is deliberately thin, and you have to work to see through it.

- **What it shows:** the Insights tab (search categories, audience insights, asset audience signals), asset performance ratings, and an asset-group-level breakdown. Useful directionally, not surgically.
- **The search terms insight panel** shows **categories/themes**, not the full raw search-term report you get in Search. You cannot see or add negatives against every individual query the way you can in Search — you get grouped categories and a limited negative-keyword capability. Treat it as a directional read, not a complete one.
- **Channel breakdown via scripts.** PMax does not natively show how spend/conversions split across Search vs Shopping vs Display vs YouTube. Use a PMax channel-breakdown script (the well-known community scripts) or the Google Ads API to pull the channel distribution. This is often the most revealing diagnostic you have — a PMax that's secretly 70% cheap Display/remarketing is a very different campaign from one serving on Shopping and Search.
- **Diagnosing "working vs just spending."** Ask: is it *incremental*, or harvesting existing demand? Check the channel split (is it leaning on remarketing/Display to claim conversions?), check brand vs non-brand (are the conversions just brand you already owned?), and compare account-level totals before/after launch rather than PMax's own self-reported numbers. If PMax "ROAS" is great but account-level new-customer revenue didn't move, PMax is re-attributing, not growing. Pair this with new-customer acquisition reporting where available.

## Lead gen considerations

PMax for lead gen carries extra risk because the thing it optimises toward (form submissions) is not the thing you sell (qualified pipeline), and PMax gives you *less* visibility to catch the gap than Search does. See [[lead-gen]] and [[smart-bidding]].

- **Offline conversion import is a requirement, not an option.** Without feeding lead *quality* back (MQL/SQL/closed-won, ideally with values), PMax optimises for cheap form fills and will reliably find you a flood of low-quality and spam submissions across Display and Discover inventory. OCI is the price of admission for lead-gen PMax.
- **The form asset / lead form question.** Be cautious with native lead forms in PMax — they lower friction in a way that often *lowers* lead quality and invites bots. Many practitioners disable easy/low-friction lead capture and drive to a qualified landing page with real form friction instead.
- **Feed-only/asset-light often beats full-asset in lead gen.** Full-asset PMax pushes into Display and Discover, which for lead gen are frequently where the junk comes from. A tighter, asset-light setup with strong signals and OCI tends to hold quality better. If you can build a "feed" (e.g. a page feed of services), use it to constrain serving.
- **Guard hard with brand exclusions, account negatives, and audience signals** built from real converters — lead-gen PMax needs more fencing than ecomm, not less.

## Ecomm considerations

Ecommerce is PMax's home turf, and **feed-only (or asset-light) PMax is the default for most ecomm accounts.** It behaves like a smarter Shopping campaign, stays close to high-intent inventory, and is the easiest to attribute. Reach for full-asset only when you deliberately want the upper-funnel spread and have the measurement to justify it. See [[ecomm]], [[shopping]], and [[smart-bidding]].

- **Segment asset groups / campaigns by product performance tier**, not category — best-sellers and high-margin lines with an aggressive tROAS, mid-tier at target, clearance/low-performers in a separate bucket. This is where most ecomm PMax gains actually come from: bidding each tier to its true value instead of one blunt account-wide target. Optimise toward **profit (POAS)** where margins vary, by feeding margin-adjusted values or using value rules — raw tROAS over-invests in high-revenue, low-margin SKUs (see [[smart-bidding]]).
- **Interaction with Standard Shopping.** PMax outranks Standard Shopping for the same products. Running both for the same catalogue means PMax simply wins the overlap — so either commit to PMax for those products, or deliberately ring-fence (some accounts keep Standard Shopping for control/edge cases and accept the trade). Don't run both unwittingly and assume they're additive; they're competing, and PMax takes the auction.
- **Merchant Center feed quality is a core PMax input.** In feed-driven PMax the feed *is* the targeting and a primary signal. Titles, product types, GTINs, attributes, images, pricing accuracy, and availability all feed the model — a thin or stale feed degrades PMax exactly like bad conversion data does. Feed optimisation is PMax optimisation. Fix disapprovals, enrich titles/attributes, and keep availability accurate.
- **Seasonal budget adjustments.** PMax responds to budget headroom; plan budget and use Smart Bidding seasonality adjustments ahead of known peaks (and exclusions around anomalies like a site outage or a one-day sale), rather than yanking budget mid-learning. Give it room before peak, not during.

## Related
[[search]], [[shopping]], [[smart-bidding]], [[creative-strategy]], [[audience-strategy]], [[campaign-structure]], [[ecomm]], [[lead-gen]], [[pmax-audit-framework]].
