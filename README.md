# Foundation First Observation Tracker — GitHub Pages edition

The tracker as a website, the same way the Team Inventory System is hosted (mowcky.github.io/ff-inventory). No Supabase, no sign-in, no database. GitHub hosts the **tool only**; observation data lives in each user's browser and moves between computers with JSON backup files.

## Files in this repository

| File | Purpose |
|---|---|
| `index.html` | The full tracker (dashboard, weekly schedule, CSV uploads, Upload Review Center, schedule vs submitted, workflow & bulk dates, payment email summary, submission log, change history, observers) |
| `tutorial.html` | Staff quick-start guide (also opens from **More → Quick Start Tutorial**) |
| `README.md` | This file |
| `.gitignore` | Blocks `.json`, `.csv`, `.xls`, `.xlsx` from being committed by Git |

`config.js`, `cloud.js` and `schema.sql` from the Supabase package are **not used** and should not be uploaded.

## Publish (about 5 minutes)

1. On GitHub, click **+ → New repository**. Name it `ff-observations`. Public is fine because the repo contains no data. Do not add a README (this package has one).
2. Click **uploading an existing file** and drag in `index.html`, `tutorial.html`, `README.md`. Commit to `main`.
3. **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save.**
4. After 1–2 minutes the site is live at **https://mowcky.github.io/ff-observations/**.

> Uploading through the GitHub website ignores `.gitignore` — it only protects Git/GitHub Desktop pushes. When dragging files in, double-check you are not including any backup or CSV.

## Load your existing records (once per computer)

1. Open the site, then **⬆ Restore** in the bar under the header.
2. Choose `observation-tracker-backup-2026-10-20.json` (810 observations, 18 submission log entries, FY27 Fall Window).
3. Confirm and check counts on the dashboard.

Backups from the earlier Supabase version (`observation-tracker-cloud-backup-….json`) restore the same way.

## How data is kept

- Every change saves automatically to that browser (localStorage). Different browsers/computers do **not** share data.
- **⬇ Backup now** downloads a full JSON file: all seasons, submission history, Upload Review queue and Change History. Save it to the team OneDrive/SharePoint folder.
- The status dot is green after a recent backup and amber if none in 7 days.
- Clearing browser data, private/incognito windows, or a different browser will show an empty tracker — restore the newest backup.

## Working rules for the team

1. One person edits at a time. Whoever edits downloads a backup when done and saves it to the shared folder.
2. Before editing on another computer, **restore the newest backup first**. Restore replaces everything in that browser.
3. Never upload backups, schedule CSVs or payment CSVs to GitHub.

## Updating the tool later

Replace `index.html` (or `tutorial.html`) in the repo via **Add file → Upload files**. Data is unaffected because it lives in browsers, not in the repo — but download a backup before testing a new version.

## Workflow summary

Scheduled → Submitted → Processing → Completed. Fall window Aug 17–Dec 23, Spring Jan 19–May 29 (fixed, regardless of weekends/holidays); Fall 2026 = FY27 Fall Window. Flat rates: Contractor $325, Internal $50. Outstanding submissions flag orange at 30–59 days, red at 60+. See `tutorial.html` for step-by-step use.

## If you later need real-time sharing

Browser storage can't sync between people. If several staff need to edit at the same time, the Supabase package (`cloud.js`, `config.js`, `schema.sql`) adds sign-in and a shared database on top of this same site.
