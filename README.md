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
- **Draft:** core Google Ads knowledge, contexts, and the first three skills.
- **Coming:** more skills, audit frameworks, and Meta Ads in v2.

## Licence

MIT. Use it, fork it, build on it.
