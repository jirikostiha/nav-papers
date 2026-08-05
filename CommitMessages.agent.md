---
name: "CommitMessages"
description: "Commit message rules (Conventional Commits)."
kind: "rule"
applies: "when creating any commit message"
version: 2026-07-16
---

# Commit Message Rules

All commits **MUST** follow Conventional Commits format:

```text
<type>[optional scope][optional !]: <description>
```

## Types (canonical, exhaustive)

`feat` · `fix` · `docs` · `style` · `refactor` · `perf` · `test` · `build` · `ci` · `chore` · `revert`

**Forbidden:** `feature`, `bugfix`, `hotfix`, `maintenance`, or any synonym.
Non-canonical types **MUST** be normalized (e.g. `feature` → `feat`).

**Testing Code Mapping:** If a commit contains changes **only** in tests, testing projects, and/or test-automation tooling (and no other source code), the commit type **MUST** be `test`.

## Scope

- Optional, lowercase, concise subsystem name
- MUST NOT repeat the type
- **Common Scopes & Mappings:**
  - `agent`: used for modifying agent instruction files (`*.agent.md`, `AGENTS.md`). **MUST** be used with the `chore` type (e.g., `chore(agent): ...`).
  - `script`: used for modifying scripts (e.g., in the `cmd/` folder)
  - `props`: used for MSBuild property files (`.props`)
  - `testing`: used for tests and testing utilities
  - `apps`: used for standalone or console applications
  - `ui`: used for user interface components and chart visuals
  - `api`: used for public API surface changes
  - `cli`: used for command-line interface entry points
  - `config`: used for app config changes
  - `tool`: used for created helper apps/tools/utilities
  - `vs`: used for Visual Studio / IDE workspace files
  - `git`: used for git configuration (`.gitignore`, `.gitattributes`)
  - `prompt`: used for changes to prompt definitions in the `prompt/` directory. **MUST** be used with the `chore` type (e.g., `chore(prompt): ...`).
- No scope means core/main code logic

## Description

- Imperative mood, lowercase start, no trailing period. Do NOT use the word `add` as the first word (as it is implied by default).
- **Component Prefixing:** When a commit affects a specific component, class, or method, you may prefix the description with the EXACT name of that entity (preserving its original capitalization).
- **Separator:** If using a component prefix, separate it from the rest of the description with a hyphen surrounded by spaces (`-`).
- Example: `fix: Parser - correct token handling`
- Example: `refactor(ui): Button - remove legacy variant`

## Breaking Changes

- Mark with `!` after scope and/or `BREAKING CHANGE:` footer

## Defaults

- When uncertain: use `feat`
- Omit scope rather than guessing

## Validation Regex

```text
^(feat|fix|docs|style|refactor|perf|test|build|ci|chore|revert)(\([a-z0-9-]+\))?(!)?: .+$
```
