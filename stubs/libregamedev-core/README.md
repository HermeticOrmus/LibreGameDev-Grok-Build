# libregamedev-core (Grok plugin stub)

v0 record, superseded in v1.0.0. This folder had no manifest, so `grok plugin install` took it as an unversioned plugin holding only a copy of the stub orchestrator. The melted skills now ship as [plugins/libre-gamedev-grok](../../plugins/libre-gamedev-grok/). The text below describes the v0 layout.

Bundles core LibreGameDev skills for install-from-path.

v0: skill bodies live under repo `skills/` (canonical) and `.grok/skills/` (dogfood). Copy or symlink into this plugin's `skills/` when packaging. This plugin is not required for the QUICK_START first run.

Melted in the pack: `game-loop-feel`, `game-design-critique`, `playtest-checklist`. Honest inventory: [docs/DEPTH_MATRIX.md](../../docs/DEPTH_MATRIX.md).
