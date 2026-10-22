# SarariCorp App Privacy Policies

Static GitHub Pages website for publishing per-app privacy policies with a premium SarariCorp corporate black-space theme.

## What this repository provides

- A branded SarariCorp privacy center landing page (`/`).
- One self-contained folder per app under **`/apps/<app-slug>/`**.
- A reusable starter template in `apps/_template/`.
- Dependency-free static hosting (no backend, no build tooling required).

## Corporate black-space theme structure

The shared theme lives in `assets/css/styles.css` and includes:

- Pure/near-black cosmic background treatment.
- High-contrast typography and polished cards/borders.
- Responsive navigation and CTA styles.
- Visible keyboard focus states.
- Reduced-motion support with `prefers-reduced-motion`.
- Skip-link support for keyboard/screen-reader users.

## Branding and logo replacement

Current branding uses a **text-based SarariCorp wordmark placeholder** (no fabricated official logo).

When the official logo is ready:

1. Update header/hero branding in `/index.html`.
2. Replace each app logo placeholder file (`apps/<app-slug>/logo.svg` or `logo.png`).
3. Keep alt text descriptive for accessibility.

## Folder structure

```text
.
├── .github/workflows/deploy-pages.yml
├── .nojekyll
├── assets/
│   └── css/styles.css
├── apps/
│   ├── _template/
│   │   ├── index.html
│   │   └── logo.svg
│   └── example-app/
│       ├── index.html
│       └── logo.svg
├── index.html
└── README.md
```

## App folder pattern (scales to future apps)

Each app folder should be self-contained:

- `apps/<app-slug>/index.html` → app privacy policy page
- `apps/<app-slug>/logo.svg` (or `logo.png`) → app logo/placeholder asset

### Add a new app policy

1. Copy `apps/example-app/` to `apps/<your-app-slug>/`.
2. Update `apps/<your-app-slug>/index.html` policy content.
3. Replace `apps/<your-app-slug>/logo.svg` with your real app logo (or keep a clearly marked placeholder until available).
4. Add/update an app card on root `index.html` linking to `./apps/<your-app-slug>/`.

## Required privacy-policy customization fields

`apps/example-app/index.html` is a template only. Replace **all** marked placeholders before publishing:

- `[REPLACE APP NAME]`
- `[REPLACE COMPANY NAME]`
- `[REPLACE FREE/PAID/SUBSCRIPTION]`
- `[REPLACE WITH EXACT DATA TYPES ...]`
- `[REPLACE WITH SPECIFIC USES ...]`
- `[REPLACE WITH ONLY THE SERVICES ACTUALLY USED ...]`
- `[REPLACE WITH RETENTION PERIODS ...]`
- `[REPLACE WITH APP-SPECIFIC CHILDREN PRIVACY STATEMENT.]`
- `[REPLACE WITH REASONABLE TECHNICAL/ORGANIZATIONAL SAFEGUARDS USED.]`
- `[REPLACE CONTACT EMAIL]`
- `[REPLACE DATE]`

Do not claim real data practices until these fields are accurately customized.

## URL convention (GitHub Pages)

This repo preserves the **`/apps/example-app/`** URL convention and uses relative paths so links/assets work on both root and nested pages.

### Project site URLs (this repository)

- Landing page: `https://<owner>.github.io/app-privacy-policies/`
- Example app policy: `https://<owner>.github.io/app-privacy-policies/apps/example-app/`

### User/organization site variant (if this repo is renamed to `<owner>.github.io`)

- Landing page: `https://<owner>.github.io/`
- Example app policy: `https://<owner>.github.io/apps/example-app/`

## Local preview

```bash
cd /path/to/app-privacy-policies
python3 -m http.server 8000
```

Open: `http://localhost:8000/`

## GitHub Pages setup

1. Open repository **Settings → Pages**.
2. Set **Source** to **GitHub Actions**.
3. Ensure `.github/workflows/deploy-pages.yml` is enabled.
4. Push to `main` (or use manual dispatch) to deploy.

## Static deployment workflow

- Workflow: `.github/workflows/deploy-pages.yml`
- Triggers:
  - push to `main`
  - manual `workflow_dispatch`

## Manual steps after merge

- Replace template placeholders with app-specific legal/privacy details.
- Replace placeholder logo assets with official app logos when available.
- Confirm Pages source remains **GitHub Actions**.
