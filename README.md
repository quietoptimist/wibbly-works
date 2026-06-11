# wibbly.works

Company website for **Wibbly Works Inc** — built to satisfy Apple's requirements for
migrating the individual Apple Developer account to an organization account
(needed before we can ship IAP/subscriptions under the company).

## What Apple requires of this site

From Apple's organization enrollment/migration rules:

- The website must be **publicly available and functional** (not parked, not
  minimal content, not just a social-media page).
- The **domain must be associated with the organization** — wibbly.works is
  owned by Wibbly Works Inc. ✓
- Good practice that smooths verification: the **legal entity name visible**
  (footer: "© Wibbly Works Inc"), a **contact email on the company domain**
  (hello@wibbly.works), and a real description of what the company does.

Separately (not website, but same migration): a **D-U-N-S number** for the
legal entity, and the requester must have **binding authority** (owner/founder
is simplest). See `QUESTIONS.md` for the full checklist.

## Structure

Plain static HTML — no build step, same hosting pattern as `betweenies-web`
(Vercel, auto-deploy from main).

- `index.html` — single-page site: hero, games (Betweenies), about, contact, footer with legal name
- `privacy.html` — company-level privacy policy (placeholder facts — review before relying on it)
- `QUESTIONS.md` — open questions + launch checklist (not served; harmless if it is)

## Deploy

1. Create a GitHub repo (e.g. `quietoptimist/wibbly-works`) and push.
2. Import into Vercel → framework preset "Other" (static).
3. Add the `wibbly.works` domain in Vercel → set DNS at the registrar
   (A `76.76.21.21` / CNAME `cname.vercel-dns.com`, per Vercel's instructions).
4. Decide apex vs `www` canonical (apex is fine here — unlike betweenies.app
   there's no AASA/universal-link constraint on this domain).

## Local preview

```sh
cd wibbly && python3 -m http.server 8080
# open http://localhost:8080
```
