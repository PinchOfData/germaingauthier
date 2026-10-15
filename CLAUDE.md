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

Open `http://127.0.0.1:4000/germaingauthier/` to view locally (the site uses `baseurl: /germaingauthier`).

## Architecture

- **Pages**: `index.md` (About), `papers.md`, `teaching.md`, `software.md` (Markdown with YAML front matter; `title` sets the browser tab title), plus `404.html`
- **Layout**: `_layouts/default.html` is the sole template, using Liquid templating
- **Includes**: `_includes/head.html` holds the `<title>`, meta description and Open Graph tags
- **Configuration**: `_config.yml` contains site settings (title, description, URL, baseurl)
- **Styling**: Custom CSS in `stylesheets/style.css`
- **Abstracts**: Working papers use an indented `<details><summary>Abstract</summary><p>…</p></details>` block inside the list item
- **Assets**: Images in `images/`, PDFs in `pdfs/`

## Deployment

The site deploys automatically to GitHub Pages on push to master. CI (`.github/workflows/ci.yaml`) builds the site with the same builder as GitHub Pages and checks internal links (PDFs, pages, images) with html-proofer.
