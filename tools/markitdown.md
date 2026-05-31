---
title: Markitdown
version: v0.1
updated: 2026-05-31
status: draft
---

# Markitdown

> A reference guide, not a skill. How to convert documents to clean markdown before feeding them to Claude — the single highest-leverage habit for keeping the context window efficient.

## What Markitdown is

Markitdown is a **free, open-source command-line tool from Microsoft** that converts files — PDFs, Word docs, PowerPoint, Excel, HTML, images, and audio — into clean markdown. One command in, lightweight markdown out. No subscription, no account, no cloud round-trip. It's purpose-built to turn messy document formats into the plain, token-efficient text that language models read best.

GitHub: **[microsoft/markitdown](https://github.com/microsoft/markitdown)**

## Why it matters for this OS

In the Robots & Brains OS, **context window efficiency is everything.** Claude's context window is a finite budget — every token a document consumes is a token unavailable for reasoning, instructions, and your account data. Feed a 500KB PDF directly and you spend a huge slice of the window on the file's binary bloat, formatting cruft, and encoding overhead. The cost isn't just space: a bloated context **degrades output quality** (the signal gets buried in noise) and **slows the session**.

The same content converted to markdown is typically **10–20× smaller** — pure, structured text with none of the overhead. For a paid media practitioner, this is the difference between a sharp, fast session and a sluggish, mediocre one whenever you feed Claude:

- **Client briefs and onboarding documents**
- **Google Ads policy documents**
- **Competitor research PDFs**
- **Monthly report templates**
- **Google's own help documentation**

Convert first, and Claude reads the *content* instead of choking on the *container*.

## Installation

```
pip install markitdown
```

Or, for full format support (all the optional converters — Office, audio, images, etc.):

```
pip install 'markitdown[all]'
```

## Basic usage

One command per file. Pipe the output to a `.md` file:

```
markitdown input.pdf  > output.md
markitdown input.docx > output.md
markitdown input.pptx > output.md
```

The resulting markdown file is ready to paste into Claude or save into your Obsidian vault. That's the whole workflow — convert, then use the markdown.

## Practical workflows for paid media practitioners

Five concrete ways this fits day-to-day paid media work:

1. **Client onboarding PDF → vault.** Convert the onboarding pack to markdown and drop it into `{VAULT_PATH}/clients/{client-name}/`, so Claude can read it as private client context (see [vault structure](../obsidian-template/vault-structure.md)) instead of you re-pasting a giant PDF each session.
2. **Google Ads policy PDFs → repo reference.** Convert policy documents into clean markdown and store them as reference knowledge under `google-ads/`, so they become part of the public, universal knowledge layer.
3. **Competitor research reports → analysis input.** Convert a research PDF to markdown *before* feeding it to Claude for analysis — you'll get a faster, sharper read and leave room in the context window for the actual reasoning.
4. **Monthly report templates (Word) → markdown skills.** Convert a recurring Word report template into markdown and adapt it into a repeatable reporting workflow (pairs with the [monthly report brief](../skills/monthly-report-brief.md) skill).
5. **Landing page HTML → creative analysis.** Convert a saved landing page's HTML to markdown so Claude can audit ad-to-page message match without wading through markup (see [creative strategy](../google-ads/best-practices/creative-strategy.md)).

## Size comparison examples

Typical real-world reductions:

| Document | Raw size | As markdown | Reduction |
|----------|----------|-------------|-----------|
| Google Ads policy PDF | ~2 MB | ~150 KB | ~13× |
| Client brief (Word) | ~500 KB | ~30 KB | ~17× |
| Competitor research report (PDF) | ~5 MB | ~400 KB | ~12× |

**The principle:** if you are going to feed a document to Claude, convert it to markdown first. **Always.**

## Integration with this OS

Markitdown is the on-ramp that feeds the three-layer system cleanly (see [CLAUDE.md](../CLAUDE.md)):

- **Universal reference → the repo.** Converted documents that are *universal and public* — Google Ads policies, platform help docs, general best-practice references — belong in `google-ads/` as knowledge files, with proper frontmatter and kebab-case names.
- **Client-specific → the vault.** Converted documents that are *private and client-specific* — briefs, onboarding packs, account notes — belong in the Obsidian vault under the relevant client folder, never in this repo (see [what never goes in this repo](../CLAUDE.md)).

The standing rule: **never feed raw PDFs (or Word, PowerPoint, etc.) to Claude when a markdown version is possible.** Convert, file it in the right layer, then work.

## Limitations

- **Scanned / image-only PDFs** (no text layer) need **OCR first** — Markitdown extracts existing text, it doesn't read pixels. Run an OCR pass before converting.
- **Complex tables** may lose some formatting in the conversion; spot-check important tabular data.
- For the **vast majority of paid media documents** — briefs, policies, reports, research — the output is clean and immediately usable as-is.

## Related
[skills/overview.md](../skills/overview.md) · [vault structure](../obsidian-template/vault-structure.md) · [CLAUDE.md](../CLAUDE.md) · [monthly report brief](../skills/monthly-report-brief.md)
