# CallKeep marketing site

Static HTML/CSS site for **CallKeep** — after-hours / when-they're-busy client capture for local service businesses (contractors, shops, trades, towing, auto repair, HVAC, plumbing, electrical, and similar) in Castle Rock and Denver metro, Colorado.

Prepared for **Cloudflare Pages** (drag-and-drop or Git deploy). No build step required.

## Local preview

Open `index.html` in a browser, or from this folder:

```bash
# optional local server
python3 -m http.server 8080
# then visit http://localhost:8080/
```

All internal links use **relative URLs** so the site works from a local file path, `*.pages.dev`, or a custom domain.

## Deploy to Cloudflare Pages

1. Log in to [Cloudflare Dashboard](https://dash.cloudflare.com/) → **Workers & Pages** → **Create** → **Pages**.
2. **Option A — Direct upload:** Upload the contents of this folder (`callkeep-site/`), not the parent directory. Root should contain `index.html`, `robots.txt`, `sitemap.xml`, `assets/`, etc.
3. **Option B — Git:** Push this folder to a GitHub/GitLab repo and connect it. Build settings:
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Build output directory: `/` (or the subdirectory if the repo root is above this folder)
4. After deploy, note the URL (e.g. `https://callkeep.pages.dev`).
5. Cloudflare Pages automatically serves `404.html` for missing routes.

Do **not** run a bundler unless you intentionally add one later. Current stack is plain HTML + one CSS file + a tiny nav script.

## Changing the base URL (canonicals & sitemap)

Placeholder production base used everywhere today:

```text
https://callkeep.pages.dev
```

When you buy a custom domain (e.g. `https://callkeep.com`):

1. **Attach the domain** in Cloudflare Pages → Custom domains.
2. **Find/replace** the old base with the new one in:
   - Every page’s `<link rel="canonical" href="...">`
   - Open Graph `og:url` (and related absolute URLs in OG tags)
   - JSON-LD `@id` / `url` / `item` values
   - `sitemap.xml` (`<loc>` entries)
   - `robots.txt` (`Sitemap:` line)
3. Quick check from this directory:

```bash
rg -n 'callkeep\.pages\.dev' .
```

4. Redeploy. Submit the new sitemap in Google Search Console.

Relative `href`s for navigation (`index.html`, `contact.html`, etc.) do **not** need changing.

## Site map (pages)

| File | Purpose |
|------|---------|
| `index.html` | Home — problem, solution, 3 steps, who it’s for, CTA |
| `how-it-works.html` | Workflow detail |
| `industries/index.html` | Industries hub — all verticals + other local service businesses |
| `industries/hvac.html` | HVAC answering service page (one of the industries we help) |
| `industries/plumbing.html` | Plumber after-hours answering |
| `industries/electrical.html` | Electrical contractor answering |
| `industries/towing.html` | Towing company after-hours answering |
| `industries/auto-repair.html` | Auto repair / auto shop answering |
| `service-area.html` | Castle Rock, Parker, Highlands Ranch, Denver metro |
| `about.html` | About / owner |
| `contact.html` | Phone + email CTAs |
| `faq.html` | Long-tail FAQ + FAQPage schema |
| `privacy.html` | Privacy stub |
| `404.html` | Not found |
| `robots.txt` / `sitemap.xml` | Crawlers |
| `assets/styles.css` / `assets/nav.js` | Design + mobile menu |
| `SEO-BACKLINKS.md` | 30-day local citation checklist |

## Primary keywords used (B2B — shops searching)

- answering service for contractors / local service businesses Denver / Colorado
- after-hours answering service for plumbers / HVAC / towing / auto repair
- 24/7 call answering for contractors Castle Rock / Denver metro
- capture after-hours calls service business
- answering service for home service companies / local service businesses Colorado
- towing answering service Denver; auto repair answering service Denver

Supporting themes woven into copy: Castle Rock, Parker, Highlands Ranch, south Denver, Denver metro suburbs; contractors and shops; trades and mobile services; HVAC / plumbing / electrical / towing / auto repair; busy-line / after-hours client capture.

**Pitch language (do not replace with “AI” or “missed-call text-back” leads):** a custom workflow that answers when the shop can’t, collects caller contact info and what service they need, and gets that to the shop so jobs don’t go to the next Google listing.

## Contact (on-site)

- **William** (Cory William Ernest)
- Phone: 303-915-3605
- Email: corywilliam3@gmail.com
- Area: Castle Rock, CO

## Notes

- No fake reviews, case studies, or client logos.
- No custom domain purchased as part of this build.
- Expand `privacy.html` when you add analytics, CRM, or formal client agreements.
