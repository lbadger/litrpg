# 02 – Races

Five playable races at launch. All belong to the Concord, and any race can play any class. Race choice decides starting cutscene flavor, a racial trait, cosmetic options, and home Great House. **It does not decide the starting zone.** Everyone begins in Hearthmere Vale (see [scope](../production/scope-and-risks.md)).

## Production constraint: one skeleton

Every race uses **one shared humanoid skeleton** (with masculine and feminine body presets). Race differences come from:

- Proportion scaling (bone scale on the shared rig: dwarves shorter and broader, orcs taller and bulkier)
- Heads, ears, tusks, horns, and hair as swappable skeletal mesh parts
- Materials and decals (Scriptborn glyph skin, Ashclan warpaint)

UE5's IK Retargeter and runtime retargeting let one animation set cover all five races. This is the most important art-cost decision in the project.

## Racial traits

Racials are small, flavorful, and never mandatory for any class or role.

### Humans: the Vaelish
- **Look:** varied. Soldiers, scholars, farmers.
- **Home House:** House Vael
- **Racial: *Quick Study*.** +10% skill Proficiency gain.
- **Flavor:** the Chronicle's most thoroughly documented people. Their bureaucracy has a bureaucracy.

### Dwarves: the Stonekin
- **Look:** short, broad, braided beards (optional), stone-and-rune tattoos.
- **Home House:** the Deepholds
- **Racial: *Stoneblood*.** 10% shorter stun and poison durations. Gathers ore faster.
- **Flavor:** they carve important records into stone because "ink can be erased." They now look very clever.

### Elves: the Eldrin
- **Look:** tall and slender, silver or autumn-toned hair, leaf-shaped ears.
- **Home House:** the Eldrin Archive
- **Racial: *Long Memory*.** +3 Perception, and the Analyze skill starts at Proficiency 2.
- **Flavor:** some Eldrin are old enough to remember the Sundering. None of them agree about what happened.

### Orcs: the Ashclans
- **Look:** big, green-grey to ash-grey skin, tusks, ash-paint patterns that record personal deeds.
- **Home House:** the Ashclans
- **Racial: *Defiance*.** Below 35% health, gain 10% damage reduction for 8 seconds (2-minute cooldown).
- **Flavor:** the Chronicle once recorded them as villains. They *refused*, and the Chronicle rewrote them. They are the living proof that fate can be edited, which also makes them the Redactor's most personal enemy.

### Scriptborn: the Free Glyphs
- **Look:** humanoid figures made of animated script. Pale vellum-like skin covered in slowly moving glyphs, eyes like wet ink. Customization lets players choose their glyph "language" and color.
- **Home House:** the Free Glyphs
- **Racial: *Marginalia*.** Sees hidden text in the world: faint glyphs that point to hidden quests, secret doors, and lore. Other races can find the same secrets, just with more effort (high Perception or careful exploration).
- **Racial (minor): *Self-Revision*.** Remove one harmful effect from yourself (3-minute cooldown).
- **Flavor:** stray fragments of the First Script that woke up about a century ago. The Scriptborn are the game's signature race and the most "LitRPG" option.

> **Balance note:** *Marginalia* must never gate required content. It reveals *optional* secrets sooner, and every hidden quest must also be findable another way.

## Character creation flow

1. Choose a race, then pick a body preset and customize.
2. Choose a class (see [Classes](03-classes.md)).
3. Choose a name. The Chronicle reacts: "*A name. How novel. Let it be written: ___.*"
4. Opening cinematic: you step out of a Waystone near Quillford as your first Chronicle entry writes itself on screen.
