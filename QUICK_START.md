# Quick Start — LibreGameDev for Grok Build

> From a clean machine to one critiqued player verb in under 5 minutes.

Doctrine first: put [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine (global Grok doctrine). This pack does not replace it.

## Prerequisites

- `git`
- Grok Build installed and able to see skills under `.grok/skills/` or `~/.grok/skills/`
- A game project you own (any engine), **or** this repo as the working tree

## Layout this file assumes

Verified against this repository (do not invent extra folders):

```
skills/<name>/SKILL.md             # canonical skill bodies (copy these)
AGENTS/gamedev-orchestrator.md
docs/DEPTH_MATRIX.md
docs/MELT_RULES.md
.grok/skills/<name>/SKILL.md       # dogfood copy; must match skills/
.grok/plugins/libregamedev-core/   # plugin stub; not required for first run
```

Melted (usable now): `skills/game-loop-feel/SKILL.md`, `skills/game-design-critique/SKILL.md`, `skills/playtest-checklist/SKILL.md`.
Still stubs: the other six skills + the orchestrator. Honest table: [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Install (pick one)

### A. Dogfood this repo (fastest)

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git
cd LibreGameDev-Grok-Build
# Skills are already at .grok/skills/ — open this folder in Grok Build.
```

### B. Install into your game project

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git ~/LibreGameDev-Grok-Build
cd /path/to/your-game
mkdir -p .grok/skills
cp -R ~/LibreGameDev-Grok-Build/skills/* .grok/skills/
```

Confirm the copy landed:

```bash
test -f .grok/skills/game-loop-feel/SKILL.md
test -f .grok/skills/game-design-critique/SKILL.md
test -f .grok/skills/playtest-checklist/SKILL.md
ls .grok/skills
```

You should see nine skill directories, matching `skills/` in this repo.

### C. User-global

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git ~/LibreGameDev-Grok-Build
mkdir -p ~/.grok/skills
cp -R ~/LibreGameDev-Grok-Build/skills/* ~/.grok/skills/
```

Same three `test -f` checks as B, under `~/.grok/skills/`.

### Optional orchestrator (stub)

Copy `AGENTS/gamedev-orchestrator.md` only when you want a multi-skill pass. It is still a stub coordinator. Merge into project `AGENTS.md` / `.grok/AGENTS.md`. Do not overwrite Reality OS doctrine.

## First-run teach cue

In Grok Build, on a real verb you own (jump, dash, shoot — any engine):

1. **Teach** — "Run game-loop-feel on this jump. Name the verb, the tick, and whether response is measured or unverified."
2. **Critique** — "Run game-design-critique on that same verb: teaching fails, feedback, loop integrity. No /10 score."
3. **Playtest** — "Run playtest-checklist for a 15-minute stranger session that can falsify 'they discover the verb before the second gap.'"

Leftovers (stubs — name them, do not invent depth): `input-feel` for buffer/coyote, `godot-patterns` / `unity-patterns` for engine wiring.

You used melted LibreGameDev depth on Grok — not a Claude paste, not a fake plugin count.

## Smoke checklist

- [ ] The three melted skill files exist at the install path you chose
- [ ] Grok can see `game-loop-feel`, `game-design-critique`, and `playtest-checklist`
- [ ] One verb named with a tick (Hz/ms) and measured-or-unverified response
- [ ] One critique returned with severity-ranked findings and remediations (no `/10` score)
- [ ] One playtest plan with a single goal and a no-coaching protocol
- [ ] No secrets in prompts, examples, or output

## Gold Hat

[GOLD_HAT.md](./GOLD_HAT.md) — empower or extract? Teach the rule; do not extract tester time or player attention.

## Suite

- Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os)
- This pack: [LibreGameDev-Grok-Build](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build)
- Sibling Libre*-Grok-Build packs: [Arch](https://github.com/HermeticOrmus/LibreArch-Grok-Build) · [Copy](https://github.com/HermeticOrmus/LibreCopy-Grok-Build) · [DevOps](https://github.com/HermeticOrmus/LibreDevOps-Grok-Build) · [Embed](https://github.com/HermeticOrmus/LibreEmbed-Grok-Build) · [FinTech](https://github.com/HermeticOrmus/LibreFinTech-Grok-Build) · [GameDev](https://github.com/HermeticOrmus/LibreGameDev-Grok-Build) · [GEO](https://github.com/HermeticOrmus/LibreGEO-Grok-Build) · [MLOps](https://github.com/HermeticOrmus/LibreMLOps-Grok-Build) · [MobileDev](https://github.com/HermeticOrmus/LibreMobileDev-Grok-Build) · [SecOps](https://github.com/HermeticOrmus/LibreSecOps-Grok-Build) · [SessionFlow](https://github.com/HermeticOrmus/LibreSessionFlow-Grok-Build) · [UIUX](https://github.com/HermeticOrmus/LibreUIUX-Grok-Build) · [WhatsApp](https://github.com/HermeticOrmus/LibreWhatsApp-Grok-Build)
- Skills collections: [grok-skills](https://github.com/HermeticOrmus/grok-skills) · [grok-build-skills](https://github.com/HermeticOrmus/grok-build-skills)
- Claude proof (upstream, not this inventory): [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code)
- https://ormus.solutions
