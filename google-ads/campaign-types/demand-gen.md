---
title: Demand Gen
version: v0.1
updated: 2026-05-31
status: draft
---

# Demand Gen

## What Demand Gen actually is

The honest version: **Demand Gen is Google's answer to Meta's feed advertising.** It's a visual, interruption-based campaign type that serves across YouTube (in-feed and in-stream/Shorts), Discover, and Gmail — the surfaces where people are browsing and scrolling, not searching. You're paying to interrupt attention with a compelling image or video, the same fundamental motion as a Meta or TikTok ad. It replaced Discovery campaigns and folded in much of what you'd previously have run as standalone YouTube action campaigns.

What it is **not**, and these matter:
- **Not a Search replacement.** Search captures *existing* demand from people actively looking. Demand Gen *creates* demand by interrupting people who weren't looking. Different job, different funnel stage, different mindset.
- **Not a PMax substitute.** PMax is goal-led automation across *all* inventory including Search and Shopping, optimising primarily for conversions wherever it can find them. Demand Gen is a *channel-specific, creative-led* campaign you actually control — you choose the audiences, the creative, the placements-by-surface. You'd run Demand Gen precisely when you want hands-on control of the visual/social surfaces rather than handing them to PMax's black box.

**Inventory it actually reaches:** YouTube (in-feed video discovery, in-stream, and Shorts), the Discover feed (the personalised feed in the Google app and on Android/Chrome surfaces), and Gmail (the Promotions/Social tabs). That's it — it does **not** touch Search, standard Shopping, or the broader Display network (that's a separate Display campaign).

**How the auction and funnel position work:** like the rest of the system it's Smart Bidding under the hood (see [[smart-bidding]]), bidding auction-time for attention based on conversion likelihood. But because it serves to people in a *browsing* rather than *searching* state, intent is lower and the funnel position is **upper-to-mid**: awareness, consideration, demand creation, and retargeting — not bottom-of-funnel demand capture. Judge it accordingly (see Bidding and measurement).

## When Demand Gen makes sense

Most practitioners do one of two wrong things: ignore Demand Gen entirely (leaving the visual/social surfaces to PMax or to Meta), or switch it on with no idea what it's doing and then kill it a month later because the last-click CPA looked bad. Both are mistakes. Here's when it earns its place.

**Use Demand Gen when:**
- **You have genuinely good visual/video creative** — or can make it. This is the gating condition. Demand Gen without strong creative is dead on arrival (see Creative requirements). If you can't feed it creative, don't run it.
- **You're a visually-driven brand** — ecomm, consumer products, lifestyle, food/beverage, travel, anything where the product or experience *looks* compelling.
- **You want to build demand, not just harvest it** — you've maxed out efficient Search/Shopping demand capture and need to create new demand to grow.
- **You run Meta and want Google's equivalent inventory** — Demand Gen is the natural way to extend social-style prospecting and retargeting into the Google ecosystem.
- **You have strong first-party audiences** to seed prospecting and a retargeting pool to re-engage.

**Ignore it (for now) when:**
- **You have no usable creative and no way to make it.** Non-negotiable.
- **You're a pure bottom-of-funnel, capture-only account** with limited budget — spend it on Search/Shopping first; Demand Gen is a growth layer, not a foundation.
- **You can't measure beyond last-click** and won't get buy-in to evaluate it on view-through/assisted/incremental terms — you'll mis-judge it and waste the spend (see measurement).
- **The account is tiny** — Demand Gen needs room and conversion volume to learn like any Smart Bidding campaign.

**Minimum viable setup:** strong creative across the required formats (image *and* video, multiple ratios), at least one well-built audience (first-party seed for prospecting, a retargeting list, or a relevant custom/in-market segment), clean conversion tracking, a Smart Bidding goal you'll evaluate *honestly*, and the measurement framing agreed up front so the campaign isn't judged on the wrong metric.

## Creative requirements

**Demand Gen is a creative-led campaign type — weak creative kills it regardless of targeting or budget.** This is the single most important thing to accept. In Search, a mediocre ad still serves on high-intent queries and converts; in Demand Gen, mediocre creative simply gets scrolled past and the campaign never works. The creative *is* the campaign. See [[creative-strategy]].

**Formats required and what they must do:**
- **Images** — high-resolution, multiple ratios (1:1 square, 1.91:1 landscape, and importantly **4:5 / vertical** for mobile-first feeds and Shorts). They must stop the scroll in the first instant — clear subject, strong visual, minimal text overlay, on-brand.
- **Video** — increasingly the highest-performing format, especially for YouTube in-stream and Shorts. Provide vertical video for mobile feeds; lead with a hook in the first 1–2 seconds; design for **sound-off viewing** (captions, visual storytelling).
- **Carousel** — multiple images/cards for product ranges or sequential messaging.
- Plus headlines, descriptions, logo, and business name as supporting text.

**The visual standard:** this is a feed competing with organic content and with Meta/TikTok-grade ads. The bar is *social-native*, not display-banner. Polished, authentic, native-feeling creative wins; obvious stock, cluttered banners, and corporate stiffness lose. If it looks like a display ad, it will perform like one.

**Interruption context vs intent context — the mindset shift:** in Search you answer a question someone already asked, so the creative can be direct and transactional. In Demand Gen nobody asked — you have to *earn* the attention. Creative must hook, intrigue, and give a reason to care *before* it sells. Lead with the visual/emotional hook, the benefit, or the curiosity gap; the hard sell comes second. Writing Demand Gen creative like a Search ad ("Get 20% Off — Shop Now") into a cold browsing audience is the classic failure.

**Video vs image — when each works:** **video** is stronger for demand creation, storytelling, demonstrating a product in use, and YouTube/Shorts inventory — use it as the primary format when you have it. **Image** is faster/cheaper to produce, strong for retargeting (where the audience already knows you), product showcases, and Discover/Gmail feeds. Best practice is to run **both** and let Smart Bidding allocate; don't starve the campaign of video if you want YouTube reach.

## Audience strategy for Demand Gen

Audiences work differently here than in Search, and audience *quality matters more*. In Search, intent comes from the query, so the audience is a secondary signal. In Demand Gen there is no query — **the audience and the creative are the entire targeting**, so a weak audience means you're interrupting the wrong people with no intent signal to save you. See [[audience-strategy]].

- **Customer Match — your highest-value asset, as everywhere.** Use converter and high-value lists to seed prospecting (the system's lookalike expansion builds from them) and to power retargeting and suppression. First-party data is the strongest foundation for Demand Gen prospecting.
- **Lookalike expansion.** Demand Gen builds lookalike-style reach automatically from your first-party seed lists (with reach/similarity controls). This is now the primary way to prospect at scale — feed a strong, clean seed (qualified customers, not raw site traffic) and let it expand. Garbage seed → garbage expansion.
- **Similar segments / in-market.** Standalone "similar audiences" are gone as a manual target — expansion happens off your seeds (see [[audience-strategy]]). **In-market** segments are a reasonable *prospecting* layer here (people researching a category), more useful as targeting in Demand Gen than in Search because Demand Gen is audience-led by nature. **Affinity/custom segments** (by interests, URLs, apps) round out interest-based prospecting.
- **Build two distinct stacks:**
  - **Prospecting stack** — first-party seeds + lookalike expansion + relevant in-market/custom segments, with existing customers *suppressed*. Goal: reach new people who resemble good customers.
  - **Retargeting stack** — site visitors, video viewers, engagers, cart abandoners, past purchasers. Goal: re-engage warm audiences who already know you. Keep these separate so you can budget, bid, message, and measure them differently — retargeting will always show a better CPA, and mixing them hides what prospecting is really doing.

## Bidding and measurement

**Bidding:** standard Smart Bidding — Maximize Conversions / Maximize Conversion Value, with tCPA/tROAS once you have the volume to support a target (see [[smart-bidding]]). Demand Gen also supports **view-through and engagement-oriented goals** (e.g. optimising for clicks/site visits to fill the funnel) which can be appropriate for upper-funnel objectives. Start without a tight target to let it learn, then add one; don't strangle a demand-creation campaign with an aggressive last-click CPA target on day one.

**The measurement challenge — this is where most practitioners get Demand Gen wrong.** Demand Gen drives **view-through conversions and assisted conversions** that **last-click attribution misses entirely.** Someone sees your YouTube ad, doesn't click, searches your brand two days later, and converts via Search — last-click hands the entire credit to Search and shows Demand Gen a near-zero CPA. Judge Demand Gen on last-click and you'll kill the campaign that *created* the demand Search took credit for.

How to evaluate it honestly:
- **Look at view-through and assisted conversions**, not just last-click — Demand Gen's contribution lives largely in the paths it *started*.
- **Use a data-driven attribution model** so credit is distributed across the journey rather than dumped on the last touch.
- **Think incrementality, not attribution.** The real question is "did running Demand Gen grow *total* conversions / brand search / new customers?" — measured by holdout/lift testing or by watching account-level totals and brand-search volume before and after, not by Demand Gen's self-reported CPA.
- **Comparing Demand Gen CPA to Search CPA is the wrong frame.** They do different jobs at different funnel stages — Search harvests cheap existing intent; Demand Gen creates new, more expensive demand. Demand Gen will *always* look worse on last-click CPA, and that comparison tells you nothing useful. Compare Demand Gen to other *upper-funnel* options (Meta prospecting, YouTube, Display), and judge it on incremental growth and funnel contribution.

## Demand Gen and the funnel

Position it as the **demand-creation layer that feeds the demand-capture layer.** Search and PMax are brilliant at converting people who already want what you sell — but they can only harvest the demand that exists. When you've captured the efficient existing demand and want to *grow*, you have to create new demand, and Demand Gen (alongside Meta/YouTube) is how you do it on Google's surfaces.

- **It builds the audience pool that Search and PMax convert.** Demand Gen interrupts cold/warm browsers, introduces the brand/product, and seeds interest — those people later search, return to site, or get retargeted, and *that's* where Search and PMax close them. The conversions often appear in the capture campaigns; the *cause* is often the demand-creation campaign. This is exactly why last-click under-credits it.
- **Sequencing logic:** Demand Gen creates awareness/interest → it builds retargeting and brand-search pools → Search and PMax capture and convert that warmed demand. Build the retargeting audiences deliberately so the funnel actually connects.
- **Budget allocation between upper and lower funnel:** fund efficient demand-*capture* (Search, Shopping, PMax) first — it's the cheapest conversion. Allocate to demand-*creation* (Demand Gen) once capture is maxed and you need growth, sizing it as a deliberate growth investment with an honest measurement frame, not as a campaign expected to win on last-click CPA against Search. The split depends on how demand-constrained the account is: demand-constrained accounts (capped Search) need more upper-funnel; demand-rich accounts can stay capture-heavy longer.

## Lead gen considerations

- **Use it for awareness and retargeting, not as a primary lead source.** For lead gen, Demand Gen's strongest roles are top-of-funnel awareness (introducing the brand/offer to cold audiences who'll later search and convert via Search) and **retargeting** site visitors and non-converters who didn't fill the form. Don't expect it to be your main last-click lead engine — it feeds the funnel Search closes. See [[lead-gen]].
- **The lead form asset.** Demand Gen supports lead form extensions/assets for in-platform capture. Useful for low-friction volume, but apply the standard caution: low-friction forms on a cold, interrupted audience produce **lower-intent leads and more junk** than a high-intent Search query does. Qualify in the creative and consider driving to a real landing page when quality matters more than volume (see [[creative-strategy]] and [[pmax]] on lead-form caution).
- **Why Demand Gen lead quality differs from Search — and how to account for it.** A Search lead raised their hand by searching; a Demand Gen lead was interrupted mid-scroll. Same form, very different intent — Demand Gen leads need more nurturing and convert to sale at lower rates. Account for it by tracking lead-to-sale by source (don't pool them), feeding lead *quality* back via offline conversion import so Smart Bidding optimises for qualified leads not raw form-fills, and setting a *separate, looser* CPA expectation for Demand Gen leads than for Search. Judging Demand Gen leads by the Search lead CPA will make a useful awareness/retargeting channel look like a failure.

## Ecomm considerations

Ecommerce is Demand Gen's strongest use case — it's visual, it has a product feed, and it has rich retargeting audiences. See [[ecomm]], [[shopping]], and [[pmax]].

- **Product feed integration.** Demand Gen can pull your Merchant Center product feed into the creative, turning campaigns into a **visual catalogue** — dynamic product imagery, pricing, and retargeting the specific products a user viewed. Connect the feed to unlock product-level relevance and dynamic retargeting.
- **The visual catalogue use case.** For considered/lifestyle purchases especially, Demand Gen lets shoppers *discover* products in a browsing context — a feed-driven, visually-merchandised showcase across YouTube/Discover/Gmail. This is genuine demand creation: people find products they weren't searching for.
- **Retargeting cart abandoners and past purchasers.** Build a retargeting stack on your highest-intent ecomm audiences — cart/checkout abandoners (dynamic product retargeting is potent here), product-viewers, and past purchasers for cross-sell/replenishment. These are usually Demand Gen's most efficient conversions; keep them in a separate stack from prospecting so the efficient retargeting numbers don't flatter (and hide) the prospecting investment.
- **How it complements Shopping and PMax rather than competing.** Shopping and PMax *capture* product demand (the user searching/ready); Demand Gen *creates* it (the user discovering) and *re-engages* it (retargeting). Run them together: Demand Gen fills the top of the funnel and the retargeting pool, Shopping/PMax convert at the bottom. The same measurement caveat applies — don't judge Demand Gen's contribution on last-click against Shopping/PMax; it's building the demand they're harvesting.

## Related
[[creative-strategy]], [[audience-strategy]], [[smart-bidding]], [[search]], [[pmax]], [[shopping]], [[video]], [[lead-gen]], [[ecomm]].
