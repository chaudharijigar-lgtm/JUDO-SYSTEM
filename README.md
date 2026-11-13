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
