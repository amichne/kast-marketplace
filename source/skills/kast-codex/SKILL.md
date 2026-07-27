---
name: kast-codex
description: Use when Kotlin or Gradle work needs compiler-backed discovery, repository questions, native graph queries, mutations, diagnostics, validation, or exact-root readiness through Kast.
---

# Kast for Codex

1. Resolve the canonical Git root, pass it explicitly to `kast context`, and
   gate semantic work on `kast ready --for kotlin`. On macOS use the IDEA
   backend. `INDEXING` means the runtime is reachable, not semantically ready.

2. Read scoped `kast agent --help` before raw Kotlin or Gradle searches. Route
   natural-language identity, path, impact, architecture, and context questions
   to `kast agent repository`. Route persisted native topology to
   `kast agent graph`. Use the focused symbol, relationship, diagnostic, and
   mutation commands for their typed contracts.

3. Preserve Kast's proof-carrying result. Do not guess through `AMBIGUOUS`,
   `EMPTY`, or `QUALIFIED_EMPTY`; use returned canonical keys, continuations,
   coverage, and next requests. Mutations apply and validate synchronously, and
   exit code 0 is terminal success.

Read [lifecycle.md](references/lifecycle.md) only for installation, exact-root
runtime startup, typed readiness blockers, or restart.
