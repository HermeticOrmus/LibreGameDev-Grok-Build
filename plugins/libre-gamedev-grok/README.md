# libre-gamedev-grok

The Grok-native LibreGameDev plugin. It carries the skills melted for Grok Build, and only those:

| Skill | Job | Melted from |
|-------|-----|-------------|
| `game-loop-feel` | Teach the loop: verb, tick, juice, fail-states that teach | docs and architecture loop gold |
| `game-design-critique` | Engine-agnostic daily critique of one verb, loop, or encounter (no `/10`) | `playtesting`, feel, architecture (no Claude twin of this name) |
| `playtest-checklist` | One-goal session plan, protocol, triage | `playtesting` |

Install:

```bash
grok plugin marketplace add HermeticOrmus/LibreGameDev-Grok-Build
grok plugin install libre-gamedev-grok@libre-gamedev-grok --trust
```

The six stub skills are not in this plugin. They live in [stubs/](../../stubs/), and each names the pack plugin that holds the real depth. The same marketplace installs those pack plugins from [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development).

Manifest: [.grok-plugin/plugin.json](./.grok-plugin/plugin.json). Honest inventory: [docs/DEPTH_MATRIX.md](../../docs/DEPTH_MATRIX.md). The v0 bundle stub this plugin replaces is kept at [stubs/libregamedev-core/](../../stubs/libregamedev-core/).
