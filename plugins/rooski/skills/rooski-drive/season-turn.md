# Season turn: put this year away, start next year

**Free and Pro:** his own AI runs it, at his first chat on or after the turn date. It starts when the light check returns a `turn` line, or when he says "new season" or "our season's over". A program drive is turned by Rooski on the head coach's yes. Each coach's own season is still turned here.

The turn has two halves:
- **The build half** (next year's folders and files, plus a copy of this year's roster) needs no yes.
- **The put-away** is one set of moves, made only on his yes.

## 1. Ask for the turn

Call `rooski_tree_plan` with `step: "turn"`, `home_map` and `today`. It takes only these extra arguments:

| Argument | When to send it |
|---|---|
| `turn_date`, `last_game_date` | From the check's `turn.args`, or from his Season Hub, or from him. |
| `schedule`, `last_regular` | Next year's games, if he has them already. |
| `listing` | **Pro and Program only.** The same listing as the weekly tidy (`weekly-tidy.md`, step 2). It turns on the three cleanup calls. On Free, leave it out. |

Read the answer:

| Field | What to do |
|---|---|
| `needs: "last_game_date"` | Ask him its `line`, then ask for the turn again with his answer. If he doesn't know yet, ask again on `ask_on`. |
| `ok: false` with `problems` | Show them in plain words. Most say to run the tree check first: run `weekly-tidy.md`, then come back. |
| `due: false` | The turn date hasn't come. Show `preview.screen`. Go on only if he says to turn now. |

## 2. The build half: no yes needed

1. **Build each item in `build`** under the build rule:
   - `from: "every_year_master"`: copy `master_id`.
   - `from: "rooski_starter"`: a starter item (SKILL.md, The build rule, step 5).
   - `from: "empty"`: an empty file of that `kind`.
   - folders: as usual.
2. **The `snapshot`, if there is one:** copy `copy_of.id` into `parent_id` under `name`. Do it before anything moves.
3. Keep a row for every built item; it goes in the map at step 4.

## 3. Show the turn

1. Show `preview.screen`. In a Season Review, show the `season_review` block instead.
2. **The cleanup calls** (`calls.promote`, `calls.retire`, `calls.early`; Pro and up): each is its own offer, one `line` each, on his yes.
3. **Lessons Learned:** ask him the `lessons_learned.prompts`, two or three at most.
   - If his tools can write inside the file named by `lessons_learned.id`, add his answers under today's date.
   - Otherwise give him the lines to paste in.
4. Ask: "Say go, not yet, or change any line."

## 4. His answer

### Go

1. **The receipt:** `receipt.text`, adding the `receipt_line` of each cleanup call he said yes to under `## Moves`. Make it as `receipt.name` (`.md`) in `receipt.parent_id`. Write it **before any move**.
2. **The put-away:** move each `put_away` item's `id` into `to_parent_id`, in `step` order.
3. **The calls he said yes to:**
   - `promote`: move `id` into `to_id` and name it `new_name`.
   - `retire`: move `id` into `to_id`.
   - `early`: move `id` into `to_id`. If there is no `to_id`, use the ID of the folder you built for `to_slot`.
4. **The Home Map:** a new file with `home_map_after.text`, plus a row for each item you built (SKILL.md, Writing the Home Map).
5. Tell him in one line that his season is put away and next year is ready.

### Not yet

1. Nothing moves. What you built stays.
2. Write a new Home Map:
   - header: `if_not_yet.header`;
   - rows: the old rows plus a row for each item you built.
3. Say `if_not_yet.line`. The check stays quiet until `if_not_yet.ask_again_on`, then raises the turn again. The next turn finishes the put-away and builds nothing twice.

### He changes a line

- **A cleanup call:** drop it, or keep it, as he says.
- **The put-away:** it is all or nothing. If he wants any of it to wait, that is "not yet".

## 5. Undo the turn

He says "undo that" or "undo the turn".

1. **Find the turn receipt** in the `receipts` row's folder: the newest one whose text begins `# Turn`. Read its whole text.
2. Call `rooski_tree_plan` with `{ step: "turn_undo", receipt, today, home_map }`. Pro and up: add `listing`. It takes no other arguments.
3. If the answer has `ok: false`, show `problems` and stop.
4. Show `summary` and each `kept_live` line. Ask: "Undo the turn?"
5. **On his yes:**
   1. **The undo receipt first:** make `receipt.name` in `receipt.parent_id` with `receipt.text`.
   2. **Then each item in `moves`, in `step` order:** move `id` into `to_parent_id`, and name it `name` when one is given.
      - An item with `find_in` and no `id`: list that folder and take the item with that `name` and `kind`.
   3. **The Home Map:** `home_map_after.text`. If there is no `home_map_after`, follow `home_map_note`.
6. Tell him: "Your `<season>` season is live again. I'll ask about the turn again on `<ask_again_on>`."

Nothing the turn made is deleted. It goes to the archive, by the tool's own moves.
