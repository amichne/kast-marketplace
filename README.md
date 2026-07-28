# Kast marketplace

Install the Kast plugin directly with the Codex CLI:

```sh
codex plugin marketplace add amichne/kast-marketplace --ref main --json
codex plugin add kast@kast --json
```

Start a new Codex thread after installation so the rewritten skills and hooks
are loaded.

Version `0.3.0-beta.3` requires Kast `0.17.8` or newer. The launcher fails
closed on older or unparseable versions rather than invoking an incompatible
hook.

On a fresh install, run `/hooks` in Codex CLI, inspect the `kast-codex` hook
definitions, and trust the exact current definitions. Codex skips plugin hooks
until they are reviewed and trusted, and asks for review again when they change.

The plugin contains:

- `kast-query` for read-only Kotlin and Gradle discovery.
- `kast-change` for requested Kotlin mutations and post-change validation.

The two skills own Kotlin and Gradle semantics. Graphify is not a fallback for
blocked, incomplete, or empty Kast evidence.

The compatible Kast installer also performs these two plugin commands when
Codex is available.
