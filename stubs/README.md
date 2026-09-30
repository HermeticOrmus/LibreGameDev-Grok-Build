# Stubs

A stub is a thin cue: a name, a one-line job, and five steps. It is a reminder, not a playbook, so nothing here installs. Each stub names the pack plugin that holds the real depth, and that plugin installs from this repo's marketplace.

| Stub | Job | Real depth (pack plugin) | Install |
|------|-----|--------------------------|---------|
| [godot-patterns](./godot-patterns/SKILL.md) | Godot 4 scenes / signals cue | [`godot-development`](https://github.com/HermeticOrmus/claude-code-game-development/tree/main/plugins/godot-development) | `grok plugin install godot-development@libre-gamedev-grok --trust` |
| [unity-patterns](./unity-patterns/SKILL.md) | Unity composition / ScriptableObjects cue | [`unity-development`](https://github.com/HermeticOrmus/claude-code-game-development/tree/main/plugins/unity-development) | `grok plugin install unity-development@libre-gamedev-grok --trust` |
| [input-feel](./input-feel/SKILL.md) | Buffer, coyote, deadzones, remap cue | [`input-systems`](https://github.com/HermeticOrmus/claude-code-game-development/tree/main/plugins/input-systems) | `grok plugin install input-systems@libre-gamedev-grok --trust` |
| [save-systems](./save-systems/SKILL.md) | Slots, migration, cloud hazards cue | [`save-systems`](https://github.com/HermeticOrmus/claude-code-game-development/tree/main/plugins/save-systems) | `grok plugin install save-systems@libre-gamedev-grok --trust` |
| [performance-game](./performance-game/SKILL.md) | Frame budget, GC, draw calls cue | [`performance-optimization`](https://github.com/HermeticOrmus/claude-code-game-development/tree/main/plugins/performance-optimization) | `grok plugin install performance-optimization@libre-gamedev-grok --trust` |
| [monetization-ethics](./monetization-ethics/SKILL.md) | Gold Hat on money cue | [`monetization-ethics`](https://github.com/HermeticOrmus/claude-code-game-development/tree/main/plugins/monetization-ethics) | `grok plugin install monetization-ethics@libre-gamedev-grok --trust` |

The stub `save-systems` and the pack plugin `save-systems` share a name; the same is true of `monetization-ethics`. The stub is a skill folder here that nothing installs; the pack plugin is what `grok plugin install save-systems@libre-gamedev-grok --trust` brings.

Also here: [libregamedev-core/](./libregamedev-core/), the v0 plugin bundle stub. It had no manifest and installed only a copy of the stub orchestrator. It is kept as the record; [plugins/libre-gamedev-grok](../plugins/libre-gamedev-grok/) replaces it.

The suite agent [AGENTS/gamedev-orchestrator.md](../AGENTS/gamedev-orchestrator.md) is also a stub coordinator. It stays where [AGENTS.md](../AGENTS.md) points, and nothing installs it: you merge it by hand.

## Melt a stub

1. Write the skill to the melted bar in [docs/MELT_RULES.md](../docs/MELT_RULES.md): when to use, steps, measurable checks, a worked example, an output shape. Engine-agnostic first (melt rule 10).
2. `git mv stubs/<name> plugins/libre-gamedev-grok/skills/<name>`, drop the stub line, and give the frontmatter a routing description (`Use when ...`).
3. Copy it to `.grok/skills/<name>/SKILL.md` (CI checks the copy matches).
4. Update [docs/DEPTH_MATRIX.md](../docs/DEPTH_MATRIX.md), this table, and the README skills table.

The dogfood copies of these stubs in `.grok/skills/` match the files here, so a session opened in this repo sees them described as stubs.
