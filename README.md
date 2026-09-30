<p align="center">
  <img src="https://ormus.solutions/mascot/pixellab_liquid_to_n64.gif" alt="LibreGameDev Grok Build" width="128" style="image-rendering: pixelated;" />
</p>

<h1 align="center">LibreGameDev Grok Build</h1>

<p align="center">
  <em>Game development for Grok Build: Grok-native feel, critique, and playtest skills plus every game plugin of the Claude Code pack, from one marketplace</em>
</p>

<p align="center">
  <a href="https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/stargazers"><img src="https://img.shields.io/github/stars/HermeticOrmus/LibreGameDev-Grok-Build?style=flat-square&color=aa8142" alt="Stars" /></a>
  <a href="https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/blob/main/LICENSE"><img src="https://img.shields.io/github/license/HermeticOrmus/LibreGameDev-Grok-Build?style=flat-square&color=aa8142" alt="License" /></a>
  <a href="https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/commits"><img src="https://img.shields.io/github/last-commit/HermeticOrmus/LibreGameDev-Grok-Build?style=flat-square&color=aa8142" alt="Last Commit" /></a>
  <img src="https://img.shields.io/badge/GameDev-aa8142?style=flat-square&logo=godotengine&logoColor=white" alt="GameDev" />
  <img src="https://img.shields.io/badge/Grok_Build-aa8142?style=flat-square&logo=x&logoColor=white" alt="Grok Build" />
</p>

---

**GameDev skills (feel, critique, playtest) for [Grok Build](https://github.com/HermeticOrmus/grok-build-reality-os)**, ported and melted from LibreGameDev, not a dumb copy. LibreGameDev's game plugins now live in [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development); the old [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code) repo is archived.

> Status: **v1.0.0**. Three skills are melted into the Grok-native plugin `libre-gamedev-grok` (`game-loop-feel`, `game-design-critique`, `playtest-checklist`). The other six are honest stubs in [stubs/](./stubs/), each pointing at the pack plugin that holds the real depth. See [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) and the [kintsugi ledger](./LEDGER.md).

## Why this exists

Generic codegen compiles but feels off. LibreGameDev owns the game loop, player-verb critique, and honest playtests. Grok Build needs the same *job* with Grok-native skills, agents, `.grok/`, and truth-seeking voice. This repo counts only what it has melted.

## Install

One marketplace brings both layers: the Grok-native plugin melted here, and every game plugin of the [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development) pack, pinned to one commit of the pack. Grok reads the pack plugins as they are.

```bash
grok plugin marketplace add HermeticOrmus/LibreGameDev-Grok-Build
grok plugin install libre-gamedev-grok@libre-gamedev-grok --trust
```

Grok installs a plugin only with `--trust`, because a plugin can run hooks, MCP servers and skills on your machine. Read what you trust: each entry's source is linked in [.grok-plugin/marketplace.json](./.grok-plugin/marketplace.json).

Then add the pack plugins your game needs, for example:

```bash
grok plugin install godot-development@libre-gamedev-grok --trust
grok plugin install input-systems@libre-gamedev-grok --trust
```

[QUICK_START.md](./QUICK_START.md) has the loop that installs every entry, the dogfood clone, and the manual copy path. From a clone:

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git
cd LibreGameDev-Grok-Build
# Dogfood: .grok/skills/ holds a copy of the skill bodies and stubs.
# Other project: cp -R plugins/libre-gamedev-grok/skills/* /path/to/your-game/.grok/skills/
```

Doctrine: install [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine first. Do not replace that doctrine with this file.

## Depth (honest)

| Artifact | This repo now | Where |
|----------|---------------|-------|
| Grok-native skills | 3 melted | `plugins/libre-gamedev-grok/skills/` |
| Stub skills | 6, not installed | `stubs/`, each names its pack plugin |
| Agents | 1 stub (`gamedev-orchestrator`), not installed | `AGENTS/` |
| Plugins in the marketplace | 1 Grok-native + 22 pack entries | `.grok-plugin/marketplace.json`, pinned to one pack commit |

Pack entries are the game plugins of claude-code-game-development: its `gaming` category, which is 20 game plugins, `libre-gamedev-hooks`, and `game-development`. The pack's general development plugins are not listed here. Pack entries are installed through this marketplace; they are not melted here, and they are not counted as this repo's skills. Do not paste Claude plugin/agent/command totals here. Update [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md) when something melts, and run `scripts/pin-pack.sh` when the pack changes.

## Depth / quality

Public Grok Build repos in this suite use a shared ladder: **L0–L5**. Definitions live in [grok-build-reality-os `docs/QUALITY_LADDER.md`](https://github.com/HermeticOrmus/grok-build-reality-os/blob/main/docs/QUALITY_LADDER.md).

This pass targets **L3–L4 hygiene** (SECURITY linked, contributing describes this repo, inventory honest, suite map complete, no inflated claims). It does not claim L5.

## Skills

| Skill | Status | Job | Pack plugin |
|-------|--------|-----|-------------|
| game-loop-feel | melted | Teach the loop: verb, tick, juice, fail-states that teach | melted from docs and architecture loop gold |
| game-design-critique | melted | Engine-agnostic daily critique (no `/10`) | melted from `playtesting`, feel, architecture |
| playtest-checklist | melted | One-goal session plan, protocol, triage | melted from `playtesting` |
| godot-patterns | stub | Godot 4 scenes / signals (cue only) | real depth in `godot-development` |
| unity-patterns | stub | Unity composition / SO (cue only) | real depth in `unity-development` |
| input-feel | stub | Buffer, coyote, deadzones, remap | real depth in `input-systems` |
| save-systems | stub | Slots, migration, cloud hazards | real depth in `save-systems` |
| performance-game | stub | Frame budget, GC, draw calls | real depth in `performance-optimization` |
| monetization-ethics | stub | Empower players; refuse extract | real depth in `monetization-ethics` |

Agent: `AGENTS/gamedev-orchestrator.md` — stub coordinator for a multi-skill pass.

## Layout (Grok Build)

```text
plugins/libre-gamedev-grok/  # the Grok-native plugin: manifest + melted SKILL.md bodies
stubs/                       # stub skills + the v0 bundle stub; not installed
AGENTS/                      # suite agents
docs/                        # DEPTH_MATRIX, MELT_RULES
scripts/pin-pack.sh          # re-pins the pack entries to the pack's main
.grok-plugin/                # marketplace: the plugin + every game plugin of the pack, pinned
.grok/skills/                # dogfood copy of the plugin skills and stubs (CI checks it)
```

Claude's `.claude/` maps to Grok skills + `AGENTS.md` + `.grok/`. Melt rules: [docs/MELT_RULES.md](./docs/MELT_RULES.md).

## Kintsugi ledger

Every crack found in v0 and how this release seals it, with the file that shows the seal: [LEDGER.md](./LEDGER.md).

## Feedback and contributing

Tell us what worked and what is missing with the [feedback form](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/issues/new?template=feedback.yml). When Grok picks the wrong skill, file a [routing miss](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build/issues/new?template=routing-miss.yml). Ways to contribute are in [CONTRIBUTING.md](./CONTRIBUTING.md).

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract? Canonical manifesto: [gold-hat-manifesto](https://github.com/HermeticOrmus/gold-hat-manifesto).

## Security

See [SECURITY.md](./SECURITY.md). Never embed secrets in skills, templates, or examples.

## Acknowledgments

The `game-development` pack entry comes from [wshobson/agents](https://github.com/wshobson/agents) by [Seth Hobson](https://github.com/wshobson), MIT, by way of claude-code-game-development and its [NOTICE.md](https://github.com/HermeticOrmus/claude-code-game-development/blob/main/NOTICE.md). It installs from that pack as it is.

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreGameDev-Grok-Build](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [UIUX](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build) · [WhatsApp](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude pack: [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development) (the game plugins of the archived [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code) continue there)
- https://ormus.solutions

## License

MIT — see [LICENSE](./LICENSE).
