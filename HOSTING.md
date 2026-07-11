# DriveMe — Static Site Hosting Guide

This folder is the **compiled DriveMe website**: plain HTML/CSS/JS. It runs on any
static host with no server, no database, no build step. Asset paths are **relative**,
so it works at a domain root, a subfolder, or a GitHub project path unchanged.

## Contents
- `index.html` — site entry
- `404.html` — copy of index.html so deep links (e.g. `/car-hire`) work on refresh
- `_redirects` — SPA fallback rule for Netlify / Cloudflare Pages
- `.nojekyll` — tells GitHub Pages to serve the `assets/` folder as-is
- `assets/` — bundled CSS + JS (hashed filenames)
- `cars/`, `hero/`, `favicon*`, `og-image.png`, `apple-touch-icon.png` — images

## Deploy to GitHub Pages
1. Create/choose a repo, put **everything in this folder** at the repo root
   (or in a `/docs` folder).
2. Repo **Settings → Pages** → Source: your branch, folder `/ (root)` or `/docs`.
3. Save. Your site goes live at `https://<username>.github.io/<repo>/` (or your
   custom domain if configured). The relative paths make both work.
4. For a custom domain, add a `CNAME` file containing your domain, and point the
   domain's DNS to GitHub Pages.

## Deploy to Netlify / Cloudflare Pages / Vercel
- Drag-and-drop this folder, or connect the repo and set the publish directory to it.
- `_redirects` already handles client-side routing.

## Notes
- **Front-end functionality is fully preserved**: fleet browsing, pricing, about,
  WhatsApp booking (`wa.me` links), become-a-driver.
- There is **no backend** in this export — it was never needed for the public site.
- To edit content or design, use the full source project (the separate source ZIP)
  and rebuild with `bunx vite build --base=./`.
