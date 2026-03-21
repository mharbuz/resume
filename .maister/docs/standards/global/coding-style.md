## Coding Style

### EditorConfig Settings
This project uses `.editorconfig` for consistent settings: 4-space indentation, UTF-8 charset, final newlines required, trailing whitespace trimmed (exception: Markdown files).

### Prettier for HTML Output
Prettier 2.8.6 formats generated HTML with: `printWidth: 1000`, `tabWidth: 4`, `singleQuote: true`, `parser: html`. Config is inline in `scripts/render-pug.js`.

### Naming Consistency
Follow established naming patterns throughout the project:
- **JavaScript identifiers**: camelCase (`renderPug`, `destPath`, `filePath`)
- **State flag constants**: UPPER_CASE (`READY`)
- **File names (scripts)**: kebab-case with verb-noun pattern (`build-pug.js`, `render-scss.js`)
- **SCSS variables**: `$kebab-case` (`$sidebar-base-width`)
- **Pug IDs**: camelCase (`sideNav`, `navbarResponsive`)
- **CSS classes**: Bootstrap convention + kebab-case custom (`resume-section`)

### Descriptive Names
Choose names that clearly communicate intent; avoid cryptic abbreviations or single-letter identifiers outside tight loops.

### JavaScript Module Style
Use CommonJS (`require`/`module.exports`) for all Node.js scripts. Export render modules as named functions: `module.exports = function renderPug() { }`.

### Variable Declarations
Use `const` by default. Use `let` only when reassignment is needed. Never use `var`.

### Function Patterns
Use arrow functions for short callbacks (event handlers, watcher callbacks). Use function declarations for named/exported functions. Prefix non-exported helper functions with underscore (`_processFile`, `_handlePug`).

### 'use strict' Directive
Include `'use strict';` at the top of Node.js modules.

### Focused Functions
Write functions that do one thing well; smaller functions are easier to read, test, and maintain.

### Uniform Indentation
4-space indentation enforced via EditorConfig across all file types.

### No Dead Code
Remove unused imports, commented-out blocks, and orphaned functions instead of leaving them behind.

### No Backward Compatibility Unless Required
Avoid extra code paths for backward compatibility unless explicitly needed.

### DRY (Don't Repeat Yourself)
Extract repeated logic into reusable functions or modules.
