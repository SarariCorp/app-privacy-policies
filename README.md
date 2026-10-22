# SarariCorp App Privacy Policies

Corporate-style, dependency-free GitHub Pages website for SarariCorp app privacy policies.

## Purpose

- Publish one policy page per app with stable review-ready URLs.
- Keep each app folder self-contained (policy page + app logo asset placeholder).
- Preserve a simple static deployment workflow with no backend and no secrets.

## URL convention

All policies follow:

- **Landing page**: `https://<owner>.github.io/app-privacy-policies/`
- **App policy page**: `https://<owner>.github.io/app-privacy-policies/apps/<app-slug>/`

The existing `example-app` route remains:

- `https://<owner>.github.io/app-privacy-policies/apps/example-app/`

All links and assets use relative paths, so deployment works under a GitHub Pages repository subpath.

## Visual and branding structure

- Shared theme/styles: `/assets/css/styles.css` (pure-black space-inspired corporate design)
- SarariCorp logo placeholder slot: `/assets/branding/sararicorp-logo-placeholder.svg`
- Landing page: `/index.html`
- App policy template route: `/apps/_template/`
- Example app route: `/apps/example-app/`

### Replacing the SarariCorp logo later

When the official logo is provided:

1. Replace `/assets/branding/sararicorp-logo-placeholder.svg` with the official asset (keep filename for zero link changes), or update references if filename changes.
2. Confirm pages rendering the logo:
   - `/index.html`
   - `/apps/example-app/index.html` (header brand text remains; no fake logo included)
   - `/apps/_template/index.html` (header brand text remains; no fake logo included)
3. Keep alt text descriptive (for example: `alt="SarariCorp official logo"`).

## App folder contract (required for every app)

Each app folder under `/apps/<app-slug>/` must contain:

- `index.html` (the app&apos;s privacy policy page)
- An app logo file or clearly marked placeholder asset (for example `app-logo-placeholder.svg`)

Current folders:

- `/apps/example-app/` → `index.html` + `app-logo-placeholder.svg`
- `/apps/_template/` → `index.html` + `app-logo-placeholder.svg`

## Add a new app policy

1. Copy `/apps/_template/` into `/apps/<your-app-slug>/`.
2. Keep the folder self-contained:
   - Update `index.html`
   - Replace `app-logo-placeholder.svg` with the app&apos;s logo (or keep placeholder until available)
3. Replace all required placeholders in the policy content:
   - `[REPLACE APP NAME]`
   - `[REPLACE COMPANY NAME]`
   - `[REPLACE FREE/PAID/SUBSCRIPTION]`
   - `[REPLACE WITH EXACT DATA TYPES OR "No personal data is collected directly by the app."]`
   - `[REPLACE WITH SPECIFIC USES OR "Not applicable because no data is collected."]`
   - `[REPLACE WITH ONLY THE SERVICES ACTUALLY USED, such as analytics, ads, crash reporting, or none.]`
   - `[REPLACE WITH RETENTION PERIODS OR "No personal data is stored by us."]`
   - `[REPLACE WITH APP-SPECIFIC CHILDREN PRIVACY STATEMENT.]`
   - `[REPLACE WITH REASONABLE TECHNICAL/ORGANIZATIONAL SAFEGUARDS USED.]`
   - `[REPLACE CONTACT EMAIL]`
   - `[REPLACE DATE]`
4. Add a card on `/index.html` linking to `./apps/<your-app-slug>/`.
5. Commit changes to `main` (deployment workflow publishes automatically).

## Accessibility and SEO notes

- Semantic landmarks (`header`, `nav`, `main`, `footer`) and heading hierarchy
- Skip link and visible keyboard focus states
- Responsive layout for mobile and desktop
- Reduced-motion support via `prefers-reduced-motion`
- Descriptive page titles and meta descriptions per page

## Local preview

```bash
cd /home/runner/work/app-privacy-policies/app-privacy-policies
python3 -m http.server 8000
```

Then open `http://localhost:8000/app-privacy-policies/` for project-subpath-like checks, or `http://localhost:8000/` for root checks.

## GitHub Pages deployment workflow

- Workflow file: `.github/workflows/deploy-pages.yml`
- Triggered on:
  - Push to `main`
  - Manual dispatch (`workflow_dispatch`)

## Manual steps after merge

- Replace placeholder policy text in each app before production publishing.
- Replace each app&apos;s `app-logo-placeholder.svg` with final logo assets.
- Replace `assets/branding/sararicorp-logo-placeholder.svg` when the official SarariCorp logo is provided.
- Verify repository **Settings → Pages** uses **GitHub Actions** as source.
