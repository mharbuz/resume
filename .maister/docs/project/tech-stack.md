# Technology Stack

## Overview
This document describes the technology choices and rationale for the Maciej Harbuz Resume project.

## Languages

### JavaScript (Node.js)
- **Usage**: Build system, client-side scripting
- **Rationale**: Native ecosystem for web tooling; aligns with npm package management
- **Key Features Used**: ES modules, async file operations, child process management

### Pug (^3.0.3)
- **Usage**: HTML templating (100% of HTML generation)
- **Rationale**: Concise template syntax inherited from Start Bootstrap Resume template; compiles to clean HTML
- **Key Features Used**: Mixins, includes, interpolation, conditionals

### SCSS/Sass (1.60.0)
- **Usage**: All stylesheet authoring
- **Rationale**: Variables, nesting, and modular imports for maintainable CSS
- **Key Features Used**: Variables, nesting, partials, @import

## Frameworks

### Frontend
- **Bootstrap 5.2.3**: Responsive grid system, navigation components (navbar, ScrollSpy), utility classes. Chosen as the foundation from Start Bootstrap template.
- **Font Awesome Free ^6.4.0**: Icon library for social links and visual elements. Loaded via CDN.

### Backend
Not applicable — this is a static site with no server-side runtime.

### Testing
No testing framework currently configured.

## Build Tools & Package Management

### npm
- **Package Manager**: npm with package-lock.json for deterministic installs
- **Scripts**: 12 custom Node.js build scripts in `scripts/` directory

### Build Pipeline
| Stage | Tool | Input | Output |
|-------|------|-------|--------|
| Templates | Pug ^3.0.3 | `src/pug/*.pug` | `docs/*.html` |
| Formatting | Prettier 2.8.6 | Generated HTML | Formatted HTML |
| Styles | Sass 1.60.0 | `src/scss/*.scss` | `docs/css/styles.css` |
| Prefixing | Autoprefixer 10.4.14 | Compiled CSS | Prefixed CSS |
| Scripts | File copy | `src/js/*.js` | `docs/js/*.js` |
| Assets | File copy | `src/assets/*` | `docs/assets/*` |

### Development Server
- **BrowserSync ^3.0.4**: Live reload development server with file watching
- **Chokidar 3.5.3**: File system watcher for triggering rebuilds
- **concurrently 8.0.1**: Parallel task runner for dev workflow

## Infrastructure

### CI/CD
- **GitHub Actions**: Automated build and deployment on push to master
- **Workflow**: `.github/workflows/npm-deploy.yml`
- **Steps**: Checkout → Node.js 20 setup → `npm ci` → `npm run build` → Deploy to GitHub Pages

### Hosting
- **GitHub Pages**: Static site hosting from `docs/` directory on master branch

## Development Tools

### Linting & Formatting
- **Prettier 2.8.6**: HTML output formatting (printWidth: 1000, tabWidth: 4, singleQuote: true)
- **EditorConfig**: Consistent editor settings (UTF-8, 4-space indent, final newlines)
- **No ESLint**: JavaScript linting not currently configured
- **No Stylelint**: SCSS linting not currently configured

### Type Checking
- **None**: Pure JavaScript without TypeScript

## Key Dependencies
| Package | Version | Purpose |
|---------|---------|---------|
| bootstrap | 5.2.3 | UI framework |
| pug | ^3.0.3 | HTML templating |
| sass | 1.60.0 | SCSS compilation |
| prettier | 2.8.6 | Code formatting |
| autoprefixer | 10.4.14 | CSS vendor prefixes |
| postcss | ^8.5.6 | CSS post-processing |
| browser-sync | ^3.0.4 | Dev server |
| chokidar | 3.5.3 | File watching |
| @fortawesome/fontawesome-free | ^6.4.0 | Icons |

## Version Management
- Dependencies managed via `package.json` with `package-lock.json` for reproducible builds
- Node.js 20 specified in CI/CD workflow

---
*Last Updated*: 2026-03-21
*Auto-detected*: All technology versions, build pipeline structure, CI/CD configuration, development tools
