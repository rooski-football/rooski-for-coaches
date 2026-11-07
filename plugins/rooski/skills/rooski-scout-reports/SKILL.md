---
name: rooski-scout-reports
description: Builds opponent scouting reports, self-scouts and tendency studies from the program's play-by-play data in Rooski — down and distance, personnel, formations, run concepts, the pass game, coverage, pressure, red zone and 3rd down, every number with its sample size and source. Use when a coach asks to scout an opponent ("scout Kansas's offense", "give me their defense on 3rd and long", "what have they done their last three games"), to self-scout his own team ("self-scout our 3rd downs", "what does a DC see when he studies us", "are we predictable", "how many explosives are we giving up"), or asks how often a team does something by down, distance, personnel, formation, coverage or field zone ("how often do they run on 2nd and long", "what do they throw out of trips in the red zone"). Not for practice plans, recruiting, player grades on their own, a prediction of one call, or watching film.
---

# Rooski play-by-play reports

One ability with three report types. The server computes every number; this skill sets the order of the work, the house rules and what a good answer looks like.

## The tools

- **They come from the Rooski connector** (MCP server `rooski-ask-the-data`): `rooski_run`, `find_plays`, `get_play_diagram`, `get_player_grades`.
- **Match a tool by its name, not its prefix.** The coach named the connector when he added it (for example "Hornets Data"), so the name in front of the tool differs by program.
- **No Rooski tools in the list:** say once that the Rooski connector isn't connected, and that he adds it under Customize > Connectors. Never answer from general football as if it were his data.
- **`rooski_run` missing but `find_plays` there:** not every seat serves the full report. Build the answer from `find_plays` the way `tendency-study.md` lays out, and say the full report isn't on his seat.

## Pick the tool from the ask

| The coach asks for | Use | Reference |
|---|---|---|
| A scouting report on one team's offense or defense | `rooski_run` kind `opponent_scout` | `scouting-report.md` |
| A self-scout of his own offense or defense | `rooski_run` kind `self_scout` | `self-scout.md` |
| One question: how often, how many, by down, personnel, formation, coverage | `find_plays` with `group_by` | `tendency-study.md` |
| Player grades | `get_player_grades` (a live pull, never part of a report) | — |
| "What will they call on 3rd and 4?" | `find_plays` for the tendency with n, plus a plain line that no single call is certain | `tendency-study.md` |
| "Teams whose defense looks like this opponent" | `find_plays` (a league comparison is not a report kind) | `tendency-study.md` |
| One play drawn | `get_play_diagram` with a play id the report or `find_plays` returned | — |

Once a report kind is clear, open its reference file. Open `output-formats.md` before writing anything longer than one screen.

## The procedure (both report kinds)

1. **Pin the ask.** You need four things:
   - the team code: the play-by-play data's code, which `find_plays` rows carry, e.g. KSUN;
   - the side: offense or defense;
   - the span: no season means the newest loaded season; `seasons` takes "2025", "2019-2025" or "all"; `games` takes "last 3" or game ids;
   - the situations, if he named any: early down, 3rd short / medium / long / XL, red zone, 2-minute, backed up, coming out.

   Ask only when the team is unclear. Otherwise go with the defaults and state them.
2. **One `rooski_run` call, `detail` concise.** Use `detail` full only when he asks for the whole book. A full report can come back in pages; `next_page` carries the arguments for the next page.
3. **Read the lead lines before the tables.** They tell you:
   - which seasons the report covers;
   - which fields a season did not chart;
   - which games are short a wave;
   - that kneel-downs are still in on export-loaded games.

   Any of these that bears on the answer goes into the answer.
4. **Drill down only where it changes the read.** Use at most 5 calls:
   - `find_plays` to cross one cell by another field;
   - `get_play_diagram` on a play id from the row the coach should see.
5. **Write it** the way `output-formats.md` lays out: a one-screen read first, then the tables he asked for.

## House rules (every report, every answer)

1. **Every number comes from a tool, as printed.** Never re-total a table. Never add rows together. Never compute 100 minus the run rate. If the tool did not print a number, it does not go in the answer.
2. **Every rate carries its n**, as printed: `58% (156/269)`.
   - `LOW` means 5–9 snaps: a film lead, not a tendency.
   - A dash means fewer than 5 snaps: give the count, never a rate.
   - A tier word (HIGH / MED / LOW) goes beside any rate you lead with.
3. **End with the Source line, word for word.** It starts "Source:". A table you quote carries its own Source line.
4. **Uncharted is not zero.** A season or game that did not chart a field is out of that table, and the report names it. Say "not charted then". Never say "never happened".
5. **Say which definitions you used** when they matter. The report prints each one and where it came from (the program's own, or the Rooski default): success, explosive, 3rd-down bands, red zone.
6. **Quote the table's own labels.** "3rd & 3–6" stays 3rd & 3–6. A coach's "3rd and medium" is the band the report printed for it.
7. **"Pressured" means the QB was pressured.** It is not a pressure call. "Blitz" means an extra rusher was sent. Never trade one word for the other.
8. **2-minute is the clock** (the last 2:00 of the 2nd or 4th quarter). A true two-minute call is hurry-up by feel, which the data can't see; say so if he means the hurry-up.
9. **Each film is its own.** The games table shows each game on its own line. A lean that lives in one game is said as one game. When the coordinator or the quarterback changed, split the span with `games` or `seasons`. Never blend across that change.
10. **No grades in a report.** Grades are a live pull, and only when he asks (`get_player_grades`).
11. **Call it play-by-play data.** The Source line the tool prints is the only statement of where the data comes from; never add one of your own.
12. **Report the threat, never the fit.** Write "Counter is their most explosive run", with its rate and n. Never write how to defend it, or how they should play it. The call is the coach's.
13. **A finding must change a call.** A finding that lists three plays and predicts nothing, or tells a coordinator what he already knows, is cut. A weak finding stays in as "a lead to check on film", with its count.
14. **Check before saying "not in the data."** First look at what the report and `find_plays` can say. When the store really can't answer something (receiver splits, RB depth, what they did after a big play), say so once, plainly, and give what it can answer.
