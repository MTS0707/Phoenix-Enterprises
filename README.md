# Phoenix Enterprises — Company Website

Marketing website for **Phoenix Enterprises** (Chikhali, Pune) — an authorized channel partner of TRIMAT & DEREK cutting tools, proprietor Gajanan Gore.

## Stack

- Plain HTML, one file per page (no build step, no bundler, no framework)
- [Tailwind CSS](https://tailwindcss.com) via CDN (`cdn.tailwindcss.com`)
- [Alpine.js](https://alpinejs.dev) v3 via CDN — used for the mobile nav menu toggle
- Google Fonts — Inter

There is no `npm install` / build step. Every page loads its dependencies straight from CDNs, so the site can be opened, edited, and deployed as static files.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Home — hero, company snapshot, strengths, brand partners teaser, product teaser, results teaser, trusted-by, CTA |
| `about.html` | Who We Are, full Strengths grid, Principal Brands (TRIMAT / DEREK) detail |
| `products.html` | Full product range (inserts, solid carbide, turning/milling/tool-holding), Tool-Holding Kit, photo gallery |
| `services.html` | The 5 service offerings (regrinding, special tooling, trials, application engineering, field support) |
| `results.html` | Documented on-site trial results table, Trusted-By client list |
| `contact.html` | Office/contact details, message form, embedded map |
| `privacy-policy.html` | Privacy Policy |
| `terms-of-service.html` | Terms of Service |
| `cookie-policy.html` | Cookie Policy |

Every page shares the same header/nav and footer markup (copy-pasted per page, not templated — there's no build step to share partials).

## Folder structure

```
Website/
├── index.html, about.html, products.html, services.html, results.html, contact.html
├── images/
│   ├── brand/       logo, proprietor photo, hero machining photo
│   ├── products/    product & tooling photos used on products.html
│   └── proof/       (unused — see DATA_LOG.md) trial-report photos, kept but not referenced
├── README.md
├── CHANGELOG.md
├── DATA_LOG.md
└── TODO.md
```

## Previewing locally

Double-clicking an HTML file works for basic browsing, but **anything that depends on the page being served over `http://` (e.g. a re-added captcha widget) will not work under `file://`**. Serve the folder instead:

```bash
npx --yes serve -l 5500 .
```

Then open `http://localhost:5500/index.html`.

## Content source

All copy on the site was extracted from the client's `Phoenix_Enterprises_Company_Profile_v11.pptx`. See `DATA_LOG.md` for exactly how, and for a map of which image came from which source file.

## Known gaps / follow-ups

See `TODO.md`.
