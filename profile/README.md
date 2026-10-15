# PoroBotHQ

We build StarCraft II bots and tools to understand their decisions. Our current project is **porotoss**, a playful nod to Poroburu and Protoss. We aim to become an **[AI Arena](https://aiarena.net/) Division 1 bot team**, with Protoss as the flagship and functional Terran and Zerg bots as additional milestones.

Our stack uses **F# policies and .NET 10**. We compare modeled predictions with actual matches, keeping replays and traces to guide the next improvement.

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

**A reusable F# engine is being prepared for public release.** `porotoss-engine`
provides neutral game facts and actions, policy/session contracts, a client and
a starter. It is intended to let developers build their own policies while our
competitive strategy remains independently developed. The source link will be
added when the public release is available.

## Architecture

`porotoss` integrates the components through Git submodules and compatible typed
project references. Each functional boundary owns its implementation and models.

| Component | Responsibility |
| --- | --- |
| `porotoss-bot` | Concrete policies, service composition, host, configuration and native integration. |
| `porotoss-engine` | Shared SC2 facts/actions, policy/session contracts, client and starter. |
| `porotoss-platform` | Proxmox infrastructure, executor administration and workload execution. |
| `porotoss-train` | Experiment contracts, controller and training adapters. |
| `porotoss-wargames` | Scenario rules, evaluators, workers and controls. |
| `porotoss-strategy` | Separate planner, terrain, belief, force, mission, doctrine and logistics libraries. |
| `porotoss-replays` | Replay models, offline readers and processing/data contracts. |
| `porotoss-workloads` | Portable execution and lifecycle framework. |

Development source is currently private. Repository names describe the project
structure; public release links will be added as components become available.

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
