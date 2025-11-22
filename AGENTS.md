# AGENTS.md

This file provides guidance to AI agents (Claude Code, Cursor, Aider, etc.) when working with code in this repository.

## Project Overview

This is a personal website for Petr Kratochvíl built with MkDocs Material. The site runs at https://krato.cz/ and is automatically deployed to GitHub Pages from the `main` branch within 1 minute via CI/CD.

## Architecture

- **Framework**: MkDocs with Material theme
- **Content**: Markdown files in `/docs/` directory
- **Multilingual**: Czech (`cs/`) and English (`en/`) versions
- **Deployment**: Automated GitHub Actions workflow for GitHub Pages
- **Package Management**: Poetry for Python dependencies

## Development Commands

### Local Development
```bash
./dev                    # Start development server (mkdocs serve)
poetry run mkdocs serve  # Alternative way to serve locally
```

### Build and Deploy
```bash
poetry install           # Install dependencies
poetry run mkdocs build  # Build static site (output in ./site/)
```

The GitHub Actions workflow automatically handles deployment when pushing to `main`.

## Project Structure

```
/
├── docs/                 # Content source
│   ├── index.md         # Main homepage
│   ├── en/cv.md         # English CV
│   └── cs/cv.md         # Czech CV
├── overrides/           # Custom MkDocs theme overrides
├── assets/              # Static assets (referenced in docs)
├── mkdocs.yml           # MkDocs configuration
├── pyproject.toml       # Poetry configuration
└── dev                  # Development server script
```

## Content Guidelines

- Main content is bilingual (Czech and English)
- CV/resume content is in separate language-specific files
- The homepage (`docs/index.md`) serves as the main landing page
- All content uses standard Markdown with some HTML for styling buttons
- Links to external profiles and projects are maintained in the main index

## Deployment

- Automatic deployment via GitHub Actions on push to `main`
- Uses Poetry for dependency management
- Python 3.13 is the target version
- Built site is deployed to GitHub Pages
- Site URL: https://krato.cz/ (custom domain)