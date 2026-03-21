# Documentation Index

**IMPORTANT**: Read this file at the beginning of any development task to understand available documentation and standards.

## Quick Reference

### Project Documentation
Project-level documentation covering vision, goals, architecture, and technology choices.

### Technical Standards
Coding standards, conventions, and best practices organized by domain.

---

## Project Documentation

Located in `.maister/docs/project/`

### Vision (`project/vision.md`)
Project overview, purpose, current state, and 6-12 month goals for the Maciej Harbuz Resume site. Covers the evolution from a Start Bootstrap template to a custom modular build system with automated CI/CD deployment.

### Tech Stack (`project/tech-stack.md`)
Complete technology inventory: Pug templating, SCSS/Sass styling, Bootstrap 5 framework, Node.js build system with 12 custom scripts, BrowserSync dev server, Prettier formatting, GitHub Actions CI/CD, and GitHub Pages hosting. Includes version details and rationale for each choice.

### Architecture (`project/architecture.md`)
Static site generator architecture with modular build pipeline. Documents source templates (Pug), stylesheets (SCSS), client scripts, static assets, build system scripts, and output structure. Includes data flow diagram, external integrations (Google Tag Manager, Font Awesome CDN), configuration locations, and deployment architecture via GitHub Actions to GitHub Pages.

---

## Technical Standards

### Global Standards

Located in `.maister/docs/standards/global/`

These standards apply across the entire codebase, regardless of frontend/backend context.

#### Error Handling (`standards/global/error-handling.md`)
Clear user messages, fail-fast validation, typed exceptions, centralized handling at boundaries, graceful degradation, retry with backoff, resource cleanup in finally blocks.

#### Validation (`standards/global/validation.md`)
Server-side validation always required, client-side for feedback, validate early, specific field-level errors, allowlists over blocklists, type/format checks, input sanitization, business rule validation, consistent enforcement across entry points.

#### Conventions (`standards/global/conventions.md`)
Build system architecture (separate build/render scripts, upath for cross-platform paths, colon-namespaced NPM scripts), build output to `docs/` directory for GitHub Pages, CI/CD pipeline (GitHub Actions, Node.js 20, `npm ci`, least-privilege permissions), master branch deployment, local dev with BrowserSync/Chokidar, predictable `src/`/`scripts/`/`docs/` structure, minimal dependencies (3 production, 10 dev).

#### Coding Style (`standards/global/coding-style.md`)
EditorConfig settings (4-space indent, UTF-8, final newlines), Prettier 2.8.6 for HTML output, naming consistency (camelCase JS identifiers, UPPER_CASE constants, kebab-case file names, $kebab-case SCSS variables, camelCase Pug IDs), CommonJS module style, const-by-default variable declarations, arrow functions for callbacks, function declarations for exports, underscore-prefixed helpers, 'use strict' directive, DRY principle.

#### Commenting (`standards/global/commenting.md`)
Let code speak through structure and naming, comment sparingly for non-obvious logic only, no change-log style comments.

#### Minimal Implementation (`standards/global/minimal-implementation.md`)
Build only what is needed, every method must have a caller or readability purpose, delete exploration artifacts, no future stubs, no speculative abstractions, review before commit, remove dead code promptly.

---

### Frontend Standards

Located in `.maister/docs/standards/frontend/`

These standards apply to frontend code (UI components, client-side logic, styling).

#### CSS & SCSS (`standards/frontend/css.md`)
Bootstrap 5.2.3 framework with utility-first approach, Font Awesome 6 icons, SCSS variables for design tokens in `src/scss/variables/`, SCSS file organization (underscore-prefixed partials, kebab-case names, variables/components/sections subdirectories), import order (variables, Bootstrap, global, components, sections), three-line section header comments, $kebab-case variable naming, 3-4 level max nesting depth, CSS purging for production.

#### Pug Templates (`standards/frontend/pug.md`)
Single-quote attribute values, dot-notation class chaining, camelCase ID naming, single-line section comments, 4-space indentation, resume entry flex-based layout pattern (flex-column/flex-md-row with flex-grow-1 content and flex-shrink-0 dates).

#### Components (`standards/frontend/components.md`)
Single responsibility, reusability with configurable props, composability over monoliths, clear prop interfaces with defaults, encapsulation, consistent naming, local state management, minimal props, documentation of usage and examples, vanilla DOM APIs only (no frontend frameworks).

#### Accessibility (`standards/frontend/accessibility.md`)
Semantic HTML elements, keyboard navigation with visible focus, 4.5:1 color contrast ratio, alt text and form labels, screen reader testing, ARIA attributes for complex components, proper heading hierarchy, focus management in dynamic content.

#### Responsive Design (`standards/frontend/responsive.md`)
Mobile-first approach, standard breakpoints, fluid percentage-based layouts, relative units (rem/em), cross-device testing, touch-friendly tap targets (44x44px minimum), mobile performance optimization, readable typography, content priority on small screens.

---

### Backend Standards

*Not initialized for this project. If you need backend standards, you can:*
- *Add them manually using the docs-manager skill*
- *Run `/maister:standards-discover --scope=backend` to auto-discover*

---

### Testing Standards

Located in `.maister/docs/standards/testing/`

These standards apply to all testing code (unit, integration, E2E).

#### Test Writing (`standards/testing/test-writing.md`)
Test behavior not implementation, clear descriptive test names, mock external dependencies, fast unit test execution, risk-based testing priorities, balance coverage and velocity, critical path focus, appropriate edge case depth.

---

## How to Use This Documentation

1. **Start Here**: Always read this INDEX.md first to understand what documentation exists
2. **Project Context**: Read relevant project documentation before starting work
   - Vision and roadmap for understanding project goals
   - Tech stack for understanding technology constraints
   - Architecture for understanding system design
3. **Standards**: Reference appropriate standards when writing code
   - Global standards apply to all code
   - Domain-specific standards (frontend/backend/testing) apply to relevant code
4. **Keep Updated**: Update documentation when making significant changes
   - Update project docs when goals, tech stack, or architecture changes
   - Update standards when team conventions evolve
   - Update INDEX.md when adding or removing documentation
5. **Customize**: Adapt all documentation to your project's specific needs
   - Project documentation should reflect your actual project
   - Standards should reflect your team's conventions
   - Both should be version-controlled and reviewed regularly

## Updating Documentation

### When to Update

- **Project docs**: When project goals, tech stack, or architecture changes
- **Standards**: When team conventions evolve or new patterns are adopted
- **INDEX.md**: When adding, removing, or significantly changing documentation

### How to Update

1. Edit the relevant documentation file directly
2. Update INDEX.md if the file's purpose or description changes
3. Ensure CLAUDE.md still references this INDEX.md
4. Commit changes to version control
5. Notify the team of significant documentation changes

### Getting Help

Use the Documentation Manager skill to:
- Initialize documentation in a new project
- Add new documentation files
- Update existing documentation
- Validate documentation consistency
- Manage INDEX.md automatically
- Ensure CLAUDE.md integration

---

## Documentation Priority

When making development decisions, follow this priority order:

1. **Project documentation** in `.maister/docs/` (highest priority)
   - Represents team decisions and project-specific requirements
2. **Code patterns** visible in the codebase
   - Shows how the team actually implements things
3. **User's direct instructions**
   - Specific guidance for the current task
4. **General best practices** (lowest priority)
   - Default to industry standards when no specific guidance exists

**The documentation in `.maister/docs/` represents team decisions and should be followed unless the user explicitly overrides them.**

---

**Last Generated**: 2026-03-21
**Maintained by**: Documentation Manager skill
