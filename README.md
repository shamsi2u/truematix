# TrueMatix website — hosting package

```
site/        Upload the CONTENTS of this folder to the repo root. This is the website.
internal/    Do not upload. Working notes, not for publication.
README.md    This file. Do not upload.
```

## site/

| File | Purpose |
| --- | --- |
| `index.html` | Homepage |
| `online-brand-protection/index.html` | Service page, served at `/online-brand-protection/` |
| `404.html` | Not-found page |
| `CNAME` | Sets the custom domain to `www.truematix.com` |
| `.nojekyll` | Stops GitHub Pages running Jekyll. Hidden file: make sure it is uploaded |
| `robots.txt`, `sitemap.xml`, `llms.txt` | Crawler files |
| `favicon.svg`, `apple-touch-icon.png`, `og-cover.png` | Icons and the link-preview image |
| `css/theme.css` | Reference copy of the theme. The pages carry their styles inline and do not load it |

## Deploy to GitHub Pages

1. Put the contents of `site/` at the root of the repository's `main` branch.
   `index.html` must be visible at the top level, not inside a folder.

   ```bash
   cd site
   git init
   git add -A
   git commit -m "TrueMatix site"
   git branch -M main
   git remote add origin https://github.com/<user>/<repo>.git
   git push -u origin main
   ```

   If you upload through the browser instead, drag the files inside `site/`,
   not the folder. Then create `.nojekyll` with Add file → Create new file,
   because drag-and-drop skips hidden files.

2. Settings → Pages → Source: Deploy from a branch, `main`, `/ (root)`.
3. Custom domain: `www.truematix.com`. When the DNS check passes, tick Enforce HTTPS.

DNS records, redirect behaviour and the post-launch checks are in
`internal/DEPLOYMENT.md`.

## Two things to know

- **Links are root-relative** (`/online-brand-protection/`, `/#contact`). They work
  on `www.truematix.com`. They do not work at `<user>.github.io/<repo>/`, so
  test on the custom domain or locally with `python3 -m http.server` inside `site/`.
- **The repository must be public** on a free GitHub plan, or Pages serves nothing.

## Before launch

`internal/CLAIMS-REVIEW.md` lists claims on the live pages that still need
evidence or a decision: the three headline metrics, the case study, the named
list of monitored platforms, and whether an analyst reviews every match.
