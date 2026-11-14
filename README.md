# TatamiPro · Judo tournament manager (v13)

Draw (seeding, ranking, qualifier, knockout up to 128), weigh-in, live scoreboard + TV, schedule, results, prints, QR pages and WhatsApp sharing, in one web page. The name and logo can be changed in Settings.

## Files (upload ALL of them)
- `index.html` – the whole system
- `sw.js` – offline support (opens with no internet after the first visit)
- `manifest.webmanifest`, `icon-192.png`, `icon-512.png` – install as an app
- `xlsx.full.min.js` – Excel reader/writer (works offline)
- `qrcode.js` – QR codes (works offline)
- `judo_demo_athletes.xlsx` – demo list: 359 athletes, 14 senior IJF categories

## Deploy on GitHub Pages
1. github.com → repository → "Add file → Upload files" → drag ALL files from this folder → Commit changes.
2. Settings → Pages → Deploy from a branch → main → /(root) → Save.
3. Open `https://<username>.github.io/<repo>/` on the admin laptop in Chrome once with internet.
4. Updating during a tournament: first Settings → Backup → **Download backup file**, then upload the new files **between matches** (not during a contest). Reload the admin page and the TV window once.

## Install as an app (Android · iPhone · Windows · Mac · Linux)
- Chrome / Edge (Windows, Mac, Linux, Android): the **⬇ Install** button in the top bar (or browser menu → Install).
- iPhone / iPad: Safari → Share → Add to Home Screen.
- Laptop and desktop get the desktop layout; phones get the phone layout (menu scrolls sideways, tables scroll).

## Menu
Dashboard · Athletes · Draw · Scoreboard · Schedule · Results · Print · Settings, with Share (WhatsApp), Lock, TV and Light/Dark at the top right. Bottom bar: last save, athletes, contests done, TV connection, last backup, mat, clock.

## Athletes & weigh-in
- Upload Excel / CSV. Columns are found by name: Name, District/Club, Gender, Age Group, Weight Category, Seed, Ranking, Weight.
- A **Weight** (or Weigh-in / Actual weight) column is taken as the official weight: above the category limit = OVER → disqualified automatically. Overweight athletes stay in all lists (struck through, "DQ") but are **not put in the draw**.
- Weigh on the day: Athletes page → type the weight → Enter. A typing mistake can be corrected; the athlete is back in.

## Draw
- **Draw: Ranking order (1 v last)** (default): with a Ranking column the whole bracket is placed by rank, IJF positions (1 v last, 2 v second-last, rank 1 and 2 in opposite halves…). **Top-8 seeds + random** keeps the old method. A Seed column overrides.
- Brackets up to **128** athletes (stage-1 sheets: Pool A–D, each in 2 parts).
- **🎯 Qualifier + top %** (per category, before results): everybody fights once; winners are ranked by points (Ippon / hansoku-make / opponent DQ 10 · Waza-ari 7 · Yuko 5 · shido or decision 1, then fewer shido, faster win, ranking). Type the % (e.g. 50) → **Apply cut & make knockout**: only the top % go into a new knockout drawn in qualifier order; the rest are listed **NQ** in the results. "Undo qualifier cut" brings it back. Qualifier contests are scored on the scoreboard like normal matches.

## Contest time
Settings → Tournament details: Sub-Junior 3 min, Cadet / Junior / Senior 4 min by default. The scoreboard (and the TV) take the time of the age group automatically when a match is loaded from the draw.

## Schedule (menu → Schedule)
- Every category is an event. Set first day, day start, number of mats, extra minutes per contest. **⚡ Auto-arrange** orders by age group and spreads the events over the mats.
- Time of an event = contests × (contest time + extra minutes). Type a time to fix it (📌), "auto" goes back. Add breaks / ceremonies (all mats), info rows (weigh-in, reporting) and new days.
- Publish: **Print / PDF** (A4, with QR), **WhatsApp**, or **▣ QR** for the notice board. The QR opens the schedule on any phone.

## WhatsApp sharing
Share (top bar), the WhatsApp buttons on Draw, Results, Schedule and Dashboard: tournament details & events, schedule, fixture of a category, fixtures of all categories, results of a category, all medal winners + tally. Edit the text, then **WhatsApp** (opens WhatsApp with the text; also copied) or **Copy text**. When the system runs from its website link, a link to the live phone page is added.

## TV
- Scoreboard → Open TV window (Windows + P → Extend → drag to the TV → click once for full screen).
- Logos: organiser top-left, associations top-right (Settings → Branding & logos).
- **QR on the live TV** (Settings → Tournament details, off until ticked): bottom-right QR for the category being fought, follows the next category by itself, refreshes after every result, hides during osaekomi. It opens the top places (live results) or the draw.

## Printing (menu → Print)
Elimination, final block, full draw, results, blank fixture, score sheets (blank / filled from the scoreboard), qualifier sheet, schedule, athlete list (roll call), weigh-in sheet, all blank forms; scope this / all / boys / girls / saved events; empty sizes 2–128. Always black on white A4, logos in grey.

## Security & privacy (Settings)
- **Admin PIN** (4–8 digits): the admin opens locked in every new window; Clear all, Restore and Erase ask for the PIN again; Lock button in the top bar; auto-lock after 10 / 15 / 30 / 60 minutes without use (never while the clock runs); 5 wrong tries → 30 s wait. TV and QR pages are never locked. The PIN is stored only as a salted hash. Forgot the PIN = erase this device and restore a backup file.
- **Public names**: full name, first name + initial, or initials only, and show / hide district, for QR pages, WhatsApp and the TV QR (printed sheets for officials keep full names). Suggested for under-18 events: first name + initial.
- **Erase this device**: after the event on a borrowed laptop (download the backup file first).
- Honest limit: everything stays in this browser (no server, no tracking). The PIN stops volunteers and spectators; it is not bank-level security against a technical person who has the laptop. Keep the laptop with you and use the computer's own login password.
