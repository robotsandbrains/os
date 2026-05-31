---
title: Contributing
version: v0.1
updated: 2026-05-31
status: draft
---

# Contributing

Thanks for wanting to improve the Robots & Brains OS. This repo is maintained by practitioners for practitioners, and contributions are welcome — knowledge files, skills, contexts, tools, fixes. This guide covers *how* to contribute and, importantly, the principles we've learned for writing skills that actually work.

## 1. How to contribute

We work **outline-first.** Don't write a full file and open a giant PR cold — propose the *shape* first:

1. **Open a GitHub issue** with the proposed outline — section headings and a one-line description under each. For a skill, sketch the four sections (what it does, when to use it, the prompt, example output).
2. **Get agreement on the shape.** A maintainer (and the community) reacts to the structure before a word of content is written. This is where most of the quality conversation happens.
3. **Write the content** once the outline is agreed, and open a PR referencing the issue.

Why: agreeing the structure up front keeps quality high and avoids wasted effort — it's far cheaper to rework an outline than a finished file. It's the same discipline we apply to client work: agree the plan, then execute.

## 2. The two-slider principle for writing skills

The hardest part of writing a good skill is restraint. When you write one, resist two equal and opposite temptations:

- **Too many instructions.** Over-explaining removes the model's room to think. LLMs are smart; spelling out every micro-step often produces *worse* results than giving Claude the goal and letting it find the route. Show what *good* looks like, set checkpoints, and let Claude figure out the path between them. If you're writing the tenth sub-bullet of a step, you're probably over-instructing.
- **Too much data.** Flooding a skill with context degrades output — the signal drowns in noise and the context window fills with bloat. **Pre-process data before it reaches Claude** (convert documents to markdown — see [tools/markitdown.md](tools/markitdown.md) — summarise, strip the irrelevant), or teach Claude how to **fetch what it needs in chunks** rather than feeding it everything at once.

The skills that work are the ones where you resisted the urge to over-explain *and* over-feed. Both sliders pulled too far ruin a skill; the craft is finding the middle.

## 3. The checkpoint model

Structure skills around **checkpoints, not step-by-step instructions.** Between checkpoints, let Claude reason freely — that's where the model earns its keep. A checkpoint is one of two things:

- **A human-in-the-loop moment** — the practitioner reviews or supplies input before Claude proceeds (e.g. "confirm inputs before analysing," "flag findings for review before acting"). This keeps the human in control of consequential decisions.
- **A data validation point** — Claude checks it's on the right track before continuing (e.g. "verify conversion tracking is sound before trusting any performance number," "state the threshold you used").

Design the skill as a sequence of checkpoints with open reasoning in between, rather than a rigid script. The existing skills ([account-audit](skills/account-audit.md), [search-term-analysis](skills/search-term-analysis.md)) follow this shape — load context, confirm inputs (checkpoint), reason, output in a defined format (checkpoint).

## 4. Skill lifecycle

Every skill (and file) carries a `status` in its frontmatter:

- **`coming-soon`** — placeholder only; frontmatter and maybe a one-line description, no real content.
- **`draft`** — written, but **not yet tested in real accounts.** Usable, but treat the output critically.
- **`stable`** — tested, reliable, and recommended for use.

**Only promote a skill to `stable` after using it on at least one real account and verifying the output.** "It reads well" is not stable; "it produced correct, useful output on a live account" is. Promotion is an evidence bar, not a confidence bar.

## 5. What belongs in the repo vs the vault

The dividing line is simple — *is it universal, or is it yours?*

- **Universal, non-client-specific knowledge → the repo.** Best practices, campaign-type mechanics, contexts, skills, tools, templates.
- **Anything that identifies a client, account, or business → the vault only.** Names, account IDs, budgets, performance data, briefs.
- **Personal SOPs and agency-specific approaches → the vault only.** Your edge, your processes, your client-specific playbooks stay private.

If you're unsure, ask: would this make sense in *anyone's* account? If yes, repo. If it only makes sense for a specific client or your specific agency, vault. See [CLAUDE.md](CLAUDE.md) for the full privacy model.

## 6. File conventions

- **Kebab-case filenames** (`smart-bidding.md`, not `Smart Bidding.md`).
- **Frontmatter on every file:** `title`, `version`, `updated`, `status`.
- **Wikilinks for cross-references** — `[[file-name]]` format, for Obsidian compatibility.

Match the voice and structure of the surrounding files: direct, opinionated where the evidence supports it, practitioner-written, no filler.

## Related
[README.md](README.md) · [CLAUDE.md](CLAUDE.md) · [skills/overview.md](skills/overview.md) · [tools/markitdown.md](tools/markitdown.md)
