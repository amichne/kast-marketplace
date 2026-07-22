---
name: kast-codex
description: Use when Kotlin or Gradle work needs compiler-backed discovery, mutations, diagnostics, validation, or worktree readiness through Kast.
---

# Kast for Codex

1. Resolve the exact workspace with `kast context --workspace-root <root>` and verify it with `kast ready --workspace-root <root> --for agent`. The step is complete when Kast reports the intended root and a usable backend.

2. Use `kast agent` and scoped `--help` before manual Kotlin or Gradle discovery, reads, relationship searches, or edits. Use `$kast-graphify` for repository graph builds and graph-backed architecture or impact questions. The step is complete when the result comes from the narrowest compiler-backed command that covers the task.

3. Pass the exact workspace root to semantic commands. Mutations plan, apply, and validate diagnostics synchronously; exit code 0 is terminal success. On failure, report only Kast's structured error code, message, and actionable details.

Read [lifecycle.md](references/lifecycle.md) only when installation, worktree initialization, background IntelliJ launch, or runtime restart is required.
