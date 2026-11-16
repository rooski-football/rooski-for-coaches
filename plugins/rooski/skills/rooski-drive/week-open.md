# Week open: a game week, a playoff week, a schedule change

**Pro and Program, in his own Drive.** On Free the light check builds the week folders and there are no week files, so run `session-start.md` instead. A program drive's weeks are opened by Rooski, not here.

**When:** he says "open this week" or names this week's game, a new week starts, or his schedule changes (a playoff game, a new opponent, a moved date).

## 1. Find the Home Map

Use SKILL.md, Every routine, step 1.

## 2. Pin the week and the schedule

1. **The schedule** comes from his Season Hub, or from him. Send every game you know as `{ week, opponent, date, playoff }`. The check lays it over the weeks already in the map.
2. **The week:** the one he names. Otherwise leave `open_week` out, and the check takes the next game on or after today.
3. **A playoff game** is `{ week, opponent, date, playoff: true }`. The opponent may be empty until it is known.
   - Its week number is the next one after the last game played.
   - The first playoff game takes the playoff week already in the map.

## 3. Call the check

Call `rooski_tree_check` with `{ home_map, today, mode: "light", schedule }`, plus `open_week` when he named the week.

Read `open_week`, `build` and `name` (the table in `session-start.md`).

## 4. Build the week

1. **Folders first:** build each folder in `build` under the build rule (a new week or playoff week).
2. **The week's files** are the `build` items with `when: "week_start"`. Each one says where it comes from:
   - `from: "every_year_master"`: copy the file `master_id` (its master, `master_name`).
   - `from: "rooski_starter"`: the master isn't in the map. Make the file as a starter item (SKILL.md, The build rule, step 5).
   - `from: "empty"`: make an empty file of its kind.
   - **A head coach's practice plan:** if the header says `head_coach: yes` and not `upgraded: yes`, the Practice Plan's master is the `p.practice_plan` row (in his head coach folder), not the one in Templates. Copy that row's ID when the map has it; otherwise use the line's own source.
   - **No `from` on the line** (an older connector): find the masters once the old way. Call `rooski_tree_plan` with the map header's answers (`tree`, `plan`, `head_coach`, `life`, `teaching`, `upgraded`), plus `year` set to the header's `live_year`, `today`, `schedule` and `open_week`. The master for a week file is the plan item with the **same `starter`** whose `parent` is `templates` (for a head coach's practice plan, `p.practice_plan`). Its Drive ID is that slot's row in the Home Map.
3. **For each week file:**
   - list the week folder first (the build rule);
   - then **copy** the master into the week folder (`parent_id`) under the item's `name`.
   - If there is no master to copy, make the file as a starter item (SKILL.md, The build rule, step 5).
4. **Name lines** (a playoff opponent is now known): one question; on his yes, receipt first, then rename (`session-start.md`, step 4).

## 5. Move the star

1. Star the open week's folder.
2. Unstar the week before it, if it was starred.
3. If his Drive tools can't star, tell him: "Open the week folder, tap the three dots, then Add to Starred."

## 6. Write the map and tell him

1. Write a new Home Map (SKILL.md, Writing the Home Map). Use the current header with `open_week:` set to the week you opened and `written:` set to today. Add every new row.
2. Tell him in one line, with names from the answer: "`<week folder>` is open: `<file names>`."
