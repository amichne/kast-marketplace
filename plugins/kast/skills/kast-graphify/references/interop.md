# Graphify interoperability

## Install

If Graphify is unavailable, install its CLI and Codex skill, then start a new Codex session so the skill is discovered:

```sh
uv tool install --upgrade graphifyy
graphify install --platform codex
```

## Ownership

Graphify owns corpus detection, non-Kotlin extraction, semantic content extraction, merge, clustering, health checks, reports, and visualization. Kast owns Kotlin and Kotlin-script structural extraction from the compiler-built symbol index.

For a full build, the Graphify workflow calls:

```sh
kast agent graphify \
  --workspace-root "$GRAPHIFY_ROOT" \
  --manifest graphify-out/.graphify_detect.json \
  --output-file graphify-out/.graphify_ast_kotlin.json
```

For an incremental build, it must preserve Kast identities by adding:

```sh
--manifest graphify-out/.graphify_incremental.json \
--base-graph graphify-out/graph.json
```

Pass the exact root and let Kast own batching, boundary symbols, identity schema, coverage, and atomic output. `FULL_REBUILD_REQUIRED` means rerun the full Graphify build; do not synthesize or normalize Kast node IDs manually.
