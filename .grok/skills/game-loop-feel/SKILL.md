---
name: game-loop-feel
description: Teach the game loop and player-verb feel. Use when movement, attacks, or feedback feel late, mushy, or silent. Engine-agnostic.
---

# Game Loop Feel

Teach the loop that makes a verb feel like a game: **input → simulate → present → feedback**. Timing and juice are measurements, not taste.

Gold Hat: name the player verb first, then teach the rule while you fix the frame. A polish dump that hides a late input or a silent fail extracts attention; a named latency and a fail state that teaches empowers the next verb.

This skill is Godot / Unity / Unreal / web agnostic. Do not start in `godot-patterns` or `unity-patterns`. Those remain stubs. Hand engine wiring there only after the verb, the tick, and the feedback are named.

## When to use

- A control "feels off" and you need a named cause (late, floaty, silent, noisy)
- Designing or reviewing one player verb (jump, dash, shoot, interact)
- Translating "add juice" into one purpose per effect
- Teaching how the game loop differs from a request/response web app

Use `game-design-critique` after the verb is named if you need a severity-ranked pass. Use `input-feel` (still a stub) for buffer / coyote / deadzone / remap detail. Use `playtest-checklist` to test the verb with a real player. Do not invent those skills' missing depth.

## Operating steps

1. **Name the verb.** Who presses what, what must happen, what success and fail look like. Stop if you cannot name it. Ask.
2. **Name the tick.** Variable render vs fixed simulate. Say the target frame time (16.6 ms at 60 Hz, 8.3 ms at 120 Hz) and whether physics uses a fixed step.
3. **Measure response.** Press → first visible or audible change. If you did not measure, mark **unverified** and say how to measure (frame log, input timestamp vs pose change).
4. **Walk the loop below.** Record only findings you can point at (file/system + current behavior + check).
5. **Propose three concrete fixes** (or fewer if the verb is already clean). Each fix names the check it serves.
6. **Teach one sentence.** Why this change, reusable on the next verb.

Guessing "it needs more juice" without a verb or a tick is extraction.

## Loop (measurable)

```
input  →  simulate (fixed step when physics/gameplay must be stable)
       →  present (render / audio / haptics interpolated to the display)
       →  feedback (the player reads the result and presses again)
```

A web handler returns once. A game loop never stops. If simulate and present share one variable delta, feel and collisions become frame-rate dependent. That is a defect, not a style.

### Response

The verb must start on the press, not on the next animation or the next network tick unless you named that delay.

| Check | Pass | Fail |
|-------|------|------|
| First response | Visible or audible change within **1–2 frames** of the press (unverified if not timed) | Press waits on a long wind-up with no start cue |
| Same tick | Input sampled before simulate on that step | Input applied one full step late with no buffer |
| Target | You stated 30 / 60 / 120 Hz and the budget in ms | "Smooth" with no number |

### Simulate vs present

| Check | Pass | Fail |
|-------|------|------|
| Gameplay step | Fixed delta for movement, hit detection, resources | Variable `delta` drives jumps, guns, or economy |
| Spiral of death | Accumulator capped (e.g. 0.25 s) so a hitch does not cascade | A spike catches up by simulating seconds of game time in one frame |
| Presentation | Render interpolates or snaps on purpose | Physics on the display clock; display on the physics clock |

### Juice without noise

Juice is one purpose: confirm the verb, sell impact, or keep orientation. Decoration that delays the next press is noise.

| Check | Pass | Fail |
|-------|------|------|
| Purpose | Each shake / flash / freeze / rumble names a job | Three overlapping hits of the same event |
| Duration | Accent is short (often 2–8 frames for freeze/flash) | Hit-stop or fade blocks the next input |
| Restraint | Heavy juice is rare; light juice is routine | Constant camera shake; the world never rests |

Start with impact freeze + a short camera punch if you must pick one pair. Add particles after the timing is honest.

### Fail states that teach

A miss, a death, a blocked dash must say **what happened** and **what to try**. Silent failure feels like a broken button.

| Check | Pass | Fail |
|-------|------|------|
| Readable cause | Player can name why they failed after one attempt | "I jumped" and the body did nothing |
| Next action | I-frames, recovery, or prompt points at a retry | Soft-lock, invisible wall, or death with no cue |
| Honesty | The rule that killed them is the rule they can practice | Random extra hit after the telegraph ended |

### Feedback loop

The player is part of the loop. If they cannot read the result, they cannot aim the next press.

Look for: no land dust after a jump they thought connected, no reject spark on a blocked attack, HUD that updates a beat after the body.

## Problem → check → fix

| Complaint | Check | First fix |
|-----------|-------|-----------|
| "Jump / fire is late" | Response | Apply the verb on the press frame; add a 1–2 frame start cue if a wind-up stays |
| "Feels different at 30 vs 60" | Simulate vs present | Fixed gameplay step; interpolate only presentation |
| "Stiff / dead" | Juice without noise | One impact freeze + one punch; then stop |
| "I thought I pressed it" | Fail states that teach | Reject VFX/SFX when the verb is denied |
| "Too much going on" | Juice without noise | Cut overlapping effects; keep the one that confirms the verb |

## Worked example — jump

Job: 2D or 3D character jumps. Primary verb: jump. Success: leave ground and land where aimed. Fail: miss the ledge or get no jump.

Weak (language-agnostic):

```
on pressed(jump):
    if grounded: velocity.y = jump_speed
# render and physics share whatever delta the display sent
# no land cue, no denied-jump cue
```

Critique of the loop (not a score):

- **Response (unverified):** If `pressed` is sampled after simulate, the jump starts next step. Measure press time vs first `velocity.y` change.
- **Simulate vs present:** Jump height scales with frame time if gravity uses a variable delta.
- **Fail that teaches:** Press while not grounded does nothing. The player learns "the button is broken," not "I was late."
- **Juice:** Land is silent. The next jump has no confirmation the last one ended.

Stronger (principle-tagged, still engine-agnostic):

```
fixed_step(dt = 1/60, max_frame = 0.25):
    read jump_pressed
    if jump_pressed and (grounded or coyote_remaining):
        apply jump impulse          # response: same step
        play start cue              # 1-frame squash or SFX
    elif jump_pressed and not grounded:
        play reject cue             # fail teaches: not a dead button
        remember press for buffer   # hand detail to input-feel (stub)
    integrate gravity with dt
    move body
present(alpha):
    interpolate pose for display
    if just_landed: land dust + short punch   # juice, one purpose
```

Three concrete fixes if you only have the weak loop: (1) fixed step for the jump and gravity, (2) reject cue when jump is denied, (3) land confirmation — then run `game-design-critique` and leave buffer/coyote numbers to `input-feel` (stub).

## Output shape

```markdown
## Verb
[who / input / success / fail]

## Tick
[Hz and ms] — [fixed simulate? yes/no] — [measured or unverified]

## Findings
- [check] — [where] — [current] → [needed]

## Fixes (≤3)
1. [change] — serves [check]
2. …
3. …

## Teach
[one reusable sentence]

## Leftovers
- [skill] — [what you did not pretend to finish]
```

If nothing is wrong, say so. Empty findings are allowed. Invented juice is not.

## Quality bar

A pass names the verb, states the tick, and refuses vibe-only notes ("more juicy", "snappier") unless they become a check + a change. Do not claim a millisecond figure you did not measure.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../../README.md).
