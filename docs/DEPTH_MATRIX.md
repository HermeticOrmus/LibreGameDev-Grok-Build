# Depth matrix

Update this table when melting. Status words mean what they say:

| Status | Meaning |
|--------|---------|
| stub | Thin cue only. Usable as a reminder, not a playbook. |
| melted | Real Grok skill: when-to-use, steps, measurable checks, example, output shape. |

Never copy Claude plugin / agent / command totals into this inventory. Upstream [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development) is proof that the *job* exists, not a count this repo has earned. (The melt sources below were read in LibreGameDev-Claude-Code, now archived; its game plugins continue in claude-code-game-development under the same `plugins/<name>` paths.)

| ID | Kind | Status | Source (Claude, for melt) | Notes |
|----|------|--------|---------------------------|-------|
| game-loop-feel | skill | melted | docs + architecture loop gold | Teach: verb, tick, juice, fail-states. Engine-agnostic. |
| game-design-critique | skill | melted | playtesting + feel + architecture (no Claude twin of this name) | Daily critique. No engine APIs. No `/10`. |
| godot-patterns | skill | stub | plugins/godot-development | Engine cue only. |
| unity-patterns | skill | stub | plugins/unity-development | Engine cue only. |
| input-feel | skill | stub | plugins/input-systems | Buffer / coyote / deadzone still thin. |
| save-systems | skill | stub | plugins/save-systems | Versioning cue only. |
| playtest-checklist | skill | melted | plugins/playtesting | Session goal, protocol, triage. No heatmap product. |
| performance-game | skill | stub | plugins/performance-optimization | Frame-budget cue only. |
| monetization-ethics | skill | stub | plugins/monetization-ethics | Gold Hat pointer only. |
| gamedev-orchestrator | agent | stub | (suite coordinator) | Coordinates the skills; not a melted specialist. |

This repo now: **3 melted skills**, **6 stub skills**, **1 stub agent**.

Where they live: melted skills in `plugins/libre-gamedev-grok/skills/<name>/SKILL.md` (the plugin installs them); stubs in `stubs/<name>/SKILL.md` (nothing installs them); the agent in `AGENTS/gamedev-orchestrator.md`.

Dogfood copies of every skill live at `.grok/skills/<name>/SKILL.md` and must match the canonical file above. CI checks it.

## Pack entries (installed, not melted)

The marketplace also lists the game plugins of [claude-code-game-development](https://github.com/HermeticOrmus/claude-code-game-development) as remote entries: **22 entries**, all pinned to one pack commit (the `sha` in `.grok-plugin/marketplace.json`). Grok reads those plugin folders as they are. They are not counted in the melted inventory above.

Which pack plugins: the pack's `gaming` category, selected in `scripts/pin-pack.sh` with `.plugins[] | select(.category == "gaming")`. That is the 20 game plugins, `libre-gamedev-hooks`, and `game-development` (Seth Hobson, [wshobson/agents](https://github.com/wshobson/agents), MIT). The pack's other plugins are general development plugins derived from wshobson/agents and are not part of this edition.

`scripts/pin-pack.sh` re-pins them; CI fails when the pack gains or loses a game plugin.

## Depth / quality (ladder, not inventory)

Melted vs stub is inventory. The shared hygiene ladder is L0–L5 in [grok-build-reality-os `docs/QUALITY_LADDER.md`](https://github.com/HermeticOrmus/grok-build-reality-os/blob/main/docs/QUALITY_LADDER.md).

This pass targets **L3–L4 hygiene** (honest inventory, SECURITY linked, contributing describes this repo, suite map complete, no inflated Claude totals). It does not claim L5: remaining skills and the orchestrator are still stubs, and the melted three are not yet session-verified in the wild.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Sibling Libre*-Grok-Build packs: [README suite footer](../README.md).
