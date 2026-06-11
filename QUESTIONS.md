# Wibbly Works — open questions & launch checklist

Placeholders currently baked into the site are marked ⚠️. Work through these
before (or alongside) submitting the Apple account migration.

## 1. Facts I guessed — please confirm or correct

- ⚠️ **Contact email**: site uses `hello@wibbly.works` (index, privacy, footer).
  Does this address exist yet? If you prefer `support@` / `contact@`, say so.
- ⚠️ **Founded year**: About section says "founded in 2026". Correct?
- ⚠️ **"Inc"**: I've written "Wibbly Works Inc" everywhere (no period, matching
  how you wrote it). Confirm the exact registered legal name — Apple matches it
  against the D-U-N-S record, so it must be character-correct.
- ⚠️ **"A couple more wibbly things in the works"**: I saw CosyWords and
  Speakerly folders but didn't name them. Want them teased/named on the site,
  or kept quiet?
- ⚠️ **Privacy policy claims**: I wrote it to match Betweenies as built (no
  ads, no tracking, optional leaderboard name, Supabase + RevenueCat + Apple as
  processors). Review it — especially the children/COPPA paragraph — and
  consider a proper legal review before IAP launches.

## 2. Infrastructure to set up

- [ ] **Email on the domain** — `hello@wibbly.works` must actually receive
      mail. Cheapest: registrar/Cloudflare email forwarding to your Gmail.
      Apple also strongly prefers the developer Apple ID to use an email on the
      company domain — consider `john@wibbly.works` or similar for the account.
- [ ] **Hosting + DNS** — push to GitHub, import to Vercel, point wibbly.works
      DNS (see README). Verify it loads over HTTPS at the bare domain.
- [ ] **Git repo** — `git init` + first commit (folder is not a repo yet);
      create the GitHub remote.

## 3. Apple migration prerequisites (beyond the website)

- [ ] **Legal entity exists** — Wibbly Works Inc must be registered
      (state/country of incorporation needed for D-U-N-S).
- [ ] **D-U-N-S number** — free via Apple's lookup/request tool
      (developer.apple.com/enroll/duns-lookup). New numbers can take ~5 business
      days (longer outside the US). Company name + address must match the
      registration exactly.
- [ ] **Binding authority** — the migration must be requested by someone with
      legal authority to bind the company (owner/founder = you, simplest case).
- [ ] **Company phone number** — D-U-N-S and Apple verification both want one
      that reaches the business.
- [ ] **Start the migration** — sign in as Account Holder at
      developer.apple.com/account → "Convert to Organization" → submit request
      (or contact Apple Developer Support, topic "Account Updates and
      Renewals"). Apps, Team ID (WS4X33KDWC), and certificates carry over; the
      App Store **seller name changes** to "Wibbly Works Inc".

## 4. After the migration clears (IAP launch chain, from CLAUDE.md)

- [ ] Complete **Tax & Banking** in App Store Connect under the company.
- [ ] Create the `collection_2_unlock` product in App Store Connect.
- [ ] Set `expo.extra.revenueCatIosKey` in app.json (currently empty → IAP no-ops).
- [ ] Flip `collection_2.free` back to `false` in collections.json
      (don't re-sync from the editor export blindly — see CLAUDE.md).
- [ ] New eas build + submit.

## 5. Nice-to-haves (not required by Apple)

- [ ] Real OG/social share image (og:image is currently unset).
- [ ] Press kit page (icon, screenshots — marketing/raw already has these).
- [ ] Link Betweenies support/privacy pages and this site to each other for a
      consistent paper trail (App Store support URL can stay betweenies.app).
- [ ] Favicon as a real .png/.ico in addition to the inline SVG (some crawlers
      ignore data-URI icons).
