# LK Design and Build

Production website for **LK Design and Build** — Adelaide premium home renovations, additions and custom builds.

- **Live now:** https://cjmuldoon.github.io/lk/ (GitHub Pages default URL)
- **Target domain:** `lkdesignandbuild.com.au` — registered with **Crazy Domains**, not yet wired up. See [Custom domain](#custom-domain) below.

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

Right now the site is served from the GitHub Pages default URL:

> **https://cjmuldoon.github.io/lk/**

To move it onto **`lkdesignandbuild.com.au`** (registered with Crazy Domains), do the DNS first, then GitHub. Don't add the repo `CNAME` file until DNS is in place — adding it early makes GitHub redirect the working `.github.io` URL to a domain that isn't resolving yet.

### Step 1 — DNS at Crazy Domains

1. Sign in at **crazydomains.com.au** → **My Account**.
2. Open **Manage** for `lkdesignandbuild.com.au`, then go to **DNS** (also labelled *Manage DNS* / *DNS Settings*).
3. Confirm the domain is using **Crazy Domains' own nameservers** — the DNS panel only takes effect if it is (it's the default for domains registered with them).
4. **Delete** any existing parking/default `A` record on the root host (`@`) and any `CNAME` on `www` that points at a Crazy Domains parking page.
5. Add these records:

   **Apex (`lkdesignandbuild.com.au`) — four A records.** Host `@` (some panels want it blank or the bare domain):

   | Type | Host | Points to |
   |------|------|-----------|
   | A | @ | `185.199.108.153` |
   | A | @ | `185.199.109.153` |
   | A | @ | `185.199.110.153` |
   | A | @ | `185.199.111.153` |

   **IPv6 (optional but recommended) — four AAAA records.** Host `@`:

   | Type | Host | Points to |
   |------|------|-----------|
   | AAAA | @ | `2606:50c0:8000::153` |
   | AAAA | @ | `2606:50c0:8001::153` |
   | AAAA | @ | `2606:50c0:8002::153` |
   | AAAA | @ | `2606:50c0:8003::153` |

   **`www` subdomain — one CNAME:**

   | Type | Host | Points to |
   |------|------|-----------|
   | CNAME | www | `cjmuldoon.github.io` *(note the trailing dot if the panel requires it: `cjmuldoon.github.io.`)* |

6. Leave TTL at the default (1 hour is fine). Save. DNS propagation usually takes 15–60 min, occasionally up to 24 h.

### Step 2 — point GitHub Pages at the domain

7. In this repo on GitHub: **Settings → Pages → Custom domain** → enter `lkdesignandbuild.com.au` → **Save**. GitHub runs a DNS check and, on success, writes a `CNAME` file to the repo automatically.
8. Wait for the green "DNS check successful", then tick **Enforce HTTPS** (GitHub provisions the TLS certificate — can take up to an hour).

### Verify

```
dig lkdesignandbuild.com.au +short        # should list the four 185.199.x.153 IPs
dig www.lkdesignandbuild.com.au +short    # should show cjmuldoon.github.io
```

Once it resolves, `https://lkdesignandbuild.com.au` and the `www` form both load the site; GitHub handles the redirect between them.

## Contact

- Lyda — Interior Designer | Project Manager
- M: 0401 061 246
- E: lyda@lkdesignandbuild.com.au
- A: PO Box 867 Prospect East SA 5082
- ABN: 17 697 207 391
