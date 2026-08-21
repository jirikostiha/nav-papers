---
name: nav-paper
description: >-
  Write or edit a "navigation paper" — a short Markdown reference file for a
  software product, tool, library, or technical topic in the nav-papers repo.
  Each paper is a curated list of the most useful links (home, CLI, tutorials,
  commands, clients, extensions, …) under section headings, in a category folder
  such as cache/, databases/, ide/, network/, scm/, pms/, containers/, math/,
  security/, or dotNet/. Use whenever the user asks to add a tool/product page,
  document a technology, or extend an existing .md here, even if they don't say
  "navigation paper".
---

# Navigation paper

A tiny, link-first file answering "where do I go to work with this tool?".
Value is curation, not prose — most papers are under 25 lines. Before writing,
skim two or three existing papers in the same category folder and match them;
they are the source of truth for any category-specific choice.

## File placement

- Group by category folder at the repo root (`cache/`, `databases/`, `ide/`,
  `network/`, `pms/`, `scm/`, `containers/`, `cloud/`, `cicd/`, `math/`,
  `security/`, `dotNet/`, …); create a new one only if nothing fits.
- Filename = the product's real name with real casing/spacing, e.g.
  `Redis.md`, `Visual Studio Code.md`. Nest closely-related items one level
  deeper (`security/passw managers/KeePass.md`, `dotNet/C#/threading.md`).

## Structure

```markdown
# Product Name

Optional 1–3 line description (usually the product's own tagline).

[home](https://example.com)  
CLI yes

## Tutorials

Source: [Tutorial title](https://example.com/tutorial)  
```

- `# Title` = the product's proper name (matches filename).
- Home/CLI block: `[home](…)` (or `[documentation](…)`), plus `CLI yes` or
  `[CLI](…/cli)`. Optional `[wikipedia](…)`.
- `##` sections group links, chosen to fit the tool: `Tutorials`, `Commands`,
  `Clients`, `Extensions` (bullet list), databases use `Connection strings` /
  `DB Viewers` / `Adapters` / `Query Builders`, screencasts go under a
  `### Video` subsection. Include only sections you have real links for; don't
  invent links.

## Formatting & CI rules

- **End every link line with two trailing spaces** — the hard line break the
  repo relies on. Easiest thing to get wrong; check each line.
- Link shape: bare `[Title](url)` or attributed `Source: [Title](url)` — prefer
  what the folder uses. Favor official docs over quantity.
- markdownlint (`.github/markdownlint.yml`) runs in CI: lines ≤ 160 chars; only
  `<div>` and `<font>` raw HTML; one H1; blank lines around headings/lists.
- Add new proper nouns/acronyms to `.github/wordlist.txt` so the spellchecker
  passes.
- Commit with a specific, imperative message (`add Redis navigation paper`).
