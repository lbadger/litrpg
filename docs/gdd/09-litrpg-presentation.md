# 09 – LitRPG Presentation

This doc defines how the game **looks and reads** like a LitRPG novel: system windows, notifications, stat sheets, the Chronicle's voice, and the Chronicle Journal.

## Visual language: "living script on vellum"

LitRPG books use "blue boxes." Our in-world equivalent is **glowing script written onto translucent vellum**:

- **System windows:** semi-transparent parchment panels with a soft inner glow. The text *writes itself in* with a fast quill-stroke reveal (skippable, and instant with reduced-motion on).
- **Color coding by source:**
  - **Chronicle (System):** deep ink-blue text with a gold border. This is our "blue box."
  - **World First / server-wide:** gold ink with an illuminated-manuscript initial capital.
  - **Blotted / Redactor:** black ink bleeding through the page, with glitching letters.
  - **NPC speech:** normal dialogue UI, clearly *not* System text.
- **Typography:** a readable serif for body (e.g., *Cormorant* or *EB Garamond*), a calligraphic display face for headers, and a monospace-like "tabular" face for stat numbers.
- **Accessibility:** scalable text, high-contrast mode, dyslexia-friendly font option, reduced motion, and screen-reader hooks for system windows (CommonUI + UMG).

## Notification catalog

| Type | Trigger | Size | Example (templated baseline) |
|---|---|---|---|
| **Level Up** | Level gained | Large, center | **LEVEL UP!** *You have reached Level 7.* +2 free attribute points. New ability: *Footnote*. |
| **Skill Gain** | New ability learned | Medium | **Skill Acquired: Shield Bash (Proficiency 1)** |
| **Proficiency** | Skill Proficiency up | Toast, corner | *Firebolt Proficiency increased (3 → 4).* |
| **Evolution Ready** | Skill hits Proficiency 10 | Large + choice | **Your Firebolt Yearns to Evolve.** Choose one: … |
| **Quest Received / Complete** | Quest events | Medium | **Quest Received: A Page Gone Missing** |
| **Title Earned** | Deed threshold | Medium | **Title Earned: *Wolfbane*.** *+2% damage vs wolves.* |
| **Path Offered** | Level 10/20/30 | Full-screen moment | **The Chronicle Offers You a Path** + 2–3 cards |
| **Hidden Discovery** | Hidden quest found | Medium, gold | **Hidden Quest Discovered!** *Few would have noticed.* |
| **World First** | First on server | Server-wide banner + chat | **WORLD FIRST!** *Let it be written: the Company "Inkstained" is the first to defeat Errata, the Twice-Written.* |
| **Unique** | Unique item awarded | Server-wide banner | **A UNIQUE ITEM HAS BEEN CLAIMED.** *The Quill of the First Word now belongs to Wren.* |
| **Death** | Player death | Center, desaturated | *A bold final sentence. Unfortunately not the final one.* |
| **Chronicle Aside** | Rare or funny moments (AI) | Small toast, italic | *The Chronicle notes that you have now fallen off this particular bridge four times.* |

**Rules**

- Every notification has a **templated baseline** that is always correct and instant. The **AI Narrator may add a flavor line** asynchronously (a line under the box, or an "aside" toast) when the moment is rare enough to deserve it. See [AI Narrator](../tech/ai-narrator.md).
- **Verbosity setting:** *Terse* (templates only), *Standard* (templates + occasional asides), *Chatty* (more asides). Default is *Standard*.
- **Priority queue:** notifications never stack more than three on screen, and lower-priority toasts wait during combat.

## Stat sheets

Players can open their **Character Sheet** (default `C`) at any time. It is styled as a page from the Chronicle:

```
╔══════════════════════════════════════════════╗
║  WREN OF QUILLFORD            the Unbroken   ║
║  Level 12 Human Warden (Bulwark)             ║
║  Path: Unbroken Bastion                      ║
╠══════════════════════════════════════════════╣
║  HP   1,840 / 1,840      Resolve   0 / 100   ║
║                                              ║
║  STR  38 (+6)   AGI  17        VIT  41 (+8)  ║
║  INT   9        WIS  11        PER  14 (+2)  ║
║  Free points: 2                  [Assign]    ║
╠══════════════════════════════════════════════╣
║  Armor 1,204   Block 18%   Crit 6.1%         ║
║  Haste 3.2%    Mastery 9.4%                  ║
╠══════════════════════════════════════════════╣
║  SKILLS                                      ║
║  Shield Bash ....... Prof 7  ▓▓▓▓▓▓▓░░░      ║
║  Hold the Line ..... Prof 5  ▓▓▓▓▓░░░░░      ║
║  Oathguard ......... Prof 4  ▓▓▓▓░░░░░░      ║
╚══════════════════════════════════════════════╝
```

(Mockup only; the real UI uses the vellum style described above. The ASCII layout shows the information hierarchy.)

**Analyze windows** use the same format for enemies, with fields hidden as `???` until the Analyze Proficiency reveals them (see [Combat](05-combat.md#analyze)).

## The Chronicle's voice

The Chronicle is the most important "character" in the game. Its voice style guide is also part of the AI Narrator's system prompt.

**Personality:** ancient, precise, dry, a little amused. It is a record-keeper, not a cheerleader and not a bully. It respects the Unwritten because they are the only thing in a thousand years that has surprised it.

**Do**
- Use short, declarative sentences. Understatement. A pause before the joke.
- Use book and writing metaphors *sparingly*: page, ink, margin, entry, chapter, draft.
- Refer to the player by name or as "the Unwritten."
- Keep system facts exact. Numbers in the templated box are always correct.
- Use formal phrases for big moments: "*Let it be written:*" for world firsts, and "*It is recorded.*" for completions.

**Don't**
- Mock players cruelly or insult them for failing. This is dry wit, not *Dungeon Crawler Carl* snark.
- Use modern slang, memes, or fourth-wall breaks about "the game," "servers," or "players." (Hall of Record announcements may say "on this world.")
- Make promises about loot, mechanics, or the future. The Chronicle *records*; it doesn't predict.
- Get long-winded. One or two sentences for asides.

**Examples**

| Moment | Line |
|---|---|
| First login | *"An unrecorded soul. How unusual. Let us begin a new entry."* |
| Level 10 | *"Ten levels. The early chapters are always the fastest."* |
| Near-death survival | *"You survived with 3 health. The Chronicle has corrected its earlier prediction."* |
| Repeated fall death | *"Gravity, too, is recorded here. It has never once been late."* |
| Hidden quest found | *"Few would have noticed. You are, it seems, not few."* |
| World first | *"Let it be written: on this world, before all others, it was Wren."* |

## The Chronicle Journal

The Journal is the game's most distinctive feature: **every play session becomes a chapter of a LitRPG novel about your character.**

### How it works

1. During play, the zone server writes **structured events** (quests, kills of note, level-ups, deaths, loot, discoveries, party members, world firsts) to the character's session log.
2. On logout (or after about 3 hours of play), the session is **closed** and queued for the Narrator.
3. The AI Narrator **selects highlights** (it doesn't narrate every wolf), writes a chapter of 600–1,200 words in LitRPG style with **real stat blocks inserted from event data**, and gives it a title.
4. The next time the player logs in: *"A new chapter has been added to your Chronicle."*
5. Chapters collect into **Volumes** (a volume per 10 levels or per story act). Players can read them in-game, rename chapters, hide chapters, **export** them to a web page or ePub, and **share** a link.

**Fallback:** with AI off, the Journal still produces a **templated summary chapter**: a structured recap with headings, stat blocks, and highlights. The feature degrades; it doesn't disappear.

**Privacy:** Journals are private by default, and sharing is opt-in per chapter. Other players are named only by character name, and players can opt out of appearing in others' Journals.

### Sample chapter (target quality)

> ### Volume I, Chapter 4: The Keep That Held Its Breath
>
> The Old Keep of Sir Vellan had been empty for a century, which was why Wren found it odd that someone had lit the braziers.
>
> She was not alone. Tobble, a Stonekin Arcanist who talked to his fireballs, had followed her up the hill, and a quiet Scriptborn named Ninth Stanza trailed behind them, glyphs drifting across her skin like fish under ice.
>
> The first skeleton came through the gate at a run. Wren met it shield-first.
>
> > **Shield Bash** — *Proficiency increased (6 → 7).*
>
> "You're getting better at that," Tobble said.
>
> "It's getting better at me," Wren said, which didn't mean anything, but it sounded good.
>
> They fought through the courtyard. Twice, Ninth Stanza's Footnotes caught Wren just before the numbers turned red. The third time, the Warden-Captain's greatsword came down and Wren felt the world go thin and white at the edges. Then the pain simply *wasn't there anymore*, and Ninth Stanza lowered a hand wet with ink.
>
> *Revise.* Wren had heard of it. She had not known it felt like being forgiven.
>
> When the Warden-Captain fell, the Chronicle spoke, as it did now and then, in that dry voice only she could hear:
>
> > ╔══════════════════════════════════╗
> > **LEVEL UP!** You have reached **Level 10**.
> > +2 free attribute points.
> > **The Chronicle has a Path to offer you.**
> > ╚══════════════════════════════════╝
>
> *"Ten levels,"* it added. *"The early chapters are always the fastest."*
>
> Wren looked at the offered Paths for a long moment. *Shieldwright* was sensible. *Unbroken Bastion* was, apparently, what she had already become.
>
> She chose the one that was already true.
>
> > **Path Chosen: Unbroken Bastion.**
> > **Title Earned: *the Unbroken*.**

(The Narrator's output format is Markdown with fenced stat-block sections, which the client renders into styled vellum boxes.)

## Audio (light touch)

- A **quill-scratch** sound for system window reveals, pitched differently by notification type.
- A **choir swell** for level-ups and a **bell toll** for world firsts, audible server-wide at low volume.
- **Voice acting (later):** the Chronicle's templated lines could be recorded, or synthesized with a licensed TTS voice. Out of scope until Phase 5.
