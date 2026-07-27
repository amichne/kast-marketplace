# Kast lifecycle

## Install or update

Use the installer published with a compatible Kast release. Version
`0.3.0-beta.1` of this plugin requires a Kast beta whose `kast agent --help`
includes both `repository` and `graph`.

For the Codex plugin alone:

```sh
codex plugin marketplace add amichne/kast-marketplace --ref main --json
codex plugin add kast@kast --json
```

The hook never runs a networked installer. Restart IntelliJ and start a new
Codex thread after the compatible Kast release or plugin changes.

## Start the exact-root runtime

`SessionStart` forwards the event to
`kast developer codex hook session-start`; Rust owns root resolution, host
selection, runtime startup, and retry policy. For an explicit manual start:

```sh
ROOT="$(git rev-parse --show-toplevel)"
kast developer runtime up --workspace-root "$ROOT" --backend idea --accept-indexing
kast ready --workspace-root "$ROOT" --backend idea --for kotlin
```

Do not launch another IDE process or bypass the exact-root runtime. Treat
`HEADLESS_LOCAL_UNSUPPORTED`, `IDEA_PLUGIN_UPDATE_REQUIRED`,
`IDEA_VERSION_UNSUPPORTED`, and `IDEA_HOST_AMBIGUOUS` as terminal typed
blockers. `INDEXING` is not `READY`.

## Restart the runtime

Restart only after an update or when Kast's structured response asks for it:

```sh
ROOT="$(git rev-parse --show-toplevel)"
kast developer runtime restart --workspace-root "$ROOT" --backend idea
```
