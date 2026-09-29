# 03 – Classes

## Overview

Six classes at launch, each with **two specs**. The first three (**Warden, Scrivener, Arcanist**) form the vertical slice's tank/healer/DPS trinity. The other three arrive in Phase 4 (see [Roadmap](../production/roadmap.md)).

| Class | Armor | Resource | Spec A | Spec B | Phase |
|---|---|---|---|---|---|
| **Warden** | Plate | Resolve | Bulwark (tank) | Vanguard (melee DPS) | P1–P2 |
| **Scrivener** | Cloth | Ink | Annotator (healer) | Redliner (ranged DPS) | P2 |
| **Arcanist** | Cloth | Mana | Pyremancer (ranged DPS) | Frostbinder (ranged DPS / control) | P2 |
| **Cleric** | Mail | Mana | Mender (healer) | Zealot (melee DPS) | P4 |
| **Shade** | Leather | Energy + Edge | Assassin (melee DPS) | Duelist (melee DPS) | P4 |
| **Ranger** | Mail | Focus | Beastbond (ranged DPS + pet) | Marksman (ranged DPS) | P4 |

**Design rules**

- **Small kits.** About 12 active abilities per spec at level 30, fewer than modern WoW. Every button should matter.
- **Spec swap** is free outside combat at any Waystone. Specs share gear stats where possible.
- **Abilities are Gameplay Ability System (GAS) assets.** Data lives in DataTables, so tuning never needs a code change (see [Architecture](../tech/architecture.md)).
- Every ability has **Proficiency** and a possible **Evolution** (see [Progression](04-progression.md#skills-proficiency-and-evolution)).

---

## Warden: "The Line That Holds"

Plate-wearing defenders who swear an oath to a place or a person. Waystones are said to have been built on Warden graves.

**Resource: Resolve (0–100).** Builds when you take or deal damage and decays out of combat. Tanks spend it on mitigation, DPS on finishers.

| Ability | Spec | Notes |
|---|---|---|
| Shield Bash | Both | Interrupt + small threat |
| Hold the Line | Bulwark | Taunt |
| Bulwark Stance | Bulwark | +armor, +threat, −damage |
| Oathguard | Bulwark | Spend Resolve: absorb shield on self |
| Rally the Line | Bulwark | Short party damage reduction (cooldown) |
| Cleave | Both | Frontal AoE builder |
| Sundering Strike | Vanguard | Big 2H finisher, spends Resolve |
| Charge | Both | Gap-closer, roots briefly |
| Last Stand | Bulwark | Emergency: +30% max HP |

**Signature fantasy:** standing at a chokepoint with Hold the Line while the party does its work.

## Scrivener: "Edit the Outcome" (signature class)

Scholars who learned to write in the living Script. They heal by *revising* wounds and harm by *striking through* their enemies' stories. Scrivener is the game's signature class; it only makes sense in a LitRPG world.

**Resource: Ink (0–100).** Regenerates steadily. Some abilities leave **Annotations** (marks on allies or enemies) that other abilities *consume* for bonus effects.

| Ability | Spec | Notes |
|---|---|---|
| Mend Text | Annotator | Direct heal |
| Footnote | Annotator | HoT; bonus if the target is Annotated |
| Errata | Annotator | Cleanse |
| **Revise** | Annotator | **Signature:** undo the last 3 seconds of damage taken by an ally (long cooldown) |
| Appendix | Annotator | Group HoT, channeled |
| Strikethrough | Redliner | **Signature DPS:** deletes a % of target's current HP (capped vs bosses) |
| Red Ink | Redliner | DoT, Annotates the target |
| Marginal Note | Both | Places an Annotation (buff on ally / debuff on enemy) |
| Proofread | Both | Analyze upgrade: reveals the target's next cast |
| Redact | Redliner | Silence/interrupt |
| Second Draft | Both | Battle resurrection: rewrites a fallen ally (long cooldown, once per boss fight) |

**Signature fantasy:** the tank takes a huge hit, and a Scrivener *Revises* it out of existence.

## Arcanist: "Raw Script"

Mages who speak pieces of the First Script aloud without a Scrivener's discipline. They are powerful and a little reckless.

**Resource: Mana.**

| Ability | Spec | Notes |
|---|---|---|
| Firebolt | Pyremancer | Filler cast; evolves at Proficiency 10 (see Progression) |
| Ignite | Pyremancer | DoT; crits spread it |
| Pyre | Pyremancer | Big cast, consumes Ignites |
| Frost Lance | Frostbinder | Filler cast, slows |
| Glacial Prison | Frostbinder | Crowd control (breaks on damage) |
| Shatter | Frostbinder | Bonus vs frozen targets |
| Blink | Both | Short teleport |
| Arcane Ward | Both | Absorb shield on self |
| Counterspell | Both | Interrupt |

## Cleric (Phase 4): "Voice of the Scribe-Gods"

Priests of the faded gods. Clerics channel what is left of divine intent. *Mender* is a classic direct healer with strong single-target throughput. *Zealot* is a mail-wearing melee hybrid that heals a little when it deals damage.

## Shade (Phase 4): "Between the Lines"

Rogues who live in the gaps between recorded moments. **Energy + Edge** is a builder/finisher system like WoW combo points. *Assassin* uses poisons and bleeds. *Duelist* uses parries and ripostes. Signature: **Unrecorded**, a stealth that the Chronicle literally doesn't notice (Analyze can't see you).

## Ranger (Phase 4): "Wild Margins"

Hunters of the frontier. *Beastbond* has a persistent pet with its own Proficiency tree (pets level and evolve too). *Marksman* is a pure ranged DPS with long-range shots. Pet AI is a real cost, which is why Ranger comes last.

---

## Class Paths (advancement by deeds)

At **levels 10, 20, and 30** the Chronicle offers each character **a choice of 2–3 Class Paths**. The offer depends on the character's **Deeds**, counters the server tracks all the time (see [Progression](04-progression.md#deeds)).

- A Path adds **one passive, one ability or ability modifier, and a title**.
- Paths are **sidegrades**: they specialize, they don't simply add power.
- Every character always gets **at least two** offers, including a "default" Path per spec, so nobody is locked out by playing "wrong."
- **Paths come from a curated design table.** The AI Narrator writes the *offer text* ("*The Chronicle has noticed how often you stood between death and the weak…*"). It never invents mechanics.

### Example Path table (Warden, level 10)

| Path | Deed requirement | Passive | Ability / modifier | Title |
|---|---|---|---|---|
| **Shieldwright** (default, Bulwark) | — | +5% block chance | Shield Bash also taunts | *Shieldwright* |
| **Unbroken Bastion** | Blocked 5,000 attacks | Blocking grants Resolve | *Bastion*: 4s immunity to knockback + 20% DR | *the Unbroken* |
| **Oathkeeper** | Took 50 killing-blow-eligible hits aimed at an ally (via Intervene/taunts) | Damage taken by nearby allies is 5% redirected to you | *Intervene*: leap to an ally and guard them | *Oathkeeper* |
| **Reaver** (default, Vanguard) | — | Crits refund Resolve | Sundering Strike cleaves | *Reaver* |
| **Last to Fall** | Survived 25 fights below 10% HP | +10% healing received below 30% HP | *Refuse*: cheat death once per 10 min | *Last to Fall* |

### Hidden Paths

A few Paths per class have **secret deed requirements** and are only discovered by doing something unusual. The Chronicle hints at them in [hidden quests](06-world-and-content.md#hidden-quests) and item lore. Examples:

- **Warden: Waystone Warden.** Die and respawn at 100 different Waystones. Grants a short-range personal Waystone teleport.
- **Scrivener: Ghostwriter.** Heal 1,000 players who aren't in your party. Your heals are anonymous and 10% stronger on strangers.
- **Arcanist: Misspoken.** Get killed by your own spells' side effects 10 times. Unlocks a chaotic random-element Firebolt.

Hidden Paths are **no stronger** than normal ones. The reward is rarity, the title, and the story.

---

## Balancing approach

- The target is **"everything viable"**: a group of any three roles clears all 5-player content at appropriate gear.
- All tuning numbers live in data (DataTables/CSV). Balance passes happen in spreadsheets.
- **Proficiency and Evolutions** give roughly +10–15% total power across a level band. Tuning assumes average Proficiency for the level.
- Server-side combat logs allow DPS/HPS analysis per spec (internal tools, Phase 3+).
