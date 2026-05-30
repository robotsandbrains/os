---
title: Claude Projects Setup
version: v0.1
updated: 2026-05-31
status: draft
---

# Claude Projects Setup

Step-by-step guide to using the Robots & Brains OS with **Claude Projects** (claude.ai) as an alternative to Claude Code — suitable for practitioners who prefer the browser interface and for small business owners.

New here? Read [getting-started.md](getting-started.md) first to choose your path and privacy level.

## What Claude Projects is — and why it works here

A **Project** in claude.ai is a workspace that bundles two things: **Project knowledge** (files you upload once, which Claude can reference in every conversation in that Project) and **custom instructions** (a standing system prompt that shapes how Claude behaves). That maps almost perfectly onto this OS: the repo's knowledge files become Project knowledge, and [`CLAUDE.md`](../CLAUDE.md) becomes the custom instructions. The result is a browser-based version of the OS — no install, no terminal, no Git required. It's the easiest on-ramp, and the right choice if you'd rather work in a chat window than a command line.

## 1. Create a new Project

In [claude.ai](https://claude.ai), open the sidebar and click **Projects → Create Project**. Name it something like *"Robots & Brains OS — [Your Business]"* and create it. You'll add knowledge and instructions in the next steps.

## 2. Upload the right files as Project knowledge

**Don't upload the whole repo** — Project knowledge has limits, and dumping everything dilutes relevance. Upload a focused set:

- **Always:** [`CLAUDE.md`](../CLAUDE.md) (also used for instructions in step 3).
- **The Google Ads files relevant to you** — start with the foundations and your context:
  - [`smart-bidding.md`](../google-ads/best-practices/smart-bidding.md), [`campaign-structure.md`](../google-ads/best-practices/campaign-structure.md), [`audience-strategy.md`](../google-ads/best-practices/audience-strategy.md), [`creative-strategy.md`](../google-ads/best-practices/creative-strategy.md)
  - The campaign types you run: [`search.md`](../google-ads/campaign-types/search.md), [`pmax.md`](../google-ads/campaign-types/pmax.md), [`demand-gen.md`](../google-ads/campaign-types/demand-gen.md)
  - Your business context: [`lead-gen.md`](../google-ads/contexts/lead-gen.md) **or** [`ecomm.md`](../google-ads/contexts/ecomm.md) (you usually only need one)
- **The skill files you'll actually run** — e.g. [`account-audit.md`](../skills/account-audit.md), [`campaign-review.md`](../skills/campaign-review.md), [`monthly-report-brief.md`](../skills/monthly-report-brief.md).

To get the files: download the repo as a ZIP from GitHub (green **Code → Download ZIP** button) — no Git needed — and upload the relevant `.md` files. Add more later as your needs grow; keep the set lean and current.

## 3. Set your custom instructions

Open the Project's **custom instructions** and **paste in the full contents of [`CLAUDE.md`](../CLAUDE.md)**. This gives every conversation in the Project the OS's operating principles, navigation map, and skill-running rules as a standing system prompt — the same orientation Claude Code gets by reading the file on launch. Update this if CLAUDE.md changes.

## 4. Handle vault context (without VAULT_PATH)

Claude Projects has no access to your local filesystem, so there's no `VAULT_PATH`. You load private context manually: **at the start of a conversation about a specific client, paste that client's file** (your filled-in [client file](../obsidian-template/templates/client-file.md)) straight into the chat. Then ask your question. Claude uses it for that conversation only.

Keep your vault in Obsidian as usual (see [obsidian-setup.md](obsidian-setup.md) and [vault structure](../obsidian-template/vault-structure.md)) — it stays local and private; you're just copy-pasting the relevant slice when you need it. For recurring clients, keep each client file handy so pasting it in is a two-second job. *(If you're "repo only" with no vault, skip this — just describe your account in the chat.)*

## 5. Limitations vs Claude Code

Worth knowing what you trade for the browser convenience:

- **No Git integration.** You can't pull updates or run version control from the Project — you re-download and re-upload files when the repo changes.
- **Manual vault loading.** No automatic `{VAULT_PATH}/clients/...` lookup; you paste client context into each conversation yourself.
- **Skills require copy-paste.** Instead of Claude reading a skill file in place, you open the skill and paste its prompt into the chat to run it.
- **Knowledge is a snapshot.** Project knowledge is whatever you uploaded; it won't reflect repo edits until you re-upload.

None of these block the work — they're just a bit more manual. For most practitioners and small business owners, the browser simplicity is the better trade.

## Your first five minutes

1. **Create the Project** in claude.ai and name it.
2. **Upload** `CLAUDE.md` plus `smart-bidding.md` and your context file (`lead-gen.md` or `ecomm.md`) — you can add more later.
3. **Paste `CLAUDE.md`** into custom instructions.
4. **Start a chat:** "I run Google Ads for a [lead gen / ecomm] business. Read your knowledge and confirm the five operating principles."
5. **Run a skill:** open [account audit](../skills/account-audit.md), paste its prompt into the chat, and follow along. Paste your client file first if you want account-specific output.

That's a working setup — entirely in the browser.

## Related
[getting-started.md](getting-started.md) · [claude-code-setup.md](claude-code-setup.md) · [obsidian-setup.md](obsidian-setup.md) · [client file template](../obsidian-template/templates/client-file.md) · [CLAUDE.md](../CLAUDE.md)
