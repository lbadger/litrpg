# 05 – Combat

## Model

Classic **tab-target** MMO combat, deliberately close to WoW so it feels familiar right away:

- **Targeting:** Tab cycles hostile targets in front of you, click selects, and there are focus-target and target-of-target frames.
- **Global cooldown (GCD):** 1.5s base, reduced by Haste down to a 1.0s floor.
- **Cast bars** with interrupts, pushback on hit (casters), and moving-cancels-cast (except instant or "while moving" abilities).
- **Auto-attack** for melee and ranged weapon users.
- **Range and facing** checks run on the server (see [Architecture](../tech/architecture.md#authority-and-security)).
- **Crowd control** with diminishing returns (after three applications within 18s, the target is immune for 18s).

All abilities, effects, and attributes are implemented with Unreal's **Gameplay Ability System (GAS)**: `GameplayAbility`, `GameplayEffect`, `AttributeSet`, and `GameplayTags`. The server is authoritative, and the client predicts only cast starts and cooldown visuals.

## Roles and threat

| Role | Job | Tools |
|---|---|---|
| **Tank** | Hold threat, position enemies, mitigate | Taunts, threat multipliers, active mitigation |
| **Healer** | Keep the group alive, cleanse | Direct heals, HoTs, cleanses, Revise |
| **DPS** | Kill things, interrupt, avoid mechanics | Rotations, interrupts, CC |

**Threat:** each enemy keeps a **threat table**. Damage makes 1× threat, healing makes 0.5× split across engaged enemies, and tank stances apply ×3. Enemies switch targets when someone passes 110% of the current target's threat in melee range or 130% at range, as in WoW. Taunt sets you to the top of the table plus 10%.

## Enemies

- **Creature families** (wolves, bandits, Blotted, undead, constructs, giants...) share AI behavior trees and deed counters (*Wolfbane*).
- **Ranks:** Normal, **Elite** (group-worthy, gold nameplate dragon), **Rare** (named spawn with a timer and better loot, silver nameplate), **Boss**.
- **AI:** UE5 **StateTree** (or Behavior Trees) + EQS for positioning. Leashing, evade-on-reset, and call-for-help radius.
- **Blotted mechanics:** *Redact* (removes one buff), *Smear* (briefly untargetable, reappears nearby), and *Blank Zone* (a no-casting ground AoE). They are consistent across the game so players learn the "language" of the enemy.

## Analyze

Every character has **Analyze** (no GCD, short cooldown). It's the LitRPG "Identify" skill, and it has **Proficiency** like any other skill.

| Analyze Proficiency | Revealed |
|---|---|
| 1 | Name, level, rank, creature family, health % |
| 3 | Exact health, resource, main attribute |
| 5 | Resistances and weaknesses |
| 7 | Ability list (with names; tooltips at 8) |
| 9 | Loot table preview (rarity bands) |
| 10 | Evolution choice: *Deep Analysis* (full stat sheet), *Tactical Read* (shows next cast), or *Appraisal* (item and loot detail) |

**Perception** adds +1 effective Proficiency per 25 PER, and the Eldrin *Long Memory* racial starts Analyze at 2. Bosses resist Analyze by rank: raid bosses show only what Proficiency 10 + the *Deep Analysis* evolution reveals. The results appear as a **stat window** in the LitRPG style (see [Presentation](09-litrpg-presentation.md#stat-sheets)).

## Death and respawn

- At 0 HP you are **Unwritten-down**: a ghost-like state in which the world desaturates into blank vellum.
- **Release** to respawn at the nearest **Waystone**, or wait for a resurrection: in combat from a Scrivener (*Second Draft*) or a Cleric (*Resurrect*), or out of combat from any healer.
- **Penalty:** a 10% durability loss on equipped gear (a gold sink) and **Faded** (−10% stats for 60s, stacking to 3 on repeated deaths). No XP loss.
- **Chronicle line** on death (templated, AI-flavored when available): *"A bold final sentence. Unfortunately not the final one. Return to the Waystone; your story is not yet finished."*
- Deaths are **deeds** (by cause: fall damage, drowning, a specific boss...). Some titles and one hidden Path reward dying in interesting ways.

## The combat log as prose

There are two logs:

1. **Standard combat log** (numbers, parseable, exportable for raiders).
2. **Narrated log** (a toggleable tab): a LitRPG-style running account generated from **templates** (not AI) in real time:

   > *Your Firebolt strikes Gnoll Brute for **142** fire damage. **Critical!***
   > *Gnoll Brute is **Ignited**.*
   > *Gnoll Brute has been slain. **+38 XP.***
   > *Firebolt Proficiency increased. (3 → 4)*

The **AI Narrator** is never involved in live combat text; latency and cost rule it out. It uses the event stream afterward for **Journal chapters** and for occasional flavor lines on *rare* events (first kill of a rare, near-death survival, a boss kill). See [AI Narrator](../tech/ai-narrator.md).

## Dungeon and boss design principles

- **3–5 bosses per dungeon**, ~30–40 minutes per run.
- Each boss teaches **one mechanic** clearly (interrupt this, move out of that, switch targets, spread out).
- Telegraphs use **ground decals in ink-and-parchment style**: a spreading ink blot means "move," and glowing script circles mean "stack."
- Boss abilities are **announced as system text**: *"Errata, the Twice-Written begins to cast **Rewrite: Mortality**."*
- A **hard mode** (the *Annotated* difficulty) for later phases adds one mechanic per boss and gives better loot.
