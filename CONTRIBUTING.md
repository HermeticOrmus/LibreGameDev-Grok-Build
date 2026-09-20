# Contributing

## Melt, don't clone

Ports from LibreGameDev-Claude-Code must follow Liquid Gold:

1. Keep model-agnostic GameDev knowledge.
2. Strip Claude-only paths, `model:` pins, Anthropic install residue.
3. Ship as Grok `SKILL.md` / agents under `.grok/` conventions.
4. Teach while helping (Gold Hat).
5. Prefer engine-agnostic design skills before melting `godot-patterns` or `unity-patterns`.

## Skill format

```
skills/<name>/SKILL.md
```

YAML frontmatter: `name`, `description`. Body: when to use, steps, measurable checks, example, output shape.

## PR bar

- Honest depth: only count what you melt. Status is `stub` or `melted` in [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).
- No "Grok killer" language. No Claude plugin/agent/command totals as this repo's inventory.
- Suite footer on README / QUICK_START / AGENTS.md: Reality OS + sibling Libre*-Grok-Build packs.
- Canonical skill body is `skills/<name>/SKILL.md`. Keep `.grok/skills/<name>/SKILL.md` identical.
- No secrets in skills, templates, or examples.
- Link [SECURITY.md](./SECURITY.md) and the [quality ladder](https://github.com/HermeticOrmus/grok-build-reality-os/blob/main/docs/QUALITY_LADDER.md) when you touch landing docs.
