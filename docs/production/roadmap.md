# Roadmap

**Team assumption:** solo / hobby (1–3 people). **Rule:** every phase ends with something **playable**. Durations are rough ranges for a part-time-to-full-time solo developer and will be re-estimated at the end of each phase.

| Phase | Name | Rough duration | Players |
|---|---|---|---|
| P0 | Pre-production & spikes | 1–3 months | Just us |
| P1 | Combat prototype (single-player) | 2–4 months | Just us |
| P2 | Networked vertical slice | 4–6 months | Friends (≤10) |
| P3 | Group content, closed alpha | 4–6 months | 20–50 |
| P4 | World expansion, alpha 2 | 6–10 months | 100–200 |
| P5 | Endgame-lite, open beta | 6–9 months | 500+ |
| P6 | Launch & live ops | ongoing | Public |

Total to launch: roughly **2–3.5 years**, which is realistic for a small MMO with a tiny team. Scope cuts (see [Scope and Risks](scope-and-risks.md#cut-list)) are the lever if it slips.

---

## P0: Pre-production & spikes

**Goal:** prove the risky tech and settle the design before building content.

**Deliverables**
- ✅ This design doc set (vision, GDD, tech, roadmap)
- Lore bible + Chronicle style guide compiled into `/content/lore/`
- Art direction board: a painterly style, the vellum UI mockup, and a Blotted shader concept
- **Spike 1: GAS tab-target.** One ability with a cast bar, GCD, and cooldown, targeted by Tab, running on a listen/dedicated server.
- **Spike 2: Dedicated server + Nakama.** Log in through Nakama, get a join ticket, connect to a Linux dedicated server, and save and load a character document.
- **Spike 3: Zone transfer.** Two dedicated server processes with a handoff between them.
- **Spike 4: Narrator prototype.** Feed a hand-written event log to Claude and get back a chapter plus an aside; measure quality, latency, and token cost.
- **Spike 5 (optional): SpacetimeDB check.** A half-day evaluation of its Unreal support versus our plan.
- Repo scaffolding: `/game`, `/backend`, `/services/narrator`, `/content`, `.gitattributes`, CI skeleton

**Exit criteria:** all spikes work end to end on the dev box. The architecture doc is updated with anything we learned. Engine version is pinned.

## P1: Combat prototype (single-player)

**Goal:** make combat feel good before anything else.

**Deliverables**
- Third-person MMO camera and movement (WoW-style mouse-look, click-to-move optional)
- Tab-targeting, target frames, action bars, cast bars, GCD, auto-attack
- **Warden (Bulwark)** with ~5 abilities, Resolve resource, and threat
- 3 enemy types (Normal, Elite, and one Blotted variant with *Redact*) using StateTree AI, leashing, and threat tables
- LitRPG HUD v1: level-up window, Proficiency toasts, the Character Sheet, Analyze (Proficiency 1–5)
- Levels 1–5 in a gray-box test map, free attribute points, templated narrated combat log
- Data pipeline: abilities, enemies, and XP curve imported from `/content` CSV

**Exit criteria:** a 15-minute play session is fun with placeholder art. Combat feels responsive, and "numbers go up" feels good.

## P2: Networked vertical slice

**Goal:** a small but real MMO experience in one zone.

**Deliverables**
- Everything from P1 running on **dedicated servers** with 10 concurrent players
- **Hearthmere Vale** (levels 1–10) with real art: Quillford, about 25 quests, the Brackwater erasure set piece, the Old Keep elite area
- Classes: **Warden, Scrivener, Arcanist** (both specs each, abilities to level 10)
- Races: **Humans + Scriptborn** (the other three can follow in P3/P4 on the shared skeleton)
- Loot, inventory, equipment, vendors, repairs, death and Waystones
- Nakama: accounts, character persistence, chat (say/party/zone/whisper), parties
- **Narrator v1:** Tier 1 curated aside pools, live asides for rare moments, **Journal chapters via batch** with the templated fallback, budget controls
- Basic ops: Docker Compose deploy, backups, Grafana dashboards

**Exit criteria:** friends can play levels 1–10 together over several evenings. Journal chapters are good enough that testers *want* to read them. AI cost per player-hour has been measured, and the model/tier decision is made.

## P3: Group content, closed alpha (20–50 players)

**Goal:** prove group play and LitRPG progression depth.

**Deliverables**
- **The Thornwood** (levels 10–18), about 35 quests
- **Dungeon: Gloamroot Hollow** (4 bosses) as an instance server, plus loot rules
- **Skill Proficiency 1–10 + Evolutions** for all slice abilities
- **Deeds, titles, Class Paths at level 10** (Warden/Scrivener/Arcanist tables, with 1 hidden Path each)
- **World First registry + Hall of Record** (in-game plaque and a simple web page)
- Races: Dwarves, Elves, Orcs
- Group finder (Nakama matchmaker)
- First hidden quests (3 in the Vale, 3 in the Thornwood)
- Narrator: Path offer text, Chronicle bounties

**Exit criteria:** groups of strangers from the group finder complete Gloamroot Hollow. At least one hidden Path is found by a tester without hints. Server stable at 50 CCU.

## P4: World expansion, alpha 2 (100–200 players)

**Goal:** the full leveling experience to about level 25.

**Deliverables**
- **Ironspine Reaches**, **Saltglass Barrens**, and **Lexandria** (capital)
- Dungeons: **Deepforge Undercroft**, **Tomb of the Unread King**
- Classes: **Cleric, Shade, Ranger**
- Professions: Mining, Blacksmithing, Herbalism, Alchemy, **Inscription**, Cooking
- **The Exchange** (auction house), Companies (guilds), Great House reputation
- **AI NPC dialogue** for ~10 key NPCs, and Company Chronicles
- Class Paths at level 20, Chronicle Legacy for alts

**Exit criteria:** new players reach level 25 without running out of content. The economy's gold in/out is roughly balanced. Several zone servers run at once without issues.

## P5: Endgame-lite, open beta

**Goal:** a complete level-30 game, hardened for the public.

**Deliverables**
- **The Blotted March** (levels 27–30) and daily Chronicle Events
- **Raid: The Palimpsest Citadel** (4 bosses, 8–10 players), **Unique** items
- *Annotated* dungeon difficulty, Marks of Record, Class Paths at level 30, remaining hidden Paths
- NPC dialogue expanded to ~20 NPCs, Journal export/share pages
- Ops hardening: Kubernetes + Agones (if needed), monitoring alerts, bot heuristics, GM tools, moderation workflows, load testing to 500 CCU
- Accessibility pass, low-spec mode, audio pass, and the onboarding tutorial polished
- Business model implemented (see [Open Questions](open-questions.md))

**Exit criteria:** open beta sustains the target CCU. The first raid World First happens on the beta server. Crash rate and AI cost are within budget.

## P6: Launch & live ops

- Launch on a single world (one region). Add a second world only when there's a queue.
- **Content cadence** for a tiny team: a **seasonal Chronicle Event** every ~3 months, a new hidden quest or Path every month or so (cheap and high-delight), and balance patches.
- **First expansion ideas** (level 30→40): a second continent across the Margin, the Redactor's scriptorium, floating "paragraph islands" to explore, Rated Arenas, two new professions (Tailoring, Leatherworking).
