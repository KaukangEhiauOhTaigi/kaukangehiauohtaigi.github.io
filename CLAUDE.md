# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

"狗公會曉學台語" (Learn Taigi in 9 Days) — a Hugo static documentation site for learning Taiwanese Hokkien, using the Docsy theme. Deployed to GitHub Pages at https://oh.taigi.info/.

## Build & Development Commands

```bash
npm install              # Install dependencies (first time / after changes)
npm run serve            # Local dev server at localhost:1313 (with drafts/future/expired)
npm run build            # Dev build (includes drafts/future/expired)
npm run build:production # Production build (minified, no drafts)
npm run build:preview    # Preview build (minified, for Netlify deploy previews)
npm run check:links      # Check for broken links (runs build first via precheck:links)
npm run clean            # Remove public/ and resources/
npm run test             # Alias for check:links
```

For local Docsy development (using a local clone): `npm run local -- npm run serve`

## Tech Stack

- **Hugo** (extended) v0.154.5 — static site generator, min version 0.151.0
- **Docsy** v0.13.0 — Hugo theme (imported as Go module from github.com/google/docsy)
- **Node.js 20** — build tooling (PostCSS, autoprefixer)
- **Go modules** — Hugo module dependency management (`go.mod`/`go.sum`)

## Content Structure

All content lives in `content/zh-tw/` (Traditional Chinese, primary and only active language):

- `chuliau/` — Main learning materials, subdivided into sections (khikoo, bunhian, haksip, siataibun, kauhak, chhutpan)
- `kauchai/` — Learning guide
- `chapchhe/` — Discussion/communication
- `bunchiunn/` — Related content

Content files are Markdown with TOML/YAML front matter. Hugo shortcodes are used throughout.

## Language Conventions

This is a Taiwanese Hokkien language education site. Content uses:
- Traditional Chinese characters (繁體中文)
- Taiwanese romanization systems (Pe̍h-ōe-jī / POJ, and Tâi-lô)
- Special combining characters for tone marks (e.g., o͘, e̍)
- i18n strings in `i18n/zh-tw.toml`

## Key Configuration

- `hugo.toml` — Main site config (base URL, language settings, Docsy params, Google Analytics, module imports)
- `assets/scss/` — Custom SCSS overrides
- `layouts/` — Custom Hugo template overrides
- `static/` — Static assets (fonts, favicons, images)

## CI/CD

GitHub Actions (`.github/workflows/deploy-github-pages.yml`):
- Triggers on push to `main`, PRs, and manual dispatch
- Builds with `npm run build:production`
- Deploys to GitHub Pages with custom domain `oh.taigi.info`

## Copyright

Content is for non-profit learning use only. No unauthorized copying. Author: Ngô͘ Hê-bí.
