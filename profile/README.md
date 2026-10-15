# PoroBotHQ

![Poro in blue space-marine armor, with an orange visor reflection and a cyan HUD.](https://raw.githubusercontent.com/PoroBotHQ/.github/main/assets/poro-space-marine.png)

We build StarCraft II bots and tools to understand their decisions. Our current project is **porotoss**, a playful nod to Poroburu and Protoss. We aim to become an **[AI Arena](https://aiarena.net/) Division 1 bot team**, with Protoss as the flagship and functional Terran and Zerg bots as additional milestones.

Our stack uses **F# policies and .NET 10**. We compare modeled predictions with actual matches, keeping replays and traces to guide the next improvement.

## Repository layout

[porotoss](https://github.com/PoroBotHQ/porotoss) is the integrated development
workspace. Its Git submodules group source by functional purpose and pin reviewed
component versions. Typed project references preserve contracts between those
components while allowing the runtime and trainer to compose the same libraries.

| Functional purpose | Repository | Responsibility |
| --- | --- | --- |
| Concrete bot runtime | [porotoss-bot](https://github.com/PoroBotHQ/porotoss-bot) | Concrete policies, selected service factory, host, configuration, models and native integration. |
| Bot engine core | [porotoss-engine](https://github.com/PoroBotHQ/porotoss-engine) | Neutral SC2 facts/actions, policy/session contracts, optional native client and starter. |
| Proxmox platform | [porotoss-platform](https://github.com/PoroBotHQ/porotoss-platform) | Infrastructure, executor administration and currently selected workload execution modules. |
| Trainer | [porotoss-train](https://github.com/PoroBotHQ/porotoss-train) | Experiment contracts, controller, training adapters and proof tools. |
| Wargames | [porotoss-wargames](https://github.com/PoroBotHQ/porotoss-wargames) | Scenario rules/evaluators, native workers, normalization and scenario controls. |
| Strategy libraries | [porotoss-strategy](https://github.com/PoroBotHQ/porotoss-strategy) | Separate typed planner, terrain, opponent-belief, force, mission, doctrine-contract and production-logistics libraries. |
| Replay libraries | [porotoss-replays](https://github.com/PoroBotHQ/porotoss-replays) | Prepared replay domain, offline readers and processing/data contracts. |
| Workload libraries | [porotoss-workloads](https://github.com/PoroBotHQ/porotoss-workloads) | Prepared portable execution/lifecycle framework for supported jobs and retained results. |

These development repositories are currently private; links require collaborator
access. The reusable engine has a separate public-release path.

Shared typed models stay with their semantic owner: engine facts, strategy/planner
models, train experiment contracts, replay domain/data contracts and workload
execution contracts. The `porotoss-train` product preserves existing
`Porotoss.Experiments` code and wire identities. Collaborators can consult the
[boundary map](https://github.com/PoroBotHQ/porotoss/blob/main/docs/repository-boundaries.md)
and [glossary](https://github.com/PoroBotHQ/porotoss/blob/main/docs/glossary.md) for
current ownership and adoption details.

## What we want to understand

- **Economy:** resources collected, worker efficiency and production delays.
- **Combat:** resources lost through destroyed units, positioning, technology and upgrades.
- **Decisions:** what the bot intended, what it commanded and what happened.
- **The match over time:** traces, maps and visual analysis that reveal patterns.

Changes are reviewed in pull requests and tied to issues. Offline checks establish their scoped behavior; actual matches supply gameplay evidence. A completed loss is useful when it shows us what to improve.
