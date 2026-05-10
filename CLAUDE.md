# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of self-contained web projects served via XAMPP on localhost. Most projects are a single HTML file; a few are directories with an `index.html`. There is no build, compile, or install step.

## Serving

XAMPP must be running (Apache). Access projects at:
```
http://localhost/sites/claude/<filename>.html       # single-file project
http://localhost/sites/claude/<directory>/          # directory project
```

## Current Projects

| Path | Description |
|------|-------------|
| `tictactoe.html` | Two-player Tic Tac Toe — dark UI, score tracking, win animations |
| `complyloft/index.html` | ComplyLoft homepage redesign — enterprise compliance automation platform |
| `argus/index.html` | Argus — niche trend-tracking landing page |
| `report/index.html` | Anthropic News Report (April 2026) |
| `firsttest/index.html` | Marketing Camelot — Doberman Dan |

## Repository Conventions

- Each project is a **single self-contained HTML file** — all CSS in `<style>`, all JS in `<script>`, no CDN/npm.
- The one exception: directory projects (`complyloft/`) use `index.html` inside a folder but are still self-contained.
- Commit messages follow Conventional Commits: `feat:`, `fix:`, `style:`, `refactor:`, `chore:`.
- Commit and push after every logical unit of work — never batch unrelated changes, never leave a session without pushing.

```bash
git add <file>
git commit -m "feat: description"
git push
```

## Design Systems

Projects each have their own design system. Do not carry tokens across projects.

### ComplyLoft (`complyloft/`)

Brand-accurate design system — do not deviate from these tokens:

| Token | Value |
|-------|-------|
| Font | Rubik (400/500/600/700/800) via Google Fonts |
| Primary accent | `#5910F8` (purple); hover `#6B24FF` |
| Accent light | `#F3EFFE` (optin bg, featured-card tint) |
| Dark / primary | `#040A17` |
| Border radius | **0px** on all containers, cards, inputs; **6px** on buttons only |
| Secondary button | `#040A17` bg · `#E8E0FD` text · `#E8E0FD` border |

Product: document auditing automation, PII redaction, accessible PDF remediation.

### Tictactoe (`tictactoe.html`)

| Token | Value |
|-------|-------|
| Background | `#0f0f13` |
| Surface | `#1a1a24` |
| Border | `#2a2a38` |
| X accent | `#7c6af7` (purple) |
| O accent | `#f97a6a` (coral) |
| Font | `'Segoe UI', system-ui, -apple-system, sans-serif` |
| Radius | Cards 16px · cells/inputs 12px |

## Frontend Design Workflow

For new or redesigned pages, invoke the `frontend-design` skill. It encodes:
- Full CSS custom property token system (`:root` block)
- Component patterns: buttons, cards (light/dark/featured), floating badge, sticky nav, grids, scroll reveal, email optin form
- Accessibility baseline (skip link, `aria-labelledby`, `role="list"`, `prefers-reduced-motion`)
- Pre-delivery checklist

The skill requires `ui-ux-pro-max` to be run first (with `--design-system`) to generate the design system when starting a new project.

## Accessibility Baseline (all projects)

- `<a href="#main-content" class="skip-link">` as first element in `<body>`
- `<main id="main-content">` wraps page content
- `aria-labelledby="heading-id"` on every `<section>`
- `aria-label` on every `<nav>` and `<footer>`
- No emoji as icons — inline SVG only (Heroicons / Lucide paths)
- `prefers-reduced-motion` handled on all animations
