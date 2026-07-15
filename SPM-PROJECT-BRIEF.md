# SPM Website — Project Brief for Claude Code

You are working on a real client website. Read this whole file before touching anything.

## Business context

- **Client:** Strategic Pest Management, Inc. — family-owned pest control company in El Segundo, CA, operating since 1999. Owner: Beau Blacksten. Office contact (writes on Beau's behalf): Sharon, strategicpest@aol.com. Phone (call/text): (310) 322-5001. Fax: (310) 322-2697. Mailing: P.O. Box 3404, El Segundo, CA 90245.
- **They have an old site** at www.strategicpestmanagement.com (do not touch it, do not link to it). We are replacing it.
- **This is client #1 of YourSitesDone.com**, Matt Mirick's website business. Quality bar is high — this site is also the portfolio piece.
- The client reviewed a draft and sent back written feedback + hand-annotated printouts on Jul 14, 2026. ALL of that feedback is already applied to the current file. The content rules below are LOCKED client decisions — do not undo them.

## Where everything lives

- **Repo:** `mmirick/yoursitesdone-website` (GitHub, public). Matt's `gh` CLI on this Mac is already authenticated as `mmirick` — no new tokens needed. `gh repo clone mmirick/yoursitesdone-website`
- **The site (single file):** `previews/strategic-pest-management.html` — self-contained HTML, all CSS inline in `<head>`, no build step, no dependencies except Google Fonts.
- **The logo:** `previews/spm-logo.svg` — layered vector (cobalt star silhouette + white text paths), traced from the client's high-res print original. Referenced by the nav as `spm-logo.svg` (relative path — keep them siblings).
- **Live preview (GitHub Pages, already serving):** https://mmirick.github.io/yoursitesdone-website/previews/strategic-pest-management.html
- Pages config: legacy build, `main` branch, root path. Any push to `main` auto-deploys in ~1 min.
- Note: yoursitesdone.com (the custom domain on a DIFFERENT fork) is stale/unrelated — ignore it. Do not touch the repo `ask-manny-mb/yoursitesdone-website`.

## LOCKED content rules (client decisions — never revert these)

1. **No "free inspection" anywhere.** They quote over the phone. All CTAs = "Get a Quote" / "Call or Text."
2. **"No contracts — cancel anytime" is a headline selling point.** Keep it prominent (hero, trust bar, FAQ #1).
3. **License:** "Licensed, Bonded & Insured" ONLY. Never any license number (the old OPR9966 was a fake placeholder — must never reappear).
4. **Family owned & operated since 1999.** Keep prominent.
5. **Service area:** "West Los Angeles & the South Bay" as text ONLY. Never a list of city names.
6. **Pest list (exactly these 14, text list, no photo grid):** rats, mice, cockroaches, water beetles, ants, silverfish, stored grain pests, earwigs, crickets, fleas & ticks, mites, carpet beetles, fabric pests, wasps.
7. **Never mention:** termites, bees, spiders, wildlife trapping — not even as "we don't do this." Just absent.
8. **Services include:** residential (with eco-friendly treatment options), commercial & industrial (NOT restaurants — word must not appear), rodent control, exclusion work (crawl-space vent repair/rebuild, sealing openings), ongoing plans (monthly / bi-monthly / quarterly), one-time treatments.
9. **Hours framing (positive only, no "Closed" rows):** Phone & text monitored 24/7 · Appointments Mon–Fri 6:00 AM–5:00 PM · Weekends: we return calls & texts. Same-day response.
10. **Brand color:** cobalt blue (site uses #0047AB primary / #2E7CE4 accent). No green.
11. **Reviews section stays** (client loved it).
12. **"Creative Solutions"** is their real slogan — currently footer-only, italic. Fine to keep there; do not promote it back to the hero (client crossed it out as a headline).
13. **Lead notifications must eventually reach the client by EMAIL AND TEXT** (see form step below).
14. No certifications/associations section (they have none they want listed).

## Open items Matt may tweak (not locked)

- Hero headline is currently "Family-Owned Pest Control. / No Contracts. Ever." — Matt's assistant's wording, Matt may reword.
- "Rich Blacksten" appears in the Owner-Operated card (sourced from Yelp reviews). Pending confirmation with the client (owner of record is Beau Blacksten). If in doubt, change to "The Strategic team" phrasing without a first name.
- Logo star fill is site-cobalt #0047AB. The client's print original is closer to indigo #37348F. One-line change in the SVG's first `<g fill=...>` if Matt wants print-exact.

## Launch runbook (what's actually left)

### 1. Domain — buy `strategicpestmgmt.com`
Client's ranked picks: strategicpest.com (TAKEN, third party since 2013), **strategicpestmgmt.com (verified available Jul 14 — buy this)**, strategicpestmanagementinc.com, strategicpestmgmtinc.com. Registrar: Matt's choice (Cloudflare Registrar = at-cost, or Namecheap). Matt must do the purchase/payment himself.

### 2. Hosting — two acceptable paths
- **Path A (fastest, already working): GitHub Pages.** Copy `previews/strategic-pest-management.html` → `index.html` and `spm-logo.svg` into a NEW repo `mmirick/spm-website`, enable Pages (main/root), set custom domain `strategicpestmgmt.com` + enforce HTTPS. DNS at registrar: apex A records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` + `www` CNAME → `mmirick.github.io`.
- **Path B (the original architecture plan): Cloudflare Pages.** Same new repo, connect at pages.cloudflare.com (framework: none, no build, output dir root). If domain is bought at Cloudflare, DNS is one click.
- Either way: the preview copy in `yoursitesdone-website/previews/` stays as the portfolio/demo copy.

### 3. Lead form (required before client handoff)
Form currently posts to `https://formspree.io/f/placeholder` — dead. Requirements: notifications to strategicpest@aol.com AND text alert (client requirement). Suggested: Formspree or Web3Forms free tier for email now (Matt creates the account, gets real endpoint ID, swap into the `action=` attr); SMS = phase 2 (Zapier SMS, Twilio hook, or Formspree→email-to-SMS). Do not ship the site to the client with a dead form — if SMS isn't ready, email-only is acceptable for launch, SMS follows.

### 4. Pre-launch polish checklist
- `<title>`/meta/og tags: point at final domain, og:image (can generate from logo on cobalt background, 1200×630)
- favicon: derive from the star mark in `spm-logo.svg` (32px + 180px apple-touch)
- Remove the "Built by YourSitesDone.com" footer line ONLY if Matt says so (it's the portfolio backlink — default keep)
- Lighthouse pass: page is a single ~34KB HTML + 216KB SVG; should score 95+ out of the box. Consider inlining a compressed logo or width-capped raster fallback only if LCP flags it.
- 301 plan for the old site is NOT ours — client controls www.strategicpestmanagement.com separately.

### 5. Handoff
Final URL goes to Matt, who sends it to the client. 

## Hard guardrails

- **NEVER contact the client** (no emails to strategicpest@aol.com, nothing). All client communication goes through Matt personally.
- **Never send email from Matt's accounts, period.**
- Work only in `mmirick/*` repos. Do not touch `ask-manny-mb/*`.
- Don't undo the LOCKED content rules above, even if a "better" design instinct says otherwise — they are client decisions.
- The phone number (310) 322-5001 and email strategicpest@aol.com are the client's real contacts — exact digits matter everywhere they appear.
