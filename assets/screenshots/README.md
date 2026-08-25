# Screenshots — real app captures go here

The site references these files. Until they exist, each slot on the site shows a
labelled placeholder (the `onerror` fallback on each `<img>`), so nothing looks
broken.

**Filenames the pages expect** (portrait phone PNGs, ideally ~1080×2340 or the
device's native portrait resolution):

| File | Shows |
|---|---|
| `month-view.png` | Month calendar with a photo background — the hero shot |
| `import-review.png` | The schedule-import review list, mid-approval |
| `week-view.png` | Week view, several people's events colour-coded |
| `privacy-picker.png` | The "who can see this" picker on an event |
| `today-view.png` | Today screen with greeting and upcoming events |
| `theme-packs.png` | The theme gallery — light/dark plus the pack shelf |

## Rules (from the brief)

- **Real app only.** No mock-ups — store reviewers compare listing screenshots
  against the actual app.
- **A purpose-made demo family.** Do NOT use the developer's own calendar; it
  holds real medical appointments, a hospital name, and children's names/school
  dates. Invent innocuous events: "Soccer practice", "Dentist", "Trash night",
  "Grandma visits".
- The app's own mock schedules in the app repo's `test/fixtures/schedules/` are
  good, realistic-but-fake material for demoing the import feature.

## Capture workflow (run when the phone is plugged in)

Prerequisites: Android phone connected over USB with debugging on; Postgres,
the backend, and the Flutter app all running from the `fcc_app` repo.

1. Start the stack (from the app repo): Postgres up, `cd backend && npm run
   start:dev`, then `adb reverse tcp:3000 tcp:3000` and
   `flutter run -d <device-id> --dart-define=FCC_API_BASE_URL=http://localhost:3000`.
2. Create/seed a **demo family** with invented members and events. Add a couple
   of repeating events ("Soccer practice — Mon/Wed/Fri") and a photo background
   so the month view looks its best.
3. For the import shot: use one of `test/fixtures/schedules/*.png`, run the photo
   import, and stop on the review list before approving.
4. Capture each screen:
   ```bash
   adb exec-out screencap -p > month-view.png
   ```
   (repeat per screen; app must be FOREGROUND — see app repo CLAUDE.md gotcha 39).
5. Scrub each image for any real personal data before it lands here.
6. Drop the PNGs in this folder with the names above. The placeholders disappear
   automatically.

Alt text is already written into each page's `<img alt="...">`; update it if a
screenshot's content changes.
