# longtablelabs.com — charter

Owner session: **Science Officer WEB · Site** (commissioned 2026-10-20 by Fleet
Commander on Grant's order). This session is the sole editor of this repo.
The earlier Ensign CAD · Play & Web session handed over on 2026-10-20 and no
longer edits it.

## What this is

The static marketing and legal site for **Longtable Labs LLC** and its
products. Plain HTML + one CSS file, no build step, no JavaScript framework,
no third-party requests (fonts are self-hosted in `assets/fonts/`; see its
README for licences).

| File | Purpose |
|---|---|
| `index.html` | Company page (navy/coffee parent brand) → Products band → Cadent Family product section (warm Cadent brand) |
| `support.html` | Support / FAQ — Google Play's support URL |
| `contact.html` | Contact addresses on the domain |
| `privacy.html` | Cadent Family privacy policy — Play's privacy and "delete account" URL |
| `privacy-echo-night.html` | Echo Night privacy policy |
| `styles.css` | Shared stylesheet |
| `serve.js` | Dev-only static server on port 8087 (`node serve.js`); not deployed |
| `docs/` | Audits and working notes (not linked from the site) |

## Hosting

- **GitHub Pages** from the root of `main` in the public repo
  `granttyreit-hub/longtablelabs-site`. Every push to `main` deploys live in
  1–2 minutes (Pages caches for 10 min). `www.` redirects to the apex; HTTPS
  is enforced via GitHub's Let's Encrypt cert.
- **`CNAME` holds `longtablelabs.com` — never delete or edit it.** Removing it
  drops the domain binding and HTTPS.
- Cloudflare holds DNS, **DNS-only / grey cloud** on every record. Turning the
  proxy on breaks the Pages certificate and causes redirect loops.
  Nameservers stay on Cloudflare; the domain never transfers; Email Routing
  (hello@, support@, privacy@ to Gmail) and DMARC `p=none` depend on it.
- **Fixed paths:** `/privacy.html`, `/support.html` and
  `/privacy-echo-night.html` are pasted into Google Play Console. Their paths
  never change.
- `link.longtablelabs.com` is a **Cloudflare Worker** (`cadent-links`, live
  since 2026-10-17) serving Cadent's permanent contact links
  `https://link.longtablelabs.com/add/<code>` and `.well-known/assetlinks.json`.
  Source: `fcc_app/site-handoff/add-worker.js`. Contact links are **not** on
  this site. The apex `longtablelabs.com/add/*` currently 404s; if such pages
  are ever added here they must **302 to the link host**, never be served
  statically (decided 2026-10-15).

## Workflow — review before push

`main` is production. The loop is:

1. Work on a branch.
2. Run `node serve.js` (port 8087, gitignored) and check
   <http://localhost:8087> at desktop, **375 px and 320 px** for any layout
   change. Take screenshots.
3. Show Fleet Commander the screenshots (or the local preview) and wait for
   an explicit **"push"**.
4. Merge to `main` and push only on that word.
5. Poll the live URL for 1–2 minutes and grep for a phrase that sits on one
   line of the changed page; report the commit hash and the URL checked.

Run `git fetch` and `git status` before every edit: other sessions have
pushed to this repo in the past.

Commit messages: imperative, one topic per commit, ending with the
attribution line the session is given.

## Brand rules

- **Parent brand (Longtable Labs):** navy `--lt-ink #14263d`, coffee
  `--lt-coffee`, crema `--lt-crema`, brass `--lt-brass` buttons, Fraunces
  headings, Nunito body. Company hero and products band use it.
- **Cadent Family (product brand):** warm palette — coral `--coral`, amber,
  plum headings, blush paper. Everything from `#cadent` down uses it.
- Echo Night has no colour system on the site yet; it uses the product card
  only. Keep it inside the parent-brand products band.
- Fonts stay self-hosted. **No Google Fonts CDN, no analytics, no trackers,
  no third-party scripts.** The privacy pages promise this.
- Honesty rule from the original brief: claim only what is built and
  shipped. No user counts, no testimonials, no store badge unless it links to
  a live listing (Cadent's is live; Echo Night's is not yet).
- Copy voice: calm, plain, short sentences. "The app proposes; you decide."
- Naming: statements about who we are say **"Longtable Labs LLC"** (privacy
  pages, footers); plain brand mentions stay "Longtable Labs". Public Play
  developer name is "Longtable Labs".
- Never publish the home address or a phone number. Contact is email only.
- Never imply an iPhone app exists; ICS feeds are read-only; phone sign-in was
  removed from the app and is never mentioned.

## The demo-family rule

Every screenshot, video frame and example on the site shows only the
invented demo family — **Maya, David, Leo, Ava** (plus linked contacts
Grandma Rose and Coach Alvarez) — from the app's showcase/demo data. Never a
real calendar, real child, real school, or real appointment. Scrub any
capture for developer-only labels (e.g. "Unlimited imports (developer)")
before it lands here. Store screenshots must be real app captures, not
mock-ups. Web-ready media lives in `assets/demo/`; raw sources in
`fcc_app/assets/demo_media/` and `C:/Users/grant/video-studio/final`. No
real names or the home address anywhere.

## Background documents (private, never copied into this public repo)

- `C:/Users/grant/WEBSITE_HANDOFF.md` — site infrastructure, email, brand
  assets, live state as of 2026-09-12.
- `C:/Users/grant/CADENT_PLAY_AND_WEB_HANDOFF.md` — Play Console state and the
  rules for policy copy.
- `C:/Users/grant/CADENT_FEATURE_HANDOFF.md` — data flows for policy wording
  (2026-08-12; stale on sign-in, deletion and pricing — `fcc_app/CLAUDE.md` wins).
- `fcc_app/PLAY_DATA_SAFETY.md` and `privacy.html` must name the same service
  providers (Render, Firebase Authentication, Firebase Cloud Messaging, an
  email delivery provider, Anthropic). Keep them in step.

## Only Grant touches

- DNS, Cloudflare (zone, Worker, Email Routing), the domain registration.
  Keep DMARC at `p=none`. This session never opens the Cloudflare dashboard.
- Google Play Console, store listings, and the apps' release builds.
- **Privacy pages are legal text.** Edit `privacy.html` or
  `privacy-echo-night.html` only with Fleet Commander's explicit approval of
  the exact wording, and bump "Last updated" when you do.

## Cost rule

Free tools only. Images, if any are generated, come from the local
Qwen3 + ComfyUI stack described in the global CLAUDE.md. Never OpenArt.

## Facts the site must reflect (as of 2026-10-20)

- Cadent Family **1.0.9 is live on Google Play**
  (`com.longtablelabs.cadent`, https://play.google.com/store/apps/details?id=com.longtablelabs.cadent).
- Membership: **$1.99/month** for 10 AI schedule imports a month, rolling
  over to a cap of 20; without it a family keeps a 3-import trial and every
  other feature. Theme packs are free.
- 1.0.9 people model: kid mode on a shared tablet, "Viewing as" acts for the
  child, bounded undo on chore completions, claim a device so a grown child
  keeps their points. Realtime catch-up. Permanent contact links.
- Echo Night (`com.longtablelabs.echonight`) is in Play **internal testing**,
  shows house ads for Cadent Family, no third-party ads.
- Unreleased, not to be listed as products: Electro Swim, 4th Kind, Cursive,
  Sunset Grove, PC Builder, Time Travel Nurse.
- Social: TikTok `@longtable.labs.llc`, YouTube `youtube.com/@longtablelabs`.
  Daily Cadent demo videos come from `C:\Users\grant\video-studio\final`.

## Changelog

- **2026-10-21** — `privacy.html` revised for app 1.0.9: Play membership
  record, contact links, kid mode PIN, claiming a place in the family, a
  parent acting for a child, the Children line on claimed sign-ins, and the
  deletion note that removing our record does not cancel a Google Play
  subscription. Wording from `docs/PRIVACY-DRAFT-2026-10-20.md`, facts
  verified by Captain CAD · App, **approved by Grant via Fleet Commander,
  2026-10-21**. "Last updated" moved to October 21, 2026.
- **2026-10-20** — Science Officer WEB · Site commissioned; charter written;
  site audit in `docs/AUDIT-2026-10-20.md`. Batch 1 (launch truth: Play
  link, pricing, no email capture) pushed as 3dde060. Batches 2–5 built on
  stacked branches (features for 1.0.9; social links, demo clips, Open
  Graph, sitemap; polish; cadent.html, echo-night.html, 404) awaiting the
  push word. Privacy wording for 1.0.9 drafted in
  `docs/PRIVACY-DRAFT-2026-10-20.md`, not applied. Batch 3 touched both
  privacy pages in `<head>` (meta, icons, font preload) and the footer
  (Products and Follow columns) only; no policy text changed (Fleet
  Commander accepted this 2026-10-20).
- 2026-10-20 — (Ensign CAD · Play & Web) Echo Night privacy page revised for
  house ads; Echo Night product card added.
- 2026-10-19 — Demo video sound button.
- 2026-09-12 — Privacy policy names Longtable Labs LLC; deletion section.
- 2026-08-26 — Narrated AI-import demo video; monogram retired.
- 2026-08-25 — Screenshots refreshed in the Sunset theme.
- 2026-08-07 — Initial site; company-first restructure followed in August.
