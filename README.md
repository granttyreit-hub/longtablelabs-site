# longtablelabs.com

Static marketing site for **Longtable Labs** and its first product, **Cadent
Family** — a shared family organiser. Separate project from the app; shares the
brand and nothing else.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Home / marketing — problem-led, the photo-import pitch, honest feature points, coming-soon + email capture |
| `privacy.html` | Privacy policy (required live before Google Play submission) — **read every line before publishing** |
| `support.html` | Support / FAQ (Play requires support contact details) |
| `contact.html` | Contact addresses on the longtablelabs.com domain |
| `styles.css` | Shared stylesheet — no build step, no dependencies |
| `assets/screenshots/` | Real app screenshots + capture guide (placeholders until captured) |

## Running locally

Any static server works, e.g.:

```bash
python -m http.server 8080
```

Then open <http://localhost:8080>. There is no build step.

## Before it goes live — checklist

- [ ] Read the whole **privacy policy**; fill every `<!-- REVIEW -->` and
      `[BRACKETED]` item (publication date, legal entity, postal address if
      required, and confirm Anthropic's terms link).
- [ ] Set up the email addresses used on the site so they receive mail:
      `hello@`, `support@`, `privacy@` `@longtablelabs.com`.
- [ ] Capture the **real screenshots** (see `assets/screenshots/README.md`).
- [ ] Decide the launch email-capture mechanism. The form currently opens the
      visitor's mail client (`mailto:`). To collect addresses automatically,
      point the form `action` at a form service once hosting is chosen.
- [ ] Host it (GitHub Pages / Netlify / Cloudflare Pages) and point the domain.

## Honesty guardrails (from the brief)

Nothing on the site claims anything not built: no Google Calendar sync, no user
counts, no testimonials, no store badges (styled "Coming soon" text only, since
the trademarked badges are permitted only as links to live listings). Android is
described as closest to launch, Microsoft next, iOS furthest out.
