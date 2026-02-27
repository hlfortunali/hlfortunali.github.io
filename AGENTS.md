# AGENTS.md - Developer Guide for Mr. Green Jekyll Theme

## Overview

This is a Jekyll theme project (Mr. Green Jekyll Theme) - a multilingual static site generator fully compatible with GitHub Pages. The codebase consists of Liquid templates, SCSS stylesheets, and JavaScript files.

## Build Commands

### Local Development

```bash
# Install dependencies
bundle install

# Start local server with live reload
bundle exec jekyll serve --watch --host 0.0.0.0

# Build for local development (no compression)
JEKYLL_ENV=development bundle exec jekyll build

# Build for production (with HTML/JS/SCSS compression)
JEKYLL_ENV=production bundle exec jekyll build --safe
```

### Testing

```bash
# Production build test (same as CI)
JEKYLL_ENV=production bundle exec jekyll build --safe

# Note: There are no unit tests in this project. The "test" is the build process itself.
```

### CI/CD

The project uses GitHub Actions (`.github/workflows/build-test.yml`) which runs:
```bash
JEKYLL_ENV=production bundle exec jekyll build --safe
```

**Note**: The `--safe` flag is required for GitHub Pages compatibility and ensures no third-party plugins are used.

---

## Code Style Guidelines

### File Naming Conventions

- **JavaScript files**: kebab-case (e.g., `color-scheme-switch.js`)
- **SCSS files**: kebab-case with BEM-like naming (e.g., `navigation.scss`)
- **Liquid templates**: kebab-case with descriptive names (e.g., `auto-content-generator.liquid`)
- **Directories**: kebab-case (e.g., `_js/default/nav/`)

### JavaScript Style

```javascript
/*! Mr. Green Jekyll Theme (https://github.com/MrGreensWorkshop/MrGreen-JekyllTheme)
 *  Copyright (c) 2022 Mr. Green's Workshop https://www.MrGreensWorkshop.com
 *  Licensed under MIT
 */

/* Dependencies: other-file.js */

(function () {
  'use strict';

  // Use const/let, avoid var
  const myConstant = 'value';
  let myVariable = 'value';

  // Function naming: camelCase
  function myFunctionName(param) {
    if (param == null) return;
    // implementation
  }

  // Event listeners at the end
  document.addEventListener("DOMContentLoaded", initFunction);

})();
```

- Use IIFE wrapping with `'use strict'`
- Always use `const` or `let`, never `var`
- Use camelCase for function and variable names
- Add copyright header to all new JS files
- Check for null/undefined before using parameters
- Use descriptive function names that explain their purpose

### SCSS/Style Guidelines

```scss
/* Mr. Green Jekyll Theme (https://github.com/MrGreensWorkshop/MrGreen-JekyllTheme)
 * Copyright (c) 2022 Mr. Green's Workshop https://www.MrGreensWorkshop.com
 * Licensed under MIT
 */

:root {
  @include get_scheme(bootstrap-dark-navbar-colors-);
}

.block-element {
  @include get_scheme(navigation-colors-);
  background: var(--background-color);
  transition: all 0.4s ease;
}

/* BEM-like naming */
.block__element--modifier {
  color: var(--text-color);
}
```

- Use SCSS variables and mixins from `assets/_scss/colors/`
- Use the `get_scheme()` mixin for theming
- Follow BEM naming convention: `.block__element--modifier`
- Group related styles together
- Use CSS custom properties (variables) for colors

### Liquid Template Guidelines

```liquid
{%-comment-%}
  Mr. Green Jekyll Theme (https://github.com/MrGreensWorkshop/MrGreen-JekyllTheme)
  Copyright (c) 2022 Mr. Green's Workshop https://www.MrGreensWorkshop.com
  Licensed under MIT
{%-endcomment-%}

{%- if condition -%}
  {% include path/to/include.html %}
{%- endif -%}

{%- assign variable = value -%}

{{ variable }}
```

- Use whitespace control (`-`) to minimize output whitespace
- Use `{%-` and `-%}` for control flow, `{{-` and `-}}` for output
- Use `{%-comment-%}{%-endcomment-%}` for block comments
- Always use descriptive variable names
- Group related logic together

### HTML Guidelines

```html
<!-- Mr. Green Jekyll Theme - Section Description -->
<div class="class-name" id="unique-id">
  <element attribute="value">
    Content
  </element>
</div>
```

- Use semantic HTML5 elements
- Keep indentation consistent (2 spaces)
- Use descriptive class and ID names
- Add comments for section boundaries

---

## Project Structure

```
├── _config.yml           # Jekyll configuration
├── Gemfile               # Ruby dependencies
├── _includes/            # Liquid template includes
│   ├── default/          # Default layout components
│   ├── post/             # Post-related templates
│   ├── post_list/       # Post list templates
│   ├── multi_lng/       # Multilingual support
│   ├── json/            # JSON data generators
│   └── util/            # Utility templates
├── _layouts/            # Page layouts
├── assets/
│   ├── _scss/           # SCSS source files
│   ├── css/             # Compiled CSS
│   ├── js/              # JavaScript files
│   │   └── _js/         # Source JS (compiled via main.js)
│   └── img/             # Images
├── _data/               # Configuration data (YAML)
├── _posts/              # Blog posts
└── tabs/                # Page content
```

---

## Configuration

### Key Configuration Files

- `_config.yml` - Main Jekyll settings
- `_data/conf/main.yml` - Main feature configuration
- `_data/conf/posts.yml` - Post-related settings
- `_data/owner/` - Site owner information per language

### Adding New Features

1. Create SCSS in `assets/_scss/` following the color scheme pattern
2. Create JS in `assets/js/_js/` with IIFE wrapper
3. Add include in `main.js` using Liquid conditional
4. Add configuration options in `_data/conf/`

---

## Common Patterns

### Color Scheme Support

```scss
// In SCSS, use the get_scheme mixin
.my-element {
  @include get_scheme(my-colors-);
  color: var(--my-text-color);
}
```

### JavaScript Feature Detection

```javascript
function initFeature() {
  const elements = document.querySelectorAll('.feature-selector');
  if (elements == null || elements.length == 0) return;
  // Initialize feature
}
```

### Conditional Includes in main.js

```liquid
{% if site.data.conf.main.some_feature_enabled %}
  {% include_relative _js/path/to/feature.js %}
{%- endif %}
```

---

## GitHub Pages Compatibility

- Always test with `--safe` flag before committing
- Only use plugins supported by GitHub Pages
- Test production build: `JEKYLL_ENV=production bundle exec jekyll build --safe`
- HTML compression is handled by `jekyll-compress-html`
- JS compression is configured in `_config.yml`

---

## Best Practices

1. **Test locally** before pushing: `bundle exec jekyll build --safe`
2. **Use semantic HTML** and accessible markup
3. **Keep templates modular** - use includes for reusable components
4. **Follow naming conventions** - kebab-case for files, camelCase for JS
5. **Add copyright headers** to all new code files
6. **Use configuration** over hardcoding - add options to `_data/conf/`
7. **Consider i18n** - use the multilingual system for user-facing strings
