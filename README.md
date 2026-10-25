# SarariCorp Privacy Policy Dashboard

A dependency-free GitHub Pages site for publishing SarariCorp application privacy policies.

## Website purpose

This repository only displays privacy policies. There is no add-app button, upload flow, admin panel, or user-submission form. New applications are added manually in the repository by creating a folder under `apps/`.

## Visual system

The dashboard uses a pure black, space-inspired technology theme with subtle star details, high-contrast typography, restrained neon accents, and responsive application cards. The current SarariCorp mark is a replaceable placeholder until the official logo is supplied.

## Structure

```text
.
├── assets/
│   ├── branding/sararicorp-logo.png
│   └── css/styles.css
├── apps/
│   ├── _template/
│   └── glandatlas/
│       ├── index.html
│       └── logo.png
├── index.html
└── .github/workflows/deploy-pages.yml
```

## Add an app manually

1. Copy `apps/example-app/` or `apps/_template/` to `apps/<app-slug>/`.
2. Keep `apps/<app-slug>/index.html` as the policy page.
3. Add the app's logo as `apps/<app-slug>/logo.svg` or `logo.png`.
4. Replace all policy placeholders with accurate, app-specific information.
5. Add one application card to the root `index.html`, linking to `./apps/<app-slug>/` and using the folder logo.
6. Commit the changes to `main`; the GitHub Pages workflow will publish them.

Each app policy is available at:

```text
https://<owner>.github.io/app-privacy-policies/apps/<app-slug>/
```

## Branding

Replace `assets/branding/sararicorp-mark.svg` with the official SarariCorp logo when available, preserving the filename or updating the image path in the site pages. Replace each app's local `logo.svg` with its official app logo.

## Before publishing a policy

Replace every bracketed placeholder, including the app name, company name, data collected, third-party services, retention and deletion details, children’s privacy statement, contact email, and last-updated date. Confirm the final content matches the real app and applicable legal/store requirements.

## Local preview

From the repository root:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.

## GitHub Pages

In repository **Settings → Pages**, select **GitHub Actions** as the source. The workflow deploys the static repository on pushes to `main` and supports manual dispatch.
