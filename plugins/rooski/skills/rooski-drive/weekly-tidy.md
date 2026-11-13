# Weekly tidy: the full check and strays

Every plan gets this, at his first chat of the week or when he asks ("clean up my folders"). It shows **at most 5 lines** on Free and **at most 10** on Pro and Program. Count only the lines he has to answer. The rest wait for next week.

## 1. Find the Home Map

Use SKILL.md, Every routine, step 1. If you found more than one map, the older ones go in this tidy (step 5).

## 2. List what is in his Drive

List every folder that has a row in the Home Map, by its ID. Gather each item you see as `{ id, name, kind, parent_id }`:
- `kind` is `folder`, `doc`, `sheet` or `md`; or pass Drive's `mimeType` instead.
- `parent_id` is the folder you listed.

Don't open folders he made himself. The check only needs what sits in the map's folders.

To save calls, skip the week folders of weeks already played. Past weeks hold only his own work, and the tidy never offers moves inside them.

## 3. Call the check

Call `rooski_tree_check` with `{ home_map, today, mode: "full", listing }`. Add `schedule`, `open_week` and `turn_date` when you have them.

## 4. Do these without asking

They change nothing he made:

| Field | What to do |
|---|---|
| `record` | Items the map missed: `slot`, `id`, `name`. Add each row to the map. A `tree_name` means its name differs from Rooski's; that shows up next week as a name line. |
| `build` | Missing items. Build them under the build rule. |

Skip any line for the map's own slot.

## 5. Show the lines that need his yes

Show them in this order, one per line, using the tool's `line` text, until you reach his cap:

| Field | The offer | On his yes |
|---|---|---|
| `twins` (skip any for the Home Map's own name; those are the old-copies line below) | Two items with one name in one folder. `keep_id` is the one the map knows. | He picks the one that stays. The others go to the `archive` row's folder. If the twin has a `slot`, the one he keeps gets that row. |
| `strays` | A folder he made where the tree has its own folders. `move_to` has a slot, a name and, when it is built, an ID. | Move `id` into `move_to.id`. If `move_to` has no ID, build that folder first. |
| `gone` | A map row whose item is no longer in its folder. | Look its ID up in Drive. If it is somewhere else, offer to move it back. If it is in the trash or not found, tell him; on his yes, drop the row, and the next check makes a fresh one. |
| `name_differs` | A name that differs from Rooski's (`name` and `tree_name`). | Rename `id` to `tree_name` and change its row's name. |
| `name` | A playoff folder that can carry its opponent. | Rename `id` to `to` and change its row's name. |
| `loose` | A file sitting in a folder that should hold only folders. `move_to` has a slot, a name and, when it is built, an ID. | Move `id` into `move_to.id`. If `move_to` has no ID, build that folder first. |
| Older Home Maps | "You have `<n>` old copies of your Home Map. Put them away?" | Move them to the `earlier` row's folder. |
| His Inbox | If `inbox.count` is more than 0: "Your Inbox has `<n>` items. Want to sort them now?" If the answer has no `inbox`, count the `inbox` row's folder from your listing. | Go through them (`inbox.items`, or your listing) one at a time. Suggest a home (SKILL.md, Where it goes). He says yes or names another. |

If lines are left over: "`<n>` more next week."

## 6. Make the moves

1. **Receipt first:** one receipt for every yes in this tidy (SKILL.md, Receipts before moves).
2. **Then the moves and renames,** in the order he said yes.
3. **Never move, rename or delete** anything he didn't say yes to. Nothing is ever trashed.

## 7. Close

1. Write a new Home Map with the recorded, built, renamed and dropped rows (SKILL.md, Writing the Home Map).
2. Tell him in one line what you tidied, with the count. If lines are left, add "`<n>` more next week."
3. If the answer has a `turn` line, say it last (`season-turn.md`).
