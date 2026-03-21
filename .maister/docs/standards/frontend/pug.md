## Pug Template Conventions

### Single-Quote Attribute Values
Use single quotes for all Pug attribute values: `html(lang='en')`, `meta(charset='utf-8')`.

### Class Chaining with Dot Notation
Apply CSS classes using Pug's dot-notation chaining, not class attributes:
```pug
.d-flex.flex-column.flex-md-row.justify-content-between.mb-5
```

### ID Naming: camelCase
Use camelCase for HTML element IDs: `nav#sideNav`, `#navbarResponsive`.

### Section Comments
Precede major page sections with a single-line Pug comment identifying the section: `// Navigation`, `// About`, `// Experience`.

### 4-Space Indentation
Use 4-space indentation for Pug nesting, matching the project's EditorConfig setting.

### Resume Entry Layout Pattern
All resume entries (experience, projects, education) follow this flex-based layout:
```pug
.d-flex.flex-column.flex-md-row.justify-content-between.mb-5
    .flex-grow-1
        h3.mb-0 Title
        .subheading.mb-3 Subtitle
    .flex-shrink-0
        span.text-primary Date Range
```
