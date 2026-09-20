# Depth matrix

Update this table when melting. Status words mean what they say:

| Status | Meaning |
|--------|---------|
| stub | Thin cue only. Usable as a reminder, not a playbook. |
| melted | Real Grok skill: when-to-use, steps, measurable checks, example, output shape. |

Never copy Claude plugin / agent / command totals into this inventory. Upstream [LibreGameDev-Claude-Code](https://github.com/HermeticOrmus/LibreGameDev-Claude-Code) is proof that the *job* exists, not a count this repo has earned.

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

Dogfood copies of every skill live at `.grok/skills/<name>/SKILL.md` and must match `skills/<name>/SKILL.md`.

## Depth / quality (ladder, not inventory)

Melted vs stub is inventory. The shared hygiene ladder is L0–L5 in [grok-build-reality-os `docs/QUALITY_LADDER.md`](https://github.com/HermeticOrmus/grok-build-reality-os/blob/main/docs/QUALITY_LADDER.md).

This pass targets **L3–L4 hygiene** (honest inventory, SECURITY linked, contributing describes this repo, suite map complete, no inflated Claude totals). It does not claim L5: remaining skills and the orchestrator are still stubs, and the melted three are not yet session-verified in the wild.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Sibling Libre*-Grok-Build packs: [README suite footer](../README.md).
