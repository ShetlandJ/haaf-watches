# Haaf Watches

Single-page static landing site for a friend's Shetland-based watch brand (not James's project — he's building it on their behalf). No backend, no build step, no framework.

## What "Haaf" means
Shetland dialect: *the deep sea beyond coastal waters; the deep-sea fishing carried out 30–40 miles offshore in open boats.* The brand story leans on this — Shetland heritage, sea, craft. Keep copy in that register (understated, maritime, heritage horology). Avoid generic watch-marketing language.

## Stack
- `index.html` — all markup, inline progressive-enhancement JS at the bottom
- `styles.css` — all styles, custom properties at the top (`--deep`, `--brass`, etc.)
- `assets/logo.png` — the only asset, also used as favicon/OG image
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

## Known placeholders (must be replaced before a real launch)
- **Formspree action URL** in the waitlist form — currently `https://formspree.io/f/your-form-id`. While it contains `your-form-id`, the JS falls back to `mailto:` so the CTA still works.
- **Contact email** `hello@haafwatches.com` (two occurrences in `index.html`). The friend hasn't confirmed a real address yet.
- **Sixareen No. 01 specs** (40mm, Swiss auto, 200m, sapphire, etc.) are plausible placeholders — not confirmed with the brand owner. Treat as subject to change.

## Design guardrails
- Palette pulled from the logo: deep navy/teal (`--deep` #081a26) with brass accent (`--brass` #c8a978). No purple, no generic SaaS gradients.
- Typography: Cormorant Garamond (serif, display) + Inter (sans, body), both from Google Fonts.
- Heritage watch-brand tone: understated, no emoji, no inspirational copy, no AI-sounding hype.
- Mobile-first; verified at 390px. Nav collapses to brand + Waitlist CTA under 640px.
- Respects `prefers-reduced-motion` — the hero's drift + scroll-hint animations switch off.
