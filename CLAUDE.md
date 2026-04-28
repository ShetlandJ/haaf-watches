# Haaf Watches

Single-page static landing site for a friend's Shetland-based watch brand (not James's project — he's building it on their behalf). No backend, no build step, no framework.

## What "Haaf" means
Shetland dialect: *the deep sea beyond coastal waters; the deep-sea fishing carried out 30–40 miles offshore in open boats.* The brand story leans on this — Shetland heritage, sea, craft. Keep copy in that register (understated, maritime, heritage horology). Avoid generic watch-marketing language.

## Stack
- `index.html` — all markup, inline progressive-enhancement JS at the bottom (year stamp, mobile menu toggle, waitlist form)
- `styles.css` — all styles, custom properties at the top (`--deep`, `--brass`, etc.)
- `assets/logo.png` — also used as favicon/OG image
- `assets/photos/*.jpg` — real photography from the brand owner, all pre-resized to 1600px long edge, q=82, stripped, interlaced. Naming is descriptive (`black-flatlay-ice.jpg`, `serene-watch-fish.jpg`). When adding new photos, match this pipeline.
- `assets/fonts/*.woff2` — self-hosted variable Cormorant Garamond + Inter
- `.nojekyll` — disables Jekyll on Pages so dotfiles/underscore paths aren't filtered
- No bundler, no npm, no CI. Edit → commit → push.

## Local preview
```
python3 -m http.server 8000
```

## Deployment
- GitHub: **ShetlandJ/haaf-watches** (public)
- Live: **https://shetlandj.github.io/haaf-watches/**
- Pages source: `main` branch, root. Push to `main` = deploy. Build takes ~30–60s.
- Check build: `gh api /repos/ShetlandJ/haaf-watches/pages/builds/latest --jq '.status'`

## Page sections (top to bottom)
Hero (photo) → Story (haaf definition + heritage paragraph) → Craft (three principles, photo per pillar) → Commission (the Serene LK 297 piece) → Collection (Pelagic, black + blue) → Waitlist → Footer.

## Known placeholders (must be replaced before a real launch)
- **Formspree action URL** in the waitlist form — currently `https://formspree.io/f/your-form-id`. While it contains `your-form-id`, the JS falls back to `mailto:` so the CTA still works.
- **Contact email** `hello@haafwatches.com` (multiple occurrences in `index.html`). The friend hasn't confirmed a real address yet.
- **Pelagic specs** (40mm, automatic, 200m, sapphire, compass-rose bezel, steel bracelet) are plausible placeholders — not confirmed with the brand owner. Treat as subject to change.
- **Vessel photography in the Commission section** is credited inline to Ivan Reid (watermarks preserved on source). Confirm Paul has Ivan's clearance for web use before any real launch.

## Design guardrails
- Palette pulled from the logo: deep navy/teal (`--deep` #081a26) with brass accent (`--brass` #c8a978). No purple, no generic SaaS gradients.
- Typography: Cormorant Garamond (serif, display) + Inter (sans, body). **Self-hosted** as variable woff2 under `assets/fonts/` (latin subset, weights 300–500, plus a separate 300-italic face for the display italic). Both preloaded from `index.html` — if you add new weights or styles, preload them too.
- Heritage watch-brand tone: understated, no emoji, no inspirational copy, no AI-sounding hype.
- Mobile-first; verified at 390px. Under 640px the nav collapses to brand + hamburger; tapping the hamburger drops a vertical panel of all five links (Story / Craft / Commissions / Pelagic / Waitlist). The Waitlist pill loses its desktop pill styling on mobile and sits flush as a brass-tinted item.
- Respects `prefers-reduced-motion` — the hero's drift + scroll-hint animations switch off.
- Photo-led sections use `.hero__veil` (or equivalent) — a layered linear-gradient over the image — plus multi-layer text-shadows on titles/subtitles to keep copy legible against busy hero photography. Re-use the pattern for any new image-led block; don't invent a new approach.
