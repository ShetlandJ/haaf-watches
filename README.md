# Haaf Watches — landing site

Static site. Deployed via GitHub Pages from `main`.

## Local preview
```
python3 -m http.server 8000
```
Then open http://localhost:8000.

## Things to wire up before launch
- **Waitlist form:** replace `your-form-id` in `index.html` with a real Formspree (or similar) form ID. Until then the form falls back to a `mailto:` link.
- **Contact email:** replace `hello@haafwatches.com` with the real address (both places in `index.html`).
- **Domain:** add a `CNAME` file with the custom domain if using one, then point DNS at GitHub Pages.
