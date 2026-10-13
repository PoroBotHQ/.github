# PoroBotHQ

![Poro in blue space-marine armor, with an orange visor reflection and a cyan HUD.](../assets/poro-space-marine.png)

We build StarCraft II bots and tools to understand their decisions. Our current project is **porotoss**, a playful nod to Poroburu and Protoss. We aim to become an **[AI Arena](https://aiarena.net/) Division 1 bot team**, with Protoss as the flagship and functional Terran and Zerg bots as additional milestones.

Our stack uses **F# policies and .NET 10**. We compare modeled predictions with actual matches, keeping replays and traces to guide the next improvement.

## Projects

| Name | Purpose |
| --- | --- |
| [porotoss](https://github.com/PoroBotHQ/porotoss) | Project coordination, component selection and development guidance. |
| [porotoss-bot](https://github.com/PoroBotHQ/porotoss-bot) | Proprietary bot policies, game integration, experiments and match analysis. |
| [porotoss-engine](https://github.com/PoroBotHQ/porotoss-engine) | Reusable factual SC2 contracts, optional native client and a basic starter. |
| [porotoss-platform](https://github.com/PoroBotHQ/porotoss-platform) | Infrastructure and the framework for running and retaining bounded workloads. |

These development repositories are currently private; their links require collaborator access. The reusable engine has a separate public-release path.

## Component names

- **porotoss-workloads** runs supported jobs and collects their results.
- **porotoss-experiments** plans, evaluates and resumes experiments, with micro, macro and scripting extensions.
- **porotoss-replays** captures and processes replays into attributable data.
- **porotoss-planner** constructs and simulates production paths to inform future strategy decisions.

These components live in the repositories above. Collaborators can use the [product and term glossary](https://github.com/PoroBotHQ/porotoss/blob/main/docs/glossary.md) to find their code names and boundaries.

## What we want to understand

- **Economy:** resources collected, worker efficiency and production delays.
- **Combat:** resources lost through destroyed units, positioning, technology and upgrades.
- **Decisions:** what the bot intended, what it commanded and what happened.
- **The match over time:** traces, maps and visual analysis that reveal patterns.

Changes are reviewed in pull requests and tied to issues. Offline checks establish their scoped behavior; actual matches supply gameplay evidence. A completed loss is useful when it shows us what to improve.
