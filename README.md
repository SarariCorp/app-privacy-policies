# SarariCorp App Privacy Policies

This repository hosts a static, GitHub Pages-ready website for Android app privacy policies.

## Purpose

- Publish one privacy policy page per app.
- Keep policy links stable and review-friendly for Google Play submissions.
- Maintain a simple, dependency-free static site (no backend, no build step).

## URL convention

This repository uses the **`/apps/<app-slug>/`** convention.

Examples:
- Landing page: `https://<owner>.github.io/app-privacy-policies/`
- App policy: `https://<owner>.github.io/app-privacy-policies/apps/example-app/`

All links and assets use **relative paths** so the site works from GitHub Pages project subpaths.

## Folder structure

```text
.
├── .github/workflows/deploy-pages.yml
├── .nojekyll
├── assets/
│   └── css/styles.css
├── apps/
│   ├── _template/index.html
│   └── example-app/index.html
└── index.html
```

## Add a new app policy

1. Copy the example folder:
   - From: `apps/example-app/`
   - To: `apps/<your-app-slug>/`
2. Edit `apps/<your-app-slug>/index.html`.
3. Replace **all** placeholder fields in square brackets:
   - `[REPLACE APP NAME]`
   - `[REPLACE COMPANY NAME]`
   - `[REPLACE FREE/PAID/SUBSCRIPTION]`
   - `[REPLACE WITH EXACT DATA TYPES ...]`
   - `[REPLACE CONTACT EMAIL]`
   - `[REPLACE DATE]`
4. Add a new card on `index.html` under “Available app policies” linking to `./apps/<your-app-slug>/`.
5. Commit and push to `main` (the workflow deploys automatically).

## Required customization before publishing

Do **not** publish placeholder text. Every app page must be updated with real, accurate policy details for that specific app.

## Local preview options

Because this is a static site, you can preview locally with any HTTP server:

```bash
cd /path/to/app-privacy-policies
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.

## GitHub Pages setup

1. In GitHub, open repository **Settings → Pages**.
2. Set **Source** to **GitHub Actions**.
3. Ensure the workflow in `.github/workflows/deploy-pages.yml` is enabled.
4. On push to `main` (or manual workflow dispatch), Pages deploys automatically.

## Deployment workflow

- Workflow file: `.github/workflows/deploy-pages.yml`
- Triggers:
  - Pushes to `main`
  - Manual dispatch (`workflow_dispatch`)

## Manual steps after merge

- Replace placeholder content in `apps/example-app/index.html` (or add real app folders).
- Confirm Pages is enabled with **GitHub Actions** as source in repository settings.
