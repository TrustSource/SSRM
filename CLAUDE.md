# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **TrustSource Shared Security Responsibility Model (SSRM)** — a documentation-only site describing the distribution of security responsibilities between TrustSource (provider) and its customers. It is built with MkDocs Material and deployed to GitHub Pages.

Site URL: https://trustsource.github.io/SSRM

## Build & Serve Commands

```bash
# Install dependencies
pip install zensical

# Local development server
zensical serve

# Build static site (output goes to ./site)
zensical build --clean
```

The project uses **Zensical** (an MkDocs-based tool) — not plain `mkdocs`. All build/serve commands use `zensical` instead of `mkdocs`.

## CI/CD

Pushes to `main` trigger `.github/workflows/ci.yml`, which builds with `zensical build --clean` and deploys to GitHub Pages via `actions/deploy-pages`.

## Repository Structure

- `mkdocs.yml` — Site configuration (theme, navigation, analytics, consent)
- `docs/` — All Markdown content pages (index.md, accessSecurity.md, dataIntegrity.md, artefactIntegrity.md, eos.md)
- `docs/assets/` — Images, CSS, and JS assets
- `.nojekyll` — Prevents GitHub Pages from processing with Jekyll

## Content Notes

- The site uses Material for MkDocs theme with light/dark mode toggle
- Google Fonts are disabled (`font: false`) for data privacy compliance
- Google Analytics is configured but uses a placeholder property ID (`G-xxx`)
- Content is licensed under CC-BY-SA-4.0
