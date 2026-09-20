---
name: playtest-checklist
description: Structured playtest plan — one-sentence goal, protocol, metrics, notes, triage. Use before putting a stranger on a build.
---

# Playtest Checklist

Turn a vague "we should playtest" into one session a stranger can sit through. Observation is data. Coaching is contamination.

Gold Hat: testers are not content. They keep their time, their recordings, and their right to stop. Do not instrument identity, contacts, or hidden always-on capture. Teach the designer how to see; do not extract a highlight reel.

Engine-agnostic. This skill does not ship a heatmap shader or an A/B framework. Those are leftovers. A session with a named goal beats a dashboard with no question.

## When to use

- Before the first external play (tutorial + first encounter)
- After `game-design-critique` when you need a human, not another pass on paper
- When someone asks for "metrics" but cannot name the decision the numbers will change

Do not use this skill as a live-ops telemetry platform, a full funnel product, or a replacement for `game-loop-feel` / `game-design-critique`. Those two are melted; use them first if the verb is still unnamed.

## Operating steps

1. **One-sentence goal.** The question the session must answer. If you have three questions, you have three sessions or you will answer none.
2. **Name the build and the task.** Version or commit. What the tester is asked to do. What you will *not* explain.
3. **Pick 3–5 metrics** that can falsify the goal. Drop the rest.
4. **Write the protocol** (pre / during / post) so a second observer could run it.
5. **Triage after.** Each note becomes fix now, later, or discard — with a reason.

If the only testers are teammates who already know the trick, say so. That session can smoke-test crashes. It cannot validate teaching.

## Session goal

Write one sentence you could be wrong about.

| Goal | Not a goal |
|------|------------|
| Do first-time players discover the dash before the second gap? | "See if it's fun" |
| Can they finish room 1 in under 4 minutes with ≤2 hint cards? | "Get feedback" |
| Where do they quit in the first 10 minutes? | "Collect all the data" |

Success criteria are counts or times, not vibes. Example: 4 of 5 testers complete the tutorial without a spoken hint.

## Protocol

**Recruitment.** Prefer strangers in the target audience. Friends and co-developers are systematically kind and already trained. Nielsen-style: about 5 testers expose most *teaching* issues; do not claim a percentage you did not measure.

**Length.** 15 minutes is enough for one verb or one room. 45–90 minutes for a first-level pass. Past 90 minutes, fatigue reads as design failure.

**Pre (about 5 minutes)**

- "Play as you normally would. I am watching the game, not testing you."
- "Talk through what you notice if you can."
- "I will not answer gameplay questions. I will fix a crash or a broken control."

**During**

Do not coach. The stuck moment *is* the finding. If you speak, log that you contaminated the sample.

Note line:

```
[mm:ss] [action] [visible affect] [quote]
```

Example: `[04:32] miss jump 3rd time [frustration] "why does this keep happening"`

**Post (about 10–15 minutes)**

Open questions, not leading ones:

1. What was that like, in your words?
2. What was the most confusing moment?
3. What did you want to do that you could not figure out?
4. What would you try first if you sat down again tomorrow?

Do not ask "Did you enjoy the combat?" if you need to know whether combat taught its rules.

## Metrics (only what the goal needs)

Pick from this menu. Do not implement all of it.

| Metric | Use when the goal is… | Enough detail |
|--------|----------------------|---------------|
| Completes / attempts | Teaching, difficulty | Count + where they stopped |
| Deaths or fails per obstacle | One unfair or unreadable beat | Location label, not a full heatmap product |
| Time in zone | Pacing, lost players | Enter / exit timestamps |
| Mechanic first-use | Discovery | First time + whether it was prompted |
| Hint cards you were forced to give | Clarity | Each hint is a contamination + a finding |
| Quit reason | Retention of the *session*, not live-ops | Their words, then your code |

If you log events to disk, use a local file the tester knows about. No hidden identity. No example payloads with real account IDs.

## Note template

```markdown
# Playtest
Game / build: [name + version or commit]
Date: [ISO date]
Tester: [role — e.g. "stranger, first game in genre"] — not an email
Goal: [one sentence]
Task: [what they were asked to do]

## Protocol deviations
- [coached? crashed? skipped?]

## Timeline
- [mm:ss] …

## Quotes
- "…"

## Metrics
- [name]: [value] — [measured / inferred]

## Findings → triage
| Note | Severity | Action |
|------|----------|--------|
| … | Critical/High/Medium/Low | Fix now / later / discard |
```

Severity matches `game-design-critique`: critical blocks the job; high mis-teaches; medium slows the lesson; low is polish.

## After-session triage

1. Restate the goal. Did the session answer it? If not, the plan failed — say so.
2. Promote notes that change the next build. Demote taste ("I would use a different color") unless it hid a verb.
3. Cap **fix now** at one sitting. The rest is a backlog, not a personality test.
4. Schedule the next session only after those fixes exist. Re-testing the same broken verb is extraction of tester time.

## Worked example — 15-minute dash discovery

Goal: do first-time players use dash before the second gap?

```markdown
# Playtest
Game / build: proto-dash 0.3 (commit unverified in this example)
Date: 2026-09-20
Tester: stranger, plays platformers
Goal: Do first-time players use dash before the second gap?
Task: "Get to the flag. I will not explain controls."

## Protocol deviations
- None.

## Timeline
- [00:40] walks, jumps first gap [neutral] —
- [01:15] stares at double gap [confused] "I can't jump that"
- [02:10] dies twice on the lip [frustration] —
- [03:00] never presses the dash bind

## Quotes
- "I can't jump that"

## Metrics
- Dash first-use: never — measured (observer)
- Deaths at gap 2: 2 — measured
- Hint cards: 0

## Findings → triage
| Note | Severity | Action |
|------|----------|--------|
| Dash never cued before the gap that requires it | High | Fix now: teach dash on a safe gap; reject/fail cue if they only jump |
| Jump looks like the only verb | High | Fix now: HUD or prompt after first jump, not a paragraph |
| Two deaths is not yet "too hard" | Low | Discard as difficulty until teaching exists |

## Leftovers
Death positions over many sessions → not this skill (no heatmap product here).
Input buffer if they *did* press dash and it dropped → `input-feel` (stub).
```

## Output shape

```markdown
## Goal
[one sentence]

## Build and task
[version] — [what they do] — [what you will not explain]

## Protocol
[pre / during / post in bullets]

## Metrics (3–5)
- [name] — [why it can falsify the goal]

## Notes template
[ready to print or paste]

## After
[how you will triage]

## Leftovers
- [what this session will not pretend to be]
```

## Quality bar

A pass has one goal, a protocol that forbids coaching, and metrics that could prove you wrong. Refuse 1–10 enjoyment scores as the only output. Refuse shipping heatmaps, A/B harnesses, or "80% of users" claims you did not count.

## Suite

Doctrine: [grok-build-reality-os](https://github.com/HermeticOrmus/grok-build-reality-os). Gold Hat: [GOLD_HAT.md](../../GOLD_HAT.md). Sibling Libre*-Grok-Build packs: [README suite footer](../../README.md).
