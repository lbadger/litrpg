# Stack and Tooling

## Stack summary

| Layer | Choice | Why |
|---|---|---|
| Engine | **Unreal Engine 5** (the latest stable 5.x at P0 start, pinned for each phase) | Best 3D quality, a mature dedicated-server model, and GAS for MMO-style abilities |
| Engine build | **Source build** from Epic's GitHub | Required to build **dedicated server** targets |
| Gameplay framework | Gameplay Ability System, Enhanced Input, CommonUI, StateTree, EQS, World Partition | Built-in systems fit WoW-like needs, so we write less custom code |
| Client/server code | C++ for systems, Blueprints for content and UI glue | GAS and networking belong in C++; iteration speed comes from Blueprints |
| Backend | **Nakama** (self-hosted, open source) with **TypeScript** runtime modules | Auth, chat, parties, groups, matchmaker, storage, and an official Unreal client SDK |
| Database | **PostgreSQL** | Nakama-supported, reliable, and handles JSONB for character documents |
| AI Narrator | Node.js + TypeScript + `@anthropic-ai/sdk` | Shares types with backend modules; official SDK |
| Allocator | Small TypeScript service → **Agones** later | Simple first, standard later |
| Infra | Docker Compose on a single Linux box → Kubernetes + Agones (P5) | Cheap and understandable for a solo dev |
| Observability | Prometheus, Grafana, Loki, Sentry or a self-hosted crash endpoint | Standard, free tiers or self-hosted |
| Web | Static site generator + backend API | Hall of Record, shared chapters |

## Source control

**Git + Git LFS**, hosted on GitHub (this repo).

- Code, docs, `/content` data (CSV/JSON), and backend/services live in normal Git.
- Unreal binary assets (`.uasset`, `.umap`) and source art (`.fbx`, `.png`, `.wav`, `.psd`, `.blend`) go through **Git LFS**.
- Enable **LFS file locking** for `.uasset`/`.umap` so binary assets never merge-conflict. Unreal's Git source control plugin supports locking.
- **Watch LFS storage and bandwidth quotas.** If art volume makes GitHub LFS expensive, move the `/game` binary assets to **Perforce (Helix Core free tier)** or **Diversion**, and keep everything else in Git.

### Planned `.gitattributes` (added in P0 alongside the Unreal project)

```gitattributes
# Unreal
*.uasset filter=lfs diff=lfs merge=lfs -text lockable
*.umap   filter=lfs diff=lfs merge=lfs -text lockable
# Source art & audio
*.fbx  filter=lfs diff=lfs merge=lfs -text
*.png  filter=lfs diff=lfs merge=lfs -text
*.tga  filter=lfs diff=lfs merge=lfs -text
*.psd  filter=lfs diff=lfs merge=lfs -text
*.blend filter=lfs diff=lfs merge=lfs -text
*.wav  filter=lfs diff=lfs merge=lfs -text
*.ogg  filter=lfs diff=lfs merge=lfs -text
```

Plus a standard Unreal `.gitignore` (`Binaries/`, `Intermediate/`, `Saved/`, `DerivedDataCache/`, `.vs/`).

## Build and CI

| Pipeline | Runner | Steps |
|---|---|---|
| **Docs / content lint** | GitHub-hosted | Markdown link check, CSV/JSON schema validation for `/content` |
| **Backend + Narrator** | GitHub-hosted | Typecheck, unit tests, build Docker images |
| **Unreal client + server** | **Self-hosted runner** (a home PC or cloud VM with the source-built engine) | UAT `BuildCookRun` for Linux server + Windows client, automated tests (Gauntlet / functional tests), package, upload |
| **Deploy (dev)** | Self-hosted | Pull images and server builds to the dev box, run migrations, restart services |

Unreal builds are too heavy for GitHub-hosted runners. A single self-hosted machine with a warm DDC (Derived Data Cache) is the solo-friendly answer.

## Content pipeline

- **Source of truth:** `/content/*.csv|json` for abilities, items, loot tables, quests, deeds, titles, Paths, and NPC cards.
- **Import:** an editor utility (Python or C++ commandlet) regenerates DataTables from `/content`. CI verifies that the generated assets match the source data.
- **Balance:** spreadsheets export CSV into `/content`. Balance changes never require touching C++.
- **Lore:** `/content/lore/bible.md` is compiled deterministically from the GDD's lore sections and the glossary, and feeds the AI Narrator.

## Art pipeline (solo-friendly)

- **Style:** **stylized, painterly** (WoW-like). It forgives lower polygon counts and hand-painted textures, ages well, and runs well with many players on screen.
- **Sources:** Fab/Unreal Marketplace environment kits and character packs, modular armor sets, and animation packs. Pick **one** coherent environment kit family per biome.
- **Characters:** one shared humanoid skeleton, modular armor meshes, the IK Retargeter for animation reuse, and material-based race differences (see [Races](../gdd/02-races.md#production-constraint-one-skeleton)).
- **Signature look:** the **Blotted shader** (ink erosion, glitching text) and the **vellum UI** style. These two assets define the brand, so they're worth custom effort or a commissioned artist.
- **Performance budget:** 100 players on screen in Lexandria at 60 FPS on a mid-range GPU. Nanite and Lumen are on for the environment, but profile early and offer a low-spec mode (Lumen off).
- **AI-assisted art:** allowed for concepting and iteration only. Shipped assets must be licensed and appropriately sourced (see [Open Questions](../production/open-questions.md)).

## Local development setup (target by end of P0)

1. The source-built UE5 at the pinned version.
2. `docker compose up` in `/backend` starts Nakama, Postgres, the Narrator (optional), and the allocator.
3. Launch a dedicated server from the editor or a packaged Linux server build, with PIE clients connecting through the backend login flow.
4. A `.env` file for the Anthropic API key (never committed). The Narrator runs in **template-only mode** when no key is set.
