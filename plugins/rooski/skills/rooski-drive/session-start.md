# Light check: the start of a chat

Every plan gets this, in every chat that touches his Drive or Rooski, once per chat. It builds what today needs (a week that's now scheduled, the next playoff week, the open week's files). It also names playoff folders once the opponent is known, and says when the season turn is due.

**Skip it** if the Rooski connector already returned a light check this chat. Act on that answer instead (steps 3 and 4).

## 1. Find the Home Map

Use SKILL.md, Every routine, step 1. With no map there is nothing to check. Offer setup only if he is asking about his Drive.

## 2. Call the check

Call `rooski_tree_check` with:
- `home_map`: the map's whole text;
- `today`;
- `mode`: `"light"`.

Add these when you have them:
- `schedule`: from his Season Hub;
- `open_week`: if he named the week;
- `turn_date`: from his Season Hub;
- `last_game_date`.

Don't send a `listing`; that is for the weekly tidy.

## 3. Read the answer

| Field | What to do |
|---|---|
| `ok: false` with `home_map.errors` | The map couldn't be read, so nothing was checked. Tell him once, in plain words, that his Home Map has a problem, with the first error. Offer to write a clean map without the bad rows. The weekly tidy finds those items again. |
| `build` | Items missing today, level by level, with `parent_id` where the parent is in the map. Build them under the build rule. No yes is needed. |
| `build` items with `when: "week_start"` | The open week's files (Pro and up). Make them the week-open way (`week-open.md`, step 4). |
| `name` | A playoff folder that can now carry its opponent. Each has `from`, `to`, `id` and a `line`. |
| `turn` | The season turn is due: `season`, `line`, and `args` (the dates the check used). |
| `summary`, `live_year`, `open_week` | Use these for your one line to him. |
| `home_map.warnings` | Ignore them unless one stops your work. |

## 4. Act

1. **Build** every `build` item (SKILL.md, The build rule). Skip any line for the map's own slot.
2. **Name lines:** batch them into one question. "Your playoff folder can carry the opponent now: name `<from>` as `<to>`?" On his yes:
   - write the receipt first;
   - rename each `id` to `to`;
   - change its row's name in the map.
3. **Turn:** say `turn.line` as written.
   - Yes: open `season-turn.md` and pass `turn.args`.
   - No or later: leave it. The check raises it again.
4. **Write a new Home Map** if anything was built or renamed (SKILL.md, Writing the Home Map).
5. **Tell him in one line** what changed, using names from the answer. For example: "Added `<names from build>`." If nothing changed, say nothing about his Drive.

## 5. Once a week

At his first chat of the week, offer the weekly tidy in one line: "Want a quick tidy of your Rooski Drive?" On yes, open `weekly-tidy.md`.
