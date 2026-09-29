# 08 – Social Systems and Endgame

An MMO lives or dies by its community. With a small team and a small world, we want players to meet each other often and to *remember* each other. The Chronicle Journal helps: your Journal names the people who fought beside you.

## Groups

| Group | Size | Notes |
|---|---|---|
| **Party** | up to 5 | Shared quest credit, XP bonus for grouping (+10% per extra member, up to 5), party frames |
| **Raid** | 8–10 | Raid frames, ready check, marker icons, loot rules |

- **Group Finder** (*the Summoning Circle*): queue for dungeons by role; the backend matchmaker (Nakama) forms groups and launches a dungeon instance server.
- **Open-world tagging:** anyone who damages a Normal or Elite mob gets credit, and quest mobs are shared within ±5 levels. This avoids "kill stealing" frustration and keeps strangers helping each other.

## Communication

- **Chat channels:** Say, Yell, Party, Raid, Guild, Whisper, Zone, Trade (hubs), Looking-for-Group. They run through Nakama realtime chat so cross-zone channels work.
- **Emotes** include LitRPG-flavored ones (`/analyze-stare`, `/scribble`, `/ding`).
- **Moderation:** profanity filter (optional per player), report, mute/ignore, rate limits, and GM tools (see [Architecture](../tech/architecture.md#moderation)).

## Guilds (*Companies*)

In-world, guilds are called **Companies**, as in "a company of adventurers."

- Up to 200 members; ranks with permissions; message of the day; roster.
- **Company bank** (3 tabs, expandable with gold).
- **Company Chronicle:** the AI Narrator writes a weekly **Company Chronicle** from members' notable deeds (world firsts, dungeon clears, raid kills). Guilds can publish it on their web page.
- **Company World Firsts:** raid firsts credit the whole Company in the Hall of Record.

## Reputation: Great Houses

The five Great Houses (see [Lore](01-world-and-lore.md#the-concord-of-the-quill)) each have a reputation track:

*Unknown → Noted → Recorded → Honored → Illuminated*

- Your **home House** (from your race) starts at *Noted*.
- Earned through zone quests in the House's region, House-specific dailies (at level 30), and turning in Blotted items.
- **Rewards:** House cosmetics (tabards, mounts, titles), recipes, level-30 catch-up gear, and the House's *Illuminated* title.
- **No exclusive power.** Houses are about identity and cosmetics.

## Endgame (level 30 at launch)

A small team can't match WoW's endgame breadth, so we focus on **repeatable content that stays interesting**:

| Activity | Loop |
|---|---|
| **Dungeons: Annotated difficulty** | Harder versions of all 3 dungeons with an extra mechanic per boss; weekly Marks of Record |
| **Raid: The Palimpsest Citadel** | Weekly lockout, Epic gear, Unique drops on firsts |
| **Chronicle Events** | Daily world events in the Blotted March |
| **Great House reputation** | Dailies, cosmetics |
| **Deeds, titles, hidden Paths** | Long-tail discovery and collection |
| **Skill Evolutions** | Reaching Proficiency 10 on all abilities |
| **Professions** | Max level, specializations, Unique-quality crafts |
| **Alts** | Chronicle Legacy speeds up new characters |

### Hall of Record

- **In game:** a hall in Lexandria where statues and plaques commemorate each server's world firsts. The plaques update dynamically from backend data.
- **On the web:** a public page for each server listing world firsts, the first 10 characters to reach level 30, raid-kill order by Company, and recent Unique drops.
- This is our main **"be famous"** motivator and a marketing hook (streamers love world firsts).

## PvP (deliberately minimal at launch)

| Feature | Launch? | Notes |
|---|---|---|
| **Duels** | Yes | Challenge anyone, anywhere outside hubs |
| **Company Sparring** | Yes | Friendly guild-vs-guild in the Lexandria Arena, no rewards |
| **Rated Arenas** (2v2/3v3) | Post-launch | Needs separate balance work |
| **Open-world PvP** | No | One-coalition design; a possible "Contested" server type later |
| **Battlegrounds** | No | Too much content and balance cost for a solo team |

PvP balance never drives PvE balance. If arenas arrive, they get PvP-specific modifiers.

## Community and retention features

- **Recruit-an-Unwritten:** a referral bonus for both players (cosmetic).
- **Mentor flag:** level-30 players can queue as mentors for new-player dungeons and earn Marks and the *Mentor* title.
- **Shared Journal moments:** when you group with someone often, your Journals start calling them "your companion," which is a small warm touch the AI gives us almost for free.
