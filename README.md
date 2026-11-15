# TatamiPro · Judo tournament manager (v18.6)

Draw (seeding, ranking, qualifier, knockout up to 128), weigh-in, live scoreboard + TV, schedule, results, prints, QR pages and WhatsApp sharing, in one web page. The name and logo can be changed in Settings.

## Files (upload ALL of them)
- `index.html` – the whole system
- `sw.js` – offline support (opens with no internet after the first visit)
- `manifest.webmanifest`, `icon-192.png`, `icon-512.png` – install as an app
- `xlsx.full.min.js` – Excel reader/writer (works offline)
- `qrcode.js` – QR codes (works offline)
- `jsqr.js` – reads ID card QR codes with the laptop camera at check-in (jsQR, Apache-2.0; works offline)
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

## v18.6 · one link per mat, locked mat laptops, strict schedule (15 Nov 2026)
- **Mat laptop links** (main desk · Settings → Live sync, after Create live room): one link per mat. The number of mats comes from the Schedule and can be changed right there. There is also a **Call room laptop** link. Each link has Copy, 📤 WhatsApp and QR.
- **Opening a mat link** on a laptop joins the room, names the laptop "Mat 2", makes it a Mat laptop and **locks** it to Mat 2:
  - the role buttons and the mat name cannot be changed, not even by a reload;
  - the link of another mat is refused.
  To change a locked laptop, enter the **unlock code** shown on the main desk (Mat setup → Laptop role → Unlock). Close tournament unlocks every laptop. A mat link opened on the main desk itself is refused.
- **Mat laptops show and run only their own scheduled categories** (tick it under the mat links): Run category lists only that mat's categories, and Load next and manual loads stay inside them. The main desk moves a category to another mat on the Schedule page; the change reaches the mats live.
- Checked in a 4-laptop trial (main desk + Mat 2 + Mat 3 joined by their links + call room by its link, strict on, Mat 3 offline for a while, main desk left and rejoined): same results on every laptop, every category on its own mat, no errors.

## v18.5 · audit fixes after a full 4-laptop trial (15 Nov 2026)
Trial: main desk (also Mat 1) + Mat 2 + Mat 3 + call room laptop in one live room, a whole tournament played on three mats at once, with Mat 3 losing the internet and the main desk leaving and rejoining. Faults found and fixed:
- **Settings overwritten on join (serious):** a laptop joining the room could overwrite the main desk's settings (for example the schedule's mats and mat per category) with its own empty defaults. Now the room's settings always win on joining.
- **Lock left behind:** a mat that finished a category while offline left its 🔒 in the room. A lock is now removed only when the room confirms it, and the main desk clears leftover locks of finished categories.
- **Same category on two mats:** a mat coming back online did not register its lock, and a laptop out of the room forgot the other mats' locks. Locks asked for while offline are now written as soon as the room answers. Last known locks are kept (also after a reload). While a laptop is out of touch, Load next only goes on with its own categories (a new one by hand). The app reconnects at once when the internet is back, and restarts a silent connection after 75 s.
- Clear all / new list in the room also clears the old locks. A run category taken over by another mat is unpinned. A mat laptop locks a category as soon as it loads a contest from it.
- The schedule only limits Load next when it really gives categories to mats. A renamed laptop tells the room at once. The draw page does not refresh while you type.
- Tip: give every category its mat in the Schedule (number of mats + mat per category). Then no two mats can ever start the same category, even without internet.

## v18.4 · no clashes between mats (15 Nov 2026)
- **Run category stays shown** (Scoreboard): the category you pick stays selected (green frame), also after Load next, after a result and after a reload. "Load next" first continues that category. Pick "▶ Run category: automatic" to go back to the schedule.
- **Load next goes through every waiting contest** (1 → 2 → 3 → 4 …), not back and forth between two.
- **Category lock between mats (live room)**: the mat that starts a category (picks it in Run category, uses Load next, or presses Hajime) owns it. On the other mats it shows as 🔒 "running on Mat 1" and cannot be loaded; a contest that was loaded there but not started moves to another category by itself. Finished categories are struck through and closed on the mat laptops; only the main desk can open them. The lock is released when the category is finished, or with "✋ Hand over" in Run category. The main desk can take over a locked category by picking it twice.
- **Mat laptops follow the schedule**: when the schedule has more than one mat, "Load next" on a mat laptop only gives the categories of its own mat (from the mat name, e.g. "Mat 2").
- **Leave / Rejoin live room**: when the main desk leaves the room, the mat laptops stay connected and keep sharing. Settings → Live sync → **↻ Rejoin the room** brings the main desk back with every result. "Create live room" now asks first while the old room exists (a new room would not have the mats in it).
- **Three laptop roles**: Main desk · Mat laptop (Scoreboard, Weigh-in, Mat setup) · **Call room laptop** (ID card check-in, weigh-in, Fusen-gachi for absent athletes, call room TV). Mat laptops no longer show check-in; the main desk has a "📣 Call room TV" button in the weigh-in bar.
- **Safety**: warning in the status bar when two laptops in the room have the same mat name; the browser asks before closing the page while the clock is running; the screen does not go to sleep on the scoreboard, TV and call room pages.

## v18.3 · stricter Mat Mode, Fusen-gachi at check-in, reminder to delete online data (15 Nov 2026)
- **Mat Mode** (Settings → Laptop role → Mat laptop): the menu shows only **Weigh-in**, **Scoreboard** and **Mat setup**. Dashboard, Draw, Schedule, Results, Officials, Print and Settings cannot be opened on a mat laptop. Mat setup keeps only what belongs to that laptop: role, live sync (join), backups (download), sound and the OBS overlay. Set the admin PIN (main desk role) before switching, so only the main desk can switch back.
- **Check-in → Fusen-gachi**: after the first check-in, the Weigh-in page lists the next contests on every mat where an athlete has not checked in. One button (click twice) gives Fusen-gachi to the athlete who is present. It is saved like any result and appears in the change log.
- **Delete online data after the event**: on the main desk that created the live room, a red reminder appears in the status bar once the event dates are over or every contest is done ("close the online room"). Clicking it opens Close tournament. Sub-junior and cadet athletes are minors: close the room soon after the results are final, and confirm the rules on children's data with your federation.
- Already in v18: Call room screen (Weigh-in → 📣 Call room screen), QR check-in (camera / USB scanner / name), change log (Results page + Print → 📜 Change log), Practice mode (Settings → Practice), Close tournament (Settings → Live sync).

## v18.2 · random draw with ranked athletes and districts kept apart (15 Nov 2026)
- Draw page → Draw: **Random · ranked & districts kept apart** (third option, next to "Ranking order" and "Top-8 seeds + random").
- Every place is drawn by lot. The rank and seed numbers are **not** used for the order.
- Athletes who have a rank or a seed in the Excel file go to **different pools (A–D)**, so they can meet only from the **semi-final**. With more than 4 such athletes in a category, the extra ones meet at the quarter-final at the earliest, and as few of those meetings as possible.
- Athletes of the **same district** go to different pools and never meet in the first round, whenever the numbers allow it.
- Byes are spread over the pools as usual. Draws with results or locked draws are kept. Draw editor → Auto-fix tidies a hand-edited random draw by the same rules. The printed sheet says which rule was used.

## v18.1 · live room fixes + random draw (15 Nov 2026)
- **Clear all and Upload Excel now work in a live sync room.** Before, they were blocked while the laptop was in a room (to stop athletes doubling). Now Clear all (click twice) empties the athletes, draws and results on **every laptop in the room**. Uploading a new list over an existing one first asks "Replace the athlete list on ALL laptops?" and then replaces it everywhere, once (no doubling). Every laptop keeps a backup first. A laptop that was offline follows when it comes back. Without internet nothing is deleted.
- Mat laptops in Mat Mode still cannot clear or upload (main desk only).

## New in v18 · tournament-day safety (15 Nov 2026)
- **Laptop role** (Settings → Laptop role): *Mat laptop* hides/blocks Make all draws, Re-draw, Edit, Lock, Clear all, Excel upload, demo data, branding and the live-room create/leave/close buttons (from v18.3 the menu shows only Weigh-in, Scoreboard and Mat setup). An orange badge in the status bar shows the role. With an admin PIN set (Settings → Security), switching back to Main desk needs the PIN.
- **Clock check**: when the laptop clock is more than 1 minute off the internet time (live sync server or the website's own clock), a red warning shows in the status bar. New results are stamped with the corrected time, so the change log and merges stay in order.
- **Close tournament** (Settings → Live sync, main desk that created the room): deletes the online room and the public live results page. Every laptop keeps its own data; the join and live links stop working. Needs the **new Firebase rules** (Copy rules → Firebase → Realtime Database → Rules → Publish).
- **Call room screen** (Athletes → Check-in → 📣 Call room screen, or `#callroom`): a TV page with the next 5 contests on every mat (on the mat · get ready · warm up), with check-in marks. Updates by itself.
- **Check-in** (Athletes page): scan the QR on the ID card with the laptop camera or a USB QR scanner, or type a name. Athletes due soon who are not checked in are listed in red, and on the call room screen.
- **Change log** (Results page, bottom; Print → 📜 Change log): every result entered, changed or removed, with time, mat and the old winner when it changed. For the jury and appeals.
- **Practice mode** (Settings → Practice): puts the real tournament aside on this laptop, loads demo athletes and draws, and pauses live sync, folder backups and the OBS overlay. *End practice* brings the real tournament back exactly as it was.
- **Smaller backups**: the 12 automatic backups are now compressed (several times smaller), so they never fill the browser storage. Old backups still restore.
- **Operator guide** (Print → ❓ Mat operator guide): one A4 page with the keys, every-contest steps, what to do when something goes wrong and the main desk names.
- Outside the software: keep every laptop on a charger/UPS, use a wired keyboard for the scoreboard, and keep a mobile hotspot ready as backup internet.

## v17.2 · audit fixes (15 Nov 2026)
- Security: a category name containing HTML (from the Excel file) could run as code in the scoreboard's category list. Now shown as plain text everywhere (checked: admin, TV, overlay, QR pages, all 16 print types).
- Certificates: each certificate keeps one number for good (per athlete and type) and numbers never repeat between separate prints.
- Live sync: restoring an old backup no longer rolls back newer results of other mats (it merges with the room). Removing an athlete (or the last athlete of a category) is now shared and does not come back. Clear all, a new athlete list and demo data are blocked while the laptop is in a live room (they would double every athlete).
- Checked: 431 athletes / 48 categories / 509 contests, every page at 390–1920 px, every print type, no memory or listener growth, about 50–70 ms per saved result, about 1.8 MB of the browser's ~5 MB storage.

## New in v17 · live sync between mats + public live results page (internet, free Firebase)
- Settings → **☁ Live sync between mats**. Every laptop keeps working offline; with internet, draws, results, weigh-ins, officials and event settings reach every other laptop in 1–3 seconds.
- **Main desk, once:** create a free Firebase project → Realtime Database (Singapore, locked mode) → Rules: paste the rules from TatamiPro (Copy rules) → Publish → Authentication → Anonymous → Enable → copy the Database URL and Web API key into TatamiPro → **Create live room**.
- **Mat laptops:** open the **join link** (WhatsApp) or paste the join code → Join. Set the mat name on the Draw page.
- Same category changed on two laptops (for example while one was offline): results are merged contest by contest; a different winner for the same contest → the newer result wins (listed under "Recent"). Deleting is never shared: a cleared laptop gets everything back from the room.
- **Public live results page** (link / WhatsApp / QR): every mat's current contest with scores and clock, medal winners, district medal tally, overall championship. Read only; it reads small files every 5 seconds, so the free plan is enough (100 connections, 10 GB a month).
- Security: only laptops with the join code can read or change the room (the room key is long and random); the public page can only read results. Keep the join code inside the organising team.

## New in v16.2 · mats → main desk (offline, no internet)
- **📤 Results file** (Results page or Settings → Backup & restore) on each mat laptop → send it to the main desk (pen drive, WhatsApp, email).
- **📥 Merge results files from mats** on the main desk (several files at once). Results are added contest by contest, nothing is deleted; a different winner for the same contest → the newer result wins and the report lists it. Weigh-ins and late athletes come over too. Lists uploaded separately on each laptop are matched by name + district + category.
- A backup is saved just before every merge. Merging the main desk file on a mat laptop gives it every other mat's results.

## New in v16
- **Backups outside the laptop** (Settings → Backup & restore → 📁): pick a folder on a USB pen drive or inside Google Drive / OneDrive for desktop; a backup file is written there when a category finishes and every N contests (plus "Write backup now"). Chrome / Edge only. After the page is opened again, click "⚠ Backup folder: click to reconnect" in the bottom bar and pick the same folder. Optional: also download a backup file into Downloads.
- **Certificates** (Print → 🎓 Certificates, or Results → Certificates): merit certificates for medal winners (finished categories only) and participation certificates for every athlete who fought. Full design or "text only" for pre-printed certificate paper; numbered, with a QR to check them.
- **Overall championship** (Results page): district points per medal (default Gold 7 · Silver 5 · Bronze 3, editable), overall + boys / girls + each age group; print and WhatsApp.
- **Round robin for small categories** (Draw → "Small categories"): Knockout (default) or round robin for 3, 3–4 or 3–5 athletes. Every athlete meets every other (IJF contest order, no back-to-back where possible); places by wins → contest between two level athletes → points from the wins → fewer shido; one bronze. Pool sheet, blank pool sheets and empty "round robin pool of 3 / 4 / 5" sizes.
- **Officials page** (menu → Officials): coaches, managers, referees, judges, table and technical officials, medical, volunteers, media (add or upload Excel / CSV). **Referee assignment** by session and mat (auto-fill, print, WhatsApp).
- **ID cards** (9 per A4 sheet, 86 × 54 mm): event, role, name, district, category, photo box, QR that shows the role and event on any phone.
- **Gujarati / Hindi** (Settings → Branding): second language under headings, table titles, round names, roles and signatures on prints and certificates; on the TV the category line switches language every 6 s and the winner label has a second line.
- **Live streaming overlay for OBS → YouTube / Facebook** (Settings → Branding → 🎥 Live streaming), OBS 28 or newer on the same laptop:
  1. OBS → Tools → WebSocket Server Settings → tick "Enable WebSocket server" → Show Connect Info → copy the Server Password.
  2. TatamiPro → enter the password → **Connect to OBS** (Chrome asks once about apps on this device / local network → Allow). It reconnects by itself whenever TatamiPro or OBS is reopened; the bottom bar shows "🎥 OBS live".
  3. OBS → Sources → + → **Browser** → URL = the copied link (this site + `#obs`), 1920 × 1080. Transparent background, no green screen.
  Style: score bar (lower third) or full scoreboard; position and size change live from TatamiPro. Shows names, district, scores, shido, clock, golden score, osaekomi, winner and medal winners. The old window-capture way (green / magenta / black) is still there; its running clock is now white so the colour key does not remove it.
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
