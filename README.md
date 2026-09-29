# Everwrit Online

> *"Every deed is written."*

**Everwrit Online** (working title) is a 3D fantasy MMORPG in the style of World of Warcraft, presented like a **LitRPG novel**. It has tab-target combat, dungeons, raids, guilds, and an auction house. On top of that sits a System that talks to you, stat sheets you can open at any time, skills that grow and evolve through use, titles for what you do, server-wide World First announcements, and a journal that writes up each play session as a chapter of your own LitRPG book.

- **Engine:** Unreal Engine 5 (client and dedicated zone servers)
- **Backend:** Nakama + PostgreSQL
- **AI:** a hybrid "AI Narrator" built on Claude. The server applies every rule; the AI only narrates.
- **Team:** solo / hobby (1–3 people), so the scope is a deliberately small MMO

## Status

**Phase 0: Pre-production.** This repo holds the design and planning docs. The Unreal project, backend, and services will be added under the layout in [architecture](docs/tech/architecture.md#future-repository-layout).

## Design pillars

1. **Your story is written.** Anything interesting you do gets recorded, named, and told back to you by the Chronicle.
2. **Growth you can feel.** You can see numbers go up often: levels, free attribute points, skill Proficiency, evolutions, titles.
3. **Classic MMO feel.** Tab-target combat, the tank/healer/DPS trinity, dungeons and raids. The LitRPG layer sits on top of these and does not replace them.
4. **Discovery rewards attention.** Hidden quests, secret Class Paths, and Unique items go to players who look closely.
5. **Small world, deep systems.** One continent and 30 levels, built to be polished and expandable rather than huge.

## Documentation

| Area | Doc |
|---|---|
| Vision | [00 – Vision](docs/00-vision.md) |
| Names & terms | [Glossary](docs/glossary.md) |
| **Game design** | |
| World & lore | [01 – World and Lore](docs/gdd/01-world-and-lore.md) |
| Races | [02 – Races](docs/gdd/02-races.md) |
| Classes | [03 – Classes](docs/gdd/03-classes.md) |
| Progression | [04 – Progression](docs/gdd/04-progression.md) |
| Combat | [05 – Combat](docs/gdd/05-combat.md) |
| Zones & content | [06 – World and Content](docs/gdd/06-world-and-content.md) |
| Items & economy | [07 – Items, Economy, Crafting](docs/gdd/07-items-economy-crafting.md) |
| Social & endgame | [08 – Social and Endgame](docs/gdd/08-social-and-endgame.md) |
| LitRPG presentation | [09 – LitRPG Presentation](docs/gdd/09-litrpg-presentation.md) |
| **Technical** | |
| Architecture | [Architecture](docs/tech/architecture.md) |
| AI Narrator | [AI Narrator](docs/tech/ai-narrator.md) |
| Stack & tooling | [Stack and Tooling](docs/tech/stack-and-tooling.md) |
| **Production** | |
| Roadmap | [Roadmap](docs/production/roadmap.md) |
| Scope & risks | [Scope and Risks](docs/production/scope-and-risks.md) |
| Open questions | [Open Questions](docs/production/open-questions.md) |
