# 04 – Progression

Progression is the heart of a LitRPG, so numbers going up has to feel good. There are three loops:

| Loop | Cadence | Systems |
|---|---|---|
| **Short** (minutes) | Frequent small dings | Skill Proficiency, Analyze reveals, deed counters, loot |
| **Medium** (an evening) | 1–3 per session | Levels, free attribute points, new abilities, quests, titles |
| **Long** (weeks) | Milestones | Class Paths, skill Evolutions, dungeon/raid gear, Hall of Record, reputation |

## Levels (1–30)

- **Level cap at launch: 30.** Future expansions raise it in blocks of 10.
- **Time to cap target:** about 60–80 hours for a first character, faster for alts through a shared **Chronicle Legacy** XP bonus.
- **XP sources:** quests (~60%), kills (~25%), discovery and exploration (~10%), dungeons (bonus).
- Each level-up is a full System moment: the level-up window, attribute points to assign, an ability unlock if any, and a Chronicle line.

## Attributes

| Attribute | Abbr. | Effect |
|---|---|---|
| Strength | STR | Physical damage (plate/melee), block value |
| Agility | AGI | Physical damage (leather/ranged), crit, dodge |
| Vitality | VIT | Max health, health regen |
| Intellect | INT | Spell damage and healing, max resource |
| Wisdom | WIS | Resource regeneration, healing crit, resistances |
| Perception | PER | Hit chance, detecting stealth/traps, **reveals hidden content**, Analyze depth |

### Allocation

- **Class growth:** each level the class automatically adds its fixed spread (Warden: +2 STR, +2 VIT, +1 AGI).
- **Free points:** **2 per level** (58 total by level 30), assigned by the player.
- **Respec:** free up to level 10. After that it costs gold at any Waystone (the cost scales with level and is a gold sink).
- **Soft caps**, not hard caps: diminishing returns past a threshold stop degenerate all-in builds.
- **Gear** supplies about 60% of attributes at cap, so free points are meaningful but don't decide everything.

> **Why free points in an MMO?** It is a core LitRPG fantasy. To keep it from turning into a trap: respec is cheap, the UI suggests an allocation per spec, and gear does most of the work.

### Perception as an exploration stat

Perception is our LitRPG-flavored stat. Higher PER:

- Reveals **hidden objects** (secret doors, buried caches, faint glyph hints) above per-object thresholds.
- Adds detail to **Analyze** results.
- Unlocks bonus dialogue and investigation options on some quests.

Every PER-gated item is **optional**, and the threshold is reachable through gear or temporary consumables (*Eyedrops of the Archivist*).

## Skills: Proficiency and Evolution

### Proficiency

Every active ability has its own **Proficiency level (1–10)**.

- Using a skill **meaningfully** grants Proficiency XP: casting on valid, level-appropriate targets in combat. Anti-exploit rules: no gain against training dummies after P3, reduced gain against grey mobs, and diminishing returns per target.
- Each Proficiency level gives a small, specific improvement: −0.1s cast time, +3% damage, −1s cooldown, and so on, shown on the skill tooltip.
- New Proficiency levels trigger a quiet notification (not the full level-up fanfare).
- Racial *Quick Study* (Humans) gives +10% Proficiency gain.

### Evolution

At **Proficiency 10**, a skill can **evolve** into one of **2–3 sidegrade variants**. This is a permanent choice per character, reversible at a Lexandria trainer for a large gold cost.

**Example: Firebolt (Arcanist)**

| Evolution | Change | Fantasy |
|---|---|---|
| **Searing Bolt** | Slower cast, much higher damage, applies Ignite | Single-target nuker |
| **Firestorm Volley** | Splits into 3 bolts on nearby targets | AoE / cleave |
| **Wildfire Bolt** | Instant cast while moving, lower damage | Mobility |

**Example: Footnote (Scrivener)**

| Evolution | Change |
|---|---|
| **Extended Footnote** | Longer duration, can stack twice |
| **Cross-Reference** | Jumps to a second Annotated ally |
| **Ibid.** | When it expires, reapplies itself at 50% strength |

Evolutions come from a **curated design table**. The AI Narrator only writes the moment ("*Your Firebolt has been spoken so often it wants to become something more…*").

## Deeds

**Deeds** are server-side counters attached to a character: blocks, heals on strangers, kills by creature family, deaths by cause, Waystones visited, hidden glyphs read, and so on.

- Deeds drive **Class Path offers**, **titles**, **hidden quests**, and **Journal highlights**.
- Tracking is cheap: they are aggregated in the zone server and flushed to the backend with the character save.
- A **Deeds page** on the character sheet shows *discovered* deed categories. Hidden ones appear as `???` until first progress.

## Titles

- Earned by deeds, quests, world firsts, and reputation.
- **One active title**, shown above the nameplate and in the Journal.
- Most titles are **cosmetic**. A few give a **small, situational bonus**: *Wolfbane* gives +2% damage vs wolves. Bonuses never matter in raids.
- **World First titles** are unique per server (see below).

Examples: *the Unbroken*, *Wolfbane*, *Ghostwriter*, *Late to Everything* (arrive after a world event ends five times), *First of the Unwritten* (first character on a server to reach level 30).

## World Firsts

A **World First** is the first completion of a notable feat on a server: first to level 10/20/30, first dungeon clear, first raid-boss kill, first discovery of a hidden Path, and so on.

- **Server-wide broadcast** in the style of a LitRPG announcement (see [Presentation](09-litrpg-presentation.md#notification-catalog)).
- A **unique title** that only the first player or group ever holds.
- Recorded forever in the **Hall of Record** (in-game in Lexandria, plus a web page).
- The backend's **World First registry** arbitrates firsts with a single atomic write, so two zone servers can't both award one (see [Architecture](../tech/architecture.md)).

## Achievements = Chronicle entries

Achievements are presented as **Chronicle entries**, short lore-flavored records in a book UI, not as a checklist. Each one also feeds the Journal.

## Item rarity

| Rarity | Color | Notes |
|---|---|---|
| Common | White | Vendor and crafting fodder |
| Uncommon | Green | Quest rewards, world drops |
| Rare | Blue | Dungeon drops, good crafts |
| Epic | Purple | Raid drops, top crafts |
| Legendary | Orange | Long questlines, very rare; one per class at launch (maybe) |
| **Unique** | **Gold-ink shimmer** | **One copy per server at a time.** See [Items](07-items-economy-crafting.md#unique-items) |

## Leveling alts: Chronicle Legacy

When a character reaches level 30, the account gets **Chronicle Legacy**: +50% XP for new characters, shared discovered-map knowledge, and shared cosmetic titles. The Chronicle remembers "*a previous draft.*"
