# Kast marketplace

Install the Kast plugin directly with the Codex CLI:

```sh
codex plugin marketplace add amichne/kast-marketplace --ref main --json
codex plugin add kast@kast --json
```

Start a new Codex thread after installation so the rewritten skills and hooks
are loaded.

Version `0.3.0-beta.1` requires a compatible Kast beta whose `kast agent --help`
includes both `repository` and `graph`.

The plugin contains:

- `kast-codex` for compiler-backed Kotlin and Gradle repository work.

The compatible Kast installer also performs these two plugin commands when
Codex is available.
