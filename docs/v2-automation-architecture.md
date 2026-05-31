---
title: V2 Automation Architecture
version: v0.1
updated: 2026-05-31
status: draft
---

# V2 Automation Architecture

## What this document is

This is the **architectural spec for the v2 automation layer.** The public OS as it stands (v1) is deliberately **read / analyse / recommend**: Claude works from data the practitioner provides, with no API or special access required. V2 adds **scheduled automation** at two levels, depending on the practitioner's setup. This document defines the tiers, the principle that holds across all of them, and the deliberate line between what ships publicly and what Robots & Brains runs internally. It is a spec, not a shipped feature — see the roadmap note at the end.

## The core principle that does not change

**Claude reasons and recommends. Humans decide what crosses into the live account.**

This holds at every tier, without exception. It is **not a safety disclaimer bolted on after the fact — it is a design decision.** The OS is built to make practitioners *better*, not to replace their judgement. Automation removes the friction of *initiating* analysis and *preparing* recommendations; it never removes the human from the decision to change a live account. Every tier below is designed around keeping that decision with the practitioner.

## The three tiers

### Tier 1 — Public OS (v1, live now)

- **Who it's for:** everyone, including small business owners.
- **How data gets in:** the practitioner exports from the Google Ads UI and pastes or uploads it.
- **What Claude does:** reads, analyses, recommends, drafts.
- **Automation:** none — fully manual trigger.
- **Requirements:** a Claude subscription only.

Tier 1 is the entire public OS today. Nothing here needs developer access, tokens, or infrastructure — just Claude and the knowledge layer.

### Tier 2 — Practitioner automation (v2, planned)

- **Who it's for:** solo practitioners and small agencies with Claude Max.
- **How data gets in:** **Google Ads Scripts** export data to Google Sheets or Drive on a schedule — **no API developer token required.** Script access is built into every Google Ads account.
- **What CoWork does:** watches for the file, triggers the relevant skill automatically, and surfaces the output.
- **What Claude does:** the same as Tier 1 — reads, analyses, recommends, drafts — but **triggered automatically rather than manually.**
- **Automation:** scheduled, CoWork-orchestrated, no human trigger needed.
- **Requirements:** Claude Max, CoWork, and Google Ads script access (built into every account).

**Example workflow:** a Google Ads Script exports the search term report to Drive every Monday at 6am → CoWork picks it up → the [search term analysis](../skills/search-term-analysis.md) skill runs → the practitioner wakes up to a structured report with negatives ready to review.

### Tier 3 — Agency layer (internal Robots & Brains)

- **Who it's for:** agencies with existing Google Ads API access.
- **How data gets in:** directly via the **Google Ads API.**
- **What the pipeline does:** **Reason** (Claude logs its reasoning) → **Build payload** (structured JSON; Claude never calls the API directly) → **Validate** (API validate-only mode) → **Human review** (a real blocker — explicit approval required) → **Execute** (the approved payload is submitted).
- **What Claude does:** reasons and builds payloads; **code executes and submits** — Claude never touches the API itself.
- **Automation:** fully scheduled, API-connected, with a human approval gate on every write.
- **Requirements:** a Google Ads API developer token, OAuth setup, API approval from Google, and existing infrastructure.

> **This tier is not part of the public OS.** It is what Robots & Brains runs internally on top of the OS foundation.

## Why the line between Tier 2 and Tier 3 exists

The dividing line is **access, not ambition.** Google Ads **API** access requires a developer token and Google's approval — not accessible to most solo practitioners or small business owners. Google Ads **Scripts** are built into every account, require no approval, and can export any data the UI can show.

- **Tier 2 uses Scripts deliberately** because they work for *everyone* — no gatekeeping, no approval process, available the moment you have a Google Ads account.
- **Tier 3 uses the API** because Robots & Brains already has it, and because the API enables **write access**, which Scripts do not.

The line is drawn to keep the public tier universally accessible while reserving write-capable automation for the internal layer that already meets Google's API bar.

## What Tier 2 unlocks for practitioners

The shift from **"I run skills when I remember to"** to **"skills run on a schedule and I review the output."** Same knowledge, same recommendations, zero manual trigger. The practitioner stays in control of what happens next — the automation only removes the friction of *initiating* the analysis, never the decision that follows it. That's the whole value: the analysis is waiting for you instead of waiting *on* you.

## Roadmap note

**Tier 2 is planned, not built.** This spec exists so the architecture is clear when the build begins. The Google Apps Script templates and CoWork task configurations will ship as part of the [`tools/`](../tools/) folder when ready.

## Related
[skills/overview.md](../skills/overview.md) · [tools/markitdown.md](../tools/markitdown.md) · [README.md](../README.md) · [CLAUDE.md](../CLAUDE.md)
