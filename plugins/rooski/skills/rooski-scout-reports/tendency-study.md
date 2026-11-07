# Tendency study (a coach's question → `find_plays`)

Use this when a coach asks one question ("how often do they…", "what do we do on…"). There is no report kind for it: the answer is one or two `find_plays` calls. If the question needs success, explosives or conversions, which `find_plays` does not compute, run `rooski_run` with `situations` and quote that table.

## Turn his words into filters

| He says | `find_plays` filter |
|---|---|
| their offense / their defense | `offense: "<code>"` / `defense: "<code>"` |
| 3rd and short / medium / long / XL | `down: 3`, plus `distance_min` and `distance_max` from the program's bands (short 1–2, medium 3–6, long 7–10, XL 11+ unless his definitions say otherwise) |
| 1st and 10 | `down: 1` (every first down) |
| red zone / inside the 10 / goal line | `red_zone: true` / `ytg_max: 10` / `ytg_max: 3` |
| backed up (own 1–5) / coming out (own 6–19) | `ytg_min: 95` / `ytg_min: 81, ytg_max: 94` (unless his definitions say otherwise) |
| 11 personnel, 12 personnel | `personnel: "11"`. Variants like "12 (+Q)" are separate values, so `group_by: "personnel"` shows them |
| trips, empty, 2x2 | `group_by: "formation_group"`, then filter on the value he means |
| Cover 3, Cover 1 | `coverage: "COVER 3"` (it matches the variants too: 3 Seam, 3 Cloud; "COVER 2" also catches Cover 2 Man, so `group_by: "coverage"` when that matters) |
| blitz / pressure | `blitz: true` (extra rusher) / `pressure: true` (QB pressured) |
| play action, screen, motion, tempo | `play_action`, `screen`, `motion`, `tempo` |
| this year / last year / since 2019 | no season (the newest loaded season) / `season:` the year before it / `seasons: "2019-<newest>"`, reading the newest from the season line |
| self-scout snap rule | `universe: "competitive"` |

## Cross two things

Use one filter set plus one `group_by`. Example: their 3rd & long (7–10) by formation is `{offense, season, down: 3, distance_min: 7, distance_max: 10, run_pass: "P", group_by: "formation_group", universe: "competitive"}`. For a second cross, run it again with the next value as a filter. Never add one answer's counts to another's.

## Read the answer before quoting it

- **The lines before the JSON are part of the answer.**
  - POOLED means more than one season or both teams.
  - The season line means the newest season only.
  - A charting line means a season or games that did not chart the field.
  - Say each one that applies.
- **n is the real count.** Never count the play list yourself. `group_by` gives every value with its n and tier.
- **A zero needs a reason.** It may mean the games are not loaded or the field is not charted, so check before saying "never".
- **Several seasons:** `group_by: "season"` gives each season as a rate. Compare rates across seasons, not counts, because the number of teams charted changed.

## Sample rules

- HIGH is 25+, MED 10–24, LOW under 10.
- A LOW cell is a film lead.
- Never lead with a rate under 5 snaps.
- One film's lean is said as one film's.

## Not a tendency question

- **A single-call prediction** ("what will they call?"): give the tendency with n and say plainly that no call is certain.
- **"Teams that look like this opponent":** this is a league comparison. Answer it with `find_plays` across teams if he gives the trait. It is not a report.
