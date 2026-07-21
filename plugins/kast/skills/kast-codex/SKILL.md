---
name: kast-codex
description: Use when Kotlin or Gradle work needs compiler-backed discovery, mutations, diagnostics, or validation through Kast.
---

# Kast for Codex

Use `kast agent` and scoped `--help` for compiler-backed Kotlin and Gradle work.

Pass the exact workspace root to semantic commands. Mutations plan, apply, and validate diagnostics synchronously; treat exit code 0 as terminal success. On failure, report only Kast's structured error code, message, and actionable details.

The plugin hooks ask the effective `kast` CLI to open the workspace runtime at session start and diagnose changed Kotlin files after writes. The CLI owns daemon, compatibility, and execution decisions.
