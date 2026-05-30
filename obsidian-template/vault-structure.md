---
title: Vault Structure
version: v0.1
updated: 2026-05-31
status: draft
---

# Vault Structure

The vault is the **private layer** of the Robots & Brains OS. The repo holds universal knowledge; the vault holds everything specific to the practitioner's clients and business. Claude reads from the vault before answering anything account-specific.

## Why Obsidian is the private layer
Obsidian is the recommended home for private context because it fits the privacy model of this system:

- **Local-first** — notes live as plain files on the practitioner's own machine, not on a third-party server.
- **Markdown-based** — the same format as this repo, so Claude reads vault files and repo files the same way.
- **No third-party AI training** — content stays local and is never sent off to train someone else's model. Claude only sees a file when the practitioner's session reads it.
- **Compatible with Claude Code** — because the vault is just a folder of markdown, Claude Code can read it directly when given the path.

The principle: **universal knowledge is public (the repo); client knowledge is private (the vault).**

## Recommended vault structure
```
my-vault/
├── clients/
│   └── {client-name}/
│       ├── client-file.md        # primary context Claude reads first
│       ├── account-context.md    # detailed account / structure notes
│       └── meetings/             # dated meeting notes
├── meetings/                     # cross-client or internal meetings
├── templates/                    # local copies of the repo templates
└── inbox/                        # unsorted notes, to file later
```

What goes where:

- **`clients/{client-name}/`** — one folder per client. Use kebab-case for the folder name (e.g. `acme-roofing`). This is the path Claude looks in for account-specific context.
- **`client-file.md`** — the single most important file: the snapshot Claude reads before every account-specific response. See [[client-file]].
- **`account-context.md`** — deeper detail on account structure, history, and configuration that doesn't fit the snapshot. See [[account-context]].
- **`meetings/`** — dated notes from calls and reviews, per client and/or global. See [[meeting-notes]].
- **`templates/`** — local copies of the templates in `obsidian-template/templates/` so new clients and notes start consistent.
- **`inbox/`** — a holding area for quick notes before they're filed into the right client folder.

## Setting VAULT_PATH in a Claude Code session
Claude needs to know where the vault lives. At the start of a session, tell Claude the absolute path, for example:

> "My vault is at `/Users/me/Documents/my-vault`. Use that as `VAULT_PATH`."

Claude will then read client context from `{VAULT_PATH}/clients/{client-name}/` before responding to account-specific questions. If no path is set, Claude will ask for one before answering anything client-specific. (Optionally, set `VAULT_PATH` as an environment variable so it persists across sessions.)

## Optional Drive sync without breaking privacy
The vault can be synced across machines (Google Drive, iCloud, Dropbox, Obsidian Sync) for backup and continuity. This preserves the privacy model **as long as**:

- The synced folder remains private — not shared with anyone who shouldn't see client data.
- Sync is used only for storage and backup, never to expose the vault to a third-party AI service.
- The repo and the vault stay separate — never sync vault contents into the public repo.

Drive sync moves files between the practitioner's own devices; it does not change who can read them.

## What belongs in the vault vs the repo
| Vault (private, local) | Repo (public, shared) |
|---|---|
| Client names, account IDs | Best practices and principles |
| Budgets, KPIs, performance data | Campaign-type playbooks |
| Meeting notes, stakeholders | Skills and templates |
| Business rules, brand terms | Conventions and setup docs |
| Anything client-identifying | Universal knowledge only |

If a piece of information would identify a client or expose their numbers, it belongs in the vault — never the repo.

## Using the templates
The templates in `obsidian-template/templates/` are starting points. To use them:

1. Copy the template into the vault (into `clients/{client-name}/` or `templates/`).
2. Rename it appropriately (e.g. `client-file.md` inside the client folder).
3. Fill in the placeholder values (`[CLIENT NAME]`, `[MONTHLY BUDGET]`, etc.).
4. Keep it updated — Claude is only as good as the context the file holds.

Available templates: [[client-file]], [[account-context]], [[meeting-notes]].
