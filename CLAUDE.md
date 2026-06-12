# CLAUDE.md

Company website for **Wibbly Works Inc** (wibbly.works) — built to satisfy
Apple's website requirement for migrating the Apple Developer account from
individual to organization (which unblocks IAP/subscriptions in Betweenies).

## Status

- **LIVE at https://wibbly.works since 2026-06-12.** GitHub
  `quietoptimist/wibbly-works` → Vercel auto-deploys `main`. Pushing to main
  IS deploying — treat every commit as production.
- DNS at Namecheap: A record on the apex + CNAME on `www` (values from the
  Vercel dashboard). The apex is canonical (matches the `<link rel=canonical>`
  in index.html); www redirects via Vercel. Namecheap's "URL Redirect" record
  was deleted — it secretly adds a competing A record and breaks HTTPS.
  **Mail/MX settings in Namecheap must not be touched** — `m@wibbly.works`
  (Monica) routes through them.
- Company facts: legal name **"Wibbly Works Inc"**, D-U-N-S **145004806**,
  registered at 8 The Green, Suite 300, Dover, DE 19901 (in the site footer).
  Phone and Monica's email are deliberately NOT on the public site.
- Remaining migration steps + unconfirmed placeholders: see `QUESTIONS.md`.

## Structure

Plain static HTML, no build step (same hosting pattern as `betweenies-web`):

- `index.html` — single page, all CSS inline: hero ("playful games and useful
  apps"), Games & apps cards (Betweenies → App Store id6766250257;
  SlashCart → app.slashcart.app), About values, contact, footer with legal
  name/address/D-U-N-S.
- `privacy.html` — company-level policy, written around Betweenies' actual
  practices. SlashCart's data practices (receipt uploads) are NOT covered —
  flagged in QUESTIONS.md.
- `QUESTIONS.md` — Apple-migration checklist + open facts to confirm.

## Conventions & gotchas

- Brand: cream `#fdf6ec`, ink `#223047`, orange `#d4693a` (shared with
  Betweenies), Baloo 2 + Nunito (Google Fonts). Tone: friendly, playful,
  small-studio honest — no corporate filler.
- The public contact is `hello@wibbly.works` everywhere; keep it that way
  (verify the alias actually receives mail — see QUESTIONS.md).
- `overflow-x: hidden` must live on `html`, not just `body`: the decorative
  blobs are absolutely positioned against the viewport, so body's overflow
  doesn't clip them.
- Headless-Chrome screenshots below ~500px width are silently cropped (Chrome
  clamps its window to a minimum) — a "broken" 390px capture is usually that,
  not a CSS bug. Test narrow layouts at 500px or in a real device emulator.
- Preview locally: `python3 -m http.server 8080` in the repo root.
