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
poetry install                    # Install dependencies
poetry run mkdocs build           # Build static site (output in ./site/)
poetry run mkdocs build --strict  # Pre-commit check: fails on warnings such as broken links
```

The GitHub Actions workflow automatically handles deployment when pushing to `main`. It does not run on pull requests, so a PR shows no checks and `mkdocs build --strict` is the only gate before merge. Its INFO message listing the `cv-old-*.md` files as not included in nav is expected.

## Project Structure

```
/
├── docs/                 # Content source
│   ├── index.md         # Main homepage
│   ├── cs/cv.md         # Czech CV
│   ├── en/cv.md         # English CV
│   ├── pl/cv.md         # Polish CV
│   └── assets/          # Static assets referenced in docs (common.css, QR codes)
├── overrides/           # Custom MkDocs theme overrides
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
- Dovednosti (Skills / Umiejętności) - one bullet per domain (Backend, LLM/AI, DevOps & Cloud, Linux, Cybersecurity, Web, Databáze); merged former "Oblasti zájmu" and "Klíčové dovednosti"
- Dovednosti v rozvoji (Skills in Development / Umiejętności w rozwoju) - single-line list of technologies currently being learned; Dovednosti must contain only proven skills, aspirational items belong here
- Pracovní zkušenosti (Work Experience) - with "AI specialista" at end of OSVČ entry
- Vzdělání (Education)
- Výzkum (Research)
- Absolvované kurzy (Completed Courses) - organized by categories:
  - AI Development
  - Cloud Architecture
  - Cybersecurity & Networking
- Probíhající kurzy (Ongoing Courses / Kursy w trakcie)
- Plánované kurzy (Planned Courses) - ends with a link to the learning repo for long-term considered courses
- Veřejné projekty (Public Projects) - with Claude Code Plugin Marketplace first, Kratokurz second
- Vybrané zkušenosti (Selected Experience / Wybrane doświadczenie)
- Zájmy (Interests)
- Vizitka QR kód (Business Card QR code)

**Important conventions:**
- Keep all three language versions structurally identical
- "AI specialista" / "AI specialist" / "specjalista AI" appears at end of OSVČ/Self-employed description
- LLM/AI skills include: "AI agents, RAG, fine-tuning, Prompt Engineering, AI Interaction Design"
- Course entries format: `**Course Name** (provider, year, hours, instructor: Name - Title, Company, [course](link)) – topics`
- Use full YouTube URLs in project links (not shortened versions)
- Employer and university names in Work Experience/Education link to their websites (default theme link styling on web; common.css prints all content links as plain text)
- Maintain DRY, SOLID, Scrum in "Selected Experience" section
- Course sections are a condensed copy of the README in [kratocz/learning](https://github.com/kratocz/learning), which is the source of truth: completed courses verbatim; ongoing and planned courses without payment details, phone-call notes or volatile run dates; long-term considered courses only via the link. Never name the company that pays for the courses, nor its people - write only "the company that pays for my courses"

## Deployment

- Automatic deployment via GitHub Actions on push to `main`
- Uses Poetry for dependency management
- Python 3.13 is the target version
- Built site is deployed to GitHub Pages
- Site URL: https://krato.cz/ (custom domain)