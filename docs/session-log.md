---
title: Session Log
version: v0.1
updated: 2026-05-31
status: draft
---

# Session Log

A running log of build sessions. Newest entries at the top. Concise by design — this tracks decisions and direction, not a full project map (see [README.md](../README.md) and [CLAUDE.md](../CLAUDE.md) for that).

## 2026-06-02

**What was built**
- `tools/token-counter.md` — reference guide and script for measuring a document's true token cost (PDF text + per-page image tokens) vs its markdown conversion, via Anthropic's free `count_tokens` endpoint. Companion to the Markitdown guide; wired into the README tools list.
- Markitdown LinkedIn post finalised and grounded with a real measurement: Google's Demand Gen implementation guide costs 31,278 tokens as a PDF vs 2,718 as markdown — an 11.5× token reduction (446× by bytes). Post lives in the practitioner's vault, not this repo.

**Notes**
- The 2026-05-31 "what's next" list is now mostly done: the four `small-business/` files and the `meeting-notes` / `account-context` Obsidian templates all exist.

**What's next**
- Collectors skill (Client Context Collector).
- Discord — week two.
- v2 automation layer (Tier 2 build).

**Repo state:** latest commit on `main` at time of writing — `b25dd1d`.

## 2026-05-31

**What was built**
- Full repo scaffold (folder structure, frontmatter conventions, status lifecycle).
- 22 files written to full content — CLAUDE.md, README.md, the four Google Ads best-practices files, three campaign types, both context files (lead-gen, ecomm), both audit frameworks, four skills (account-audit, campaign-review, monthly-report-brief, search-term-analysis), skills index, three setup guides, the Markitdown tool guide, the vault structure + client-file template, CONTRIBUTING.md, and the v2 automation spec.
- Public landing page.
- LinkedIn launch post.

**Key decisions**
- **Skill taxonomy** — four kinds: Collectors, Diagnostics, Builders, Reviews. Collectors are next on the roadmap.
- **Three-tier automation architecture** — Tier 1 public/manual, Tier 2 practitioner automation via Google Ads Scripts + CoWork, Tier 3 internal agency API layer with a human approval gate. Line between T2/T3 is access (Scripts vs API), not ambition.
- **Two-slider principle** — writing skills means resisting over-instructing and over-feeding; set checkpoints and let Claude reason between them.
- **Client brief context-window analogy** — convert documents to markdown before feeding Claude (Markitdown); container bloat steals reasoning budget.

**What's next**
- Write the small-business files (getting-started, first-campaign, reading-your-results, when-to-get-help).
- Write the remaining Obsidian templates (meeting-notes, account-context).
- Markitdown post.
- Discord — week two.

**Repo state:** latest commit on `main` at time of writing — `2539919`.
