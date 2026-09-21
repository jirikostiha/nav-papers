# Agent Instructions

## Commit messages

- Write commit messages based on the actual change you made.
- Do **not** use generic merge-style messages
  (for example: `merge`, `merge branch`, `Merge pull request ...`).
- Use clear, specific, imperative wording.
- Example: `add Mermaid to diagrams section in toolstack`.

## Navigation Paper Guidelines

When creating or revising a navigation paper:

- **CLI line**:
  - If official documentation/web link exists: `[CLI](<url>)`
  - If it is a standalone command-line tool or no dedicated page exists: `CLI yes`
  - If an unofficial CLI exists: `[CLI](<url>) (unofficial)`
  - If the product has no CLI: omit.
- **MCP line**:
  - If official MCP server link exists: `[MCP](<url>)`
  - If built-in MCP server exists without standalone page: `MCP yes`
  - If an unofficial MCP server exists: `[MCP](<url>) (unofficial)`
  - If multiple alternatives exist: list each on a separate line (with two trailing spaces).
  - If no MCP server exists: omit.
- **Line breaks**: End every link line in the header block with two trailing spaces.
- **Formatting**: Adhere to markdownlint (lines ≤ 160 characters, single H1 heading).
