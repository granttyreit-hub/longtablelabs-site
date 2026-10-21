# longtablelabs.com

Static marketing site for **Longtable Labs** and its first product, **Cadent
Family** — a shared family organiser. Separate project from the app; shares the
brand and nothing else.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Company page, Products band, the Cadent Family section (features, demo, gallery, Get card) |
| `cadent.html` | Cadent Family product page |
| `echo-night.html` | Echo Night product page |
| `support.html` | Support / FAQ for both products (Play's support URL) |
| `contact.html` | Contact addresses on the longtablelabs.com domain |
| `privacy.html` | Cadent Family privacy policy (Play's privacy and delete-account URL) |
| `privacy-echo-night.html` | Echo Night privacy policy |
| `404.html` | Branded not-found page (GitHub Pages serves it for any missing path) |
| `styles.css` | Shared stylesheet, no build step, no dependencies |
| `assets/demo/` | Web-ready demo clips with posters and captions (sources live in `video-studio/final`) |
| `assets/screenshots/` | App screenshots used on the home page |
| `assets/cadent/`, `assets/echo-night/` | Product-page frames (WebP) |
| `docs/` | Audits and drafts, not linked from the site |

## Running locally

```bash
node serve.js
```

Then open <http://localhost:8087>. There is no build step. `serve.js` is
git-ignored and dev-only.

## Rules

See `CLAUDE.md` for the charter: review before push, brand rules, the
demo-family rule, and what only the owner may touch. Nothing on the site claims
anything not built and shipped.
