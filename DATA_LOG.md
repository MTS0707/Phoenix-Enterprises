# Data Log — Content & Asset Provenance

This file records where every piece of copy and every image on the site came from, so future edits can trace a claim back to its source instead of guessing.

## Copy source: the company profile PPTX

All body copy (company stats, strengths, brand descriptions, product range, services, trial results table, client list, contact details) was extracted from:

```
D:\Customers\Phoenix Enterprises\Phoenix_Enterprises_Company_Profile_v11.pptx
```

**How it was extracted:** no PowerPoint reader, `python`, or `python-pptx` was available in this environment. The `.pptx` is a zip archive of XML, so it was unzipped directly and the text runs (`<a:t>...</a:t>`) were pulled out of each `ppt/slides/slideN.xml` with `sed`/`grep`. All 14 slides were extracted this way; that text is the canonical source for the copy on every page.

Slide → page mapping:

| Slide | Content | Used on |
|---|---|---|
| 1 | Cover: tagline, stats, address/phone/email | `index.html` hero |
| 2 | Who We Are, stats, Gajanan Gore quote | `index.html`, `about.html` |
| 3 | Our Strengths (6 items) | `index.html`, `about.html` |
| 4 | Principal Brands — TRIMAT / DEREK | `index.html`, `about.html` |
| 5 | Product Range — Inserts & Solid Carbide Tools | `products.html` |
| 6 | Product Range — Turning, Milling & Tool-Holding | `products.html` |
| 7–8 | Product Gallery (milling / turning-grooving-threading) | `products.html` |
| 9 | What We Offer — 5 services | `services.html` |
| 10 | Documented trial results table | `results.html` |
| 11 | On-site trial documentation photos | *(removed from site — see below)* |
| 12 | Trusted By — client list | `index.html`, `results.html` |
| 13 | Contact details, GST no., proprietor | `contact.html`, footer (all pages) |
| 14 | Thank you / closing | not used |

## Deliberate deviations from the PPTX source

- **Competitor names removed.** The original slide 10 table named specific competitor products (Kyocera, BT Silmax, Win Tech, Korloy) in the "Benchmark" column. Per client request (2026-07-27), these were replaced with generic wording ("vs a competitor insert brand", etc.) on both `results.html` and the `index.html` teaser. **The source PPTX still has the real names** — if the deck is ever regenerated from the site or vice versa, don't copy the generic wording back into the PPTX without checking which is wanted where.
- **"Ognebene" → "Ognibene India" → removed.** The client list (slide 12) spells this client "Ognebene"; corrected to "Ognibene India" on the website per client request (2026-07-27). Per further client request (2026-08-03), this client was removed entirely from both `index.html` and `results.html`. The source PPTX still lists "Ognebene" and was not corrected.
- **Slide 11 (trial documentation photos) removed entirely from the site.** Was originally built as an "ON-SITE TRIAL DOCUMENTATION" section on `results.html` with a click-to-enlarge lightbox of 5 signed trial reports. Client asked to remove it (2026-07-27) since the results table already covers the comparison. The 5 images are **still present but unused** at `images/proof/trial-1.jpeg` … `trial-5.jpeg` — kept on disk in case the section is wanted back, but nothing on any page references them.

## Image provenance

| Website file | Source file | Notes |
|---|---|---|
| `images/brand/logo.png` | `Logo/LOGO_Phoenix Enterprises.png` | Also used to derive the site's color palette (see below) |
| `images/brand/gajanan-gore.png` | `Logo/Photo of Gajanan Gore.png` | Proprietor headshot |
| `images/brand/machining-hero.jpg` | `Logo/Image of machining.jpg` | Used as the background photo on every page's hero/title band |
| `images/products/insert.jpeg` | `Products/Insert.jpeg` | |
| `images/products/carbide-end-mill.jpeg` | `Products/Carbide End mill.jpeg` | |
| `images/products/milling.jpeg` | `Products/Milling.jpeg` | |
| `images/products/taps.jpeg` | `Products/Taps.jpeg` | |
| `images/products/variety.jpeg` | `Products/Variaties.jpeg` | |
| `images/products/grooving-tool-1.jpeg` | `Products/Grooving tool.jpeg` | |
| `images/products/grooving-tool-2.jpeg` | `Products/Grooving tool_.jpeg` | |
| `images/products/trimat-end-mill-packaged.jpeg` | `Products/WhatsApp Image 2026-07-13 at 12.52.52 PM (5).jpeg` | Added 2026-07-27; re-rotated 90° (source was sideways) |
| `images/products/derek-tool-kit-case.jpeg` | `Products/WhatsApp Image 2026-07-13 at 12.52.52 PM (6).jpeg` | Added 2026-07-27; re-rotated 90° (source was sideways) |
| `images/products/derek-tool-kit-open.jpeg` | `Products/WhatsApp Image 2026-07-13 at 12.52.52 PM (7).jpeg` | Added 2026-07-27; used in the Tool-Holding Kit banner on `products.html` |
| `images/proof/trial-1.jpeg` … `trial-5.jpeg` | `Info/Trial results1.jpeg` … `5.jpeg` | Unused — see "Deliberate deviations" above |

## Color palette provenance

The dark-section navy (`#071E4A`) and mid-blue (`#0A3A8C`) used across every page's dark backgrounds and gradients were **not** picked arbitrarily — they were sampled from the actual logo pixels using a PowerShell/.NET script reading `images/brand/logo.png`:

- Deep wingtip blue sampled at `#0646A1` → site uses a deepened `#071E4A` for large dark backgrounds (better text contrast than the sampled value)
- Mid-wing blue sampled at `#016EC5` → site uses `#0A3A8C` for gradient end-stops / secondary panels
- Bright accent sampled at `#189CE7` (used in the "ENTERPRISES" wordmark) → close enough to Tailwind's `sky-500`/`sky-600` that those utilities were kept as-is rather than replaced

CTA buttons (orange, `bg-orange-500`) were deliberately **not** changed to blue — kept for contrast against the blue palette, and because it echoes the orange coolant-hose fittings visible in the machining hero photo.
