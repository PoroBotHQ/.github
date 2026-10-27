# PoroBotHQ

We build StarCraft II bots and tools to understand their decisions. Our current project is **porotoss**, a playful nod to Poroburu and Protoss. We aim for **[AI Arena](https://aiarena.net/) Division 1** with Protoss, Terran, Zerg and Random, alongside race-bound cheese profiles. The first cheese profile to reach Division 1 meets that part of the goal; the remaining cheese entries are tracked separately and do not all gate the first release.

Our stack uses **F# policies and .NET 10**. We compare modeled predictions with actual matches, keeping replays and traces to guide the next improvement.

Poroburu coordinates the project, with a playful coordinator-cat and process-enjoyer persona 🐈. In conversation, Poro is welcome; on GitHub, **porointern** is the separate machine account used by coding agents. We enjoy making the next experiment easier to run and its results easier to understand.

## What we are building

A bot is a continuous loop: observe the game, maintain a useful model, choose a
plan and issue legal actions. We separate the reusable SC2 engine from concrete
bot policy through typed contracts. The same strategy libraries can be composed
into the playing bot and the trainer, so experiments exercise the code we intend
to use in matches.

The strategy work includes production construction and simulation, terrain
analysis, opponent belief, force assessment, mission planning and production
logistics. We develop these as bounded models with explicit assumptions and
uncertainty. Deterministic examples and seeded property checks help test the
models; matches and replays show where their assumptions need improvement.

**A reusable F# engine is being prepared for a future public release.**
`porotoss-engine` provides neutral game facts and actions, policy/session
contracts, a client and a starter. Its source is currently private. Public
release remains future work, with disclosure, licensing and standalone-use
criteria to meet before a public source link is available.

## Architecture

`porotoss` integrates the components through Git submodules and compatible typed
project references. Each functional boundary owns its implementation and models.

| Component | Responsibility |
| --- | --- |
| `porotoss-bot` | Concrete policies, service composition, host, configuration and native integration. |
| `porotoss-engine` | Shared SC2 facts/actions, policy/session contracts, client and starter; currently private. |
| `porotoss-platform` | Infrastructure, executor administration and currently selected workload execution. |
| `porotoss-bot/trainer` | Current training source: experiment contracts, controller and training adapters. |
| `porotoss-bot/wargames` | Current wargames source: scenario rules, evaluators, workers and controls. |
| `porotoss-strategy` | Separate planner, terrain, belief, force, mission, doctrine and logistics libraries. |
| `porotoss-replays` | Standalone replay domain/processing preparation; current consumers remain bot-owned. |
| `porotoss-workloads` | Standalone execution-framework preparation; current consumers remain platform-selected until coordinated cutover. |

Training and wargames were imported into `porotoss-bot` on October 19, 2026,
and cut over on October 20. Their former repositories retain archived history.
Development source is currently private; these names describe source boundaries
and preparation, without claiming public availability or consumer adoption.

## What we want to understand

- **Economy:** resources collected, worker efficiency and production delays.
- **Combat:** resources lost through destroyed units, positioning, technology and upgrades.
- **Decisions:** what the bot intended, what it commanded and what happened.
- **The match over time:** traces, maps and visual analysis that reveal patterns.

Changes are reviewed in pull requests and tied to issues. Offline checks establish
their scoped behavior; actual matches supply gameplay evidence. A completed loss
is useful when it shows us what to improve.

![Poro in blue space-marine armor, with an orange visor reflection and a cyan HUD.](https://raw.githubusercontent.com/PoroBotHQ/.github/main/assets/poro-space-marine.webp)

*“Hell, it's about time.”*
