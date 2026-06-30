# FORGE — Project Page

Static project page for **FORGE: Fine-Tuning Over Reward Generations through Evolution**, ready to deploy on GitHub Pages.

## Files

```
site/
├── index.html          # the page (single file, no build step)
├── paper.pdf           # the paper, linked from the "Paper (PDF)" button
├── .nojekyll           # tells GitHub Pages to serve files as-is
└── assets/figures/     # figures extracted from the PDF
```

## Deploy on GitHub Pages

1. Create a repo and push the **contents of this `site/` folder** to the root of a branch (e.g. `main`).
   - For a user/org site, name the repo `<username>.github.io`.
   - For a project site, any repo name works; the page will live at `https://<username>.github.io/<repo>/`.
2. In the repo: **Settings → Pages → Build and deployment**.
3. Set **Source = Deploy from a branch**, pick your branch and the `/ (root)` folder, then **Save**.
4. Wait ~1 minute, then open the URL shown on that settings page.

```bash
git init
git add .
git commit -m "FORGE project page"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

## Before publishing

- Replace the `#` placeholders in `index.html` for the **arXiv** and **Code** buttons with real URLs.
- Update the **BibTeX** block once the paper is de-anonymized.
- Author/affiliation are intentionally left anonymous for double-blind review.

The page uses only CDN resources (Google Fonts + MathJax), so no build tooling is required.
