# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based personal academic website for Germain Gauthier, hosted on GitHub Pages.

## Build Commands (WSL)

Bundler hangs on WSL due to the Windows filesystem. Use globally installed Jekyll instead:

```bash
# Install Jekyll globally (first time only)
gem install --user-install jekyll webrick

# Add to PATH (add this to ~/.bashrc)
export PATH="$HOME/.local/share/gem/ruby/3.2.0/bin:$PATH"

# Run local development server
JEKYLL_NO_BUNDLER_REQUIRE=1 jekyll serve

# Build the site (output to _site/)
JEKYLL_NO_BUNDLER_REQUIRE=1 jekyll build
```

Open `http://127.0.0.1:4000` to view locally.

## Architecture

- **Single-page site**: The main content is in `index.md` (Markdown with YAML front matter)
- **Layout**: `_layouts/default.html` is the sole template, using Liquid templating
- **Includes**: `_includes/` contains reusable HTML partials (head.html, signoff.html, pagination.html)
- **Configuration**: `_config.yml` contains site settings (title, URL, analytics)
- **Styling**: Custom CSS in `stylesheets/style.css` and `stylesheets/syntax.css`
- **Assets**: Images in `images/`, PDFs in `pdfs/`

## Deployment

The site deploys automatically to GitHub Pages on push to master. CI runs via GitHub Actions (`.github/workflows/ci.yaml`).
