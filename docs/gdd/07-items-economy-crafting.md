# 07 – Items, Economy, and Crafting

## Gear

- **Slots (12):** head, shoulders, chest, hands, legs, feet, main hand, off hand, neck, ring ×2, trinket. There are fewer slots than WoW, which means fewer art assets and simpler UI.
- **Armor types:** cloth, leather, mail, plate. Each class wears one primary type.
- **Stats:** primary attributes (STR/AGI/INT + VIT; WIS and PER on some pieces) and secondaries (Crit, Haste, Mastery, and *Clarity*, which is Proficiency XP gain and only appears on leveling gear).
- **Item level** drives power. Rarity sets the stat budget and how many secondary stats a piece gets.
- **Item flavor text** is written in-world and sometimes hints at hidden quests.

## Loot rules

- **Personal loot** in the open world (every tagging player gets their own roll; no ninja-looting).
- **Dungeons and raids:** personal loot by default, with **trading within the group for 2 hours** among eligible players. A classic *Need/Greed* option can be added for groups that want it.
- **Bind rules:** Bind on Pickup (dungeon/raid/quest), Bind on Equip (world drops, most crafts), Account-bound (cosmetics, Legacy items).
- **Bad-luck protection** on dungeon bosses: each failed roll on the boss's loot table raises your odds next time.

## Unique items

**Unique** is our signature LitRPG rarity: **only one copy exists per server at a time.**

- **Sources:** world-first boss kills (the raid's Errata, each dungeon's first *Annotated* hard-mode clear), hidden-quest finales, and rare world events.
- **Power:** roughly Epic-level stats plus **one distinctive effect** (usually utility or visual), such as *Quill of the First Word*: a staff whose spells leave trailing golden script, plus a once-per-day "read aloud" emote that gives nearby players a small buff.
- **Bound to the character. They can't be traded or sold.**
- **Rebinding:** if the holder is inactive for 60 days, the Unique "returns to the Chronicle" and can drop again from its source. Every change of hands is a server announcement. This keeps Uniques alive as a story instead of sitting in an inactive player's bank forever.
- **Registry:** the backend owns the **Unique registry** (item ID → current holder). Zone servers must reserve a Unique atomically before awarding it (see [Architecture](../tech/architecture.md)).

> **Why Uniques won't break balance:** their stats are Epic-equivalent. What makes them special is their story and identity.

## Currency

- **Gold / silver / copper** is the single main currency.
- **Marks of Record** are a dungeon/raid currency for catch-up gear and cosmetics (weekly cap).
- **House Favor** is per-Great-House reputation currency (see [Social](08-social-and-endgame.md#reputation-great-houses)).
- **No premium currency that buys power.** See [Open Questions](../production/open-questions.md) for the business model.

## Professions

Each character picks **two primary professions** (gathering + crafting pairs are natural but not required) plus the secondary **Cooking** available to everyone. Professions have their own levels (1–150) and deeds, and specializations are offered as small "profession Paths."

| Profession | Type | Makes / gathers | Pairs with |
|---|---|---|---|
| **Mining** | Gathering | Ore, stone, gems | Blacksmithing |
| **Blacksmithing** | Crafting | Plate & mail armor, weapons | Mining |
| **Herbalism** | Gathering | Herbs, reagents | Alchemy, Inscription |
| **Alchemy** | Crafting | Potions, flasks, transmutes | Herbalism |
| **Inscription** (signature) | Crafting | **Scrolls** (one-shot spells), **Glyphs** (minor ability modifiers), **Tomes** (skill Proficiency boosts), Waystone attunement scrolls | Herbalism (inks) |
| **Cooking** | Secondary | Food buffs | — |

**Cut for launch (later expansions):** Leatherworking, Tailoring, Enchanting, Skinning. Cloth and leather armor come from drops and vendors at launch. See [Scope and Risks](../production/scope-and-risks.md#cut-list).

### Inscription: the LitRPG profession

- Uses inks milled from herbs, plus **Script Fragments** (dropped by Blotted enemies).
- **Glyphs** add small sidegrade modifications to abilities, e.g. *Glyph of the Long Footnote*: Footnote lasts 3s longer but heals 10% less per tick.
- **Tomes of Practice** give Proficiency XP to one skill. They are capped per week so they can't replace play.
- Master Scribes can write **Personal Chronicle Bindings**, cosmetic physical book items of your own Journal volumes that other players can inspect.

## The Exchange (auction house)

- A single **server-wide** market, reachable in Lexandria and at every zone hub's Exchange Clerk.
- Listings, bids, and buyouts go through the **backend** (Nakama storage + a Postgres-backed order book), never through zone servers, so the market is consistent across shards.
- **Fees:** a 5% deposit plus a 5% cut on sale. Both are gold sinks.
- **Price history** graphs come from the backend.

## Gold sinks

| Sink | Notes |
|---|---|
| Repairs | Durability loss on death and use |
| Respecs | Attribute point respec after level 10, and skill evolution resets |
| Exchange fees | Deposit and cut |
| Mounts | Riding skill at level 20 (the land mount) is the big one; a flying mount is post-launch, maybe never |
| Waystone travel | Small fee for fast travel between attuned Waystones |
| Cosmetics | Transmog (the *Rebinding Desk*), dyes, titles' calligraphy styles |
| Guild costs | Charter and guild bank tabs |

## Economy health metrics (Phase 3+)

Track them from backend data: gold created vs destroyed per day, median price of key reagents, Unique item churn, and bot-suspicion signals (inhuman gathering routes, 24/7 play).
