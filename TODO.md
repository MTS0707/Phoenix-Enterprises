# TODO / Pre-Launch Checklist

Open items before this site is ready to publish live.

## Blocking

(none currently)

## Done

- [x] ~~No git repository~~ — initialized 2026-08-03, pushed to `github.com/MTS0707/Phoenix-Enterprises`.
- [x] ~~No hosting/domain decided~~ — published 2026-08-03 via GitHub Pages at `https://mts0707.github.io/Phoenix-Enterprises/`. Custom domain `phoenixenter.com` (registered at Hostinger) attached 2026-08-03: A records for `@` pointed at GitHub Pages' four IPs, `www` CNAME'd to `mts0707.github.io`, domain set in repo Settings → Pages. Live and serving over HTTPS at `https://phoenixenter.com`.
- [x] ~~Re-add a captcha to `contact.html`~~ — added 2026-08-03 as a simple client-side math challenge (e.g. "what is 4 + 7?"), no external service/API key needed; Send button stays disabled until answered correctly. Client asked for "something simple" over hCaptcha. Note: this only deters basic bots, not a determined attacker — revisit with hCaptcha (real key) if spam becomes an actual problem.
- [x] ~~Decide on the contact-form backend~~ — switched from `mailto:` to web3forms.com (AJAX POST) on 2026-08-03, matching Structura Nordic's pattern. Fixes the "This form is not secure, autofill has been turned off" browser warning that `mailto:` forms trigger. Form now shows an in-page "Message Sent" confirmation instead of opening the visitor's email client. Access key is embedded in `contact.html` (web3forms keys are meant to be public/client-side, not secret).

## In progress

- [ ] **Gate Google Analytics behind the cookie-consent banner.** GA4 (`G-LBF8840F8F`) was added to all 9 pages on 2026-08-03 but currently loads unconditionally on every page view — it does **not** yet respect a visitor clicking "Reject" on the consent banner, even though `cookie-policy.html` implies cookie choices are honored. Fix: only load the `gtag.js` script/init when `localStorage.getItem('phx-cookie-consent') === 'accepted'`, and trigger the load from the Accept button's click handler for first-time visitors. Started this and got interrupted mid-edit — no partial/broken state was left in the files, just not done yet.
- [ ] `cookie-policy.html` still says "We do not currently use Google Analytics... or any other tracking or marketing cookies on this site" — this is now **inaccurate** since GA4 was added 2026-08-03. Needs a rewrite of the "Cookies set by embedded third-party content" section once the consent-gating above is settled (so the policy text matches actual behavior), plus bump the "Last updated" date.

## Non-blocking / nice-to-have

- [ ] Confirm the client is happy with the current color palette (logo-derived navy `#071E4A` + `#0A3A8C`, orange CTAs) — this went through several iterations; get an explicit sign-off before treating it as final.
- [ ] `images/proof/trial-*.jpeg` (5 files) are unused since the "ON-SITE TRIAL DOCUMENTATION" section was removed from `results.html`. Either delete them or leave them in case that section comes back — no action needed unless the client asks.
- [ ] The source `Phoenix_Enterprises_Company_Profile_v11.pptx` still has the real competitor names (Kyocera, BT Silmax, Win Tech, Korloy) and the "Ognebene" spelling that were deliberately changed on the website — if the deck is ever regenerated from the site, double check which version is wanted where (see `DATA_LOG.md`).
- [x] ~~Consider SEO basics before launch~~ — `sitemap.xml` and `robots.txt` added 2026-08-03 (listing all 9 pages, priority-weighted). GA4 analytics added same day (see "In progress" above for the consent-gating follow-up).
- [ ] Have the client's legal/compliance advisor review `privacy-policy.html`, `terms-of-service.html`, and `cookie-policy.html` — they were drafted generically to match what the site actually does and are not a substitute for legal review. Now also needs to account for GA4 (see above).
