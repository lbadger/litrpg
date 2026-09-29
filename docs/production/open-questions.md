# Open Questions

Decisions deliberately deferred. Each one lists the phase it must be settled by and the current leaning.

| # | Question | Decide by | Current leaning |
|---|---|---|---|
| Q1 | **Final title.** *Everwrit Online*, *Worldscribe*, *The Living Chronicle*, or something else? | P3 (before any public alpha) | *Everwrit Online*; run a trademark search first |
| Q2 | **Business model.** Free hobby project, buy-to-play, subscription, or free-to-play with cosmetics? It must cover server costs and AI costs (an estimated $1.80–3.30 per active player per month at ~30 hours, see [AI Narrator](../tech/ai-narrator.md#models-effort-and-cost)) | P4 | **Buy-to-play + cosmetic shop**, no pay-to-win; possibly an optional "Illuminated" subscription that raises AI budgets (more NPC chat, longer chapters) |
| Q3 | **AI model tiering.** Keep all live features on Claude Opus 5.5 at low effort, or move high-volume routes (asides, NPC turns) to Sonnet 5.5 / Haiku 4.5? | End of P2 | Decide from measured quality and cost on real tester sessions |
| Q4 | **Race count at launch.** All five, or ship Humans + Scriptborn + 2 others? | P3 | All five (cheap on the shared skeleton) |
| Q5 | **Level cap 30 vs 40** | P4 | 30; expansions add levels |
| Q6 | **Two-faction option.** Should we ever add player factions (e.g., a Redactor-aligned "Revisionist" faction for PvP)? | Post-launch | Not at launch; revisit with arenas |
| Q7 | **Target platform.** PC only (Windows first; Linux via Proton), consoles later? | P2 | PC-only through launch; controller support in P5 |
| Q8 | **Server region** for the first world | P4 | Wherever the alpha community is |
| Q9 | **Journal sharing format.** Web page, ePub, and/or printable PDF? | P5 | Web page first, ePub second |
| Q10 | **Voice acting** for the Chronicle | P5 | Undecided. Human VO for templated lines vs licensed TTS; the budget decides |
| Q11 | **AI-generated art** in shipped assets | P2 | No, concept work only; ship licensed or commissioned assets |
| Q12 | **Source control for art** if LFS gets expensive | When LFS quota nears its limit | Move `/game` binaries to Perforce or Diversion |
| Q13 | **Hardcore / "Ironbound" mode** (permadeath: the Chronicle closes your book) | Post-launch | Great LitRPG hook; separate ruleset server later |
| Q14 | **Player-written lore.** Let players write their own Journal marginalia that others can read? | P5 | Maybe, but it needs moderation |
| Q15 | **SpacetimeDB vs UE dedicated + Nakama** | End of P0 | UE dedicated + Nakama unless the spike shows a clear win |

## How to resolve a question

1. Write a short decision note (context, options, decision, consequences) in `docs/decisions/NNNN-title.md`.
2. Update the affected docs and the [Glossary](../glossary.md) if names change.
3. Remove the question from this table and link the decision note.
