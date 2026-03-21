# System Architecture

## Overview
A static site generator that compiles Pug templates and SCSS stylesheets into a single-page resume website, deployed to GitHub Pages via GitHub Actions.

## Architecture Pattern
**Pattern**: Static Site Generator with Modular Build Pipeline

The project uses a build-time compilation approach where source templates and styles are transformed into static HTML/CSS/JS assets. There is no runtime server — the output is purely client-side.

## System Structure

### Source Templates
- **Location**: `src/pug/`
- **Purpose**: HTML structure and content definition
- **Key Files**: `index.pug` (564 lines — single-page resume with all sections)

### Stylesheets
- **Location**: `src/scss/`
- **Purpose**: Visual styling with modular organization
- **Key Files**:
  - `styles.scss` — Main entry point with imports
  - `_variables.scss` — Design tokens and custom variables
  - `_global.scss` — Base styles
  - `components/_sidenav.scss` — Sidebar navigation styles
  - `components/_icons.scss` — Icon styles
  - `sections/*.scss` — Per-section styles

### Client Scripts
- **Location**: `src/js/`
- **Purpose**: Client-side interactivity
- **Key Files**: `scripts.js` (29 lines — Bootstrap ScrollSpy initialization, responsive navbar handling)

### Static Assets
- **Location**: `src/assets/`
- **Purpose**: Images and favicon
- **Key Files**: `img/profile.jpg`, `img/favicon.ico`

### Build System
- **Location**: `scripts/`
- **Purpose**: Asset compilation and development tooling
- **Key Files**:
  - `build-pug.js` — Pug compilation + Prettier formatting
  - `build-scss.js` — SCSS compilation + Autoprefixer
  - `build-scripts.js` — JavaScript processing
  - `build-assets.js` — Static asset copying
  - `clean.js` — Output directory cleanup
  - `start.js` — Development server orchestration

### Build Output
- **Location**: `docs/`
- **Purpose**: Generated static site (served by GitHub Pages)
- **Key Files**: `index.html`, `css/styles.css`, `js/scripts.js`, `assets/`

## Data Flow

```
Source Files          Build Pipeline              Output
─────────────       ──────────────────          ────────────
src/pug/index.pug → Pug compile → Prettier →   docs/index.html
src/scss/*.scss   → Sass compile → Autoprefixer → docs/css/styles.css
src/js/scripts.js → Copy →                      docs/js/scripts.js
src/assets/*      → Copy →                      docs/assets/*
```

## External Integrations
- **Google Tag Manager**: Analytics tracking embedded in HTML head
- **Font Awesome CDN**: Icon library loaded via external script
- **GitHub Pages**: Static hosting and content delivery

## Configuration
- **Build config**: Hardcoded in individual build scripts (no central config file)
- **Prettier config**: Inline in `scripts/render-pug.js` (printWidth: 1000, tabWidth: 4)
- **Editor config**: `.editorconfig` for consistent editor settings
- **CI config**: `.github/workflows/npm-deploy.yml`

## Deployment Architecture

```
Developer Push (master) → GitHub Actions → npm ci → npm run build → GitHub Pages
```

The `docs/` directory is the deployment artifact. GitHub Pages serves it directly as a static website. No containerization or cloud infrastructure is involved.

---
*Based on codebase analysis performed 2026-03-21*
