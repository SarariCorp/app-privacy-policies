# SarariCorp App Privacy Policies

A dependency-free, static GitHub Pages site for SarariCorp app privacy policies.

## What this repository provides

- Corporate-styled landing page with a pure-black, space-inspired theme.
- One self-contained folder per app at `/apps/<app-slug>/`.
- Stable app-policy URLs for store submissions and user access.
- Shared styles in `/assets/css/styles.css` with responsive, accessible defaults.

## Theme and branding structure

- Current branding uses a **text-based SarariCorp wordmark** in header/footer copy.
- Shared visual system lives in `/assets/css/styles.css`.
- App cards and policy pages use polished gradients, high-contrast text, focus-visible states, and reduced-motion support.
- A decorative starfield effect is included with motion-safe fallbacks.

## Replacing SarariCorp and app logos later

No official SarariCorp logo is embedded yet.

- Keep the text wordmark or replace it in each page header when the official logo is ready.
- Each app folder must include its own logo file:
  - `apps/<app-slug>/logo.svg` (preferred) or `logo.png`
- Current placeholders:
  - `apps/example-app/logo.svg`
  - `apps/_template/logo.svg`

Replace the placeholder file in each app folder with the official app logo while preserving the same filename to avoid link updates.

## URL convention (GitHub Pages project-site compatible)

This repository uses the **`/apps/<app-slug>/`** convention.

Examples for this repo (`app-privacy-policies`):

- Landing page: `https://<owner>.github.io/app-privacy-policies/`
- Example app policy: `https://<owner>.github.io/app-privacy-policies/apps/example-app/`
- Any app policy: `https://<owner>.github.io/app-privacy-policies/apps/<app-slug>/`

All links and assets use relative paths so they work from both root and nested app pages on project-site subpaths.

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
└── index.html
```

## Add a new app folder and policy

1. Copy the example folder:
   - From: `apps/example-app/`
   - To: `apps/<your-app-slug>/`
2. Keep this self-contained app pattern:
   - `apps/<your-app-slug>/index.html`
   - `apps/<your-app-slug>/logo.svg` (or `logo.png`)
3. Edit `apps/<your-app-slug>/index.html` and replace every placeholder.
4. Add an app card in root `index.html` under “Available app policies” linking to `./apps/<your-app-slug>/`.
5. Commit to `main` (Pages deploy workflow publishes automatically).

## Required policy customization fields (before publishing)

Do **not** publish placeholders. At minimum replace all bracketed fields such as:

- `[REPLACE APP NAME]`
- `[REPLACE COMPANY NAME]`
- `[REPLACE FREE/PAID/SUBSCRIPTION]`
- `[REPLACE DATA TYPES COLLECTED ...]`
- `[REPLACE CONTACT EMAIL]`
- `[REPLACE DATE]`

Also ensure third-party services, retention details, and children/privacy statements match the real app behavior.

## Local preview

```bash
cd /home/runner/work/app-privacy-policies/app-privacy-policies
python3 -m http.server 8000
```

Open `http://localhost:8000/app-privacy-policies/` if served above this folder, or `http://localhost:8000/` when serving this repository root directly.

## GitHub Pages setup

1. In GitHub, open **Settings → Pages**.
2. Set **Source** to **GitHub Actions**.
3. Ensure `.github/workflows/deploy-pages.yml` is enabled.
4. Pushes to `main` (or manual `workflow_dispatch`) deploy automatically.

## Static deployment workflow

- Workflow file: `.github/workflows/deploy-pages.yml`
- Upload path: repository root (`.`)
- Runtime: static files only (no backend, no secrets)

## Remaining manual steps after merge

- Replace placeholder policy content with real app-specific legal text before publication.
- Replace placeholder logo assets with official SarariCorp/app logos when available.
- Verify final production URLs in Google Play Console or other distribution portals.
