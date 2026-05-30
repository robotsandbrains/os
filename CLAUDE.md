---
title: Robots & Brains OS — Operating Guide for Claude
version: v0.1
updated: 2026-05-31
status: draft
---

# CLAUDE.md

> Primary interface: Claude Code (CLI). Also structured to load cleanly as a Claude Project knowledge base.

## 1. What this repository is
One-line: an open-source AI operating system that turns paid media best practices into runnable, repeatable workflows for practitioners.

## 2. How to use this repo with Claude
- **Claude Code (primary):** point Claude Code at this repo root; it reads this file first as the system map.
- **Claude Projects (secondary):** upload the repo (or key folders) as Project knowledge; this file doubles as the Project's custom instructions.
- **Obsidian vault:** how the markdown here mirrors a practitioner's working vault.

## 3. Operating principles
- Principle-led, platform-second — strategy before tactics.
- Human-in-the-loop — Claude drafts, the practitioner decides.
- Evidence over opinion — every recommendation ties to account data.
- Reusable over bespoke — prefer skills and templates to one-off prompts.

## 4. Repository map
- `google-ads/` — platform knowledge: best practices, campaign types, contexts, audits.
- `skills/` — runnable workflows (audit, review, reporting, client comms).
- `meta-ads/` — Meta platform knowledge (coming soon).
- `obsidian-template/` — vault structure and note templates for client work.
- `setup/` — onboarding for the tools (Claude Code, Obsidian).

## 5. How knowledge is organised
- **Best practices** = durable principles. **Campaign types** = platform mechanics. **Contexts** = how principles shift by business model (lead-gen vs ecomm). **Skills** = the verbs that combine them.

## 6. How to run a skill
- Where skills live, the four-part anatomy (what/when/prompt/output), and how to invoke one in a Claude Code session.

## 7. Conventions
- Filenames in kebab-case; frontmatter on every file; `status` lifecycle (`coming-soon` → `draft` → `stable`); versioning with `v0.1`.

## 8. Working with client data
- What never goes in the repo (PII, account IDs), where client context lives (vault), redaction expectations.

## 9. Contributing
- How to propose a new skill or best-practice file; the outline-first workflow; review expectations.

## 10. Roadmap pointers
- Where to look for what's planned vs shipped; status fields as the source of truth.
