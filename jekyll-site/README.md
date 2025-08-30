# MIMIC Jekyll Website

This is the Jekyll version of the MIMIC website, built using the [Just the Docs](https://just-the-docs.github.io/just-the-docs/) theme.

## Local Development

### Prerequisites

- Ruby 3.1 or higher
- Bundler gem

### Setup

1. Install dependencies:
   ```bash
   cd jekyll-site
   bundle install
   ```

2. Run the development server:
   ```bash
   bundle exec jekyll serve
   ```

3. Open your browser to `http://localhost:4000`

### Building for Production

```bash
bundle exec jekyll build
```

The built site will be in the `_site` directory.

## Site Structure

```
jekyll-site/
├── _config.yml          # Jekyll configuration
├── _includes/            # Reusable content snippets
│   └── database/         # Database column definitions
├── _docs/               # Main documentation
├── _tutorials/          # Step-by-step guides
├── _concepts/           # Conceptual explanations
├── _faqs/               # Frequently asked questions
├── assets/              # Images, CSS, JS
└── index.md             # Homepage
```

## Key Features

### Collections
- **docs**: Main documentation organized by MIMIC version and module
- **tutorials**: Step-by-step guides for common tasks
- **concepts**: Explanatory content about database design and analysis
- **faqs**: Common questions and answers

### Includes System
Reusable content snippets for database column definitions:
```liquid
{% include database/subject_id.md %}
```

### Navigation
Hierarchical navigation with automatic menu generation based on front matter:
```yaml
---
title: "Page Title"
parent: "Parent Page"
nav_order: 1
---
```

## Content Guidelines

### Front Matter
All pages should include appropriate front matter:

```yaml
---
title: "Page Title"
layout: default
parent: "Parent Page"  # if applicable
nav_order: 1           # for ordering in navigation
permalink: /custom-url/ # if different from default
description: "Page description for SEO"
---
```

### Using Includes
For database column definitions, use the includes system:

```liquid
{% include database/subject_id.md %}
{% include database/hadm_id.md %}
```

### Code Blocks
Use fenced code blocks with language specification:

```sql
SELECT subject_id, COUNT(*) 
FROM patients 
GROUP BY subject_id;
```

### Callouts
Use Just the Docs callouts for important information:

```markdown
{: .note }
> This is a note callout.

{: .important }
> This is an important callout.

{: .highlight }
> This is a highlight callout.
```

## Deployment

The site is automatically deployed via GitHub Actions when changes are pushed to the main branch. See `.github/workflows/deploy-jekyll.yml` for the deployment configuration.

## Theme Customization

The site uses the Just the Docs theme. For customization options, see the [theme documentation](https://just-the-docs.github.io/just-the-docs/).

## Migration from Hugo

This Jekyll site replaces the previous Hugo-based website. Key differences:

- **Includes**: `{{% include "file.md" %}}` → `{% include file.md %}`
- **Front matter**: TOML → YAML
- **Navigation**: Automatic based on front matter
- **Collections**: Organized content types

## Contributing

1. Make changes to content files
2. Test locally with `bundle exec jekyll serve`
3. Submit pull request
4. Changes will be automatically deployed after merge
