# Wibbly Works — open questions & launch checklist

Placeholders currently baked into the site are marked ⚠️. Work through these
before (or alongside) submitting the Apple account migration.

## 0. Registered company details (provided 2026-06-11)

- **Contact/registered person**: Monica Chitnis
- **Company**: Wibbly Works
- **Registered address**: 8 The Green, Suite 300, Dover, DE 19901, US
  (now in the site footer + privacy contact section)
- **Phone**: +1 845 764 2727 (kept OFF the public site — spam magnet; Apple
  gets it via D-U-N-S/the migration form)
- **Monica's email**: m@wibbly.works (kept off the public site; hello@ stays
  the public address)

## 1. Facts I guessed — please confirm or correct

- ⚠️ **Contact email**: site uses `hello@wibbly.works` (index, privacy, footer).
  m@wibbly.works works, so the domain has mail — make sure `hello@` is also
  routed (alias/forward to the same inbox), or tell me to switch the site to a
  different address.
- ⚠️ **Founded year**: About section says "founded in 2026". Correct?
- ⚠️ **Exact legal name / suffix**: the registration block says "Wibbly Works"
  but the site says "Wibbly Works Inc". A Delaware corporation's registered
  name normally carries a suffix (Inc./Corp./LLC…). Apple matches the name
  against the D-U-N-S record character-for-character — confirm exactly what's
  on the Delaware registration and I'll align the site (© line) to it.
- ⚠️ **Binding authority / Account Holder**: the Apple developer account is
  John's, but Monica is the registered contact. Apple's migration requires the
  requester to have authority to bind the company — if John isn't a listed
  owner/officer, Apple may ask for a reference (Monica) to confirm his
  authority. Worth deciding up front who answers that call/email.
- ⚠️ **"A couple more wibbly things in the works"**: I saw CosyWords and
  Speakerly folders but didn't name them. Want them teased/named on the site,
  or kept quiet?
- ⚠️ **SlashCart ownership & privacy**: the site now lists SlashCart as a
  Wibbly Works product. Two things to confirm: (1) slashcart.app itself never
  mentions Wibbly Works Inc — adding a "© Wibbly Works Inc" footer there
  strengthens the Apple paper trail; (2) our privacy.html is scoped to "its
  games" and written around Betweenies — SlashCart's data practices (pasted
  lists, **receipt photo uploads**, retailer carts) are different and need
  their own policy or an extended section here.
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
