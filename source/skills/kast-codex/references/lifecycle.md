# Kast lifecycle

## Install or update

Use the authoritative installer; it installs the matching CLI and IntelliJ plugin, connects the Codex marketplace, and enables background worktree opening:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/amichne/kast/main/install.sh)" -- --autostart
```

The hook never runs this networked installer automatically. After an install or plugin update, restart IntelliJ and Codex so both installed copies reload.

## Initialize a worktree

The `SessionStart` hook first asks Kast to start the IDEA backend. On `MACOS_PLUGIN_WORKSPACE_REQUIRED`, it opens the exact root in an installed IntelliJ IDEA or Android Studio app with macOS background and hidden flags, waits for plugin metadata, and retries Kast. Set `KAST_IDEA_APP` to an explicit `.app` path when automatic discovery is wrong.

This is a hidden local IDE, not a headless IntelliJ runtime. Kast currently returns `HEADLESS_LOCAL_UNSUPPORTED` for macOS developer machines; do not substitute `remote-dev-server` or claim headless execution until Kast owns that runtime contract.

## Restart the runtime

Restart only after a runtime/plugin update or when Kast's structured response asks for it:

```sh
kast developer runtime restart --workspace-root "$(git rev-parse --show-toplevel)" --backend idea
```
