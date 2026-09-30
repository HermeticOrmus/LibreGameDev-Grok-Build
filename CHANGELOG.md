# Changelog

## [1.0.0] - 2026-09-30

The Grok edition: the melted skills install as a Grok plugin, and the same marketplace installs every game plugin of claude-code-game-development, pinned to one commit of the pack. The [kintsugi ledger](./LEDGER.md) records each v0 crack and its seal.

### Added

- `plugins/libre-gamedev-grok/`, the Grok-native plugin (`.grok-plugin/plugin.json`, version 1.0.0) with the three melted skills: `game-loop-feel`, `game-design-critique`, `playtest-checklist`.
- `.grok-plugin/marketplace.json` (`libre-gamedev-grok`): the Grok-native plugin plus the 22 game plugins of claude-code-game-development (its `gaming` category: 20 game plugins, `libre-gamedev-hooks`, `game-development`) as remote entries pinned to pack commit `6959bed6b74ac0e2436089ca1748f78632938bf7`.
- `scripts/pin-pack.sh`: re-pins the pack entries to the pack's `main`, adds new game plugins, drops removed ones, and prints the diff; `--check` fails on an unreachable SHA or a changed plugin list.
- `.github/workflows/validate.yml`: `grok plugin validate`, the dogfood copy check, the doc install-line check, the pin check, and an install of every entry into a clean `GROK_HOME`.
- Issue forms for feedback, routing misses and plugin proposals, with the `feedback`, `routing-miss` and `plugin-proposal` labels.
- [LEDGER.md](./LEDGER.md), [stubs/README.md](./stubs/README.md), "Ways to contribute" in [CONTRIBUTING.md](./CONTRIBUTING.md), and a README acknowledgment for `game-development` (wshobson/agents, MIT).

### Changed

- Install is `grok plugin marketplace add HermeticOrmus/LibreGameDev-Grok-Build` then `grok plugin install libre-gamedev-grok@libre-gamedev-grok --trust`. The folder copy still works from the new path, `plugins/libre-gamedev-grok/skills/*`.
- Melted skills moved from `skills/` to `plugins/libre-gamedev-grok/skills/`; the six stubs moved to `stubs/`. The `.grok/skills/` dogfood copy stays and matches both.
- The v0 bundle stub `.grok/plugins/libregamedev-core/` moved to `stubs/libregamedev-core/`, marked superseded.
- Upstream links point at claude-code-game-development, where the game plugins of the archived LibreGameDev-Claude-Code continue.
- README gains the family header, the marketplace install and the real Depth table; QUICK_START, AGENTS.md, DEPTH_MATRIX and MELT_RULES follow the new paths.

### Fixed

- Stubs no longer install as if they were playbooks: their descriptions start "Stub, not a playbook." and name the pack plugin that holds the real depth.
- The v0 plugin folder installed as an unversioned plugin with no skills; the new plugin validates with its three skills.
- The melted skills linked `GOLD_HAT.md` and `README.md` with `../../` paths that did not resolve from the `.grok/skills/` copy; they now use absolute links that resolve from every install path.

### Upgrading from v0

- If you copied `skills/*` into a project or `~/.grok/skills/`, remove the six stub folders from that copy, or switch to the marketplace install so `grok plugin update` brings changes.
- Paths that pointed at `skills/<name>` now point at `plugins/libre-gamedev-grok/skills/<name>` (melted) or `stubs/<name>` (stubs).

## [0.1.0] — 2026-09-20

### Changed

- Melted `skills/game-loop-feel/SKILL.md` (game-loop teach) and `skills/playtest-checklist/SKILL.md`.
- Added melted `skills/game-design-critique/SKILL.md` (Godot/Unity-agnostic design critique). Dogfood copies under `.grok/skills/` match.
- Rewrote [QUICK_START.md](./QUICK_START.md) for a clean-machine install (<5 min) with paths that exist in this repo.
- Updated [docs/DEPTH_MATRIX.md](./docs/DEPTH_MATRIX.md): 3 melted, 6 stub skills, 1 stub agent. No Claude inventory counts.
- Suite footers on README, QUICK_START, and AGENTS.md now link Reality OS plus the sibling Libre*-Grok-Build packs.
- README Depth / quality points at the shared L0–L5 ladder. This pass targets L3–L4 hygiene, not L5.

## [0.0.1] — 2026-09-19

### Added

- Public scaffold for LibreGameDev-Grok-Build (v0 stubs).
- Stub SKILL.md for first skills + suite orchestrator agent.
- README, LICENSE (MIT), GOLD_HAT, QUICK_START, CONTRIBUTING, SECURITY.
- Depth matrix + melt rules docs.

### Notes

- Honest stubs — not fake upstream depth counts. Melt next.
