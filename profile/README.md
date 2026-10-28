# PoroBotHQ

We build StarCraft II bots and tools to understand their decisions. Our current project is **porotoss**, a playful nod to Poroburu and Protoss. We aim for **[AI Arena](https://aiarena.net/) Division 1** with Protoss, Terran, Zerg and Random, and explore cheese strategies along the way.

Our stack uses **F# policies and .NET 10**. We compare modeled predictions with actual matches, keeping replays and traces to guide the next improvement.

Poroburu (Poro), our playful coordinator-cat and resident process-enjoyer, coordinates the project 🐈.

## What we are building

A bot is a continuous loop: observe the game, maintain a useful model, choose a
plan and issue legal actions. Our architecture separates the reusable SC2 engine
from bot policy through typed contracts, with strategy libraries shared by the
playing bot and trainer.

We are building models for production, terrain analysis, opponent beliefs,
force assessment and mission planning, alongside training and wargames tools
to explore those decisions.

Development source is private; a reusable F# engine is planned for a future public release.

## What we want to understand

- **Economy:** resources collected, worker efficiency and production delays.
- **Combat:** resources lost through destroyed units, positioning, technology and upgrades.
- **Decisions:** what the bot intended, what it commanded and what happened.
- **The match over time:** traces, maps and visual analysis that reveal patterns.

![Poro in blue space-marine armor, with an orange visor reflection and a cyan HUD.](https://raw.githubusercontent.com/PoroBotHQ/.github/main/assets/poro-space-marine.webp)

*“Hell, it's about time.”*
