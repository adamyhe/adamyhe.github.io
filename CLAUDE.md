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

Requires Ruby, Bundler, Node.js, and `webrick` gem (for Ruby 3.0+). Ruby version is pinned via `.ruby-version` (rbenv).

If a conda/miniforge environment is active, its `CC`/`CXX`/`LDFLAGS`/`CPPFLAGS` (pointing at `miniforge3`) get picked up by native gem extension builds (`bigdecimal`, `nokogiri`, etc.) and break them with duplicate-`LC_RPATH` or "compiler cannot create executables" errors. Run `bundle install` / `rbenv install` with those variables unset (or `conda deactivate` first) if this happens.

## Architecture

**Static site generator pipeline:**
- `_config.yml` — Main site configuration (author info, social links, collections, plugins)
- `_pages/` — Site pages (about, cv, publications, etc.) written in Markdown with YAML front matter
- `_publications/` — Individual publication entries (Markdown), rendered as a collection
- `_talks/` — Talk entries (Markdown), rendered as a collection
- `_portfolio/` — Software/package entries (Markdown), rendered as a collection and listed on the `/portfolio/` page (`_pages/portfolio.html`); front matter's `link` points to the project's GitHub repo
- `_layouts/` — Jekyll HTML layout templates (single, talk, archive)
- `_includes/` — Reusable Liquid template partials (header, footer, sidebar, SEO, scripts)
- `_sass/` — SCSS stylesheets
- `_data/` — YAML data files driving navigation (`navigation.yml`) and author metadata
- `images/` — Project/research images
- `files/` — Downloadable PDFs

**Content generation:** `markdown_generator/` contains Python/Jupyter notebooks that convert TSV data into Markdown files for publications and talks.

**Key configuration in `_config.yml`:** Collections (publications, talks, teaching, portfolio), author profile, social links, permalink structure, and plugin list. The site uses kramdown with GFM for Markdown rendering.

## Content Workflow

To add a publication or talk: either create a new Markdown file in the appropriate collection directory with proper YAML front matter, or add a row to `markdown_generator/publications.tsv` / `talks.tsv` and run the corresponding `.ipynb` (documented) or `.py` (plain) script to auto-generate Markdown files. `markdown_generator/PubsFromBib.ipynb` / `pubsFromBib.py` instead generate publication Markdown directly from a BibTeX file.

`talkmap.py` (or `talkmap.ipynb`) scrapes the `location` field from every file in `_talks/`, geocodes it, and regenerates the Leaflet cluster map assets in `talkmap/`; run it from inside `_talks/`.

Pages in `pages_not_included/` and `_drafts/` are excluded from the published site.
