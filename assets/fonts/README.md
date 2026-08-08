# Fonts — self-hosted

Served from this folder so the site makes **no third-party font requests**
(honors the privacy stance; no Google Fonts CDN call).

| Family | Use | Files |
|---|---|---|
| **Fraunces** | Display / headings | `fraunces-latin.woff2`, `fraunces-latin-ext.woff2` |
| **Nunito** | Body / UI | `nunito-latin.woff2`, `nunito-latin-ext.woff2` |

Both are **variable** woff2 (one file per subset covers the full weight range),
subset to Latin + Latin-Extended. Declared as `@font-face` in `../../styles.css`
with matching `unicode-range` and `font-display: swap`.

## Licensing

Both families are licensed under the **SIL Open Font License 1.1**, which permits
bundling and self-hosting with attribution and without a separate fee.

- Fraunces © The Fraunces Project Authors — https://github.com/undercasetype/Fraunces
- Nunito © The Nunito Project Authors — https://github.com/googlefonts/nunito

Full license text: https://openfontlicense.org

## Reproducing / updating

Downloaded from Google Fonts' `fonts.gstatic.com` woff2 endpoints (the URLs the
`css2` API returns for a modern browser UA). To refresh, re-request the css2 URL
for Fraunces + Nunito, pull the `latin` and `latin-ext` woff2 files, and replace
these four.
