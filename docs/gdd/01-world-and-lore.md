# 01 – World and Lore

## Tone

High fantasy in the classic MMO tradition: bright, adventurous, and a bit heroic, with tragedy underneath. The LitRPG layer is **diegetic**. People in Vellumar have lived with levels and titles for thousands of years and treat them the way we treat weather. Humor comes from the Chronicle's dry commentary and from NPCs who find the Unwritten strange. It never breaks the fiction.

**Tone words:** wonder, legacy, erosion, defiance, wry.

## Cosmology

### The First Script

In the beginning the **Scribe-Gods** wrote **Vellumar** onto a blank page. Mountains were nouns, rivers were verbs, and every living thing was a sentence still being written. Their text, **the First Script**, did more than describe the world. It *was* the world.

### The Sundering of the Quill

The gods argued over how the story should go. One wanted tragedy, one wanted triumph, and one wanted it never to end. The argument became a war, the **Sundering of the Quill**, and the First Script shattered. The gods faded or withdrew. What was left of their text became a self-running, impersonal force:

### The Chronicle

The **Chronicle** is the shattered First Script still doing its job. It **measures** (levels, attributes), **names** (titles, classes), **records** (every notable deed), and **rewards** (skills, Paths, loot, if you believe the priests). It is not a god. It has no goals of its own, only habits. Many scholars say it has a sense of humor. The Library of Lexandria considers that question heretical and has asked everyone to stop raising it.

Gameplay-wise, the Chronicle is the System. Its voice is the [AI Narrator](../tech/ai-narrator.md), and its style guide is in [LitRPG Presentation](09-litrpg-presentation.md#the-chronicles-voice).

### The Margin

Past the edge of the page is **the Margin**: blank, silent space where erased things go. Nothing lives there. Things *used* to live there.

## The Unwritten (players)

For a thousand years every soul in Vellumar has been recorded from birth. Then, one spring morning, people started stepping out of the Waystones with **no entry in the Chronicle at all**. They are the **Unwritten**.

This explains the MMO conventions inside the fiction:

| MMO convention | In-world explanation |
|---|---|
| Respawning | The Chronicle refuses to end an unfinished story. It rewrites fallen Unwritten at the nearest **Waystone**. The *Faded* debuff is the ink still drying. |
| Hundreds of heroes at once | The Unwritten are appearing in waves. Nobody knows why, and the main story is about finding out. |
| Everyone asks *you* for help | Unwritten have no fixed fate. Locals are bound to the story the Chronicle already holds for them. The Unwritten can change it. |
| Visible stat sheets | Natives see their own sheets too, but only the Unwritten see sheets as vividly as a page of text. |
| Rapid leveling | A blank page is easy to write on. Natives level over decades; Unwritten level in weeks. |

## The threat: the Redactor and the Blotted

### The Redactor

Before the Sundering, the gods had an **Editor**, a lesser divinity that kept the First Script consistent. When the gods fell, the Editor read everything left behind and decided the story was *flawed*: full of contradictions, cruelty, and loose ends. Its answer is to erase all of it and write Vellumar again, correctly this time. It now calls itself **the Redactor**.

The Redactor sincerely believes it is acting out of mercy. It is patient, articulate, and nearly impossible to argue with, which makes it an unsettling final antagonist.

The arrival of the Unwritten is the one thing the Redactor didn't plan for. Blank pages can't be edited.

### The Blotted

**The Blotted** are creatures, people, and places the Redactor has partly erased.

- **Visuals:** ink-black silhouettes with missing chunks, text that glitches across their surfaces, and edges that "smear" as they move. They are the game's signature enemy look and cheap to build: a shader on existing models.
- **Mechanics:** Blotted enemies can *Redact* (silence abilities, erase buffs), and some flicker out of targeting.
- **Lieutenants:** the **Strikethrough Knights**, the **Proofreader**, and **Errata, the Twice-Written**. They are the bosses of the [Palimpsest Citadel](06-world-and-content.md#raid-the-palimpsest-citadel).

## History (short timeline)

| Era | Event |
|---|---|
| The Writing | The Scribe-Gods write Vellumar. |
| The Sundering of the Quill | The gods' war shatters the First Script, which becomes the Chronicle. |
| The Age of Record (~3,000 years) | Mortal kingdoms rise. The Great Library of **Lexandria** is founded to study the Chronicle. |
| The Ashclan Refusal (~400 years ago) | The orcs, recorded in the Chronicle as "raiders and villains," rewrite their own entry through a mass act of defiance and join the Concord. Nobody knew that was possible. |
| The Quiet Erasures (~50 years ago) | Villages start disappearing from maps, and from memory. |
| **Now: the First Unwritten** | Unwritten souls arrive at the Waystones. The Blotted March opens. The game begins. |

## The Concord of the Quill

A coalition of the peoples of Vellumar, bound by an old oath to protect the Chronicle. **Every player is a member.** There are no opposing player factions. Players pick one of five **Great Houses** for identity and reputation:

| Great House | People | Seat | Flavor |
|---|---|---|---|
| **House Vael** | Humans (Vaelish) | Lexandria | The crown and the Library. Diplomats and record-keepers. |
| **The Deepholds** | Dwarves (Stonekin) | Ironspine Reaches | Engineers. Their motto, "Written in stone," is taken literally. |
| **The Eldrin Archive** | Elves (Eldrin) | The Thornwood | Long memories and grudges. Keepers of pre-Sundering lore. |
| **The Ashclans** | Orcs | Saltglass Barrens | Proudly self-authored. They distrust anyone who says fate is fixed. |
| **The Free Glyphs** | Scriptborn | Lexandria (the Stacks) | Newly awakened fragments of Script. They aren't sure whether they are people or punctuation. |

Houses provide reputation tracks, cosmetic rewards, and storyline flavor, not separate content. See [Social and Endgame](08-social-and-endgame.md#reputation-great-houses).

## Main story arc (launch, levels 1–30)

1. **Act I, "A Blank Page"** (Hearthmere Vale): you arrive as an Unwritten. A village near Quillford is erased while you watch. You learn the Chronicle's rules.
2. **Act II, "Footnotes"** (Thornwood, Ironspine): the Eldrin Archive and the Deepholds hold clues. The Redactor erases *precisely*, and its targets are loose ends in the First Script.
3. **Act III, "The Unread King"** (Saltglass Barrens): an ancient king whose story was never finished holds a fragment of the original Quill.
4. **Act IV, "Palimpsest"** (Blotted March): the Redactor is writing a new world over the old one inside its Citadel. Defeating Errata ends the launch arc. The Redactor itself remains the long-term antagonist for expansions.

## Lore bible usage

This doc, the [Glossary](../glossary.md), and the Chronicle style guide are also the **lore bible** fed to the AI Narrator. Keep them accurate and short. Anything added here becomes something the AI can say. See [AI Narrator: prompt design](../tech/ai-narrator.md#prompt-and-lore-bible-design).
