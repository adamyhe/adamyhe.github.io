# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Academic personal website for Adam Y. He (computational biologist), built with **Jekyll** using the Academic Pages theme. Hosted on GitHub Pages at https://adamyhe.github.io.

## Common Commands

```bash
# Install dependencies
bundle install

# Serve locally with live reload (accessible at localhost:4000)
jekyll serve -l -H localhost

# JavaScript build
npm run build:js       # Build minified JS
npm run watch:js       # Watch for JS changes
```

Requires Ruby, Bundler, Node.js, and `webrick` gem (for Ruby 3.0+).

## Architecture

**Static site generator pipeline:**
- `_config.yml` — Main site configuration (author info, social links, collections, plugins)
- `_pages/` — Site pages (about, cv, publications, etc.) written in Markdown with YAML front matter
- `_publications/` — Individual publication entries (Markdown), rendered as a collection
- `_talks/` — Talk entries (Markdown), rendered as a collection
- `_layouts/` — Jekyll HTML layout templates (single, talk, archive)
- `_includes/` — Reusable Liquid template partials (header, footer, sidebar, SEO, scripts)
- `_sass/` — SCSS stylesheets
- `_data/` — YAML data files driving navigation (`navigation.yml`) and author metadata
- `images/` — Project/research images
- `files/` — Downloadable PDFs

**Content generation:** `markdown_generator/` contains Python/Jupyter notebooks that convert TSV data into Markdown files for publications and talks.

**Key configuration in `_config.yml`:** Collections (publications, talks, teaching, portfolio), author profile, social links, permalink structure, and plugin list. The site uses kramdown with GFM for Markdown rendering.

## Content Workflow

To add a publication or talk: either create a new Markdown file in the appropriate collection directory with proper YAML front matter, or add data to the TSV files in `markdown_generator/` and run the corresponding notebook to auto-generate Markdown files.

Pages in `pages_not_included/` are archived and not published.
