# Scope and Risks

MMOs are famous for killing studios much bigger than ours. This doc sets out the rules that keep *Everwrit Online* shippable.

## Scope rules

1. **One coalition, no faction duplication.** Every zone, quest, and dungeon serves every player.
2. **One continent at launch.** Five zones + a capital. Expansions add continents.
3. **Level cap 30 at launch.** Fewer levels means fewer abilities, fewer items, and less tuning.
4. **One shared skeleton.** No race or creature gets bespoke humanoid animation.
5. **Buy art, build systems.** Use marketplace kits for environments and characters. Custom effort goes only into the signature visuals (the Blotted shader, the vellum UI).
6. **Zones, not seamless.** Separate maps and servers with transfers. No seamless-world tech.
7. **Minimal PvP.** Duels and sparring only at launch.
8. **The AI is garnish, not a load-bearing wall.** It must never block a feature from shipping. The fallback ships first.
9. **Playable every phase.** If a phase can't end playable, cut scope until it can.
10. **No new systems after P4.** P5 is for content, polish, and hardening.

## Cut list

If the schedule slips, cut in this order (top first):

| Priority to cut | Item | Impact |
|---|---|---|
| 1 | AI NPC dialogue (keep scripted dialogue) | Loses a "wow" feature; the Journal keeps the AI identity |
| 2 | Ranger class (pet AI cost) | 5 classes instead of 6 |
| 3 | Cooking, Alchemy | Fewer professions; consumables come from vendors |
| 4 | *Annotated* dungeon difficulty | Less endgame repetition |
| 5 | Company Chronicles | Minor |
| 6 | Deepforge Undercroft dungeon | 2 dungeons + raid |
| 7 | Shade class | 4 classes |
| 8 | Saltglass Barrens zone (merge its story into the March) | Levels cap at 25–30 across four zones |

**Never cut:** the core trinity classes (Warden, Scrivener, Arcanist), Proficiency and Evolutions, Class Paths, World Firsts, the Chronicle Journal (at least templated), the raid, and the Exchange. These *are* the game.

**Already cut for launch:** Leatherworking, Tailoring, Enchanting, Skinning, battlegrounds, open-world PvP, rated arenas, flying mounts, player housing, voice acting.

## Risk register

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | **Scope creep / burnout**: the classic solo MMO failure | High | Critical | Scope rules above; playable phase exits; public cut list; scheduled breaks between phases |
| R2 | **Networking at MMO scale** (replication cost with 100 players per zone) | Medium | High | P0 spikes; Iris / Replication Graph; relevancy tuning; zone caps and layering (duplicate zone servers) when full |
| R3 | **AI running cost** exceeds revenue | Medium | High | Tier 0/1 text first; batch chapters; per-player budgets; global circuit breaker; measure in P2 before committing |
| R4 | **AI quality or safety issues** (off-lore text, invented mechanics, abuse through NPC chat) | Medium | Medium | Golden rules; placeholders for numbers; server-validated tools; evals; private-by-default output; moderation |
| R5 | **Art volume** (a 3D MMO needs a lot of assets) | High | High | Stylized art; kit-based; shared skeleton; one kit family per biome; commission only the signature pieces |
| R6 | **Server costs** at beta scale | Medium | Medium | Bare-metal/VPS first; Agones only when needed; one region |
| R7 | **Cheating and bots** | Medium | Medium | Server authority; RPC validation; heuristics in P5; GM tools |
| R8 | **Economy inflation** | Medium | Medium | Gold sinks table; metrics from P3; tunable vendor prices and fees |
| R9 | **Unreal engine upgrades** break things mid-project | Medium | Medium | Pin versions per phase; upgrade only between phases |
| R10 | **Small population** makes an MMO feel empty | High | High | One world; open tagging; group finder early; generous group XP; the Journal names companions; community building from P2 |
| R11 | **Unique items cause drama or hoarding** | Medium | Low | Epic-level stats; the 60-day inactivity return; announcements make ownership a story |
| R12 | **Legal/licensing** (asset licenses, AI-generated content, trademarks on the title) | Low | High | Track asset licenses in `/docs`; human review of AI-authored content; trademark search before announcing the final name |

## Success metrics per phase

| Phase | Measure |
|---|---|
| P1 | Internal "fun check": would we play this combat for an hour? |
| P2 | Tester sessions average ≥ 90 min; ≥ 50% of testers read their Journal chapter |
| P3 | ≥ 70% of alpha testers finish Gloamroot Hollow; at least one hidden Path is discovered organically |
| P4 | Day-7 retention of alpha 2 testers ≥ 40%; economy gold in/out ratio 0.8–1.2 |
| P5 | Beta sustains target CCU; AI cost per player-hour within budget; crash rate < 1% of sessions |
