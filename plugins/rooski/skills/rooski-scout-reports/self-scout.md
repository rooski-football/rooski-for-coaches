# Self-scout (`rooski_run` kind `self_scout`)

This is the coach's own unit, the way the next opponent will see it on film. The voice is "you / your" about his unit, and "they" about the offenses or defenses he faced.

## The snap universe (say it once)

- **Competitive snaps on downs 1–4.**
- **Left out, and counted in the census:** special teams, snaps nullified before the snap, 2-point tries, offensive penalties, garbage time, kneel-downs (where tagged) and victory formation.
- **Four-minute snaps stay in.** The store keeps no four-minute tag.
- **Recount it:** `find_plays` with `universe: "competitive"` answers the same snaps.

## Steps

1. **Call `rooski_run`** with `{kind: "self_scout", team: <his code>, side}`. The span defaults to the newest season.
   - `games: "last 3"` is the stretch an opponent will study first.
   - `situations` narrows the report to his question (3rd down, red zone, 2-minute).
2. **Read the sections in coordinator order.**
   - An **offense** opens with its broad tendency: run/pass by down, then the tells.
   - A **defense** opens with structure: front, then shell and coverage by down, then pressure by situation.
3. **The honesty check: what an opponent sees.**
   - **Offense:** the `tells` table. Each TELL row is a pre-snap look (personnel, formation, personnel and formation together, hash, motion, tempo) whose run rate sits 12+ points off his base on 12+ snaps. Those are the tips a DC will find.
   - **Defense:** `pressure` rows marked TELL. These are downs where his blitz rate swings 12+ points off his own.
   - **Coverage:** `coverage_by_down` shows when one family carries a situation.
4. **Recent against the whole span.** `recent` puts the last 3 games beside every game. A change of 5+ points reads "trending", and "too few snaps" means just that. Recent needs more than 3 games in the span.
5. **Drill only to show him the plays.** Use a row's `plays` ids with `get_play_diagram`, or `find_plays` with the row's filter for the full list.
6. **Write** per `output-formats.md`.

## What to lead with

- **Lead with what he does well**, then the tells, then what is trending.
- **Never lead with a blank or a zero.** Example (numbers made up): "you pressure more in the red zone: 10 of 25 (40%) against 25%".
- **Every tell gets its counterexample** from the same row: the snaps that went the other way.
- **Not enough snaps is a result.** "Not enough snaps to say" is said, not hidden.

## Lines a self-scout never crosses

- **No "you should".** The report says what an opponent sees. What to change is the coach's call, so offer it as a question for him ("a look worth breaking?").
- **Each film stands alone.** A lean that lives in one game is said as one game. Never sum or average weekly numbers. Re-run the span instead.
- **"Pressured" means the QB was pressured; "blitz" means an extra rusher was sent.** On a defense self-scout, "pressured" is about the QBs he faced.
- **No grades.**

## Explosives for and against (two runs)

"How many explosives are we getting and giving up" takes two calls: `side: "offense"` and `side: "defense"`. Quote each `explosives` row with its count, rate and per-game figure, and say which explosive definition the report printed.
