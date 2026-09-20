---
name: game-design-critique
description: Engine-agnostic critique of a player verb, loop, or short encounter. Hierarchy of verbs, feedback, teaching fails, agency. No scores.
---

# Game Design Critique

Daily critique loop for **one verb**, **one loop**, or **one short encounter**. Truth over flattery. Measurable findings beat "needs juice."

Gold Hat: teach the *why* of each finding. A list of defects extracts attention; a reusable rule empowers the next encounter. If a change would manipulate attention, time, or money without the player understanding the deal, it does not ship — see [GOLD_HAT.md](../../GOLD_HAT.md).

Godot-agnostic. Unity-agnostic. Unreal- and web-agnostic. Do not open with scene trees, MonoBehaviours, or Blueprint nodes. If the finding is "this node is wired wrong," that is an engine leftover for `godot-patterns` or `unity-patterns` (stubs). Stay on the design.

## When to use

- After a verb or encounter change
- When asked to "look at this jump / gun / room / loop"
- Before calling a prototype "it feels fine"
- When `game-loop-feel` has named the verb and you need severity + remediations

Use `game-loop-feel` first if the tick or the verb is unnamed. Use `playtest-checklist` to put the critique in front of a real player. Use `input-feel`, `save-systems`, `performance-game`, `monetization-ethics` (stubs) as named leftovers — do not invent their depth, and do not skip issues you can already see.

Do not invent a numeric quality score. Severity ranks are enough.

## Operating steps

1. **Restate the job** in one line (who, verb or encounter, success, fail). If unknown, infer from the build and say you inferred it.
2. **Walk the dimensions** below. For each finding: location (system, room, or file), current behavior, why it fails, exact remediation.
3. **Rank by severity.** Critical → high → medium → low. Cap the first patch list at what a person can do in one sitting.
4. **Name strengths** only when they are real (a readable telegraph, a clean retry). Do not pad.
5. **Hand off leftovers** to the matching skill (`input-feel`, `playtest-checklist`, engine stubs, `monetization-ethics`) instead of writing a fake full audit.

## Dimensions

### Verb clarity

Can a stranger name the primary action after ten seconds? Does one verb outrank the rest?

Look for: two equally loud buttons, a context action that steals the jump, a tutorial that names a verb the HUD never shows.

### Loop integrity

Does the loop close? Input → world change → readable result → next decision.

Look for: actions that spend a resource with no world change, rewards that arrive after the player has left the room, simulate/render coupling that `game-loop-feel` already flagged.

### Feedback and readability

Did the player see, hear, or feel the result? Hits, misses, blocks, and deaths need distinct cues.

If you did not play or watch a recording, mark the finding **unverified** and say what to watch. Do not invent a playtest.

### Teaching fails

The first fail should teach the rule. The tenth fail should still be the same rule.

Look for: invisible hazards, moving goals, a death that looks like a success, a tutorial that never lets the player fail safely.

### Difficulty and fairness

Challenge comes from a readable rule, not from late windows or hidden information the player could not have.

| Signal | Fair | Unfair (until proven otherwise) |
|--------|------|----------------------------------|
| Telegraph | Attack shows before the hit | Damage on the first visible frame |
| Recovery | Player has a named window to act | Stun longer than the lesson needs |
| Information | Hazard is in view or audio-cued | Off-camera kill; UI lie |

### Agency

The player should be able to choose and to undo a bad read. Soft-locks, unskippable fail-forward, and "the game plays itself" fail this dimension.

### Juice vs noise

Same bar as `game-loop-feel`: one purpose per effect. Critique the *design* of the accent (stop, cut, or keep), not the particle shader.

### Gold Hat / extract

Does the loop respect time and attention? Dark patterns (fake urgency, mislabeled odds, cannot-quit purchase, punish-to-monetize) are critical even if the verb feels good. Hand the full monetization model to `monetization-ethics` (stub); still name the extract you can see.

## Severity

| Rank | Meaning | Example |
|------|---------|---------|
| Critical | Blocks the job, soft-locks, or extracts | Jump input dropped; paywall mid-fail; death with no cue and no retry |
| High | Player will misread the rule or hesitate | Two primary verbs; silent deny; unfair first hit |
| Medium | Loop works but teaches slowly or drifts | Juice stacked on one hit; reward after the decision window |
| Low | Polish | Extra land dust; HUD noun does not match the verb name |

If unsure between two ranks, pick the higher and say why.

## Worked example — silent jump deny

Job: platformer jump. Success: leave the ledge and land. Fail: miss the jump or press too late.

```
pressed jump:
    if grounded: apply jump
    else: # nothing
land: # nothing
```

Critique (abridged):

```markdown
## Job
New player crosses a two-gap tutorial. Primary verb: jump.

## Findings
1. **Critical — teaching fails.** Air press does nothing. Player cannot tell late-press from a dead binding.
   Remediation: reject cue (SFX + tiny squash) whenever jump is denied; keep coyote/buffer numbers for `input-feel` (stub).
2. **High — feedback.** Land is silent, so the next jump starts without a closed loop.
   Remediation: one land confirmation (dust or thud), then stop.
3. **High — loop integrity (unverified).** If this runs on a variable display delta, height will change with FPS. Measure or read the step. If variable, fix the tick via `game-loop-feel`.
4. **Medium — juice vs noise.** Do not add landing camera shake until the reject cue exists; shake would hide the real bug.

## Strengths
The verb is a single button. The gap is visible.

## Fixes now
1. Denied-jump cue.
2. Land confirmation.
3. Confirm fixed-step gravity; do not add particles yet.

## Leftovers
Buffer / coyote windows → `input-feel` (stub).
Stranger play → `playtest-checklist`.
Engine node wiring → `godot-patterns` / `unity-patterns` (stubs).
```

That is a critique: locations, severity, remediations, leftovers. Not a `/10` feel card.

## Output shape

```markdown
## Job
[who / verb or encounter / success / fail]

## Strengths
- [only real ones]

## Findings (severity-ranked)
1. **[Critical|High|Medium|Low] — [dimension].** [where] [what] [why]
   Remediation: [exact change]
2. …

## Fixes now
1. …
2. …
3. …

## Leftovers
- [skill] — [what you did not pretend to finish]
```

## Quality bar

A pass is done when every finding is specific, ranked, and remediable, and the *why* is a rule the next room can reuse. Refuse vibe-only notes ("make it juicier", "more game-feel") — translate them through `game-loop-feel` or drop them. Refuse engine lectures that do not change the player's read.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../../README.md).
