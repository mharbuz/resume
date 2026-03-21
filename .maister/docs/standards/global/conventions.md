## Development Conventions

### Build System Architecture
Build process uses separate Node.js scripts for each asset type:
- Thin `build-*.js` entry points delegate to `render-*.js` modules
- Use `upath` (not `path`) for cross-platform file path handling
- NPM scripts use colon-separated namespaces: `build:pug`, `build:scss`, `build:assets`

### Build Output
All compiled output goes to the `docs/` directory (served by GitHub Pages). Never use `dist/` — this project uses `docs/` as the deployment artifact.

### CI/CD Pipeline
Automated deployment via GitHub Actions on push to master:
- **Node.js 20** as the build environment
- **`npm ci`** (not `npm install`) for deterministic dependency installation
- Build must succeed before deploy (`needs: build`)
- Single concurrent deployment (no cancellation of in-progress runs)
- Least-privilege GITHUB_TOKEN permissions (contents:read, pages:write, id-token:write)

### Master Branch as Deployment Branch
Only the `master` branch triggers automated deployments to GitHub Pages.

### Local Development
Run `npm start` to build and launch BrowserSync dev server with live reload and file watching via Chokidar.

### Predictable Structure
Organize files and directories in a logical, navigable layout. Source files in `src/` (pug/, scss/, js/, assets/), build scripts in `scripts/`, output in `docs/`.

### Up-to-Date Documentation
Keep README files current with setup steps, architecture overview, and contribution guidelines.

### Clean Version Control
Write clear commit messages, use feature branches, and add meaningful descriptions to pull requests.

### Environment Variables
Store configuration in environment variables; never commit secrets or API keys.

### Minimal Dependencies
Keep dependencies lean and up-to-date; document why major ones are included. Currently: 3 production, 10 dev dependencies.

### Consistent Reviews
Follow a defined code review process with clear expectations for reviewers and authors.

### Build What's Needed
Avoid speculative code and "just in case" additions (see minimal-implementation.md).
