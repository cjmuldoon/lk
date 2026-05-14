# LK Design and Build

Production website for **LK Design and Build** — Adelaide premium home renovations, additions and custom builds.
Lives at [lkdesignandbuild.com.au](https://lkdesignandbuild.com.au) (via GitHub Pages).

## Structure

```
.
├── index.html                 single-page site (Tailwind via CDN, no build step)
├── assets/
│   ├── branding/final/        approved logo suite (SVG + PNG)
│   │   ├── lk-logo-horizontal-champagne.svg   primary nav lockup
│   │   ├── lk-logo-horizontal-charcoal.svg    light-bg alternate
│   │   ├── lk-logo-horizontal-two-tone.svg    warm-neutral alternate
│   │   ├── lk-logo-horizontal-gold.svg        signature gold mark
│   │   ├── lk-icon-champagne.svg              icon only (favicon source)
│   │   ├── lk-logo-champagne.svg              full primary mark
│   │   ├── og-image.{svg,jpg,png}             1200×630 social share card
│   │   └── png/                               raster mirrors
│   └── images/                hero photography
│       └── hero-abstract-{1,2,3}.jpg          interim hero shots
├── favicon.ico                multi-res 16/32/48 ICO
├── icon.svg                   browser-tab SVG favicon
├── apple-touch-icon.png       iOS home-screen icon
├── icon-512.png               PWA / Android maskable
├── site.webmanifest           PWA manifest
├── robots.txt                 crawl rules
└── sitemap.xml                URL list for search engines
```

## Local preview

No build needed. Open in a browser:

```
open index.html
```

Or run a static server (so the absolute paths in `<link rel="icon" href="/…">` resolve correctly):

```
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying

This repo serves directly from GitHub Pages on the `main` branch (root). Push to `main` and the site updates.

## Updating the logo / brand assets

The canonical source is the [primedesign](https://github.com/cjmuldoon/portfolio) repo at `/assets/branding/final/`.
Copy refreshed SVGs and PNGs from there into `assets/branding/final/` here when the brand kit changes.

## Adding project photography

Drop project images into `assets/images/projects/` (create as needed), then reference them in `index.html`.
For SEO, give every non-decorative `<img>` a descriptive `alt` (location + materials).

See [SEO guidelines](https://github.com/cjmuldoon/portfolio/blob/main/assets/branding/final/docs/seo-guidelines.md) on the primedesign repo for the full meta-tag, schema, and Google Business Profile playbook.

## Custom domain

The site is configured to live at `lkdesignandbuild.com.au`. To switch on the custom domain:

1. Add a `CNAME` file at repo root containing `lkdesignandbuild.com.au`.
2. In GitHub repo Settings → Pages, set the custom domain to `lkdesignandbuild.com.au` and enable "Enforce HTTPS".
3. At the domain registrar, point an `A` record at GitHub's Pages IPs (`185.199.108.153`, `.109.153`, `.110.153`, `.111.153`) or a `CNAME` to `cjmuldoon.github.io`.

## Contact

- Lyda — Interior Designer | Project Manager
- M: 0401 061 246
- E: lyda@lkdesignandbuild.com.au
- A: PO Box 867 Prospect East SA 5082
- ABN: 17 697 207 391
