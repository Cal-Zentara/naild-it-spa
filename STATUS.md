# STATUS — Nail'd It! Spa

*Last updated: 2026-04-23*

## What this is
Full client site + discovery form for Dalena Huynh's nail salon (7443 W Cerritos Ave, Stanton CA). Includes local SEO build, review automation, and custom domain. Active paying client.

## What's live
- Main site — https://nailditspa.com (GitHub Pages, Cloudflare DNS)
- Discovery form — https://cal-zentara.github.io/naild-it-spa-discovery/
- Google Business profile verified, live on Maps
- Local SEO: 15 indexable pages (6 cities + 5 services + 3 comparisons), sitemap submitted to Google Search Console
- Review automation: Fresha checkout email → Google review link (primary trigger) + Google review button on site + QR code (printable)
- Elevasis `naild-it-review-request` workflow tested end-to-end — Resend + hello@nailditspa.com fully verified

## What's broken / blocked
- Twilio A2P SMS registration — Business Profile resubmitted April 17, waiting on approval at cal.zentara@gmail.com. Once approved: Brand → Campaign ($15 one-time + $1.50/mo)
- Review SMS on hold — Fresha has no API/webhooks, no automatic trigger possible. Email + QR is the current path.
- No real team photos yet — using letter-initial avatars until Dalena provides
- Google Maps iframe uses approximate coordinates — needs exact embed swap

## What's next
1. Print + laminate Google review QR for counter (`site/photos/NailDITSpa QR.png`)
2. Monitor Twilio Business Profile approval email
3. Check Google Search Console in 2-4 weeks — which pages indexed, any coverage errors
4. Add real team photos when Dalena provides them
5. Once automation is fully live, discuss advertising/marketing with Dalena

## Key files
- `site/index.html` — main website (single-file, ~1700 lines)
- `discovery-form/index.html` — Dalena's discovery form
- `CLAUDE.md` — full doc: sections, line numbers, decisions, deploy, version history
- Review workflow: `ZentaraHQ/operations/src/naild-it/review-request.ts`

## Deploy notes
- GitHub: `Cal-Zentara/naild-it-spa` + `Cal-Zentara/naild-it-spa-discovery`
- Domain: nailditspa.com via Namecheap (registrar) → Cloudflare (DNS, free plan, proxy OFF)
- Supabase: N/A for this project
- Version: 1.8 (Local SEO build April 19, 2026)
