# Nostromo Energy — Data Center Showcase

Static site (plain HTML/CSS/JS, no build step) for the data-center pivot.

## Pages
- `index.html` — landing hub (the pivot story + entry cards; has 2 "coming soon" slots ready for new pages)
- `operations.html` — **Operational Showcase**: animated design-day loop (overnight charge → afternoon discharge → chillers off → meter under cap → freed compute). Play / pause / scrub / speed.
- `architecture.html` — **Cloud & Control Architecture**: the planned (hourly) loop + real-time (minutely) loop, with BMS & DCIM integration. Hover any block to inspect it.
- `assets/css/main.css` — shared design tokens + nav (palette/fonts taken from your Design-Day animator).

## Run locally
Just open `index.html` in a browser, or:
```bash
cd data-center-app
python3 -m http.server 8000      # then visit http://localhost:8000
```

## Deploy to GitHub Pages
Your repo: https://github.com/eyall-dot/data-center-app

```bash
# from inside the unzipped folder
git init
git remote add origin https://github.com/eyall-dot/data-center-app.git
git add .
git commit -m "Operational showcase + architecture pages"
git branch -M main
git push -u origin main
```
Then on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main` / `/ (root)` → Save.**

Live in ~1 minute at: **https://eyall-dot.github.io/data-center-app/**

(All asset paths are relative, so it works fine under the `/data-center-app/` sub-path.)

## Adding a new page later
1. Copy `operations.html` as a template (it already links the shared CSS + nav).
2. Add a link in the `.nav-links` block on every page.
3. On `index.html`, turn one of the `.card.soon` placeholders into a real `<a class="card" href="yourpage.html">`.

## Notes on the model
The numbers in the operations animation (32 MW cap, 20 MW IT, ~7 MW store, temp curve) are **illustrative** for the design-day story — swap them in `operations.html` (`state()` / constants at the top of the script) for a real site profile. The architecture diagram is generated from the `N` (nodes) and `E` (edges) arrays in `architecture.html`, so it's easy to re-wire.
