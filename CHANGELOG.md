# Changelog

All notable changes to this site are recorded here, newest entry at the top of its date. Format is free-form (not strict Keep a Changelog) since this is a single static site, not a versioned package.

## 2026-08-03

- Removed client "Ognibene India" entirely from the site per client request — deleted from the `index.html` Trusted-By strip and the `results.html` client list.

## 2026-07-27

- **Initial build.** Created all 6 pages (`index`, `about`, `products`, `services`, `results`, `contact`) using plain HTML + Tailwind CDN + Alpine.js — no build tools, matching the stack used on the Structura Nordic AB site. Copy extracted from `Phoenix_Enterprises_Company_Profile_v11.pptx` (see `DATA_LOG.md`). Logo, proprietor photo, machining hero photo, and 7 product photos copied in from the client's source folders.
- Added a contact-form captcha: tried Google reCAPTCHA v2 (test key) first, hit an "Invalid domain for site key" error caused by opening the page over `file://` — fixed by serving the site locally (`npx serve`) instead.
- Increased the logo size in the header (`h-14`→`h-16`) and footer (`h-12`→`h-14`) on all 6 pages.
- Removed named competitors from the trial-results "Benchmark" column (Kyocera, BT Silmax, Win Tech, Korloy → generic "vs a competitor…" wording) on `results.html` and the `index.html` teaser.
- Made every contact-form field required (Name, Company, Email, Phone, Message), with a `*` marker on each label.
- Removed the entire "ON-SITE TRIAL DOCUMENTATION" section (5-photo lightbox gallery) from `results.html` — the results table already covers the same claims. Source images kept on disk but no longer referenced (see `DATA_LOG.md`).
- Switched the contact-form captcha from Google reCAPTCHA to **hCaptcha** (test key) to match the pattern used on the Structura Nordic site and drop the visible "for testing purposes only" disclaimer.
- **Removed the captcha entirely** per client request — will be re-added (with a real, registered key) closer to publishing, after trials are complete.
- Removed the "COMPANY PROFILE · 2026" eyebrow line from the homepage hero.
- Added the machining photo as a background image to every secondary page's hero/title band (previously flat dark slate); tuned visibility upward in two rounds (25% → 50% → 75% opacity, progressively lighter overlay gradient), applied identically to the homepage hero.
- Tried making the homepage hero viewport-relative (`min-h-[85vh]`) instead of content-sized; reverted per client request back to the original fixed-padding sizing.
- Increased Gajanan Gore's photo size across `about.html`, `contact.html`, and `index.html` in two rounds; restructured the homepage bio card from a horizontal photo+name row to a stacked, centered layout (matching `about.html`) so the larger photo would fit properly.
- Corrected client name spelling "Ognebene" → "Ognibene India" (`index.html` Trusted-By strip, `results.html` client list).
- **Site-wide color palette change.** Shown 3 generic "professional/trending" palette options; client asked instead to derive colors from the logo itself. Sampled the logo's actual pixel colors via a PowerShell/.NET script and rebuilt every dark section (hero backgrounds, footer, table header, stat cards, gradient cards) around the resulting navy (`#071E4A`) / mid-blue (`#0A3A8C`), converting non-button orange labels/borders to blue while keeping orange CTA buttons. Full detail in `DATA_LOG.md`.
- Added 3 new real product photos supplied by the client (packaged TRIMAT end mill, DEREK tool-kit case closed and open) into `products.html` — the open-kit photo fills the previously text-only "Tool-Holding Kit" banner; the other two were added as new gallery cards.
- Corrected the orientation of the TRIMAT end mill and DEREK case photos (both were sideways from source) — rotated 90° via a PowerShell/.NET script and re-saved in place.
- Added `README.md`, `CHANGELOG.md`, `DATA_LOG.md`, and `TODO.md`.
- Added `privacy-policy.html`, `terms-of-service.html`, and `cookie-policy.html`, and linked all three from a new legal-links row in the footer's copyright bar on every page.
- Added a cookie-consent banner (Alpine-powered, fixed to the bottom of the viewport) on all 9 pages — Accept/Reject buttons remember the visitor's choice in `localStorage` (key `phx-cookie-consent`) so it only shows once. Updated `cookie-policy.html` to describe this mechanism.
