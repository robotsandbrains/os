---
title: Token Counter
version: v0.1
updated: 2026-06-02
status: draft
---

# Token Counter

> A reference guide, not a skill. How to measure the true token cost of a document — and prove to yourself why converting to markdown first is worth it. The companion to [[markitdown]].

## Why measure tokens

[[markitdown]] makes the case that converting documents to markdown keeps the context window efficient. This guide lets you *prove the number* for any document you actually use.

The key insight: **file size and token cost are not the same thing.** A document's byte size tells you how big the file is on disk. Its token cost tells you how much of Claude's context window it consumes — and for PDFs, the two diverge sharply.

When you hand Claude a real PDF (uploaded as a document, not pasted as text), it does two things:

1. **Extracts the text** — counted as text tokens.
2. **Renders every page as an image** — counted as image tokens, roughly *(width × height) / 750* per page, often **1,500–3,000+ tokens per page** on top of the text.

That per-page image cost is invisible in the byte size and absent entirely from the markdown version. It is the real reason converting first matters, and it is why the token saving is often *larger* than the file-size saving would suggest.

(If you only ever copy-paste the *text* out of a PDF, there is no image cost — then the difference versus markdown is just the formatting cruft, which is much smaller. The big win is specifically when a PDF would otherwise be uploaded whole.)

## How it works

Anthropic's **token-counting endpoint** (`count_tokens`) returns the exact `input_tokens` Claude would see for any content — including the per-page image tokens a PDF carries. It is **free**: it does not consume tokens or cost anything. That makes it the accurate way to compare a PDF against its markdown conversion.

## Setup

```
pip install anthropic
```

You need an Anthropic API key. Set it as an environment variable so it never appears in a command or a file:

```
export ANTHROPIC_API_KEY=sk-ant-...
```

Treat the key like a password. Do not paste it into a shared session, commit it, or store it in the vault.

## The script

Save this as `token_compare.py`:

```python
#!/usr/bin/env python3
"""Compare Claude token cost: a PDF (as uploaded) vs its markdown conversion."""
import base64
import os
import sys

import anthropic

MODEL = "claude-opus-4-8"


def count_pdf(client, path):
    data = base64.standard_b64encode(open(path, "rb").read()).decode()
    r = client.messages.count_tokens(
        model=MODEL,
        messages=[{
            "role": "user",
            "content": [{
                "type": "document",
                "source": {"type": "base64", "media_type": "application/pdf", "data": data},
            }],
        }],
    )
    return r.input_tokens


def count_text(client, path):
    text = open(path, encoding="utf-8").read()
    r = client.messages.count_tokens(
        model=MODEL,
        messages=[{"role": "user", "content": [{"type": "text", "text": text}]}],
    )
    return r.input_tokens


def main():
    pdf_path, md_path = sys.argv[1], sys.argv[2]
    client = anthropic.Anthropic()  # reads ANTHROPIC_API_KEY from env

    pdf_tokens = count_pdf(client, pdf_path)
    md_tokens = count_text(client, md_path)
    pdf_bytes = os.path.getsize(pdf_path)
    md_bytes = os.path.getsize(md_path)

    print(f"{'':22}{'bytes':>12}{'tokens':>12}")
    print(f"{os.path.basename(pdf_path):22}{pdf_bytes:>12,}{pdf_tokens:>12,}")
    print(f"{os.path.basename(md_path):22}{md_bytes:>12,}{md_tokens:>12,}")
    print("-" * 46)
    print(f"{'byte reduction':22}{pdf_bytes / md_bytes:>11.1f}x")
    print(f"{'token reduction':22}{pdf_tokens / md_tokens:>11.1f}x")
    print(f"{'tokens saved':22}{pdf_tokens - md_tokens:>12,}")


if __name__ == "__main__":
    if not os.environ.get("ANTHROPIC_API_KEY"):
        sys.exit("ANTHROPIC_API_KEY not set")
    main()
```

## Usage

Convert the PDF to markdown first (see [[markitdown]]), then compare the two:

```
markitdown guide.pdf > guide.md
python3 token_compare.py guide.pdf guide.md
```

## Worked example

A real comparison, run on Google's Demand Gen implementation guide — a screenshot-heavy PDF:

| File | Bytes | Tokens |
|------|-------|--------|
| Demand Gen guide (PDF) | 3,217,574 (3.1 MB) | 31,278 |
| Same guide, as markdown | 7,210 (7 KB) | 2,718 |
| **Reduction** | **446×** | **11.5×** |

Feeding the raw PDF costs **31,278 tokens**; the markdown costs **2,718** — a saving of **28,560 tokens** on a single document, every time you use it. The 11.5× token reduction sits right inside the typical 10–20× range.

## A quick offline estimate

No API key handy? For a rough *text-only* estimate, characters ÷ 4 is a reasonable approximation for English:

```
echo "tokens ~= $(( $(wc -m < file.md) / 4 ))"
```

This is fine for sizing a markdown file, but it **understates a PDF** because it cannot see the per-page image tokens. Use the script above when the number matters.

## Limitations

- **Estimates are not billing.** `count_tokens` is exact for input; the offline character estimate is a rough proxy only.
- **Markdown can lose visual content.** A high byte-reduction ratio often means the source was image-heavy and the conversion dropped diagrams or screenshots (as in the worked example above). For text-heavy documents — briefs, policies, reports — nothing of value is lost. For visual guides, you are trading some fidelity for the token saving; decide per document.
- **Model matters.** Image-token maths and tokenisation can vary by model. The script pins one model so comparisons are consistent.

## Related
[[markitdown]] · [skills/overview.md](../skills/overview.md) · [CLAUDE.md](../CLAUDE.md)
