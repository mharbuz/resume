## CSS & SCSS

### Framework: Bootstrap 5.2.3
Use Bootstrap 5.2.3 for responsive grid, navigation (navbar, ScrollSpy), and utility classes. Prefer Bootstrap utility classes over custom CSS when possible.

### Icons: Font Awesome 6
Use Font Awesome Free 6.x (`@fortawesome/fontawesome-free`) for all iconography via CSS classes.

### Work With the Framework
Use Bootstrap patterns as intended rather than fighting them with excessive overrides.

### Design Tokens via SCSS Variables
Define colors, spacing, and typography as SCSS variables in `src/scss/variables/`. Never hardcode color values in component/section files — reference variables instead (e.g., `color: $gray-800;` not `color: #ccc;`).

### Minimize Custom CSS
Prefer framework utilities to reduce custom styling maintenance.

### SCSS File Organization
- Main entry point: `styles.scss` (not prefixed)
- All partials use underscore prefix: `_global.scss`, `_colors.scss`
- Organize by subdirectory: `variables/`, `components/`, `sections/`
- Use kebab-case for all SCSS file names

### SCSS Import Order
Follow this order in `styles.scss`:
1. Variables (`@import "./variables.scss"`)
2. Bootstrap (`@import "bootstrap"`)
3. Global styles (`@import "./_global.scss"`)
4. Components (`@import "./components/*.scss"`)
5. Sections (`@import "./sections/*.scss"`)

Always use explicit `.scss` extensions in `@import` statements.

### SCSS Section Header Comments
Start every SCSS file with a three-line section header:
```scss
//
// Section Name
//
```

### SCSS Variables Naming
Use `$kebab-case` for all SCSS variables, consistent with Bootstrap's naming convention (e.g., `$sidebar-base-width`, `$navbar-base-height`).

### SCSS Nesting Depth
Keep nesting to a maximum of 3-4 levels deep for specificity control. Example: `.social-icons { .social-icon { &:hover { ... } } }` (3 levels).

### Production Optimization
Use CSS purging or tree-shaking to remove unused styles.
