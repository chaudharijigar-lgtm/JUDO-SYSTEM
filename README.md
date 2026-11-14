# Judo Tournament System

Draw (weight category knockout with seeding) + live scoreboard + TV display, in one page.

## Files
- `index.html` – the whole system
- `xlsx.full.min.js` – Excel reader/writer (works without internet)
- `sw.js` – offline support (opens even with no internet after the first visit)
- `judo_demo_athletes.xlsx` – demo list: 359 athletes, all 14 senior IJF weight categories

## Deploy on GitHub Pages
1. github.com → New repository → name `judo-system` → Public → Create.
2. "uploading an existing file" → drag ALL files from this folder → Commit changes.
3. Settings → Pages → Source: Deploy from a branch → main → /(root) → Save.
4. Open `https://<username>.github.io/judo-system/` on the admin laptop in Chrome (once with internet).

## Tournament day
- Admin laptop: open the link (only ONE admin tab). TV on HDMI: Windows + P → Extend → Scoreboard tab → Open TV window → click TV once.
- Data saves automatically in the laptop's browser after every change; closing and reopening continues from the last point.
- Backup / Restore → Download backup file (keep a copy on a pen drive).
- Download Excel (results): medal winners, rank list, district tally, match log, all participants.

## Printing
- Draw tab → Print (or press Ctrl+P anywhere in the admin screen) → choose the stage → Print.
- Prints always come out black text on white paper, in dark mode or light mode. Blue side = black bar, white side = grey bar, winners shaded grey.
- Every sheet fits on one A4 landscape page: long first rounds shrink slightly, long rank lists go into 2–3 columns.

## Referee & file sheets (Draw tab → Print → choose)
- **Blank fixture for referees**: entry & seeding list plus every stage with empty name lines and I / W / Y / S boxes. "As per category" prints that category's bracket; an empty-sheet size (2 – 64) prints it without any athletes.
- **Score sheet · blank**: same heading as the results (tournament, category, mat, draw ID, QR), one row per contest in match order with empty score boxes for White and Blue, golden score, time, winner and remarks.
- **Score sheet · filled from the scoreboard**: made automatically from what the admin scores — final I / W / Y / S for both sides, golden score, contest time, winner, how it was won, when it was recorded, and a score log of every score/penalty with its match time. Print it after each category for the file.

## Weigh-in (Draw tab → Athletes → ⚖ Weigh-in)
- Pick the category on the left; the list shows its athletes. Type the weight in kg and press Enter (jumps to the next athlete).
- Above the category limit (e.g. 60.5 in −60 kg) = OVER → disqualified automatically. The row turns red, the opponent gets a bye, the draw shows the name struck through with "DQ", and the results show "DQ".
- Typed a wrong weight? Correct it and the athlete is back in the draw. "+" categories have no upper limit. An allowance in grams can be set (default 0).
- If an athlete who already fought is found overweight, he is flagged but no result is changed (decide on the mat).
- An Excel column named "Weigh-in" or "Actual weight" is read as the official weight on upload.

## Blank forms with no athletes at all
Print → "All blank forms" (or Athlete list / Weigh-in sheet / Blank fixture / Score sheet) → choose an empty-sheet size (2 – 64 athletes) → Print.

## Contest time by age group (Draw tab → Tournament details)
Sub-Junior 3 min, Cadet / Junior / Senior 4 min by default; change any of them (2 – 5 min). The scoreboard sets the time by itself whenever a match is loaded from the draw.

## Ranking → seeding
Add a "Ranking" column (1 = best) or "Ranking Points" column to the upload sheet. In each category the best ranked get seeds 1–8 (half the bracket in small categories) and are placed IJF-style. A category that already has a Seed column keeps those seeds.

## Events for blank sheets (Draw tab → 📋 Events for blank sheets)
Add events by hand, "+ All IJF weights" (Senior / Junior / Cadet) or "+ From athlete list". Then Print → any blank form → scope "Saved events" (or the "Print all blank forms for these events" button). Each event gets its sheets with the event heading and no names. Tick "No athlete names" to print a category's forms heading-only even when athletes are entered.

## Professional layout (v12)
- Left menu: Draw & brackets · Athletes & weigh-in · Events · Tournament setup · Scoreboard · TV display · Print centre · Results (Excel) · Backup & restore · Light / Dark.
- Top bar: page name, mat, Draw / Scoreboard switch. Bottom status bar: last save, athletes, contests done, TV connection, last backup, mat, clock.
- On small laptops (under ~1180 px wide) the menu shows icons only. The TV screen, "This screen = board" mode, the phone QR pages and all prints are unchanged.
