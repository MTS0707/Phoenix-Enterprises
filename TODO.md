# TODO / Pre-Launch Checklist

Open items before this site is ready to publish live.

## Blocking

- [ ] **Re-add a captcha to `contact.html`.** Was removed on 2026-07-27 at the client's request ("will do it after trials and publishing"). Recommended: hCaptcha, matching the Structura Nordic site — but needs a **real site key** registered at [hcaptcha.com](https://www.hcaptcha.com) for the live domain before it's wired back in (the test key used earlier always passes and gives no real protection).
- [ ] **Decide on the contact-form backend.** Currently submits via `mailto:` (opens the visitor's email client). Structura Nordic's contact form instead posts to web3forms.com via AJAX with proper success/error states. This was proposed to the client but never confirmed either way — revisit before launch.
- [ ] **No git repository yet.** The folder isn't under version control. Set one up before deployment so changes are tracked and recoverable.
- [ ] **No hosting/domain decided.** Nothing has been deployed anywhere yet.

## Non-blocking / nice-to-have

- [ ] Confirm the client is happy with the current color palette (logo-derived navy `#071E4A` + `#0A3A8C`, orange CTAs) — this went through several iterations; get an explicit sign-off before treating it as final.
- [ ] `images/proof/trial-*.jpeg` (5 files) are unused since the "ON-SITE TRIAL DOCUMENTATION" section was removed from `results.html`. Either delete them or leave them in case that section comes back — no action needed unless the client asks.
- [ ] The source `Phoenix_Enterprises_Company_Profile_v11.pptx` still has the real competitor names (Kyocera, BT Silmax, Win Tech, Korloy) and the "Ognebene" spelling that were deliberately changed on the website — if the deck is ever regenerated from the site, double check which version is wanted where (see `DATA_LOG.md`).
- [ ] Consider SEO basics before launch (title/meta tags already present per page, but no `sitemap.xml`, `robots.txt`, or analytics snippet yet — Structura Nordic has all three).
- [ ] Have the client's legal/compliance advisor review `privacy-policy.html`, `terms-of-service.html`, and `cookie-policy.html` — they were drafted generically to match what the site actually does (mailto contact form, Google Maps/Fonts embeds, no analytics yet) but are not a substitute for legal review.
