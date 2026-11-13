---
name: rooski-drive
description: Builds and keeps the coach's Rooski Drive, his football folders and files in Google Drive under "! Rooski Drive" — the first setup (or picking a stopped setup back up), the start-of-chat folder check, the weekly tidy of stray folders and twins, opening a game week, adding a playoff week, moving his folders into the program drive, and the season turn (put this year away, start next year, "not yet", undo). Use when a coach asks to set up or fix his Rooski Drive or football folders ("set up my Rooski Drive", "where do I put my call sheet", "clean up my folders", "open this week", "we made the playoffs", "I'm moving my stuff into the program drive", "new season", "undo the season turn"). Not for scouting reports, tendencies or self-scouts, writing what goes inside a practice plan, game plan or any other file, recruiting, or other Rooski asks that don't touch his Drive folders.
---

# Rooski Drive

The Rooski Drive is the coach's football home in his own Google Drive. Its top folder is `! Rooski Drive`. Two Rooski tools plan every change; his Drive connector makes it. This skill sets the order of the work. Every folder, file, name and number comes from the tools' answers or his Home Map, never from this page or from memory.

## The tools

- **Rooski connector:** `rooski_tree_plan` (what to build, upgrade, turn or undo) and `rooski_tree_check` (what is missing, misnamed or out of place). They read and change nothing in Drive; they return plans.
- **Match a tool by its name, not its prefix.** The coach named the connector when he added it, so the prefix differs by program.
- **His Drive connector** (Google Drive) does the listing, making, copying, moving, renaming and starring.
- **No Rooski tools in the list:** say once, plainly, that the Rooski connector isn't connected, so you can't plan his Rooski Drive, and that he adds it under Customize > Connectors. Never build from memory.
- **No Drive connector:** say once that his Google Drive isn't connected and that he adds it the same way.
- **A step his Drive tools can't do** (a move, a star, writing inside a file): give him the one-line steps to do it himself, and record it only after he says it's done.
- **The connector is the main path.** If its tools already ran a step this chat (the light check, for one), use that answer. Don't run it twice.

## Pick the routine

| The coach says | Routine | Reference |
|---|---|---|
| "Set up my Rooski Drive", "build my football folders", "my setup stopped, pick it up" | Setup | `setup.md` |
| The first message of a chat about his Drive or Rooski | Light check | `session-start.md` |
| "Clean up my folders", "what's out of place", his first chat of the week | Weekly tidy | `weekly-tidy.md` |
| "Open this week", "we play Central Friday", "we made the playoffs", a schedule change | Week open | `week-open.md` |
| "I'm moving my stuff into the program drive", "upgrade me to the program" | Upgrade | `upgrade.md` |
| "New season", "our season's over", "put this year away", "not yet", "undo the turn" | Season turn | `season-turn.md` |
| "Where do I put my call sheet?", "where's my game plan?" | Where it goes | below |

Open the routine's reference file before the first call.

## Every routine

1. **Find the Home Map.** It is a markdown file whose text begins `# Home Map`. Search his Drive for it.
   - **Keep only maps whose header says `tree: personal`.** A program's Room Map begins the same way, with `tree: program`. Use it only where a routine asks for the Room Map.
   - **The connector may hand you the IDs.** Its start-of-chat answer can carry a `drive` block with `home_folder_id` and `home_map_id`. Read the map by `home_map_id` when it has one (a newer map in the same folder still wins). With only `home_folder_id`, or his profile's `storage_map.home_folder`, take the map whose `root` row has that ID.
   - **Two or more left: the newest wins.** That is the latest `written:` date; on the same date, the latest Drive created time. The older ones are old copies: put them away (Writing the Home Map, step 3) and never treat them as current.
   - If you find none, he has no Rooski Drive yet. Offer setup.
2. **Read the whole map.** Its header holds his answers (plan, role, rooms, live year, open week, turn date). Its rows (`| slot | id | name |`) give every folder and file by Drive ID.
3. **Pass `today`** as his local date, YYYY-MM-DD, on every call.
4. **His plan** (`free`, `pro` or `program`) comes from Rooski when a tool gives it: the `drive` block's `plan`, or `plan` in `rooski_get` kind `my_data`. When the tool's plan is null, use the header's `plan:`. If the tool's plan differs from the header, the tool wins and the next Home Map you write carries it. Before setup there is no map and no plan from a tool: ask him once. If he isn't sure, use `free` and tell him that switching later only changes the map's header; the next weekly tidy then builds the rest.
5. **The schedule** comes from his Season Hub when its row is in the map and you can read it. Otherwise ask him. Pass each game as `{ week, opponent, date, playoff }`.
6. **Act only on the answer's fields.** Show him each offer's `line` text as the tool wrote it. If the answer has `ok: false`, `errors` or `problems`, show them in plain words and change nothing.
7. **If a call is refused for an argument,** fix that one argument and call again once. If it fails again, tell him what didn't work.

## The build rule (every routine that makes anything)

The plan's `build_rule` lines are the rule. Follow them as written:

1. Ask the tool for the items. Never build from memory.
2. Go level by level, every item at one depth before any below it. The parent's Drive ID is the `parent_id` the tool gave, or the Home Map row for the item's `parent` slot.
3. **List each parent before you make anything in it.** An item whose name and type match after normalizing (any dash read as " - ", numbers as two digits, case ignored) is reused: record its ID and make nothing.
4. Make only what is still missing:
   - `folder`: a folder.
   - `doc`: a Google Doc.
   - `sheet`: a Google Sheet.
   - `md`: a plain `.md` file, with conversion to a Doc turned off.
5. **Starter items** (an item with `starter`): make the file with the plan's exact name and type. Put one plain line in it saying what it is for and that Rooski's starter text comes later. Never invent the text.
6. Add each item's row to the Home Map as soon as it is made or reused, so a stop anywhere resumes cleanly.
7. **Never delete or rename to fix a build.** A near-match ("Week 1" beside "Week 01") or a folder he made himself is a line for him.

## Writing the Home Map

The connector can't rewrite a file, so every change to the map is a new file:

1. **Make a new `.md`** in the folder the current map is in, under the same name. Its text is:
   - the header (the tool's header when it gives one, otherwise the current header with `written:` set to today);
   - a blank line;
   - `| slot | id | name |`, then `| --- | --- | --- |`;
   - one row per item.
2. **The map has no row for itself.** Skip any check line about the map itself:
   - a build, record or gone line for its own slot (`home_map`, or `room_map` on a program);
   - a twins line for the map's own name. Old copies are handled by step 3, never as twins.
3. **Put the old map away before the routine ends.** Move it (by its ID) into the folder of the `earlier` row. A program map has no `earlier` row: use the `archive` row. The move goes on that routine's receipt first. The newest map wins.

## Receipts before moves

- **Every move or rename goes on a receipt first.** A receipt is one new `.md` per batch, named `<today> Moves.md` unless the tool names it, in the folder of the `receipts` row. If that name is already there, add ` 2`, ` 3` and so on.
- **Each line:** `- <id> · from "<folder>/<name>" to "<folder>/<name>" · by your AI · why: <why> · undo: move <id> back into <from folder id> and name it "<name>"`. Use the tool's `receipt_line` or `receipt.text` when it gives one.
- **Nothing moves without his yes.** Every offer marked `on_yes_only: true` waits for his yes, one line each.
- **Nothing is ever deleted or trashed.** What is replaced goes to the `archive` row's folder.
- **Undo:** follow the receipt's `undo:` lines from the bottom up, under a new receipt.

## Plan limits

| | Free | Pro | Program |
|---|---|---|---|
| Setup | folders and AI files | adds the coach files | adds the program drive (Rooski builds it) |
| Light check | every chat | every chat | every chat |
| Weekly tidy | at most 5 lines | at most 10 lines | at most 10 lines |
| Week open | week folders only (from the check) | the week's files too | his own Drive; Rooski opens the program drive |
| Season turn | build and put away; no cleanup calls | the full turn | the full turn; Rooski turns the program drive on the head coach's yes |
| Upgrade | — | — | head coach only |

- **Rooski-run help** (a weekly digest, safe moves) exists only for Program, and for Pro once a tool returns `drive_share: active`.
- **Never say Rooski did something** unless a tool said so. Without that, everything here is done by you, in this chat.

## Where it goes

When he asks where something goes, answer from the Home Map. Give the folder's name from its row, never a slot or an ID.

- **This week's work** (call sheet, game plan, practice plan, notes) goes in that week's folder: the `week` row for the open week.
- **A master he reuses every year** goes in the `templates` row's folder. On a program, it goes in that room's every-year folder.
- **Reading, clips and things to keep** go in the `library` row's folder.
- **Not sure:** the `inbox` row's folder. The weekly tidy sorts it with him.
- **If the folder isn't in the map yet,** run the light check (`session-start.md`) to build it first.

## House rules

1. **Find by ID, never by name.** The only names you may search for are `! Rooski Drive` and the Home Map's first line.
2. **Write for a coach on his phone.** Use short lines and plain words. Show him folder names, never slots or IDs unless he asks.
3. **Sum up a build in one line,** with the count and season the tool gave. Never list every item.
4. **Every name you show comes from a tool answer, his Home Map or his Drive.**
5. **A setup too long for one chat is normal.** The Home Map lets the next chat pick it up (`setup.md`).
