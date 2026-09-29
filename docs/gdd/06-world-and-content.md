# 06 – World and Content

## The launch continent

One continent with five zones, a capital, three dungeons, and one raid. Zones are separate UE5 levels, each hosted by its own **zone server** (see [Architecture](../tech/architecture.md)). Zones are medium-sized (about 2×2 km playable) and use World Partition with hand-placed landmarks.

```
                 [ Ironspine Reaches 15–22 ]
                           |
[ The Thornwood 10–18 ] — [ Lexandria (capital) ] — [ Saltglass Barrens 20–27 ]
                           |                                   |
                 [ Hearthmere Vale 1–10 ]            [ The Blotted March 27–30 ]
```

| Zone | Levels | Biome | Hub | Dungeon / raid | Story beat |
|---|---|---|---|---|---|
| **Hearthmere Vale** | 1–10 | Pastoral valley, farms, rivers, old watchtowers | Quillford | — (open-world elite quest chain) | Act I: A Blank Page |
| **The Thornwood** | 10–18 | Dark fey forest, overgrown Eldrin ruins, werewolves | Lanternhold | **Gloamroot Hollow** | Act II: Footnotes |
| **Ironspine Reaches** | 15–22 | Snowy mountains, dwarven mines, giants | Deephold Gate | **Deepforge Undercroft** | Act II: Footnotes |
| **Saltglass Barrens** | 20–27 | Desert with glass storms and buried libraries; Ashclan territory | Emberkraal | **Tomb of the Unread King** | Act III: The Unread King |
| **The Blotted March** | 27–30 | Frontier half erased: floating islands of land over blank white Margin | Last Line | **The Palimpsest Citadel** (raid) | Act IV: Palimpsest |
| **Lexandria** | Capital | A city built around the Great Library; canals, towers, the Stacks | — | — | Hub: trainers, the Exchange, Hall of Record, bank |

Thornwood and Ironspine overlap in level range so players can choose between them, which spreads out server load and adds replay value for alts.

## Zone highlights

### Hearthmere Vale (1–10): starting zone
- **Quillford:** a farming town built around a Waystone. The tutorial covers movement, Analyze, the first quest, the first level-up, and the first free points.
- **The Vanishing of Brackwater** (level 5 set piece): a neighboring village is erased while you watch, in a scripted phased event. This is the player's first sight of the Blotted.
- **Old Keep of Sir Vellan:** an open-world elite area that teaches group play before dungeons, ending in a 3-player-recommended quest boss.
- **Hidden:** *The Farmer Who Wasn't Written*, a hidden questline (PER 20 or Marginalia) about an NPC the Chronicle forgot.

### The Thornwood (10–18)
- **Lanternhold:** an Eldrin outpost of glass lanterns that hold memories.
- Werewolf packs that feed *Wolfbane*-style deed counters, and ghost-lit ruins.
- **Dungeon: Gloamroot Hollow** (levels 14–18, 4 bosses): a corrupted heart-tree. The final boss is **Mother Gloam**, a dryad half-Blotted, fighting her own erasure.

### Ironspine Reaches (15–22)
- **Deephold Gate:** the Stonekin fortress-city entrance. Records are carved into its walls.
- Frost giants, mine carts (a set-piece escort quest), and an avalanche world event.
- **Dungeon: Deepforge Undercroft** (levels 19–22, 4 bosses): an abandoned forge where the Stonekin tried to *carve* the Chronicle permanently. Final boss: **The Engraver**, a rune-construct.

### Saltglass Barrens (20–27)
- **Emberkraal:** an Ashclan war-camp city. Ashclan storytelling fires tell your deeds back to you (a Journal tie-in).
- Glass storms: a timed hazard that forces players into shelters, where they end up gathering together.
- **Dungeon: Tomb of the Unread King** (levels 24–27, 5 bosses): a king whose story was never finished and who cannot die. Final boss **King Aurelan the Unread** has a mechanic where the group must *finish his story* by collecting pages mid-fight.

### The Blotted March (27–30): endgame zone
- **Last Line:** the Concord's forward camp on the edge of the erased land.
- Daily **Chronicle Events**: holding erasure fronts, rescuing "half-written" NPCs.
- The visuals are the game's showpiece: land breaking into floating paragraphs over blank white.

## Raid: The Palimpsest Citadel

**10 players (flexible 8–10 for a small community), 4 bosses, level 30.** The Redactor is writing a new world over the old one here. The Citadel's architecture keeps rewriting itself between pulls.

| # | Boss | Core mechanic |
|---|---|---|
| 1 | **The Strikethrough Knights** (council of 3) | Killing one "strikes through" a buff onto the others; kill order matters |
| 2 | **The Proofreader** | Marks players with "errors"; they must be *corrected* (cleansed) in a set order or they explode |
| 3 | **The Marginalia Engine** | The room is half Margin; players on the blank side lose abilities over time and must rotate |
| 4 | **Errata, the Twice-Written** | Two phases: the "first draft" and a "revision" that repeats earlier bosses' mechanics mixed together; *Rewrite: Mortality* heals Errata unless the Scriveners' *Revise* or group cooldowns counter it |

The first kill of Errata on each server is a major **World First**, with a unique title, an announcement, and a Hall of Record entry, plus a **Unique** drop (see [Items](07-items-economy-crafting.md#unique-items)).

## Quest types

| Type | Share | Notes |
|---|---|---|
| **Story quests** | ~25% | Main acts, voiced key moments (text + light VO later), phased set pieces |
| **Zone quests** | ~50% | Classic kill/collect/escort/investigate, written with LitRPG flavor and kept short |
| **Hidden quests** | ~5% | Found through Perception, Marginalia, deeds, or odd interactions |
| **Chronicle bounties** | ~15% | Templated repeatables (hunt X, clear Y, rescue Z) that the AI Narrator flavors with local names and context |
| **Profession quests** | ~5% | Unlock recipes and specializations |

**Quest presentation:** quests arrive as system windows: *"**Quest Received: A Page Gone Missing.** The Chronicle has noted an inconsistency in Brackwater. Investigate."* Each quest has an objective box, a Chronicle-voice summary, and an NPC-voice description.

### Hidden quests

Hidden quests are the discovery pillar. Rules:

1. **Every hidden quest has at least two ways in.** Marginalia or Perception is the easy way. The other way is deliberate exploration or an unusual action.
2. The Chronicle **hints** at them in item flavor text, NPC gossip, and faint in-world glyphs.
3. Completing one gives a **Chronicle entry**, often a **title**, and sometimes progress toward a **hidden Class Path**.
4. **Discovery is a World First** the first time on each server ("*The Chronicle notes that Wren of Quillford was the first to hear the Farmer Who Wasn't Written.*").

About 3 hidden quests per zone at launch (15 total).

## World events: Chronicle Events

Scheduled or triggered open-world events:

- **Erasure Fronts** (Blotted March, recurring): hold three points while the Blotted push forward.
- **Glass Storm** (Saltglass, recurring): shelter-and-survive hazard with a rare elite spawn.
- **The Night the Lanterns Went Out** (Thornwood, weekly): memory-lantern escort.
- **Seasonal events** (live ops): *The Festival of First Words* (New Year), *Blot Night* (Halloween-ish).

Event results are written into the Journals of everyone who took part, as a shared "chapter" moment.
