# Nail'd It! Spa — Project Docs

Client: Dalena Huynh (owner)
Business: Nail'd It! Spa — 7443 W Cerritos Ave, Stanton, CA 90680
Phone: (714) 947-0303
Instagram: @naildit.spa
Yelp: https://www.yelp.com/biz/naild-it-spa-stanton
Booking: http://fresha.com/b/Pgl0k

---

## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Folder Structure](#2-folder-structure)
3. [Brand & Colors](#3-brand--colors)
4. [Main Website — site/index.html](#4-main-website--siteindexhtml)
   - 4a. Nav
   - 4b. Hero
   - 4c. About
   - 4d. Services
   - 4e. Gallery
   - 4f. Reviews Slider
   - 4g. Team
   - 4h. Book Banner
   - 4i. Location
   - 4j. Footer
5. [Discovery Form — discovery-form/index.html](#5-discovery-form--discovery-formindexhtml)
6. [Photos](#6-photos)
7. [Key Decisions](#7-key-decisions)
8. [Deployment](#8-deployment)
9. [Current Version & Status](#9-current-version--status)

---

## 1. Project Overview

A full client website + discovery form for Dalena's nail salon in Stanton, CA. Built as a real client project (Cal's first paid/friend build). Two deliverables:

- **Discovery form** — deployed first to collect Dalena's answers before the site was built
- **Main website** — full premium single-page site with gallery, services, booking, team, reviews

---

## 2. Folder Structure

```
NaildItSpa/
├── CLAUDE.md               ← this file
├── discovery-form/
│   └── index.html          ← branded discovery form (deployed to GitHub Pages)
├── logo/
│   └── Logo.jpeg           ← Dalena's original logo file
├── photos/                 ← raw photos from Dalena (not used by site)
└── site/
    ├── index.html          ← main website
    ├── logo/
    │   └── Logo.jpeg       ← logo copy used by the website
    └── photos/             ← nail photos used in gallery + site sections
        ├── 8BA25184-...jpeg
        ├── IMG_0144.jpeg
        ├── IMG_0260.jpeg
        ├── IMG_0880.jpeg
        ├── IMG_0931.jpeg
        ├── IMG_0932.webp
        ├── IMG_0947.jpeg
        ├── IMG_1103.jpeg
        ├── IMG_1261.png
        ├── IMG_1898.jpeg   ← Halloween nails — NOT in gallery (removed)
        ├── IMG_1909.jpeg   ← Halloween nails — NOT in gallery (removed)
        ├── IMG_1921.jpeg
        ├── IMG_5497.jpeg
        ├── IMG_5835.jpeg
        └── IMG_9234.jpeg   ← used as book banner background
```

---

## 3. Brand & Colors

Extracted from Dalena's logo (blush pink + terracotta + gold):

| Variable | Hex | Used for |
|---|---|---|
| `--blush` | `#F9EDE8` | Page backgrounds, soft sections |
| `--white` | `#FFFFFF` | Cards, clean sections |
| `--terracotta` | `#C4714F` | Primary CTA buttons, accents |
| `--terracotta-dark` | `#A05038` | Button hover states |
| `--gold` | `#C9A24A` | Eyebrow labels, star ratings, sparkles |
| `--gold-light` | `#F0E0B0` | Gradient accents |
| `--dark` | `#1A0F0A` | Hero background base, dark sections |
| `--text-mid` | `#6B4A3A` | Body text |
| `--text-light` | `#A0796A` | Subtext, captions |
| `--border` | `#EDD5C8` | Dividers, card borders |

Fonts: **Playfair Display** (headings, quotes) + **Inter** (body). Both loaded from Google Fonts.

---

## 4. Main Website — site/index.html

Single-file HTML/CSS/JS. Everything lives in one file. Deployed to GitHub Pages under Cal-Zentara account.

Structure: CSS styles (lines 8–1129) → HTML sections (lines 1135–1587) → JavaScript (lines 1588–end)

| Section | CSS starts | HTML starts | What it is |
|---|---|---|---|
| Nav | line 34 | line 1135 | Fixed top navigation |
| Hero | line 152 | line 1162 | Animated gradient hero |
| About | line 324 | line 1190 | Split-screen story section |
| Services | line 398 | line 1218 | 8 service cards grid |
| Gallery | line 537 | line 1315 | Square photo grid + lightbox |
| Reviews | line 614 | line 1362 | Real Yelp review slider |
| Team | line 757 | line 1491 | 4 team member cards |
| Book Banner | line 830 | line 1526 | Full-bleed CTA photo section |
| Location | line 893 | line 1537 | Hours + Google Maps embed |
| Instagram strip | line 963 | line 1567 | Handle link + follow prompt |
| Footer | line 983 | line 1573 | Links + copyright |
| JavaScript | — | line 1588 | Sparkles, nav scroll, lightbox, fade-in, slider |

---

### 4a. Nav — CSS line 34 · HTML line 1135
- Fixed top, transparent over hero → turns white + blurred on scroll (`nav.scrolled` class toggled by scroll listener at JS line ~1612)
- Logo: `logo/Logo.jpeg` with `border-radius: 8px` — intentional so the blush-toned background blends in on dark hero instead of showing a hard white square
- Mobile: hamburger icon toggles `.mobile-menu` via `toggleMenu()`

### 4b. Hero — CSS line 152 · HTML line 1162
- Full-viewport (`height: 100vh`) animated gradient — no photo by design (original photo was Halloween nail art)
- CSS `background: linear-gradient(-45deg, ...)` + `background-size: 500% 500%` + `@keyframes gradientShift` — creates slow shifting color animation
- 22 floating sparkle characters (`✦ ✧ ◇`) injected by JS (line ~1589) into `#sparkles` — each gets random size, color, duration, delay via CSS custom properties
- CTA: "Book Now" → Fresha, "See Our Work" → `#gallery`

### 4c. About — CSS line 324 · HTML line 1190
- Split layout: text left (~58%), photo right (`max-width: 42%`, `max-height: 520px`)
- Photo: `photos/IMG_5835.jpeg`
- "My mommy did nails first" → rewritten tastefully as: "Nail care has always been in her family — her mother did nails before her."

### 4d. Services — CSS line 398 · HTML line 1218
- `grid-template-columns: repeat(2, 1fr)` — 8 service cards
- Prices pulled directly from Dalena's discovery form answers
- Includes: Gel-X, Dip/SNS, Acrylic, Pedicures (3 tiers: Classic/Happy/VIP), Manicures, Nail Art
- Booking CTA at bottom → Fresha link

### 4e. Gallery — CSS line 537 · HTML line 1315
- `grid-template-columns: repeat(3, 1fr)` with `aspect-ratio: 1` on each `.gallery-item`
- `object-fit: cover; object-position: center center` — forces clean square crop on all photos
- Click → lightbox (`openLightbox()` / `closeLightbox()` at JS line ~1628)
- Excluded from gallery: `IMG_1898.jpeg`, `IMG_1909.jpeg` (Halloween nail art)
- Excluded from photo strip (poor visibility): `IMG_1261.png`, `IMG_0880.jpeg`

### 4f. Reviews Slider — CSS line 614 · HTML line 1362
- 11 real Yelp reviews — actual reviewer names and cities from Yelp screenshots Cal provided
- Slider JS at line ~1660: `perView` = 3 desktop / 2 tablet / 1 mobile, recalculated on resize
- Auto-advances every 5 seconds via `setInterval`
- Prev/next arrow buttons + dot nav + touch/swipe support
- "Read all reviews on Yelp →" → https://www.yelp.com/biz/naild-it-spa-stanton

**Reviewers:** Linette L. (Garden Grove), S K. (Cypress), Chris R. (Westminster), Jailany B. (Los Angeles), Brenda H. (San Francisco), Michelle S. (Paramount), Nadine L. (Sylmar), Katrina L. (Newport Beach), Kylie C. (Newport Beach), Bethany D. (Orange), James V. (Costa Mesa)

### 4g. Team — CSS line 757 · HTML line 1491
- 4 cards: Dalena (owner), Twee, Nancy, Mindy — names sourced from real reviews and Dalena's form
- Letter-initial avatars (no staff photos provided yet)

### 4h. Book Banner — CSS line 830 · HTML line 1526
- Full-bleed photo background: `photos/IMG_9234.jpeg` with dark overlay
- Centered CTA → Fresha booking link

### 4i. Location — CSS line 893 · HTML line 1537
- Two-column: hours + address details left, Google Maps iframe right
- Hours from Dalena's form: Mon–Fri 9:30–7, Sat 9:30–6, Sun 10–5
- Map uses approximate coordinates — to fix later, grab exact embed from Google Maps search for the address

### 4j. Footer — CSS line 983 · HTML line 1573
- Dark background, minimal — name text, nav links, Yelp + Instagram links, copyright

---

## 5. Discovery Form — discovery-form/index.html

Built and deployed before the main site. Collected Dalena's answers (services, pricing, story, goals, timeline, etc.) which were used to write all the copy and service cards on the main site.

- Formspree endpoint: `https://formspree.io/f/xvzvnkay` (Cal's shared endpoint)
- Hidden field: `client_name = "Nail'd It! Spa"`
- Autosave to localStorage on every interaction
- 6 sections: About the Business, Your Services, Your Clients, Online Presence, Your Vision, Timeline & Next Steps
- Deployed at: https://cal-zentara.github.io/naild-it-spa-discovery/

---

## 6. Photos

Dalena provided 15 nail photos + her logo. Two were removed from the gallery (Halloween/horror nail art). The rest are used across the gallery, about section, and book banner.

Files NOT used in gallery (kept in folder but excluded by design):
- `IMG_1898.jpeg` — dark Halloween nail art
- `IMG_1909.jpeg` — dark Halloween nail art
- `IMG_1261.png` — nails not clearly visible
- `IMG_0880.jpeg` — nails not clearly visible

---

## 7. Key Decisions

| Decision | Why |
|---|---|
| Animated gradient hero instead of photo | First photo tried (IMG_1898) was Halloween nail art. Gradient with sparkles looks more premium anyway. |
| Square aspect-ratio gallery grid | `object-position: center bottom` looked worse — square grid forces consistent crop and looks cleaner |
| Logo with border-radius on dark hero | Avoids a hard-edged white rectangle on the dark hero background — blush tone blends in subtly |
| Real Yelp reviews instead of placeholders | Dalena provided screenshots of 11 real reviews — always more trustworthy than fake copy |
| Fresha for booking (not Yelp) | Dalena uses Fresha as her booking system. Yelp booking mentioned but Fresha is what she actively manages. |
| Single-file HTML | Easiest to deploy on GitHub Pages, no build step, Cal can edit it directly in one place |
| Removed stock photos from gallery/strip | 3 stock photos (French tip toenails, hands/feet on white, spa/flowers) removed — only Dalena's real work shown |
| 4-square photo strip | Replaced 2-column rectangle strip with 4 square photos — cleaner look, shows more variety |
| Full set prices instead of fill prices | Dalena flagged that site showed fill prices — updated Acrylic ($50), Gel-X ($55), SNS ($40) to full set |
| Custom domain nailditspa.com | Purchased on Namecheap for $6.99/yr. DNS pointed to GitHub Pages. Cal owns the domain on behalf of Dalena. |
| Local SEO build (April 19) | Added 14 pages (6 cities, 5 services, 3 comparisons). Each page targets a different search query. Before: 1 indexable page. After: 15 pages with full schema. |
| Vietnamese nail salon angle | Real competitive differentiator for OC market — Westminster/Little Saigon audience. Dedicated page + woven into all city pages near Westminster. |
| Dropped Fullerton/Orange as target cities | Too far for nail salon clientele (15+ min). Replaced with Los Alamitos (5 min, less competition) and kept Buena Park (10 min, high demand). |
| Migrated DNS from Namecheap to Cloudflare (April 16) | Namecheap BasicDNS UI made adding a subdomain MX record difficult, which Resend requires for bounce tracking. Cloudflare is free, handles all record types cleanly, and keeps domain registered at Namecheap. Proxy disabled (DNS only) on A records + CNAME to avoid SSL conflicts with GitHub Pages. |

---

## 8. Deployment

Both deliverables are deployed to GitHub Pages under the **Cal-Zentara** account.

| Deliverable | Repo | Live URL |
|---|---|---|
| Main website | `Cal-Zentara/naild-it-spa` | https://nailditspa.com (custom domain) |
| Main website (fallback) | `Cal-Zentara/naild-it-spa` | https://cal-zentara.github.io/naild-it-spa/ |
| Discovery form | `Cal-Zentara/naild-it-spa-discovery` | https://cal-zentara.github.io/naild-it-spa-discovery/ |

**Domain:** nailditspa.com — registered at Namecheap (CalZentara account). DNS managed by Cloudflare (free plan) as of April 16, 2026 — nameservers: `jen.ns.cloudflare.com` + `scott.ns.cloudflare.com`. Points to GitHub Pages via 4 A records (185.199.108–111.153) + www CNAME to cal-zentara.github.io. All proxying disabled (DNS only / gray cloud) to avoid SSL conflicts with GitHub Pages' own cert.

To push updates to the main site:
```bash
cd "C:\Users\Aesth\Desktop\Zentara\Projects\SSP\NaildItSpa\site"
git add index.html
git commit -m "your message"
git push
```

---

## 9. Current Version & Status

**Version:** 1.8 — Local SEO build complete (April 19, 2026). 14 new pages, schema, sitemap submitted to Google Search Console.
**Status:** Active client. Twilio A2P still in progress. Local SEO live and indexed.

**Local SEO build (April 19, 2026):**
- 6 city pages: /anaheim/, /garden-grove/, /westminster/, /cypress/, /los-alamitos/, /buena-park/
- 5 service pages: /gel-x-nails/, /acrylic-nails/, /dip-nails/, /pedicures/, /nail-art/
- 3 comparison pages: /vietnamese-nail-salon-orange-county/, /gel-vs-dip-nails/, /how-much-do-acrylic-nails-cost/
- Technical files: robots.txt, sitemap.xml (15 URLs), llm.txt
- Homepage: NailSalon JSON-LD schema, meta description, canonical, "Cities We Serve" section with internal links
- Gallery alt text updated to keyword-rich descriptions (was all "Nail art")
- Google Search Console: nailditspa.com verified + sitemap.xml submitted successfully
- Each new page has: unique title, meta, canonical, NailSalon schema, FAQPage schema, mobile responsive, internal links
- New photo added: IMG_20260419.png (floral stiletto nails, April 19 2026)

**What's done:**
- Discovery form live and submitted
- Main website built and deployed in one day (April 11, 2026)
- Real Yelp reviews added (slider)
- Booking integration (Fresha)
- Mobile responsive
- Stock photos removed — only real nail photos shown
- Address corrected to 7443 W Cerritos Ave, made clickable link to Google Maps
- Phone number made tap-to-call (tel: link)
- Google Maps iframe fixed to correct address
- Full set prices updated per Dalena (Acrylic $50, Gel-X $55, SNS $40)
- Custom domain nailditspa.com purchased and connected
- Google Business profile claimed and verified — live on Google Maps
- GMB services, hours, and description fully filled out (April 15, 2026)
- Google review automation built in Elevasis (`naild-it-review-request` workflow) — deployed to ZentaraHQ/operations
- nailditspa.com fully verified on Resend (April 16, 2:28 PM) — DKIM ✅ + SPF ✅ + MX ✅. Emails from hello@nailditspa.com now send. Path to get here: migrated DNS from Namecheap BasicDNS to Cloudflare, disabled Cloudflare proxy on A/CNAME (DNS only), added MX on `send` subdomain → `feedback-smtp.us-east-1.amazonses.com` priority 10.
- Fresha "Thank you for visiting" automation — Google review link added to the "Important info" field (April 16). Now fires automatically on every checkout via email. This is the primary review automation.
- Fresha text message automation — still enabled, goes to Fresha reviews (not Google). Cannot be changed — Fresha locks the message content.
- Google review button added to website reviews section (April 16) — sits alongside Yelp button
- Google QR code saved (`photos/NaildITSpa QR.png`) — ready to print for counter display
- Twilio account created (Cal's account) — phone number purchased: +1 657 337 3433 (Cypress, CA — $1.15/mo)
- EIN obtained: 42-1942565 (Christopher D Le, Sole Proprietor, Anaheim CA)
- A2P 10DLC customer profile submitted and approved (Zentara, Active)
- Twilio support ticket #26334444 submitted (April 15, 5:57 PM) — error 30701 on brand registration, waiting on response to cal.zentara@gmail.com
- Twilio Business Profile rejected (April 17) — errors 18602 (Business ID), 18603 (address), 18604 (rep identity), 18606 (email domain mismatch). Fixed: Legal Name → Christopher D Le, Business Type → Sole Proprietorship, Business Identity → Direct Customer, Email → hello@nailditspa.com, Website → https://nailditspa.com, Job Position → CEO. Resubmitted April 17, 1:39 AM. Twilio may contact via email/phone/video within 24 hours.

**Review System — Current State (April 16):**
Three layers in place:
1. Fresha checkout email → Google review link in footer (automatic, live)
2. Google review button on website (passive)
3. QR code for counter display (passive, print and laminate)
SMS automation (Twilio) is on hold — Fresha has no API/webhooks so there's no automatic trigger. Would require staff to manually tap a checkout button. Decision: keep it simple with email + QR for now. SMS may be repurposed for Cal's own demos/future clients.

**Key finding — Fresha limitation:**
Fresha is completely closed. No API, no webhooks, no Zapier. Cannot connect anything to it externally. The only customization available is the "Important info" text field on the checkout email. If SMS automation is ever needed, Dalena would need to switch to Square Appointments (has webhooks + Zapier) — but not worth the disruption for one feature.

**Pending / Next Steps:**
- **~~Resend blocker~~ RESOLVED (April 16, 2:28 PM):** Domain fully verified. Elevasis workflow can now send review request emails from hello@nailditspa.com.
- **~~Elevasis API key blocker~~ RESOLVED (April 18):** Workflow tested end-to-end — email delivered from hello@nailditspa.com to cal.zentara@gmail.com. Full pipeline (Elevasis → Resend → inbox) confirmed working.
- **Twilio blocker:** Business Profile resubmitted April 17. Wait for approval email at cal.zentara@gmail.com. Once approved: Twilio → Regulatory Compliance → A2P 10DLC → Brand Registration → Campaign Registration ($15 one-time + $1.50/mo)
- Print and laminate QR code for Dalena's counter
- Add real team photos when Dalena provides them
- Add more gallery photos as Dalena's portfolio grows
- Dalena interested in advertising/marketing — discuss after automation is fully live
- Monitor Google Search Console in 2-4 weeks — check which pages got indexed, watch for any coverage errors
- Local SEO pages will start ranking in 2-8 weeks — check Performance tab in GSC for first impressions

**Automation Details:**
- Workflow: `naild-it-review-request` in `ZentaraHQ/operations/src/naild-it/review-request.ts`
- Email: sends from `Nail'd It! Spa <hello@nailditspa.com>` via Resend (`resend-api-key` credential in Elevasis)
- Email-only (no SMS step in current code — SMS will be a separate workflow once Twilio A2P clears)
- Google review link: `https://g.page/r/CbxE-B-vjlwBEBE/review`
- Input schema: `{ clientName: string, clientEmail: string }` (no clientPhone in current version)
- Trigger: manual for now — Cal runs it after checkout until Dalena form is built
- Run via CLI: `cd ZentaraHQ/operations && npx elevasis-sdk exec naild-it-review-request -i '{"clientName":"...","clientEmail":"..."}'`

**Twilio Cost Reference:**
- Phone number: $1.15/month
- A2P Brand registration: $4.50 one-time
- A2P Campaign verification: $15.00 one-time
- Campaign monthly: $1.50/month
- Total upfront: ~$20 | Total monthly: ~$2.65
