# Robots & Brains OS

An open-source AI operating system for paid media practitioners — best practices, runnable workflows, and a private context layer that gives Claude persistent memory of your accounts.

## What this is

Most AI tools forget everything the moment you close the tab. You re-explain the client, the account, the rules, the history — every single time. That's not an assistant, that's a goldfish.

This fixes it with three layers working together. **Claude is the brain** — the reasoning engine. **This repo is the shared knowledge layer** — durable best practices for running paid media well. **Your local Obsidian vault is the private context layer** — your clients, budgets, and business rules. Together they give Claude persistent knowledge of both the craft and your business.

It's free, open source, and maintained by practitioners for practitioners. Your client data never leaves your machine — it lives in your vault, not in this repo and not in anyone's training set.

## What's inside

- **Platform knowledge** — best practices and campaign-type playbooks for Google Ads, including [smart bidding](google-ads/best-practices/smart-bidding.md), [campaign structure](google-ads/best-practices/campaign-structure.md), and [Performance Max](google-ads/campaign-types/pmax.md).
- **Business contexts** — how strategy shifts for [lead gen](google-ads/contexts/lead-gen.md) vs [ecommerce](google-ads/contexts/ecomm.md).
- **Skills** — runnable workflows like [account audit](skills/account-audit.md), [campaign review](skills/campaign-review.md), and [monthly report brief](skills/monthly-report-brief.md).
- **Obsidian templates** — a [vault structure](obsidian-template/vault-structure.md) and a [client file template](obsidian-template/templates/client-file.md) for your private layer.

## Your privacy, your choice

The private layer is flexible — you choose how much privacy you need:

- **100% local** — if you work from one machine, your vault stays entirely on your device. Nothing leaves your computer. No sync, no cloud, complete privacy. Recommended for small business owners who want the simplest, most private setup.
- **Drive-synced** — if you work across multiple devices, sync your vault via Google Drive, iCloud, or Obsidian Sync. Your data stays in your own storage — it is never fed into an AI training pipeline or shared with any third party. Recommended for practitioners who need access across machines.
- **Repo only** — if you are not ready to set up a vault yet, the repo works without one. Claude has access to the knowledge layer and skills but not your private context. You get less personalised output but zero setup friction.

Your client data is never in this repo. The repo contains only universal knowledge — best practices, skills, and templates. Everything specific to your business stays local.

## How to get started

1. **Clone the repo** — `git clone https://github.com/robotsandbrains/os.git`
2. **Set up your vault** — build an Obsidian vault using [the structure guide](obsidian-template/vault-structure.md) and fill in a client file.
3. **Open in Claude Code** — point Claude Code at the repo and tell it your `VAULT_PATH`.
4. **Run your first skill** — try [account audit](skills/account-audit.md). Claude reads the skill, asks for inputs, and executes.

## The philosophy

This repo is the open-source foundation that powers Robots & Brains, a paid media agency. We use it every day on real client accounts. We're sharing the foundation because the industry moves faster when knowledge is open. The private layer — your clients, your SOPs, your edge — stays yours.

## Contributing

PRs welcome. We work outline-first: propose the structure of a file before writing the full content, so the shape gets agreed before the words. See [CLAUDE.md](CLAUDE.md) for conventions.

## Roadmap

- **Stable:** nothing yet — this is v0.1.
- **Draft:** core Google Ads knowledge, contexts, audit frameworks, and the first three skills.
- **Coming in v2:** Meta Ads, more skills, shopping and display campaign types, agent layer with scheduled triggers and CoWork integration.

## For small business owners

This repo is not just for paid media professionals. If you are a small business owner running your own Google Ads, there is a section built for you at [`small-business/`](small-business/). It covers setting up your first campaign, reading your results, and knowing when you need professional help.

## Licence

MIT. Use it, fork it, build on it.
