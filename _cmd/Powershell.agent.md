---
name: "Powershell"
description: "Skill for designing, writing, and reviewing PowerShell scripts."
kind: "skill"
trigger: "writing or modifying PowerShell scripts"
version: 2026-07-16
---

# PowerShell Skill

## 1. Language and compatibility

- Prefer PowerShell 7+ (`pwsh`) by default.
- If legacy compatibility is required, explicitly document limitations for Windows PowerShell 5.X.
- Use UTF-8 encoding and explicitly set `-Encoding utf8` where relevant.

## 2. Script style and structure

- Every non-trivial script must define a typed `param(...)` block.
- Prefer advanced functions (`[CmdletBinding()]`) over loose script blocks.
- Use approved verbs (`Get-Verb`) and consistent PascalCase function names.
- Prefer pipeline-friendly design (`ValueFromPipeline`, `ValueFromPipelineByPropertyName`) when appropriate.
- Do not use `Write-Host` for operational logic; prefer `Write-Verbose`, `Write-Information`, `Write-Warning`, `Write-Error`.

## 3. Errors and robustness

- For critical operations, use `-ErrorAction Stop` and handle failures with `try/finally` or focused `try/catch`.
- In `catch` blocks, log failure context (for example input parameters, target resource, and original exception).
- Do not suppress errors without reason (`SilentlyContinue` only with a documented justification).

## 4. Security

- Never hardcode secrets (passwords, tokens, connection strings).
- Use SecretManagement, environment variables, or secure input paths for sensitive data.
- Validate inputs with attributes like `[ValidateNotNullOrEmpty()]`, `[ValidateSet()]`, and `[ValidatePattern()]`.
- For destructive actions, implement `SupportsShouldProcess` and honor `-WhatIf` / `-Confirm`.

## 5. Performance and reliability

- Prefer pipeline streaming over unnecessary intermediate collections.
- Minimize external process calls; prefer native cmdlets.
- For long-running tasks, provide progress and actionable operational logging.

## 6. Testing and quality

- For shared functions, add Pester tests (Arrange/Act/Assert) for core and edge-case behavior.
- Before submitting changes, run at minimum:
    - `Invoke-ScriptAnalyzer`
    - relevant Pester tests
- Do not silence analyzer findings without a clear, code-level justification.

## 7. Documentation

- Document public functions with comment-based help (`.SYNOPSIS`, `.DESCRIPTION`, `.PARAMETER`, `.EXAMPLE`).
- Provide at least one realistic usage example for every public function.
- If a script changes system state, briefly document impact and rollback options.
