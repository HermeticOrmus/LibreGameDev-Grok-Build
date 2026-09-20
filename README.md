# LibreGameDev-Grok-Build

**GameDev skills (feel, critique, playtest) for [Grok Build](https://github.com/HermeticOrmus/grok-build-reality-os)** — ported and melted from [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code), not a dumb copy.

> Status: **public v0** — three skills melted (`game-loop-feel`, `game-design-critique`, `playtest-checklist`); the rest are honest stubs. See [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Why this exists

Generic codegen compiles but feels off. LibreGameDev owns the game loop, player-verb critique, and honest playtests. Grok Build needs the same *job* with Grok-native skills, agents, `.grok/`, and truth-seeking voice. This repo counts only what it has melted.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md) for clone, dogfood, project-local, and user-global paths.

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git
cd LibreGameDev-Grok-Build
# Dogfood: .grok/skills/ already has the skill bodies.
# Other project: cp -R skills/* /path/to/your-game/.grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first. Do not replace that doctrine with this file.

## Depth (honest)

| Artifact | This repo now | Upstream Claude |
|----------|---------------|-----------------|
| Skills | 3 melted + 6 stubs | Proof the job exists; not our inventory |
| Agents | 1 stub (`gamedev-orchestrator`) | Proof the job exists; not our inventory |
| Plugins | 1 core bundle stub | Proof the job exists; not our inventory |

Do not paste Claude plugin/agent/command totals here. Update [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) when something melts.

## Depth / quality

Public Grok Build repos in this suite use a shared ladder: **L0–L5**. Definitions live in [grok-build-reality-os `docs/QUALITY_LADDER.md`](https://github.com/HermeticOrmus/grok-build-reality-os/blob/main/docs/QUALITY_LADDER.md).

This pass targets **L3–L4 hygiene** (SECURITY linked, contributing describes this repo, inventory honest, suite map complete, no inflated claims). It does not claim L5.

## Skills

| Skill | Status | Job |
|-------|--------|-----|
| game-loop-feel | melted | Teach the loop: verb, tick, juice, fail-states that teach |
| game-design-critique | melted | Engine-agnostic daily critique (no `/10`) |
| playtest-checklist | melted | One-goal session plan, protocol, triage |
| godot-patterns | stub | Godot 4 scenes / signals (cue only) |
| unity-patterns | stub | Unity composition / SO (cue only) |
| input-feel | stub | Buffer, coyote, deadzones, remap |
| save-systems | stub | Slots, migration, cloud hazards |
| performance-game | stub | Frame budget, GC, draw calls |
| monetization-ethics | stub | Empower players; refuse extract |

Agent: `AGENTS/gamedev-orchestrator.md` — stub coordinator for a multi-skill pass.

## Layout (Grok Build)

```
skills/                 # canonical SKILL.md bodies
AGENTS/                 # suite agents
docs/                   # DEPTH_MATRIX, MELT_RULES
.grok/skills/           # dogfood copy of skills/ (keep in sync)
.grok/plugins/          # optional plugin bundle stub
```

Claude's `.claude/` maps to Grok skills + `AGENTS.md` + `.grok/`. Melt rules: [docs/MELT_RULES.md](./docs/MELT_RULES.md).

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract? Canonical manifesto: [gold-hat-manifesto](https://github.com/HermeticOrmus/gold-hat-manifesto).

## Security

See [SECURITY.md](./SECURITY.md). Never embed secrets in skills, templates, or examples.

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreGameDev-Grok-Build](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [UIUX](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build) · [WhatsApp](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof: [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code)
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
