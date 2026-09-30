# Contributing

## Ways to contribute

- **Seal a crack.** [LEDGER.md](./LEDGER.md) lists the open cracks with their evidence and the seal each one needs. Pick an `open` row, prove it with a failing check where you can, fix it, and set the row to `sealed` with your PR number.
- **Melt a pack skill into a Grok-native one.** Take a stub from [stubs/](./stubs/) or a skill from a [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development) game plugin and write it to the melted bar below. The steps are in [stubs/README.md](./stubs/README.md#melt-a-stub).
- **Report a routing miss.** When Grok picks the wrong skill, or none, the description is what needs fixing: [routing miss form](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/issues/new?template=routing-miss.yml).
- **Propose a plugin.** Name a real job, what Grok gets wrong today without it, and a check anyone can run: [plugin proposal form](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/issues/new?template=plugin-proposal.yml).

General feedback goes in the [feedback form](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/issues/new?template=feedback.yml).

## Melt, don't clone

Ports from LibreGameDev (now [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development); the old LibreGameDev-Claude-Code repo is archived) must follow Liquid Gold:

1. Keep model-agnostic GameDev knowledge.
2. Strip Claude-only paths, `model:` pins, Anthropic install residue.
3. Ship as Grok `SKILL.md` / agents under `.grok/` conventions.
4. Teach while helping (Gold Hat).
5. Prefer engine-agnostic design skills before melting `godot-patterns` or `unity-patterns`.

## Skill format

```text
plugins/libre-gamedev-grok/skills/<name>/SKILL.md   # melted
stubs/<name>/SKILL.md                               # stub
```

YAML frontmatter: `name`, `description`. The description is the routing line Grok reads: say what the skill does and when to use it (`Use when ...`). Body: when to use, steps, measurable checks, example, output shape.

Link repo files from a skill with absolute GitHub URLs, not `../../` paths: the same file is read from the plugin install, the dogfood copy and a project copy, and only an absolute link resolves from all three.

## PR bar

- Honest depth: only count what you melt. Status is `stub` or `melted` in [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).
- No "Grok killer" language. No Claude plugin/agent/command totals as this repo's inventory.
- Suite footer on README / QUICK_START / AGENTS.md: Reality OS + sibling Libre*-Grok-Build packs.
- Canonical skill bodies are `plugins/libre-gamedev-grok/skills/<name>/SKILL.md` (melted) and `stubs/<name>/SKILL.md` (stubs). Keep `.grok/skills/<name>/SKILL.md` identical; CI checks it.
- No secrets in skills, templates, or examples.
- Link [SECURITY.md](./SECURITY.md) and the [quality ladder](https://github.com/HermeticOrmus/grok-build-reality-os/blob/main/docs/QUALITY_LADDER.md) when you touch landing docs.
- `grok plugin validate plugins/libre-gamedev-grok` passes. CI runs it, checks the pack pins, and installs every marketplace entry into a clean Grok home.
- When the pack adds or drops a game plugin, CI fails and says so. Run `scripts/pin-pack.sh`, commit `.grok-plugin/marketplace.json`, and update the Depth table if the count changed.
