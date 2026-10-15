# PoroBotHQ

![Poro in blue space-marine armor, with an orange visor reflection and a cyan HUD.](https://raw.githubusercontent.com/PoroBotHQ/.github/main/assets/poro-space-marine.png)

We build StarCraft II bots and tools to understand their decisions. Our current project is **porotoss**, a playful nod to Poroburu and Protoss. We aim to become an **[AI Arena](https://aiarena.net/) Division 1 bot team**, with Protoss as the flagship and functional Terran and Zerg bots as additional milestones.

Our stack uses **F# policies and .NET 10**. We compare modeled predictions with actual matches, keeping replays and traces to guide the next improvement.

## Project structure

Our development repositories are private. This map describes the integrated
`porotoss` workspace; source access is limited to collaborators. Git submodules
group source by functional purpose and select compatible component versions.

| Functional purpose | Repository | Responsibility |
| --- | --- | --- |
| Concrete bot runtime | `porotoss-bot` | Bot policies, service composition, host, configuration and native integration. |
| Bot engine core | `porotoss-engine` | Shared SC2 facts/actions, policy/session contracts, client and starter. |
| Proxmox platform | `porotoss-platform` | Infrastructure, executor administration and workload execution. |
| Trainer | `porotoss-train` | Experiment contracts, controller and training adapters. |
| Wargames | `porotoss-wargames` | Scenario rules, evaluators, workers and controls. |
| Strategy libraries | `porotoss-strategy` | Separate typed planner, terrain, belief, force, mission, doctrine and production-logistics libraries. |
| Replay libraries | `porotoss-replays` | Replay models, offline readers and processing/data contracts. |
| Workload libraries | `porotoss-workloads` | Portable execution and lifecycle framework. |

The runtime and trainer compose the same library projects through typed
contracts. Each component owns its implementation and domain models.

## What we want to understand

- **Economy:** resources collected, worker efficiency and production delays.
- **Combat:** resources lost through destroyed units, positioning, technology and upgrades.
- **Decisions:** what the bot intended, what it commanded and what happened.
- **The match over time:** traces, maps and visual analysis that reveal patterns.

Changes are reviewed in pull requests and tied to issues. Offline checks establish their scoped behavior; actual matches supply gameplay evidence. A completed loss is useful when it shows us what to improve.
