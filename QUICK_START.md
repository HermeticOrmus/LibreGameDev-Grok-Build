# Quick Start — LibreGameDev for Grok Build

> From a clean machine to one critiqued player verb in under 5 minutes.

Doctrine first: put [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os) `AGENTS.md` on the machine (global Grok doctrine). This pack does not replace it.

## Prerequisites

- Grok Build (`grok --version` prints a version)
- `git` and `jq` for the clone paths and the install-everything loop
- A game project you own (any engine), **or** this repo as the working tree

## Layout this file assumes

Verified against this repository (do not invent extra folders):

```text
plugins/libre-gamedev-grok/                       # the Grok-native plugin
plugins/libre-gamedev-grok/skills/<name>/SKILL.md # melted skill bodies (copy these for the manual path)
stubs/<name>/SKILL.md                             # stub cues; not installed
AGENTS/gamedev-orchestrator.md
docs/DEPTH_MATRIX.md
docs/MELT_RULES.md
.grok-plugin/marketplace.json                     # the plugin + every game plugin of the pack, pinned
.grok/skills/<name>/SKILL.md                      # dogfood copy of the plugin skills and stubs
stubs/libregamedev-core/                          # v0 plugin bundle stub, kept as the record
```

Melted (usable now): `game-loop-feel`, `game-design-critique`, `playtest-checklist`, in `plugins/libre-gamedev-grok/skills/`.
Still stubs: the other six skills + the orchestrator. Honest table: [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md).

## Install (pick one)

### A. Marketplace (recommended)

```bash
grok plugin marketplace add HermeticOrmus/LibreGameDev-Grok-Build
grok plugin install libre-gamedev-grok@libre-gamedev-grok --trust
grok plugin details libre-gamedev-grok
```

Grok installs a plugin only with `--trust`, because a plugin can run hooks, MCP servers and skills on your machine. Without it, `grok plugin install` stops and asks you to re-run with the flag.

The same marketplace lists every game plugin of [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development), pinned to one commit of the pack: the 20 game plugins, `libre-gamedev-hooks`, and `game-development`. Install the ones your game needs by name:

```bash
grok plugin install godot-development@libre-gamedev-grok --trust
grok plugin install input-systems@libre-gamedev-grok --trust
```

Or install every entry:

```bash
for p in $(grok plugin list --json --available | jq -r '.[] | select(.marketplace == "libre-gamedev-grok" and .status == "available") | .name'); do
  grok plugin install "$p@libre-gamedev-grok" --trust
done
```

`libre-gamedev-hooks` is format-compatible with Grok, but its behavior inside a Grok session is not verified yet (see [LEDGER.md](./LEDGER.md)). Skip it if you only want skills and agents.

To pick up a new pin later: `grok plugin marketplace update`, then `grok plugin update`.

### B. Dogfood this repo

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git
cd LibreGameDev-Grok-Build
# A copy of the skills and stubs is already at .grok/skills/. Open this folder in Grok Build.
```

### C. Copy into your game project

The v0 path, for a project that should carry the skill files itself.

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git ~/LibreGameDev-Grok-Build
cd /path/to/your-game
mkdir -p .grok/skills
cp -R ~/LibreGameDev-Grok-Build/plugins/libre-gamedev-grok/skills/* .grok/skills/
```

Confirm the copy landed:

```bash
test -f .grok/skills/game-loop-feel/SKILL.md
test -f .grok/skills/game-design-critique/SKILL.md
test -f .grok/skills/playtest-checklist/SKILL.md
ls .grok/skills
```

You should see three skill directories, matching `plugins/libre-gamedev-grok/skills/` in this repo. The stubs are not copied: they are pointers to pack plugins, not skills.

### D. User-global copy

```bash
git clone https://github.com/HermeticOrmus/LibreGameDev-Grok-Build.git ~/LibreGameDev-Grok-Build
mkdir -p ~/.grok/skills
cp -R ~/LibreGameDev-Grok-Build/plugins/libre-gamedev-grok/skills/* ~/.grok/skills/
```

Same three `test -f` checks as C, under `~/.grok/skills/`.

### Upgrading from v0

If you copied `skills/*` into a project or `~/.grok/skills/`, that copy holds all nine folders, stubs included. Remove the six stub folders (`godot-patterns`, `unity-patterns`, `input-feel`, `save-systems`, `performance-game`, `monetization-ethics`) from the copy, or replace the copy with path A so updates arrive through `grok plugin update`.

### Optional orchestrator (stub)

Copy `AGENTS/gamedev-orchestrator.md` only when you want a multi-skill pass. It is still a stub coordinator. Merge into project `AGENTS.md` / `.grok/AGENTS.md`. Do not overwrite Reality OS doctrine.

## First-run teach cue

In Grok Build, on a real verb you own (jump, dash, shoot — any engine):

1. **Teach** — "Run game-loop-feel on this jump. Name the verb, the tick, and whether response is measured or unverified."
2. **Critique** — "Run game-design-critique on that same verb: teaching fails, feedback, loop integrity. No /10 score."
3. **Playtest** — "Run playtest-checklist for a 15-minute stranger session that can falsify 'they discover the verb before the second gap.'"

Leftovers (stubs — name them, do not invent depth): `input-feel` for buffer/coyote, `godot-patterns` / `unity-patterns` for engine wiring.

With the pack plugins installed, the real depth for those leftovers is `input-systems`, `godot-development`, and `unity-development`.

You used melted LibreGameDev depth on Grok — not a Claude paste, not a fake plugin count.

## Smoke checklist

- [ ] `grok plugin list` shows `libre-gamedev-grok` (path A), or the three melted skill files exist at the copy path you chose (C or D)
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
- Claude pack (upstream, installed through the marketplace, not this inventory): [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development). The archived [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code) is where the game plugins started.
- https://ormus.solutions
