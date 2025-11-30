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

- Main content is multilingual (Czech, English, Polish)
- CV/resume content is in separate language-specific files
- The homepage (`docs/index.md`) serves as the main landing page
- All content uses standard Markdown with some HTML for styling buttons
- Links to external profiles and projects are maintained in the main index

### CV Structure and Versions

Each language has a CV file:
- **cv.md** - Concise one-page format (~100 lines) with essential information

**Language-specific files:**
- `docs/cs/cv.md` (Czech)
- `docs/en/cv.md` (English)
- `docs/pl/cv.md` (Polish)

**Archived files (read-only, do not modify):**
- `docs/cs/cv-old-2025-11-30.md`
- `docs/en/cv-old-2025-11-30.md`
- `docs/pl/cv-old-2025-11-30.md`

**Key sections in cv.md:**
- Header with contact info (3 bullet points)
- Aktuální verze CV (Current CV versions) - single line with language links
- Profily (Profiles) - split into "IT development" and "Other"
- Oblasti zájmu (Areas of Interest) - structured bullet list
- Pracovní zkušenosti (Work Experience) - with "AI specialista" at end of OSVČ entry
- Klíčové dovednosti (Key Skills)
- Absolvované kurzy (Completed Courses) - organized by categories:
  - AI Development
  - AI Prompt Engineering
  - Cloud Architecture
  - Cybersecurity & Networking
- Plánované kurzy (Planned Courses)
- Veřejné projekty (Public Projects) - with Kratokurz first
- Další zkušenosti (Additional Experience)
- Zájmy (Interests)
- Vizitka QR kód (Business Card QR code)

**Important conventions:**
- Keep all three language versions structurally identical
- "AI specialista" / "AI specialist" / "specjalista AI" appears at end of OSVČ/Self-employed description
- LLM/AI interests include: "AI agents, RAG, fine-tuning, Prompt Engineering, AI Interaction Design"
- Course entries format: `**Course Name** (provider, year, hours, instructor: Name - Title, Company, [course](link)) – topics`
- Use full YouTube URLs in project links (not shortened versions)
- Maintain DRY, SOLID, Scrum in "Additional Experience" section

## Deployment

- Automatic deployment via GitHub Actions on push to `main`
- Uses Poetry for dependency management
- Python 3.13 is the target version
- Built site is deployed to GitHub Pages
- Site URL: https://krato.cz/ (custom domain)