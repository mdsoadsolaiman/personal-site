# Md Soad Solaiman — Personal Site

A static site (no build step) for PhD applications. Just HTML/CSS/JS — open
`index.html` through a local server, or deploy the folder to any static host.

> Open it with a server, not a bare `file://` double-click — the page loads
> `css/style.css`, `js/main.js` and `assets/…` by relative path, and some
> browsers block those over `file://`. Quick option:
> `python -m http.server` then visit http://localhost:8000

## Structure
```
index.html          All page content
css/style.css        Design system (colors, type, layout, responsive rules)
js/main.js           Mobile nav toggle only — no framework, no dependencies
assets/profile.jpg   Hero portrait
assets/CV.pdf         CV linked from the "Download CV" button (swap in your latest)
assets/favicon.svg    "SS" monogram — navy #14202B tile, amber #C98A2B letters
assets/favicon.ico / apple-touch-icon.png   raster fallbacks
assets/og-image.png   1200×630 link-preview image (Open Graph / Twitter)
netlify.toml          Deploy config: publish dir + security/cache headers
```

## Design notes (for whoever edits this next)
- Palette: cool paper background (#F2F4F5), navy ink (#14202B) for text,
  amber (#C98A2B) as the single accent, teal (#1F6F63) as a secondary
  accent for dates/tags/DOIs. Change these as CSS variables at the top of
  `style.css` (`:root`) — everything else references them.
- Type: Newsreader (serif, headings) + Inter (body) + IBM Plex Mono (dates,
  tags, small labels). Loaded from Google Fonts via `<link>` tags in
  `index.html` — swap there if you want different fonts.
- The hero graphic is a hand-built SVG (actual vs. forecast line with an
  uncertainty band) that ties directly to the time-series forecasting
  research. It's inline in `index.html` inside `.hero-figure`.

## Deployment — Netlify (Git-connected, auto-deploy on push)

The repo is already a static site with `netlify.toml`, so there is no build
command. To wire it up:

1. **Push to GitHub.** (Repo: `github.com/mdsoadsolaiman/personal-site`.)
   ```
   git add -A && git commit -m "…" && git push
   ```
2. In Netlify: **Add new site → Import an existing project → GitHub**, then
   pick `mdsoadsolaiman/personal-site`.
3. Build settings — leave **Build command** empty and **Publish directory**
   as `.` (Netlify reads these from `netlify.toml`). Deploy.
4. Netlify gives you a `*.netlify.app` URL. Rename it under
   **Site configuration → Site details → Change site name** if you want
   something tidier, or add a custom domain under **Domain management**.
5. **Update the URL in `index.html`** — the `<link rel="canonical">` and the
   `og:`/`twitter:` `…url` / `…image` tags currently point at a placeholder
   (`md-soad-solaiman.netlify.app`). Set them to your real domain and push.

After step 2, every `git push` to the default branch redeploys automatically;
pull requests get their own preview URL.

## Local checks before pushing
- `python -m http.server` and click through at desktop + mobile widths.
- Lighthouse: Chrome DevTools → Lighthouse tab → analyze (run against the
  `localhost` server, not `file://`).
