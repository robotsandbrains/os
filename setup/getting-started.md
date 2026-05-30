---
title: Getting Started
version: v0.1
updated: 2026-05-31
status: draft
---

# Getting Started

Welcome. This is the first file to read. It gets you from "I just found this repo" to "Claude is working on my account" in a few minutes — whichever interface and privacy level you choose.

## What you need before you start

Three things:

1. **A Claude subscription** — you'll use either Claude Code or Claude Projects (both covered below). See [claude.ai](https://claude.ai) for plans, and [Claude Code](https://docs.claude.com/en/docs/claude-code) if you want the CLI.
2. **Git** — to clone this repo (and, for Claude Code, to keep it updated). Install from [git-scm.com](https://git-scm.com/downloads). *(Claude Projects users who don't want to use Git can download the repo as a ZIP from GitHub instead.)*
3. **Obsidian** *(optional but recommended)* — the free, local, markdown app that holds your private client context. Download from [obsidian.md](https://obsidian.md). You can skip this if you choose the "repo only" path below.

## Choose your path

There are two ways to use the OS — pick the one that fits you:

- **Claude Code (practitioners)** — the command-line interface. Reads the repo *and* your vault directly, runs skills in place, integrates with Git. The most powerful setup. → [claude-code-setup.md](claude-code-setup.md)
- **Claude Projects (everyone)** — the browser interface at claude.ai. No install, no command line. You upload the knowledge files once and work in a chat window. Ideal if you prefer the browser, or you're a small business owner. → [claude-projects-setup.md](claude-projects-setup.md)

Not sure? If you're comfortable in a terminal, use Claude Code. If you'd rather just open a browser tab, use Claude Projects.

## Choose your privacy level

Your private context (clients, budgets, rules) lives in *your* vault, never in this repo. Decide how much privacy you need (full detail in the [README](../README.md#your-privacy-your-choice)):

- **100% local** — vault stays on one machine, nothing syncs anywhere. Simplest and most private.
- **Drive-synced** — vault syncs across your devices via Google Drive, iCloud, or Obsidian Sync. Stays in your own storage; never enters an AI training pipeline.
- **Repo only** — no vault yet. Claude uses the knowledge layer and skills but not your private context. Less personalised, zero setup.

You can start "repo only" and add a vault later — nothing is locked in.

## The three steps (same for both paths)

Regardless of interface, the shape is the same:

1. **Clone the repo** — get the knowledge layer and skills onto your machine (or download the ZIP).
2. **Set up your vault** — create your private context using the [vault structure guide](../obsidian-template/vault-structure.md) and fill in a [client file](../obsidian-template/templates/client-file.md). *(Skip if "repo only".)*
3. **Start working** — point Claude at the repo (and vault), then run a skill like [account audit](../skills/account-audit.md).

The *how* of each step differs slightly by interface — that's what the setup files cover.

## What to do first

Go to the setup file for your chosen interface and follow it end to end:

- **Claude Code →** [claude-code-setup.md](claude-code-setup.md)
- **Claude Projects →** [claude-projects-setup.md](claude-projects-setup.md)

## Your first five minutes

For the impatient — the shortest path to seeing it work:

1. **Clone it:** `git clone github-robotsandbrains:robotsandbrains/os.git` (or download the ZIP).
2. **Open it:** point Claude Code at the folder, *or* create a Claude Project and upload `CLAUDE.md`.
3. **Tell Claude what you do:** "I run Google Ads for a [lead gen / ecomm] business."
4. **Ask it something real:** "Read [[smart-bidding]] and tell me whether tCPA or tROAS fits my account."
5. **Run a skill:** open [account audit](../skills/account-audit.md), paste the prompt, and follow along.

That's it — you're working. Add a vault when you want personalised, account-specific output.

## Related
[claude-code-setup.md](claude-code-setup.md) · [claude-projects-setup.md](claude-projects-setup.md) · [obsidian-setup.md](obsidian-setup.md) · [vault structure](../obsidian-template/vault-structure.md) · [CLAUDE.md](../CLAUDE.md)
