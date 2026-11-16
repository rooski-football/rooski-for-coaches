# Rooski's help: the Sunday tidy and the share

Some help comes from Rooski itself, outside this chat. It runs once he shares his `! Rooski Drive` folder with Rooski's share account, and only on a paid plan. On Sundays Rooski looks through his Rooski Drive and moves Office lock files and exact copies, writing each move down first. Everything else still happens here, with his yes.

Rooski's answers carry the facts:
- **The connector's start-of-chat answer** has a `drive` block: `plan`, `drive_share`, `share_account` and, only when Rooski's help is on, `tidy`.
- **`rooski_get` kind `my_data`** gives `plan`, `drive_share` and `share_account` too, but never `tidy`.

Use only these facts. Never guess one, and never say Rooski did something these facts don't show.

## Who gets what

| Rooski says | What you do |
|---|---|
| `plan` is `free`, or no plan | No offer and no Rooski help. Never say anything about a share account. The weekly tidy here is his help. |
| `plan` is `pro`, `drive_share` is `none` or `lost` | The share offer (section C), when it is due. |
| `plan` is `pro`, `drive_share` is `asked` | No offer. If he asks, one line: "Rooski checks your folder overnight. Nothing changes in your Drive until it can open it." Never say help has started. |
| `plan` is `pro`, `drive_share` is `active` | Section A when the `drive` block includes `tidy`. If he asks where it stands: "Rooski can open your Rooski Drive folder. Its Sunday cleanup is on." |
| `plan` is `program`, any `drive_share` | No offer. On `tidy`, section A with the program drive's facts, never his own. If he asks about sharing his own folder: "Sharing your own Rooski Drive doesn't add anything on your plan yet." |

## A. When `tidy` is there (after the light check)

`tidy` holds `last_run`, `moves_done`, `receipt_to_file` and `open_digest_lines`. Do these three steps in order, once per chat.

`last_run` is only the date of Rooski's latest pass. Never say from it alone that Rooski looked through or tidied anything; it is set even when Rooski couldn't.

### 1. File the receipt (Pro)

Only when `receipt_to_file` isn't null. It holds `batch_id`, `file_name`, `folder` and `text`.

1. **The folder is the Home Map's `receipts` row,** read by its ID. `folder` is only words to show him; never search by it. If the map still has no `receipts` row after the light check, skip filing this chat.
2. **Look first.** List that folder. If any `.md` there has a name that starts with the date in `file_name`, and its text holds `batch_id`, it is already filed. Do nothing more. Until Rooski marks it filed, `receipt_to_file` keeps coming back; this check is what stops a second copy.
3. **Otherwise make it:** a plain `.md` with conversion to a Doc turned off, named `file_name` (add ` 2`, ` 3` if that name is taken), with `text` exactly as given. Don't change a character of it.
4. **No yes is needed.** It is a record and changes nothing he made.

### 2. Tell him what moved

Only when `moves_done` is more than 0. With 0, say nothing about moves, and never say "moved" from any other fact.

- **Pro:** say it in the chat where you file that receipt (step 1.3), and only if the date in `file_name` is `last_run` (then the count and the receipt are the same pass). If the receipt was already there, he has heard it; say nothing unless he asks. When he asks later, take the date and the count from the newest Rooski receipt in that folder (its name, and its rows marked `moved`), never from `last_run`.
- **Program:** say it only when he asks what Rooski did. Rooski's program pass runs most nights, so there is no one day to name.

**Pro, one idea per line:**
> "Rooski moved `<moves_done>` files on `<the date in file_name>`.
> Each was a leftover temp file from Word, Excel or PowerPoint, or an exact copy.
> Nothing was deleted.
> The list is in your `<receipts row's name>` folder.
> Want one back? Tell me which."

**Program, one idea per line** (the program's facts: never "your rooms" or "your files"):
> "The last time Rooski moved files in the program drive, it moved `<moves_done>`.
> Each was a leftover temp file from Word, Excel or PowerPoint, or an exact copy.
> Nothing was deleted."

The temp files are Office lock files: names starting `~$`, under 1 KB, left behind when a file was open.

### 3. The things worth a look

`open_digest_lines` is a count. No tool gives the lines themselves yet.
- **Pro, above 0:** at his first chat of the week, say it in one line and offer the weekly tidy in place of the usual offer (`session-start.md`, step 6): "Rooski's Sunday pass found `<n>` things in your Rooski Drive worth a look. Want a quick tidy now?" Rooski keeps at most 10, so at 10 say "at least 10". On his yes, open `weekly-tidy.md`. It finds the same kinds of things, here in chat.
- **Program, above 0:** say it only when he asks: "Rooski's last pass found `<n>` things worth a look in the program drive."
- **If a tool in his list ever returns the lines,** show at most 10, this week's files first, one per line.
- **0:** say nothing.
- Rooski keeps these lines; nothing is sent. Never say Rooski sent him anything or will send anything.

## B. Putting files back

He may ask after step 2 or in any later chat ("put back what Rooski moved").

1. **Find the receipt.**
   - Pro: in the `receipts` row's folder, the `.md` that holds the move. Rooski's receipts are the ones with a `batch:` line and a File / From / To / Why / Status table; the others are yours.
   - Program: the program drive's receipt for that day, in the Room Map's `receipts` row folder.
   - Each table row reads `| name (file ID) | from folder (folder ID) | to folder (folder ID) | why | status |`. Only rows marked `moved` were moved.
2. **One file, on his yes:**
   - Write your own receipt first (SKILL.md, Receipts before moves), with why: "he asked to put back Rooski's move".
   - Move the file ID back into its from folder ID.
   - **Pro:** so Rooski doesn't move it again next Sunday, add it to his Home Map's `## Not tidied` list (SKILL.md, Writing the Home Map): `### <file ID>: put back <today>`.
   - **Program:** tell him that if it's still an exact copy, Rooski may move it again. If he wants it kept where it is, pass that to Rooski (step 3).
   - **If his Drive tools can't move it,** give him the steps: "In Google Drive, open `<to folder>`, tap the three dots on `<name>`, tap Move, and pick `<from folder>`." Write the receipt and the `## Not tidied` line only after he says it's done.
3. **All of them:** Rooski puts the whole set back.
   - With `request_help` in his tools, call it with `request`: his words, word for word. If they don't name the day, add the date from the receipt's name after them.
   - If the call worked, tell him: "Passed to Rooski. The team will put them back." If it failed, use the line below.
   - Without `request_help`: "Tell your Rooski contact you want Rooski's `<date>` moves put back."
   - Never give a day it will happen.

## C. The share offer (Pro)

**Make it only when all of these hold:**
- Rooski's `plan` is `pro` (never from the map's header);
- `drive_share` is `none` or `lost`;
- `share_account` isn't null;
- his Home Map exists;
- it's due: his Home Map has no `# share offered:` line, or that line's year is older than the map's `live_year`.

**When:** at the end of a chat's light check or weekly tidy, never in the middle of other work. Once offered, it waits for the next season.

**The offer.** With `lost`, open with: "Rooski can't open your `! Rooski Drive` folder anymore, so its Sunday cleanup has stopped." With `none`, open with: "Want Rooski to help keep your Rooski Drive clean?" Then the promise lines, as written, one per line:

> "Share your `! Rooski Drive` folder with Rooski and here's what happens:
> - On Sundays, Rooski looks through your Rooski Drive for leftover temp files from Word, Excel and PowerPoint, and for exact copies.
> - It moves those into your `<earlier row's name>` folder. That's all it moves.
> - To spot exact copies, it compares your files, Docs included. It never changes what's in them.
> - Every move is written down before it happens. I put that list in your `<receipts row's name>` folder.
> - It never deletes anything, never makes files in your Drive, and never renames anything.
> - Anything else that looks out of place, it leaves alone and notes. I'll tell you how many here.
> - Want it to stop? Un-share the folder."

Take the two folder names from his Home Map's `earlier` and `receipts` rows. If either row is missing, run the light check first and offer next chat.

**How he shares:**
> "Open `! Rooski Drive` in Google Drive, tap Share, add `<share_account>` as an Editor, and tap Send. Tell me when it's done."

Use `share_account` exactly as Rooski gave it. Never type any other address.

**On his "done":**
1. Call `rooski_save` with `{ kind: "drive_share", status: "asked", folder: "<the Home Map's root row ID>" }`.
2. Save the newest Home Map's ID to his profile, so Rooski reads the right map: `rooski_save` with `{ kind: "profile", scope: "coach", fields: { storage_map: { home_map: "<the map's ID>" } } }`. From now on, every map you write is saved the same way (SKILL.md, Writing the Home Map, step 4).
3. Tell him: "Got it. Rooski checks the folder overnight. Nothing changes in your Drive until it can open it."
4. Never say Rooski's help has started. Only a later chat whose `drive_share` reads `active` shows that.
5. If a save is refused, tell him in plain words what wasn't saved, and why.

**On no, or not now:** nothing is saved anywhere but the marker.

**The marker, every time you make the offer:** one line in his Home Map, `# share offered: <live_year>`, right under the header fields. If this chat writes a new map anyway, put it there. Otherwise write one now (SKILL.md, Writing the Home Map). A new `live_year` after the season turn makes the offer due again.

**He asks first** ("how do I let Rooski help keep my Drive clean?"):
- Pro, with `none` or `lost`: answer with the offer's words and the steps (with no Home Map, offer setup first; with no `earlier` or `receipts` row, run the light check first). It's his ask, not a new offer, so it's fine even if the offer was made this season. Write the marker with this season's `live_year` if it isn't there yet.
- Pro, with `asked` or `active`: say where it stands, in one line, from the table above.
- Program: "Sharing your own Rooski Drive doesn't add anything on your plan yet. I can tidy it with you here anytime."
- Free, or no plan: "I can tidy it with you here anytime. Want a quick tidy now?" If he asks whether Rooski can do it on its own, say it comes with a paid Rooski plan. Never a price, and never a word about sharing his folder.
