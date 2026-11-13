# Setup: build his Rooski Drive

Every plan gets this. It is Lesson 2. His own AI builds his personal tree here, in chat, so every folder and file is his. A program drive is built by Rooski; the program steps at the end are only for when Rooski can't.

## 1. Look before you build

- **Find the Home Map** (SKILL.md, Every routine, step 1).
  - Found: this is a resume. Go to section 5.
  - Not found: search his Drive once for a folder named `! Rooski Drive`. If one is there, the build reuses it. Never make a second one.

## 2. Ask only what you don't know

| Argument | Ask |
|---|---|
| `plan` | "Which Rooski plan are you on: Free, Pro or Program?" Not sure: `free` (SKILL.md, step 4). |
| `head_coach` | "Are you the head coach?" |
| `life` | "Do you want an extra folder for life outside football?" |
| `teaching` | "Do you teach classes? Want a folder for that?" |
| `schedule` | "What's your schedule: week, opponent, date?" No schedule yet: build without it. Week folders come when he adds it. |
| `last_game_date` | Only if his season is already over: "When was your last game?" |

Use `tree: "personal"`. Pass `last_regular` only if he names his last regular-season week. Pass `turn_date` only from his Season Hub.

## 3. Ask for the plan

Call `rooski_tree_plan` with `{ tree, plan, today, head_coach, life, teaching, schedule }`, plus any of `last_regular`, `last_game_date` or `turn_date` you have. Leave `step` out; setup is the default.

Read the answer:

| Field | Use |
|---|---|
| `live_year`, `live_year_basis` | The season you build for. Past his turn date, it is next year. |
| `weeks`, `weeks_note` | The weeks you will build, or why there are none yet. |
| `counts` | The total to tell him. |
| `build_rule` | The rule (SKILL.md). |
| `home_map` | `file` (the map's name), `in_slot` (its folder's slot), `header`, `table`, `row` (the row shape). |
| `items` | In build order: `slot`, `parent`, `depth`, `kind`, `name`, and `starter` / `when` on some. |
| `put_away` | Only when setup falls after his last game (section 6). |

Tell him in one line: "I'll build your Rooski Drive for the `<live_year>` season: `<counts.total>` folders and files. If this chat stops, the next one picks up where it left off."

## 4. Build level by level

Use the build rule in SKILL.md, item by item, in the plan's order.

1. **Depth 0 is the top folder.** Reuse the one from section 1 if there is one; otherwise make it with the plan's name.
2. **For each parent,** list it once, then reuse or make each of its items.
   - A starter item: the name and type from the plan, and one line saying what it is for.
   - **A head coach** (`head_coach: yes`): the Practice Plan Master in Templates gets one line pointing to the real one, the `p.practice_plan` item, named with its folder's name from the plan: "Your weekly practice plans are copied from the Practice Plan Master in `<that folder>`."
   - The item whose slot is `home_map.slot` is the map itself. Don't make it as an empty file; step 3 writes it.
3. **Write the first map early.** As soon as the folder for `home_map.in_slot` exists, write the map into it:
   - name `home_map.file`;
   - text: `home_map.header`, a blank line, `home_map.table`, and one row per item built so far.
4. **After each level,** write a new Home Map with every row so far (SKILL.md, Writing the Home Map). Move the old versions once, at the end, under one receipt. If the chat stops first, the next chat still picks the newest (SKILL.md, Every routine, step 1) and puts the rest away.
5. **Watch the count.** About 55 tool calls is as far as one chat may go. If you are close, finish the level, write the map, and tell him: "Your Rooski Drive is part built. Say 'pick up my Rooski Drive setup' in a new chat and I'll finish it."

## 5. Resume a stopped setup

1. Tell him: "Picking up your setup where we left off."
2. Call `rooski_tree_check` with `{ home_map, today, mode: "full" }`. Leave out `listing`.
   - Pass `schedule` again, from his Season Hub or from him. The check only knows the weeks already in the map, so any week folder not built yet comes from the schedule.
3. Its `build` holds everything still missing, level by level, with `parent_id` wherever the parent is already in the map. For the rest, take the parent's ID from the rows you add as you go.
4. Build each item under the build rule. The listing in step 3 of the rule catches anything made after the last map write.
5. Skip any line for the map's own slot.
6. Write the Home Map after each level. When `build` is empty, the build is done: run section 6 (Finish).

## 6. Finish

1. **Star** the top folder. Tell him: "Tap Starred in Google Drive to find it."
2. **Save the top folder's ID** to his Rooski profile with `rooski_save`, if it is in his tools: `{ kind: "profile", scope: "coach", fields: { storage_map: { provider: "google_drive", home_folder: "<top folder ID>" } } }`.
3. **`put_away`** (only when setup came after his last game):
   - A line with an `id`: show its `line`. On his yes, receipt first, then move it to `to_id`.
   - A line with no `id`: nothing of that season was built, so there is nothing to move. Skip it.
4. **Sum up in one line:** "Built `<counts.total>` folders and files for your `<live_year>` season."
5. **Move the older map versions** (SKILL.md, Writing the Home Map, step 3).

## Program drive (only when Rooski can't build it)

On the Program plan, Rooski builds the program drive. Use these steps only if the head coach's program folder lives in his own Drive and Rooski can't reach it.

1. Ask for `level` (`"hs"` or `"college"`) and `school` (the name the top folder carries).
2. Set `program_upgrade: true` if his own seasons and program files will move in later (`upgrade.md`).
3. Call `rooski_tree_plan` with `{ tree: "program", plan: "program", today, level, school, schedule, program_upgrade }`.
4. Build it the same way. Its map is the Room Map (`home_map.file` names it). It sits where `home_map.in_slot` says.
5. A program tree is several times a personal one (`counts.total`). Tell him at the start that it will take more than one chat.
