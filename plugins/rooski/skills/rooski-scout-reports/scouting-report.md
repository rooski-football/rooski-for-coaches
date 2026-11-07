# Opponent scouting report (`rooski_run` kind `opponent_scout`)

How a staff reads an opponent: who they are, film by film, then the tables in the order a coordinator works them. The voice is "they / their".

## Steps

1. **Call `rooski_run`** with `{kind: "opponent_scout", team, side}`. Add:
   - `seasons`, for an older year or when a coordinator came from that team;
   - `games: "last 3"`, for what they are doing lately;
   - `situations`, when he asked for red zone, 3rd down, 2-minute, backed up or coming out.
2. **Whose film is it?** Read the `games` table, and for an offense, `quarterbacks` (full detail).
   - If one quarterback or one stretch of games is a different team, run the report again on just those games and say so.
   - If the coordinator is new, his old team's film can be scouted with `team` set to that team's code. Name it as his old team.
3. **Pick the 3–5 findings that change a call.** They come from:
   - `tells`: rows marked TELL, a pre-snap look 12+ points off their base run rate on 12+ snaps;
   - `down_distance` and `third_down`: the downs where the run/pass split swings;
   - `run_game` and `pass_game`: the concept or pass type that carries their explosives;
   - `coverage`, `shell` and `pressure` (when scouting a defense): the call that changes by down.
4. **Drill one finding**, if it needs a second cut. Use `find_plays` with the row's filter, plus one `group_by`, e.g. `{offense, season, down: 3, distance_min: 7, group_by: "formation_group", universe: "competitive"}`. A row's `plays` ids go to `get_play_diagram` for the picture.
5. **Write** per `output-formats.md`: the read first, then the tables he asked for.

## The sections, and what each answers

| Section | What it answers | Watch |
|---|---|---|
| `at_a_glance` | Run/pass, success, yards/play, explosives, negatives, turnovers, 3rd-down conversions, red zone | Turnovers and TDs are counts. Every rate has its n |
| `games` | Each film: date, opponent, snaps, run %, success, explosive, waves | A game marked "base only" has no coverage or route detail |
| `quarterbacks` (full) | Who played QB, by jersey | A second QB with real snaps is a split worth its own run |
| `down_distance` | Run/pass and results by down and band | The bands come from the definitions printed in the report |
| `personnel`, `formation` | Their groupings and splits, with run % and results | Variants fold into their group: "12 (+Q)" is 12 |
| `tells` | Pre-snap looks that tip run or pass | Only pre-snap looks. Lift is in points off their base |
| `run_game` | Concepts by share, yards, success, explosive | Concept words are the play-by-play's |
| `pass_game` | Play action, screens, quick vs held, pressured vs clean | Sacks and scrambles are dropbacks, not attempts |
| `throws` (full) | Where the ball goes: direction by depth | Counts of charted throws |
| `coverage` | Their coverage families: share, success allowed, explosive allowed | Read only from games that charted coverage (`charted_games`) |
| `shell`, `coverage_by_down` | Single-high / two-high / zero, and each family's share by down | Shell is read from the coverage played, not the pre-snap look |
| `pressure` | Blitz rate by down and band, pressured rate, sacks; TELL where the blitz rate swings | Pressured = the QB was pressured, not a pressure call |
| `front`, `def_personnel` | Fronts and personnel with run share and yards allowed | |
| `situations`, `third_down` | Early downs, red zone (high/low), backed up, 2-minute; 3rd & 4th down converted | Converted = gained the yards to go or scored |
| `explosives` | Explosive runs and passes, negatives, turnovers, sacks: count, rate, per game | Play ids are the first of each |

## What the report cannot say (say so once; never guess)

- RB depth, WR splits, TE side, alignment tips.
- What they call after a big play, a sack or a turnover (sequencing).
- The opening script.
- Route concepts by side.
- The pre-snap shell shown versus played.
- Man versus zone.
- Score and game state.

For any of these, offer what it can answer instead. For a "tip sheet", the `tells` table is the honest version.

## Sample rules

- A finding the coach should act on needs MED or better (10+).
- LOW (5–9) is "a lead to check on film".
- A dash is a count, never a rate.
- One game supports a tendency, not a trend.
- With several seasons pooled, the lead lines say so, and the games table keeps each film apart.
