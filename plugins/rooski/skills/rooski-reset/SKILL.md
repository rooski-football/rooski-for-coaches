---
name: rooski-reset
description: Runs the Rooski Reset with the coach, his close-out of 2026 and his plan for 2027, by opening Rooski's Reset steps (the same steps as the Rooski Reset Kit). Covers his player and staff survey answers and exit meetings, the season review (what went wrong this year), who's back next year and who to go get, keep, change, add and stop, his learning list, his War Map, and handing it up to his AD. Use when a coach says "start my Reset", "the Reset Kit", "season review", "what went wrong this year", "keep, change, add and stop", "who's back next year", "who do I need to go get", "what should I get better at this off-season", "my learning list", "my War Map", "my player survey answers are in", "staff survey answers", "exit meetings" or "my AD meeting". Not for setting up or tidying his Rooski Drive folders or the season turn's put-away (rooski-drive), or scouting reports, self-scouts and tendency studies (rooski-scout-reports).
---

# The Rooski Reset

The Reset is the coach's close-out of 2026 and his plan for 2027. Rooski serves its steps. This page only opens them: it holds none of their questions, columns or wording, so never fill a step in from this page or from memory.

## Open the steps

1. **In every Reset chat, open the start first:** `rooski_get` with `{ kind: "starter", id: "reset" }`. Follow what it returns, as written. Do this even when he starts in the middle ("who's back next year?").
2. **Open each step as he reaches it:** `rooski_get` with `{ kind: "starter", id: "reset-1" }`, and so on for each step id the start lists (today `"reset-1"` through `"reset-9"`). The start says which id is which step. Open a step before you work it, and don't open the ones he hasn't reached.
3. **Match a tool by its name, not its prefix.** The coach named the Rooski connector when he added it, so the prefix differs by program.
4. **His Drive connector** (Google Drive) finds, reads and saves his files, as the steps say.

## When the steps aren't there

- **No Rooski tools in his list:** say once, plainly, that the Rooski connector isn't connected, so you can't open Rooski's Reset steps, and that he adds it under Customize > Connectors.
- **`rooski_get` has no `starter` kind, or the `reset` id isn't found:** say once, plainly, that Rooski's Reset steps aren't on his Rooski yet.
- **Then, either way:** find his Kit copy with his Drive connector (a file with "Rooski Reset" in its title; his copies start "Copy of Rooski Reset"), open its Start Here tab, and work from it in the Kit's own words. If more than one matches, skip any in his Home Map's `earlier` or `archive` row folders and ask him which is his current copy. If you can't find one, ask him to open his Kit copy or paste its Start Here tab.
- **Never write the Reset's steps from memory.**

## Moving an old version, and the War Map's row

When a step has you move an old file into the folder of his Home Map's `earlier` row, or put a new War Map on the map's `war_map` row, open the rooski-drive skill and follow its "Writing the Home Map" and "Receipts before moves" sections. Don't do either from this page or from memory. If his map has no `war_map` row, don't add one: save the War Map where the step says and leave the map to rooski-drive's checks.

## Players' names

His Rooski notes, lists and profile keep no youth or high school player names. Anything naming a player goes in his own Drive files, where names are his call: use them as he does, with no warning and no refusal.
