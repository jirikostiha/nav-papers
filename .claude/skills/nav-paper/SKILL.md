---
name: nav-paper
description: >-
  Write or edit a "navigation paper" — a short Markdown reference file for a
  software product, tool, library, or technical topic in the nav-papers repo.
  Each paper is a curated list of the most useful links (home page, CLI,
  tutorials, commands, clients, extensions, …) grouped under section headings,
  and lives in a category folder such as cache/, databases/, ide/, network/,
  scm/, pms/, containers/, math/, security/, or dotNet/. Use this whenever the
  user asks to add a new tool/product page, document a technology, drop in
  reference links for a piece of software, or extend an existing .md in this
  repo, even if they don't say "navigation paper". Keeps the house style, the
  markdownlint rules, and the spellcheck wordlist consistent.
---

# Navigation paper

A navigation paper is a tiny, link-first Markdown file that answers "where do I
go to work with this tool?". The value is curation, not prose: a person scanning
the file should reach the home page, the CLI docs, a good tutorial, or the
command reference in one click. Keep papers short — most are under 25 lines.

Before writing, look at two or three existing papers in the same category folder
and match what you see. The patterns below describe the shared house style, but
the neighbours are the source of truth for any category-specific choice.

## Where the file goes

Papers are grouped by category folder at the repo root. Pick the folder that
matches the tool's domain; create a new one only if nothing fits:

`cache/` `databases/` `ide/` `network/` `pms/` (package managers) `scm/`
`containers/` `cloud/` `cicd/` `math/` `graphics/` `sound/` `security/`
`game engines/` `economy/` `legal/` `project management/` `dotNet/`

- **Filename = the product's real name, with its real casing and spacing**, plus
  `.md`. Spaces are fine: `Visual Studio Code.md`, `Redis.md`, `Github-actions.md`.
- Deeply-related items nest one more level: `security/passw managers/KeePass.md`,
  `dotNet/C#/threading.md`, `economy/markets/brokers/cTrader.md`.

## Anatomy of a paper

Build the file top-down, including only the parts you have real links for. Do
not invent links or pad with empty sections you can't fill (an empty section
heading left as a placeholder for later is fine and common, but don't add one
just to look complete).

```markdown
# Product Name

Optional one- to three-line description, usually the product's own tagline.

[home](https://example.com)  
CLI yes

## Tutorials

Source: [Tutorial title](https://example.com/tutorial)  

## Commands

Source: [Command reference](https://example.com/commands)  
```

### 1. Title

`# Product Name` — the H1 is the product's proper name, matching the filename.

### 2. Description (optional)

One to three plain sentences right under the title, taken from the product's own
description or a neutral summary. Skip it for tools whose name says everything
(many IDE and package-manager papers have none).

### 3. The home / CLI line

This block is the heart of the paper. Match the neighbours' exact form:

- `[home](https://…)` for the main site. Some papers use `[documentation](…)`
  or `[home](…)` — follow the folder.
- CLI availability on its own line: `CLI yes` when the tool has a CLI, or a
  linked form `[CLI](https://…/cli)` when there's a specific CLI docs page.
- Optional extra top links seen in the repo: `[wikipedia](…)`,
  `[documentation](…)`.

### 4. Sections

Use `##` headings to group links. Which sections exist depends on the tool —
pick the ones that fit and name them like the existing papers do:

- General tools: `Tutorials`, `Commands`
- Databases: `Connection strings`, `DB Viewers`, `Adapters`, `Query Builders`
- Caches / servers: `Commands`, `Clients`
- IDEs: `Extensions` (a `-` bullet list of extension names), `Tutorials`, `Commands`
- APIs / networking: often just the home/CLI block
- Under `Tutorials`, put screencasts in a `### Video` subsection.

## Link formatting (the details that keep lint happy)

- **Every link line ends with two trailing spaces.** This is the Markdown hard
  line break the repo relies on so consecutive links render on their own lines.
  It's the single most common thing to get wrong — check it on every line.
- Two link shapes are both in use; prefer the one the folder uses:
  - Bare: `[Redis Tutorial](https://…)`
  - Attributed with the source before it: `Tutorials Point: [Redis Tutorial](https://…)`
    or `Youtube: [Redis Crash Course](https://…)` — good when the source (MSDN,
    Atlassian, a YouTube channel) helps the reader judge the link.
- Prefer official docs and well-known sources. One or two great links beat ten
  mediocre ones.

## markdownlint rules (CI enforces these)

CI runs markdownlint with `.github/markdownlint.yml`. Stay inside it:

- **Line length ≤ 160** characters (headings and code blocks included). Long
  URLs are fine; long prose lines are not — break sentences.
- **Inline HTML:** only `<div>` and `<font>` are allowed. Don't reach for other
  raw HTML.
- Otherwise default markdownlint rules apply: one H1, ATX `#` headings, blank
  line around headings and lists, no trailing spaces *except* the intentional
  two-space line breaks above (markdownlint's MD009 default permits exactly two).

## Spellcheck wordlist

`.github/wordlist.txt` is the allow-list for the docs spellchecker. When a paper
introduces a proper noun or technical term not already there — a product name, a
vendor, an acronym — add it to `.github/wordlist.txt` so CI stays green. Scan the
file first; many common terms are already listed. Keep it one term per line,
in the file's existing loose grouping.

## Commit style

Per `AGENTS.md`: write a specific, imperative commit message describing the real
change — e.g. `add Redis navigation paper` or
`add Mermaid to diagrams section in toolstack`. Never use generic merge-style
messages like `merge` or `Merge branch …`.

## Worked example

Adding Grafana to a new `observability/` folder (or `network/` if you'd rather
not create one):

```markdown
# Grafana

Open source analytics and interactive visualization web application.

[home](https://grafana.com)  
[documentation](https://grafana.com/docs)  
CLI yes

## Tutorials

Grafana: [Get started](https://grafana.com/tutorials)  
Youtube: [Grafana Crash Course](https://www.youtube.com/watch?v=example)  

## Plugins

Grafana: [Plugin catalog](https://grafana.com/grafana/plugins)  
```

Then add `Grafana` to `.github/wordlist.txt` if the spellchecker doesn't already
know it, and commit with `add Grafana navigation paper`.

## Note on toolstack.md

The root `toolstack.md` is a different, aggregate format — a single big file of
emoji-headed sections with `* [**Name**](url) – description **Pricing**` bullets.
It is not a per-product navigation paper. Only touch it when the user
specifically asks about the tool stack list, and match its own bullet style
there rather than the paper style above.
