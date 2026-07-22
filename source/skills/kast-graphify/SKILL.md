---
name: kast-graphify
description: Graphify Kotlin codebases with Kast's compiler-backed symbol index. Use when building or updating a repository graph, or answering architecture and impact questions from graphify-out.
---

# Kast-backed Graphify

1. If `graphify-out/graph.json` exists and the request is a codebase question, run `graphify query`, `graphify path`, or `graphify explain` before scanning files. The step is complete when the answer is grounded in graph nodes and `source_location` evidence.

2. For a build or update, apply the installed Graphify workflow and require its Kotlin structural extraction to run through `kast agent graphify`. Do not substitute Graphify's generic AST for Kotlin when Kast is ready. The step is complete when Kast writes the Kotlin fragment and Graphify merges it into `graphify-out/graph.json`.

3. Run `graphify diagnose multigraph` after the merge. Treat Kast's structured exit code and Graphify's health result as the terminal outcome.

Read [interop.md](references/interop.md) when installing Graphify or building/updating a graph; a query against an existing graph does not need it.
