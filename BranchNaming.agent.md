---
name: "BranchNaming"
description: "Branch naming rules derived from Conventional Commit types."
kind: "rule"
applies: "when creating any git branch"
version: 2026-07-16
---

# Branch Naming Rules

Branches **MUST** start with a canonical commit type:

```text
<type>/<kebab-case-description>
<type>/<scope>/<kebab-case-description>
```

## Rules

- **Types:** `feat` · `fix` · `docs` · `style` · `refactor` · `perf` · `test` · `build` · `ci` · `chore` · `revert`
- **Forbidden:** `feature`, `bugfix`, `hotfix`, or any non-canonical type
- All lowercase, kebab-case only
- No spaces, underscores, or commit syntax characters

## Example

| Commit                           | Branch                         |
| -------------------------------- | ------------------------------ |
| `feat(parser): add atin support` | `feat/parser/add-atin-support` |

## Defaults

- When uncertain: use `feat`
- Omit scope rather than guessing

## Validation Regex

```text
^(feat|fix|docs|style|refactor|perf|test|build|ci|chore|revert)/([a-z0-9-]+/)?[a-z0-9-]+$
```
