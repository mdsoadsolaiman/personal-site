# MD Soad Solaiman: Personal Site

A static site (no build step) for PhD applications. Just HTML/CSS/JS. Open
`index.html` in a browser, or serve the folder with any static host.

## Structure
```
index.html      All page content
css/style.css   Design system (colors, type, layout, responsive rules)
js/main.js      Mobile nav toggle only, no framework, no dependencies
```

## Design notes (for whoever edits this next)
- Palette: cool paper background (#F2F4F5), navy ink (#14202B) for text,
  amber (#C98A2B) as the single accent, teal (#1F6F63) as a secondary
  accent for dates/tags/DOIs. Change these as CSS variables at the top of
  `style.css` (`:root`), everything else references them.
- Type: Newsreader (serif, headings) + Inter (body) + IBM Plex Mono (dates,
  tags, small labels). Loaded from Google Fonts via `<link>` tags in
  `index.html`; swap there if you want different fonts.
- The hero graphic is a hand-built SVG (actual vs. forecast line with an
  uncertainty band) that ties directly to the time-series forecasting
  research. It is inline in `index.html` inside `.hero-figure`, and is easy to
  restyle or replace with a real chart image later.

## To personalize further
1. **Profile photo**: added (`assets/profile.jpg`), pre-cropped to a portrait
   frame and shown in the hero. Swap the file (keep the same filename, or
   update the `src` in `index.html`) if you want a different shot.
2. **CV download**: add your PDF as `assets/CV.pdf`, then add a button next
   to "Email me" in the hero:
   ```html
   <a href="assets/CV.pdf" class="btn btn-ghost" target="_blank">Download CV ↗</a>
   ```
3. **Favicon**: add `assets/favicon.ico` and link it in `<head>`:
   ```html
   <link rel="icon" href="assets/favicon.ico">
   ```
4. Content (bio wording, project descriptions, publications) is all plain
   text in `index.html`. Search for the section you want to edit by its
   `<h2>` (About, Research interests, Research & projects, Publications,
   Background, Get in touch).

## Suggested next steps in Claude Code
- Ask Claude Code to set up GitHub Pages (or Netlify/Vercel) deployment for
  this folder, since it is a static site this should be a short task.
- Ask it to add a proper favicon and Open Graph image (for link previews
  when you share the site).
- If you add more projects/publications over time, ask Claude Code to keep
  the same card/list patterns already in `index.html` so the design stays
  consistent.
- Consider a lightweight analytics snippet (e.g., Plausible or Simple
  Analytics) if you want to know who's visiting before interviews.
- Run it through Lighthouse in Chrome DevTools for an accessibility/perf
  check once deployed.
