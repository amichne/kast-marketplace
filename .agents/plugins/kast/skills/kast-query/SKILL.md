---
name: kast-query
description: Use for read-only Kotlin or Gradle discovery, repository questions, native graph queries, symbol relationships, impact analysis, diagnostics inspection, or exact-root readiness through Kast, including the Kotlin or Gradle portion of a mixed corpus. Do not use for edits or purely non-Kotlin work; use Graphify only for a mixed corpus's non-Kotlin portion.
---

# Query Kotlin with Kast

1. Keep this workflow read-only. Run `kast --output json` from the target
   directory without `--workspace-root`; reuse its exact `workspaceRoot` as
   `$ROOT` instead of inferring scope from Git. The session hook normally owns
   runtime startup. If it is unavailable, run `kast developer runtime up
   --workspace-root "$ROOT" --backend idea --accept-indexing`. Then gate
   compiler-backed work on
   `kast ready --workspace-root "$ROOT" --backend idea --for kotlin` on macOS;
   `INDEXING` is not `READY`.

2. Read scoped `kast agent --help`, then choose the narrowest read command:
   `repository` for intent-driven questions, `graph` for persisted topology,
   or `workspace-files`, `symbol`, `references`, `callers`, `callees`,
   `implementations`, `hierarchy`, `impact`, and `diagnostics` for their typed
   contracts.

3. Preserve canonical keys, continuations, coverage, and next requests. Report
   typed blockers or incomplete evidence without mutation; never route Kotlin
   or Gradle semantics through Graphify as a fallback. For a mixed corpus,
   split the work and keep Graphify limited to its non-Kotlin portion.
