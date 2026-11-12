# Upgrade: his folders into the program drive

**Program plan, head coach only.** His own AI runs this, in chat. He owns his files, and only an owner can move them into a program drive. Every move keeps the item's ID, so every link he has still works.

## 1. Two maps

- **His Home Map:** SKILL.md, Every routine, step 1. Its header must say `tree: personal`.
- **The program's Room Map:** search the program drive the same way. It begins `# Home Map` and its header says `tree: program`.
- **No Room Map yet:** the program drive isn't built. Rooski builds it. If it lives in his own Drive and Rooski can't reach it, use the program steps in `setup.md`, with `program_upgrade: true`. Then come back here.

## 2. Ask for the plan

Call `rooski_tree_plan` with `{ step: "upgrade", home_map, room_map, today }`. Send only these four; the tool refuses any other argument for this step.

If the answer has `ok: false`, show `problems` in plain words and stop. One of them is "already upgraded".

Read the answer:

| Field | Use |
|---|---|
| `receipt` | `name`, `parent_id`, `text`. Write it **before any move**. |
| `moves` | In `step` order: `op` (`move` or `rename`), `id`, `from_parent_id`, `to_parent_id`, `from_name`, `to_name`. |
| `make` | What the upgrade adds: `tree` (`personal` or `program`), `slot`, `parent_id`, `kind`, `name`, `starter`, `from`, `master_id`. |
| `twins` | A program file that now has two copies (his and the starter). Each has a `line` and `on_yes_only`. |
| `home_map_after` | `remove` (the slots that moved out) and `header`. |
| `room_map_add` | The rows the program map gains: `slot`, `id`, `name`. |
| `summary` | One line for him. |

## 3. Ask once

Show `summary`, then: "Every move goes on a receipt first, nothing is deleted, every link keeps working, and you can undo it. Go?"

## 4. On his yes

1. **The receipt:** make `receipt.name` as an `.md` in `receipt.parent_id`, with `receipt.text`.
2. **The moves,** in `step` order:
   - Before each one, look the item up by `id`. If it is already in `to_parent_id` under `to_name`, skip it.
   - `move`: move `id` into `to_parent_id` and name it `to_name`.
   - `rename`: name it `to_name` where it is.
   - If a move fails, stop. Tell him which step it was, and don't write either map yet. The receipt shows where it stopped. Next time, ask for the plan again with the same two maps; the moves already done are skipped.
3. **The `make` items,** under the build rule:
   - `from: "every_year_master"`: copy `master_id`.
   - `from: "rooski_starter"`: a starter item (SKILL.md, The build rule, step 5).
   - `from: "empty"` or none: an empty file of that `kind`.
4. **`twins`:** show each `line`. On his yes, receipt first, then move the starter copy to the program's `archive` row.

## 5. Write both maps

1. **His Home Map:**
   - the header is `home_map_after.header`;
   - drop the rows in `home_map_after.remove`;
   - add a row for each `make` item with `tree: "personal"`.
2. **The Room Map:**
   - the current header with `written:` set to today;
   - add `room_map_add`;
   - add a row for each `make` item with `tree: "program"`.
3. Write each map the usual way (SKILL.md, Writing the Home Map).
4. Tell him in one line how many items moved, from the `summary`.

## Undo the upgrade

There is no tool step for this. On his yes:
1. Write a new receipt.
2. Follow the upgrade receipt's `undo:` lines from the bottom up.
3. Write both maps back:
   - **His Home Map:** start from the copy before the upgrade, in his `earlier` row's folder.
   - **The Room Map:** start from the copy before the upgrade, in the program's `archive` row's folder.
   - In both, keep any row added since the upgrade whose item didn't move back.
