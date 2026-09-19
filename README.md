# LibreGameDev-Grok-Build

**GameDev skills (Godot / Unity / Unreal feel) for Grok Build** — ported and melted from [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code), not a dumb copy.

> Status: **v0 public scaffold** — honest stubs. Melt depth next.

## Why this exists

Generic codegen compiles but feels off. LibreGameDev owns game-loop feel, engines, input, saves, playtest — melted for Grok Build from LibreGameDev-Claude-Code.

## Install (<5 min)

See [QUICK_START.md](./QUICK_START.md).

```bash
mkdir -p .grok/skills
cp -R skills/* .grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first.

## Depth matrix (honest)

| Artifact | v0 scaffold | Upstream Claude (proof) |
|----------|-------------|-------------------------|
| Skills (melted bodies) | 8 stubs → fill next | see upstream suite |
| Agents | 1 (`gamedev-orchestrator`) | upstream agents |

Counts on the right are **upstream proof**, not this repo's claim until melted.

## First skills

| Skill | Job |
|-------|-----|
| game-loop-feel | Game feel: timing, juice, feedback loops that make controls sing |
| godot-patterns | Godot 4 patterns: scenes, signals, composition over deep inheritance |
| unity-patterns | Unity patterns: composition, ScriptableObjects, scene flow |
| input-feel | Input buffering, deadzones, remapping, accessibility |
| save-systems | Save/load: slots, migration, cloud sync hazards |
| playtest-checklist | Structured playtest plan — goals, metrics, notes template |
| performance-game | Game perf: frame budget, GC, draw calls, streaming |
| monetization-ethics | Ethical monetization — empower players, avoid dark patterns |

Agent: `AGENTS/gamedev-orchestrator.md` — full suite pass.

## Layout (Grok Build)

```
skills/                 # install into .grok/skills or ~/.grok/skills
AGENTS/                 # suite agents
.grok/plugins/          # optional plugin bundle
docs/                   # DEPTH_MATRIX, MELT_RULES
```

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract?

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- Sibling: [LibreUIUX-Grok-Build](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build) · [LibreSessionFlow-Grok-Build](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [LibreGEO-Grok-Build](https://github.com/HermeticOrmus/LibreGEO-Grok-Build)
- Skills packs: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof: [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code)
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
