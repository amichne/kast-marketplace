---
name: kast-change
description: Use when the user requests a Kotlin or Gradle edit that needs typed mutations, rename safety, diagnostics, validation, or post-change compiler proof through Kast, including the Kotlin or Gradle portion of a mixed corpus. Do not use for read-only questions or purely non-Kotlin work; use Graphify only for a mixed corpus's non-Kotlin portion.
---

# Change Kotlin with Kast

1. Use this workflow only for a requested edit and keep any prerequisite
   inspection inside this workflow. Run `kast --output json` from the target
   directory without `--workspace-root`; reuse its exact `workspaceRoot` as
   `$ROOT` instead of inferring scope from Git. The session hook normally owns
   runtime startup. If it is unavailable, run `kast developer runtime up
   --workspace-root "$ROOT" --backend idea --accept-indexing`. Then run `kast
   --output json status --workspace-root "$ROOT" --backend idea` and require
   `selected.ready` to be `true` before compiler-backed work; `INDEXING` is not
   `READY`.

2. Read scoped `kast agent --help`. Use `kast agent diagnostics` before and
   after a change. Prefer the typed mutation that matches the requested edit:
   `kast agent rename`, `kast agent add-file`, `kast agent add-declaration`,
   `kast agent add-implementation`, `kast agent add-statement`, or
   `kast agent replace-declaration`.

3. Keep mutation plans, changed-file evidence, diagnostics, and validation
   results intact. Exit code 0 is terminal success; report and repair typed
   blockers rather than bypassing Kast or falling back to Graphify for Kotlin
   or Gradle. For a mixed corpus, split the work and keep Graphify limited to
   its non-Kotlin portion.
