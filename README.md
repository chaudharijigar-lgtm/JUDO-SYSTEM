# TatamiPro · Judo tournament manager (v15)

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

## New in v16
- **Backups outside the laptop** (Settings → Backup & restore → 📁): pick a folder on a USB pen drive or inside Google Drive / OneDrive for desktop; a backup file is written there when a category finishes and every N contests (plus "Write backup now"). Chrome / Edge only. After the page is opened again, click "⚠ Backup folder: click to reconnect" in the bottom bar and pick the same folder. Optional: also download a backup file into Downloads.
- **Certificates** (Print → 🎓 Certificates, or Results → Certificates): merit certificates for medal winners (finished categories only) and participation certificates for every athlete who fought. Full design or "text only" for pre-printed certificate paper; numbered, with a QR to check them.
- **Overall championship** (Results page): district points per medal (default Gold 7 · Silver 5 · Bronze 3, editable), overall + boys / girls + each age group; print and WhatsApp.
- **Round robin for small categories** (Draw → "Small categories"): Knockout (default) or round robin for 3, 3–4 or 3–5 athletes. Every athlete meets every other (IJF contest order, no back-to-back where possible); places by wins → contest between two level athletes → points from the wins → fewer shido; one bronze. Pool sheet, blank pool sheets and empty "round robin pool of 3 / 4 / 5" sizes.
- **Officials page** (menu → Officials): coaches, managers, referees, judges, table and technical officials, medical, volunteers, media (add or upload Excel / CSV). **Referee assignment** by session and mat (auto-fill, print, WhatsApp).
- **ID cards** (9 per A4 sheet, 86 × 54 mm): event, role, name, district, category, photo box, QR that shows the role and event on any phone.
- **Gujarati / Hindi** (Settings → Branding): second language under headings, table titles, round names, roles and signatures on prints and certificates; on the TV the category line switches language every 6 s and the winner label has a second line.
- **Streaming overlay for OBS** (Settings → Branding → Open overlay window): small live scoreboard on green / blue / magenta / black. OBS: Window Capture + Chroma Key.
- **Event report** for the federation (Print → 📄 Event report): summary, how contests were won, golden score, DQs, champion, participation and medals by district, every category's result.
- **Ranking points**: Results → download ranking points (Excel; 1st 100 · 2nd 70 · 3rd 50 · 5th 30 · 7th 20 · others 5, editable). Next tournament: Athletes → 📈 Apply ranking file → ranked athletes are kept apart in the draw (1 v last).

## New in v15
- **Print buttons print straight away** (category Print, Results, Schedule, Qualifier). The ▾ next to a category's Print lists every sheet for it; the Print page has every event in its list, and Results lists only finished categories.
- **Blank sheets are format only** (no athlete names). Athlete list and weigh-in sheet can also be printed "heading only, no names".
- **Date of birth + optional age check**: Excel column "Date of Birth" (DD-MM-YYYY). Settings → Age check: cut-off date and age range per age group; not eligible = DQ and kept out of the draw (off until ticked).
- **Golden score** per IJF 2025 (no limit, only a score or hansoku-make ends it, osaekomi in golden score = yuko at 5 s); optional limit + Hantei for young age groups; Decision button: Hantei / Kiken-gachi / Fusen-gachi.
- **Japanese-style sounds** (taiko, gong, hyoshigi, bell) and Japanese voice calls: Settings → Sound (Japanese voice needs Windows → Language → Japanese with speech; Android / iPhone have it).
- **TV**: animated winner screen (white background for White, blue for Blue, gold / bronze for medal contests, confetti); long names fit; category always shown in full; fills 4:3 projectors.
- Draw: fit to screen; Athletes: weigh-in filter by every category; template is a real Excel file with a "How to fill" sheet.

## Look: liquid glass
Frosted-glass menu bar, cards, buttons and dialogs floating on a soft colour background, in dark and light mode (Apple-style liquid glass look). On a slow laptop untick Settings → Branding & logos → "Liquid glass look" for the classic flat look. The TV scoreboard and all prints stay the same (solid colours / black & white).

## Menu
Dashboard · Athletes · Draw · Scoreboard · Schedule · Results · Officials · Print · Settings, with Share (WhatsApp), Lock, TV and Light/Dark at the top right. Bottom bar: last save, athletes, contests done, TV connection, last backup, mat, clock.

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
