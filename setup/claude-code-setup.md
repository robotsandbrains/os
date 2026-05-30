---
title: Claude Code Setup
version: v0.1
updated: 2026-05-31
status: draft
---

# Claude Code Setup

Claude Code is the most powerful way to run the Robots & Brains OS: it reads the repo *and* your vault directly, runs skills in place, and integrates with Git. This guide takes you from zero to a verified working setup. New here? Start with [getting-started.md](getting-started.md) first.

## 1. Install Claude Code

If you don't already have it, install Claude Code by following the official docs: **[docs.claude.com/en/docs/claude-code](https://docs.claude.com/en/docs/claude-code)**. Confirm it's installed:

```
claude --version
```

You'll also need Git ([git-scm.com](https://git-scm.com/downloads)) and, recommended, Obsidian for your vault ([obsidian.md](https://obsidian.md); see [obsidian-setup.md](obsidian-setup.md)).

## 2. Clone the repo

Clone using the SSH alias format:

```
git clone github-robotsandbrains:robotsandbrains/os.git
```

> This uses an SSH host alias (`github-robotsandbrains`) defined in your `~/.ssh/config`. If you haven't set one up, use the standard SSH remote `git@github.com:robotsandbrains/os.git`, or HTTPS `https://github.com/robotsandbrains/os.git`. The alias format keeps multiple GitHub identities tidy on one machine.

This creates an `os/` folder containing the knowledge layer and skills.

## 3. Open the repo in Claude Code

Start Claude Code from inside the repo folder:

```
cd os
claude
```

Claude Code reads [`CLAUDE.md`](../CLAUDE.md) at the repo root first — that's the system map that orients it to the OS, its principles, and how to run skills. You don't need to do anything to trigger this; it happens on launch.

## 4. Set VAULT_PATH

Tell Claude where your private vault lives so it can load client context. The simplest way is to say it at the start of a session:

```
My vault is at /Users/me/Documents/my-vault. Use that as VAULT_PATH.
```

Claude will then read client context from `{VAULT_PATH}/clients/{client-name}/` before answering anything account-specific (see [vault structure](../obsidian-template/vault-structure.md)). To make it persist across sessions, export it as an environment variable in your shell profile:

```
export VAULT_PATH="/Users/me/Documents/my-vault"
```

*(Skip this step entirely if you're running "repo only" without a vault — Claude will simply use the knowledge layer.)*

## 5. Verify it's working

Run a quick test to confirm Claude is reading both the repo and the vault:

```
Confirm your setup: (1) summarise what the Robots & Brains OS is in one sentence
from CLAUDE.md, (2) list the five operating principles, and (3) if I have a vault
configured, tell me which clients you can see in {VAULT_PATH}/clients/.
```

A correct response means: it paraphrases CLAUDE.md (repo is loaded), lists the five principles (it's actually reading the file, not guessing), and either names your client folders (vault is loaded) or tells you no vault is configured. If all three land, you're set — try a real skill next, e.g. [account audit](../skills/account-audit.md).

## Troubleshooting

The three most common setup issues:

1. **Claude doesn't seem to know about the OS / CLAUDE.md.**
   You're almost certainly running Claude Code from the wrong directory. Make sure you `cd` into the cloned `os/` folder *before* running `claude`, and confirm `CLAUDE.md` is present (`ls CLAUDE.md`). Claude reads the repo from its working directory.

2. **Claude can't find the vault or its client files.**
   Check the path is **absolute** (starts with `/`, not `~` or a relative path), that it points at the vault *root* (the folder containing `clients/`), and that your client folders use kebab-case (`clients/acme-roofing/`, not `clients/Acme Roofing/`). Re-state the `VAULT_PATH` clearly if you only set it verbally.

3. **`git clone` fails with a permissions or host error.**
   The SSH alias `github-robotsandbrains` isn't configured on your machine. Either add it to `~/.ssh/config`, or just clone with the standard remote instead: `git clone git@github.com:robotsandbrains/os.git` (SSH) or `git clone https://github.com/robotsandbrains/os.git` (HTTPS). For SSH, make sure your key is added to your GitHub account.

## Related
[getting-started.md](getting-started.md) · [claude-projects-setup.md](claude-projects-setup.md) · [obsidian-setup.md](obsidian-setup.md) · [vault structure](../obsidian-template/vault-structure.md) · [CLAUDE.md](../CLAUDE.md)
